
---
title: Object-C_UI_UIView
date: 2018/3/06 11:07:10
categories:
- Object-C
- UI
---
# UIView
#### 1、继承

**父类暴露的方法和属性都可以使用**

```objc
NS_CLASS_AVAILABLE_IOS(2_0) @interface UIView : UIResponder <NSCoding, UIAppearance, UIAppearanceContainer, UIDynamicItem, UITraitEnvironment, UICoordinateSpace, UIFocusItem, CALayerDelegate>
```

#### 2、创建

```objc
UIView *sl_view = [[UIView alloc] initWithFrame:CGRectMake(0, 0, 100, 100)];
[self.view addSubview:sl_view];

```
#### 3、属性

```objc

sl_view.backgroundColor = [UIColor redColor];
sl_view.center = self.view.center;
sl_view.tag = 101;
sl_view.clipsToBounds = YES;    // 子类多余被切掉
```

#### 4、坐标转换

```objc

- (CGPoint)convertPoint:(CGPoint)point toView:(nullable UIView *)view;  // 转换到其他视图上（点）
- (CGPoint)convertPoint:(CGPoint)point fromView:(nullable UIView *)view;  // 从其他视图上转过来（点）
- (CGRect)convertRect:(CGRect)rect toView:(nullable UIView *)view; // 转换到其他视图上（范围）
- (CGRect)convertRect:(CGRect)rect fromView:(nullable UIView *)view; // 从其他视图上转过来（范围）


```

#### 5、设置阴影
```objc
// 设置阴影颜色
sl_view.layer.shadowColor = RGB_HEX(0xe0e7ee).CGColor;
sl_view.layer.shadowOpacity = 1;
sl_view.layer.shadowOffset = CGSizeMake(1, 4);

```

#### 6、设置圆角
```objc
sl_view.layer.cornerRadius = 10;    // 圆角数
sl_view.layer.masksToBounds = YES;  // 多余切掉

```





