
---
title: Object-C_UI_UILabel
date: 2018/3/06 11:54:14
categories:
- Object-C
- UI
---
# UILabel
#### 1、继承
**父类暴露的方法和属性都可以使用**
```objc

NS_CLASS_AVAILABLE_IOS(2_0) @interface UILabel : UIView <NSCoding, UIContentSizeCategoryAdjusting>

```
#### 2、初始化
```objc
UILabel *sl_label = [[UILabel alloc] initWithFrame:CGRectMake(0, 0, 100, 50)];
sl_label.backgroundColor = [UIColor redColor];
[self.view addSubview:sl_label];
```

#### 3、常用属性
```objc
sl_label.text = @"文字";    // 设置文字
sl_label.textColor = [UIColor redColor];    // 设置字体颜色
// 设置字体大小（系统默认17.0），单位和开发尺寸一致
sl_label.font = [UIFont systemFontOfSize:30.0]; // 正常
sl_label.font = [UIFont boldSystemFontOfSize:30.0]; // 加粗
// 设置字体位置
sl_label.textAlignment = NSTextAlignmentCenter;    // 居中
```

```objc
/* Values for NSTextAlignment */
typedef NS_ENUM(NSInteger, NSTextAlignment) {
NSTextAlignmentLeft      = 0,    // Visually left aligned
#if TARGET_OS_IPHONE
NSTextAlignmentCenter    = 1,    // Visually centered
NSTextAlignmentRight     = 2,    // Visually right aligned
#else /* !TARGET_OS_IPHONE */
NSTextAlignmentRight     = 1,    // Visually right aligned
NSTextAlignmentCenter    = 2,    // Visually centered
#endif
NSTextAlignmentJustified = 3,    // Fully-justified. The last line in a paragraph is natural-aligned.
NSTextAlignmentNatural   = 4,    // Indicates the default alignment for script
} NS_ENUM_AVAILABLE_IOS(6_0);
```

#### 4、设置文字行的自适应，自动换行
```objc
// 1、设置行数
sl_label.numberOfLines = 0;
// 2、文字结尾状态
sl_label.lineBreakMode = NSLineBreakByCharWrapping;
```

#### 5、 其他属性
```objc
// 设置文字的格式：缩进、行间距等
@property(nullable, nonatomic,copy)   NSAttributedString *attributedText NS_AVAILABLE_IOS(6_0);  // default is nil

```





