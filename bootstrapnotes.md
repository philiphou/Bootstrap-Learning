### 容器
    1. 流体容器： class="container-fluid"
    2. 固定容器  class = "container"
        阈值： 媒体查询的断点：
            -  min 1200 (lg 大型屏幕)   width: 1170 （1140 +槽宽）
            -  min 992 (md 中型屏幕) and max 1200   width: 970 (940 +槽宽)
            -  min 768 （sm 平板)  and max 992  width: 750 （720+ 槽宽 gutter-width)
            -  max 768 (xs 移动手机): width: auto; (小于768， width 是 auto, 变成流体容器)
    3. 栅格系统；  默认一共分为12列；
            -   class ="row" 行
            -   class="col-lg-10" 列 占比：10/12
    4.  栅格源码分析：
        - 流体容器&固定容器的公共样式： 
            margin-right:  auto;
            margin-left:auto;
            padding-left:15px;
            padding-right:15px;
        - 固定容器有自己的特定样式： 有媒体查询区分；顺序不可变；
           @media (min-width: @screen-sm-min){
               width:@container-sm;
           }
             @media (min-width: @screen-md-min){
               width:@container-md;
           }
             @media (min-width: @screen-lg-min){
               width:@container-lg;
           }
        - 行：
            margin-left:cell((@gutter/-2))  // 槽宽是30px;
            margin-right:floor((@gutter/-2))
        - 列：
            .make-grid-colums();
            // bootstrap 里面，样式设置是移动优先；
            .make-grids(xs)
            @media (min-width:@screen-sm-min){
                .make-grid(sm)
            }
            @media (min-width:@screen-mdmin){
                .make-grid(md)
            }
            @media (min-width:@screen-lg-min){
                .make-grid(lg)
            }
        - 列排序: col-lg-pull/push-3
        - 响应式布局： visibility-xs; hidden-xs
        - 栅格盒模型设计的精妙之处
            * 容器上两边有15px 的padding， 
            * 行两边具有-15px 的 margin;
            * 列两边具有 15px 的 padding
            * 为了维护槽宽的规则，列两边必须要有15px 的padding，
            * 为了防止列里面套行出现槽宽累加， 同时行两边具有-15px的margin 也是必须的，
            * 为了把行露出的-15px margin 给包括住；同时容器上加15px padding 

        - 复习： 
            1. less 的继承
                #test{
                &:extend(.father)
                }
                或者： #test:extend(.father){

                }
                继承实质是将.father 选择器和 #test 选择器组合成一个选择器，声明块使用 .father 的
                 all: 继承所有和 .father 相关的声明块；
                 切记父类不能定义成混合；（继承不灵活但性能高，混合灵活但是性能低）
            2. less 的避免编译
                ~"不会被编译的内容"
                变量在less中属于块级作用域，延迟加载；
            3. bootstrap 的栅格系统，源码分析
                流体容器 （width：auto)  padding:15px
                固定容器： 阈值 xs sm md lg 对应的阈值： 768， 992， 1200; padding:15px;
                行：两侧 -15 px 的margin
                列: 
                    公共样式： 两侧有15px的 padding； 
                    float 
                    width: 1~12
                    left right: 0~12; 0: auto (列排序用)
                    margin-left; 0~12 （列偏移用）浮动后用 Offset: col-lg-offset-4: 表示向右偏移4列；
            4. 列排序
                注意阈值上样式的设置不能跳跃；




