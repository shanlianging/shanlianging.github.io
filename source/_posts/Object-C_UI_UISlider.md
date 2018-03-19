
---
title: Object-C_UI_UISlider
date: 2018/3/08 23:23:20
categories:
- Object-C
- UI
---
# UISlider
#### 1、继承

**父类暴露的方法和属性都可以使用**

```objc
NS_CLASS_AVAILABLE_IOS(2_0) __TVOS_PROHIBITED @interface UISlider : UIControl <NSCoding>
```

#### 2、创建
```objc
UISlider *sl_slider = [[UISlider alloc] initWithFrame:CGRectMake(0, 0, 300, 34)];   // 这样创建，高度是固定的，改变高度只能改变点击相应范围，改变不了大小，如果需要改变大小，需要重写视图
sl_slider.center = self.view.center;
[self.view addSubview:sl_slider];

```
**重写，但是不好调试，其实尽量还是给图片，或者自定义**
```objc
// 设置最大值
- (CGRect)maximumValueImageRectForBounds:(CGRect)bounds
{
return CGRectMake(0, 0, CGRectGetWidth(self.frame)/ 2, CGRectGetHeight(self.frame) / 2);
}
// 设置最小值
- (CGRect)minimumValueImageRectForBounds:(CGRect)bounds
{
return CGRectMake(0, 0, CGRectGetWidth(self.frame), CGRectGetHeight(self.frame));
}

// 控制slider的宽和高，这个方法才是真正的改变slider滑道的高的
- (CGRect)trackRectForBounds:(CGRect)bounds
{
return CGRectMake(0, 0, CGRectGetWidth(self.frame), CGRectGetHeight(self.frame));
}

// 改变滑块的触摸范围
- (CGRect)thumbRectForBounds:(CGRect)bounds trackRect:(CGRect)rect value:(float)value
{
return CGRectInset([super thumbRectForBounds:bounds trackRect:rect value:value], 10, 10);
}
```
#### 3、属性
```objc

// 滑块颜色
sl_slider.minimumTrackTintColor = [UIColor redColor];  // 划过区域的颜色
sl_slider.maximumTrackTintColor = [UIColor yellowColor];   未划过区域的颜色
sl_slider.thumbTintColor = [UIColor blackColor];   //设置滑块的颜色

// 设置滑块的图片
[sl_slider setThumbImage:[UIImage imageNamed:@"滑块"] forState:UIControlStateNormal];

// 设置滑块的视图
sl_slider.minimumValueImage = [UIImage imageNamed:@"声音"];    // 设置滑块左视图
sl_slider.maximumValueImage = [UIImage imageNamed:@"快进"];    // 设置滑块右视图

// 设置滑块的值
sl_slider.minimumValue = 0;    // 设置最小值
sl_slider.maximumValue = 100.0;    // 设置最大值
sl_slider.value = 50;   // 当前值-位置
```

#### 4、给滑块添加方法
```objc
// 添加方法
[slider addTarget:self action:@selector(sliderAction:) forControlEvents:UIControlEventValueChanged];
// 方法
- (void)sliderAction:(UISlider *)slider {
}
```

#### 5、其他属性和方法
```objc

- (void)setThumbImage:(nullable UIImage *)image forState:(UIControlState)state;
- (void)setMinimumTrackImage:(nullable UIImage *)image forState:(UIControlState)state;
- (void)setMaximumTrackImage:(nullable UIImage *)image forState:(UIControlState)state;

- (nullable UIImage *)thumbImageForState:(UIControlState)state;
- (nullable UIImage *)minimumTrackImageForState:(UIControlState)state;
- (nullable UIImage *)maximumTrackImageForState:(UIControlState)state;

@property(nullable,nonatomic,readonly) UIImage *currentThumbImage;
@property(nullable,nonatomic,readonly) UIImage *currentMinimumTrackImage;
@property(nullable,nonatomic,readonly) UIImage *currentMaximumTrackImage;

// lets a subclass lay out the track and thumb as needed
- (CGRect)minimumValueImageRectForBounds:(CGRect)bounds;
- (CGRect)maximumValueImageRectForBounds:(CGRect)bounds;
- (CGRect)trackRectForBounds:(CGRect)bounds;
- (CGRect)thumbRectForBounds:(CGRect)bounds trackRect:(CGRect)rect value:(float)value;

```





