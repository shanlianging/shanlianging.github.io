
---
title: Object-C_UI_UIImageVIew和动图
date: 2018/3/07 20:40:15
categories:
- Object-C
- UI
---
# UIImageVIew和动图
#### 1、继承

**父类暴露的方法和属性都可以使用**

```objc
NS_CLASS_AVAILABLE_IOS(2_0) @interface UIImageView : UIView
```

#### 2、创建
```obcj
UIImageView *sl_imageView = [[UIImageView alloc] initWithFrame:CGRectMake(0, 0, 100, 100)];
sl_imageView.image = [UIImage imageNamed:@"图片"];
[self.view addSubview:sl_imageView];
```
#### 3、创建动图
```objc
// 1、创建一个可变数组
NSMutableArray *sl_imagesArray = [@[] mutableCopy];
// 2、循环添加照片名字到数组中
for (int i = 1; i <= 12; i ++) {
// 准备图片名称
NSString *picName = [NSString stringWithFormat:@"%d.jpg",i];
// 根据名称创建图片
UIImage *image = [UIImage imageNamed:picName];
// 添加到数组
[sl_imagesArray addObject:image];
}
// 3、创建图片视图
UIImageView *sl_imgView = [[UIImageView alloc] initWithFrame:CGRectMake(100, 100, 200, 300)];
sl_imgView.backgroundColor = [UIColor redColor];
// 4、设置图片
sl_imgView.animationImages = sl_imagesArray;
// 5、设置播放持续时间
sl_imgView.animationDuration = 0.8;
// 6、设置重复次数
sl_imgView.animationRepeatCount = 99999;
// 7、开始动画
[sl_imgView startAnimating];
```
#### 4、属性
```objc
// 按比例不缩放充满
sl_imgView.contentMode = UIViewContentModeScaleAspectFill; // 图片的充满方式（枚举）
* iOS的控件中，绝大多数都是默认开启用户交互的，除了UILable和UIImageView等...*
[sl_imgView setUserInteractionEnabled:YES]; // 设置设置用户交互的状态，YES为开启，NO为关闭
```

```objc
typedef NS_ENUM(NSInteger, UIViewContentMode) {
UIViewContentModeScaleToFill,
UIViewContentModeScaleAspectFit,      // contents scaled to fit with fixed aspect. remainder is transparent
UIViewContentModeScaleAspectFill,     // contents scaled to fill with fixed aspect. some portion of content may be clipped.
UIViewContentModeRedraw,              // redraw on bounds change (calls -setNeedsDisplay)
UIViewContentModeCenter,              // contents remain same size. positioned adjusted.
UIViewContentModeTop,
UIViewContentModeBottom,
UIViewContentModeLeft,
UIViewContentModeRight,
UIViewContentModeTopLeft,
UIViewContentModeTopRight,
UIViewContentModeBottomLeft,
UIViewContentModeBottomRight,
};
```


#### 5、图片文件路径并创建
```objc
// 获取
NSString *path = [[NSBundle mainBundle] pathForResource:@"1" ofType:@"jpg"];
// 创建
UIImage *image = [UIImage imageWithContentsOfFile:path];
```





