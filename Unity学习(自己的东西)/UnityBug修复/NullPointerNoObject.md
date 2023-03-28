+ 首先我想表明,如果是某个Object 没有赋值的问题引起的空引用,这个自然很简单解决
+ 我所遇到的都是两个类之间的互相实例化,他们之间的往往导致空指针(往往我想把一个类面对外面,另一个类因为是组成类,所以不像外面展示)
+ 问题的本质在于,因为Playabled的特殊性,打乱了初始化顺序,同时因为不能使用Awake函数解决问题
  + 首先关于这种写法,下面的确是可行的,但是有特殊情况(第一种写法)
```C#
+ 外面的写法
AnimationAn animationAn =new AnimAdapter(PGraph, animator);
// 因为PrepareFrame她会自动调用渲染动画, 这里animationMix就一直给我报空指针,但是你看他们的实例化顺序完全没有问题,
// 首先初始化完AnimAdapter,然后是AnimationMix ,所以初始化没有问题,不可能去报错啊!
// 跟我的想法一样,Play里面的调用没有任何问题,问题出在AnimAdapter 初始化时间和PrepareFrame运行时间抢谁先,很显然PrepareFrame胜利了,所以给我报空指针
// 对于不是抢先后顺序的类,这样写没有任何问题,而且只提供了一个窗口,非常好


+ 内部类的关系
        public class AnimAdapter : PlayableBehaviour, AnimationAn
    {
        AnimationMix animationMix;   
        public AnimAdapter()
        {

        }
        public AnimAdapter(PlayableGraph PGraph, Animator animator)
        {
            animationMix = new AnimAdapter(PGraph, animator);

        }
        // 两个完全不同的函数 Play和PrepareFrame
          public void Play(AnimationClip clip1)
        {
            animationMix.AddInput(clip1.name, clip1);
            animationMix.Play(clip1.name);


        }
           public override void PrepareFrame(Playable playable, FrameData info)
        {
            base.PrepareFrame(playable, info);
            animationMix?.Excute(playable, info);

        }
    }

    public class AnimationMix{
        public AnimationMix(PlayableGraph PGraph, Animator animator)
        {
            Debug.Log($"卧槽");
            pGraph = PGraph;
            dicAnimIndexClip = new Dictionary<string, int>();
            animMixPlay = AnimationMixerPlayable.Create(pGraph, 8);
            animationPlayableOutput = AnimationPlayableOutput.Create(pGraph, "Animation1234", animator);
            scriptPlayable = ScriptPlayable<AnimAdapter>.Create(pGraph, 1);
            pGraph.Connect(animMixPlay, 0, scriptPlayable, 0);
            animationPlayableOutput.SetSourcePlayable(scriptPlayable);

        }

    }

```

+ 改正写法(既然你抢时间快慢,那么我就让空指针对象,比你类还先初始化,不就没问题了吗)
```C#
// 外面的写法 
            AnimationMix animationMix = new AnimationMix(playableGraph, animator);
            animationAn = new AnimAdapter(animationMix);

// 内部写法 这样写AnimationMix永远先初始化,自然空引用问题
    public AnimAdapter(AnimationMix AnimationMixVar)
        {
            animationMix = AnimationMixVar;

        }
```


+ 写法出现了问题(前面的有一个问题就是AnimationMix 内部创建的AnimAdatpter 和外面创建的不是同一个)
  + 所以Script<AnimAdapter>.Create(参数一 PlayableGraph, AnimAdapter) 这里可以接受一个AnimAdapter,而不是原来以为的只能在内部创建,可以接受外部的实例化类,非常好,依然无法摆脱实例化空指针问题
  + 把互相依赖的部分分开写 ,先让AnmiAdapter 拿到animationMix ,如果把init的部分放在里面,因为init需要AnimAdapter的实例,所以互相实例化需要了,就报空指针了,你需要给出一个合理的实例化过程, 最终PrepareFrame不会报错了.
```C#
 public class AnimAdapter : PlayableBehaviour, AnimationAn
    {
 public AnimAdapter(PlayableGraph PGraph, Animator animator)
        {
            animationMix = new AnimationMix(PGraph, animator);
            animationMix.init(this);  
        }
    }
    public class AnimationMix{
    
     public AnimationMix(PlayableGraph PGraph, Animator animator)
        {
            Debug.Log($"卧槽");
            pGraph = PGraph;
            dicAnimIndexClip = new Dictionary<string, int>();
            dicAnimationClipPlay = new Dictionary<string, AnimationClipPlayable>();
            animMixPlay = AnimationMixerPlayable.Create(pGraph, 8);
            animationPlayableOutput = AnimationPlayableOutput.Create(pGraph, "Animation1234", animator);
        }
        public void init(AnimAdapter animAdapter)
        {
            scriptPlayable = ScriptPlayable<AnimAdapter>.Create(pGraph, animAdapter,1);
            pGraph.Connect(animMixPlay, 0, scriptPlayable, 0);
            animationPlayableOutput.SetSourcePlayable(scriptPlayable);

        }
    }     
```