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


