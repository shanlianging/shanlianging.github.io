
---
title: Object-C_UI_UISegmentedControl
date: 2018/3/14 20:28:19
categories:
- Object-C
- UI
---
# UISegmentedControl
#### 1、继承

**父类暴露的方法和属性都可以使用**

```objc
NS_CLASS_AVAILABLE_IOS(2_0) @interface UISegmentedControl : UIControl <NSCoding>
```

#### 2、创建
```objc
NSArray *sl_array = @[@"第一页",@"第二页",@"第三页",@"第四页"];
UISegmentedControl *sl_segmentedControl = [[UISegmentedControl alloc] initWithItems:sl_array];
sl_segmentedControl.center = self.view.center;
[self.view addSubview:sl_segmentedControl];
```
#### 3、常用属性
```objc
sl_segmentedControl.backgroundColor = [UIColor grayColor];  // 设置背景色（小瑕疵：自己受到设置圆角的影响）
sl_segmentedControl.tintColor = [UIColor redColor]; // 着色（边框、文字、选中后的颜色）

// 修改内容
sl_segmentedControl.selectedSegmentIndex = 0;   //设置选中标题
[sl_segmentedControl setTitle:@"未完待续" forSegmentAtIndex:3]; // 修改某一个标题
NSString *string = [sl_segmentedControl titleForSegmentAtIndex:3];  // 获取某一个下标的内容

[sl_segmentedControl insertSegmentWithTitle:@"插入分段" atIndex:3 animated:YES];  //  插入分段

[sl_segmentedControl removeSegmentAtIndex:2 animated:YES];  // 移除分段

sl_segmentedControl.apportionsSegmentWidthsByContent = YES; // 自动为内容分配所占区域的大小

```


#### 4、为分段控制器添加方法
```objc
// 1、添加方法
[sl_segmentedControl addTarget:self action:@selector(sl_changePage:) forControlEvents:UIControlEventValueChanged];
// 2、方法
- (void)sl_changePage:(UISegmentedControl *)seg {
// 如果选择第二个分段
if (seg.selectedSegmentIndex == 1) {
// 移除第一个页面
[self.firstView removeFromSuperview];
// 插入第二个页面（下标为0，防止覆盖分段控制器）
[self.view insertSubview:self.secondView atIndex:0];
}else {
// 移除第二个页面
[self.secondView removeFromSuperview];
[self.view insertSubview:self.firstView atIndex:0];
}
```

#### 5、其他属性或方法
```objc

- (void)setTitle:(nullable NSString *)title forSegmentAtIndex:(NSUInteger)segment;      // can only have image or title, not both. must be 0..#segments - 1 (or ignored). default is nil
- (nullable NSString *)titleForSegmentAtIndex:(NSUInteger)segment;

- (void)setImage:(nullable UIImage *)image forSegmentAtIndex:(NSUInteger)segment;       // can only have image or title, not both. must be 0..#segments - 1 (or ignored). default is nil
- (nullable UIImage *)imageForSegmentAtIndex:(NSUInteger)segment;

- (void)setWidth:(CGFloat)width forSegmentAtIndex:(NSUInteger)segment;         // set to 0.0 width to autosize. default is 0.0
- (CGFloat)widthForSegmentAtIndex:(NSUInteger)segment;

- (void)setContentOffset:(CGSize)offset forSegmentAtIndex:(NSUInteger)segment; // adjust offset of image or text inside the segment. default is (0,0)
- (CGSize)contentOffsetForSegmentAtIndex:(NSUInteger)segment;

- (void)setEnabled:(BOOL)enabled forSegmentAtIndex:(NSUInteger)segment;        // default is YES
- (BOOL)isEnabledForSegmentAtIndex:(NSUInteger)segment;

/* For adjusting the position of a title or image within the given segment of a segmented control.
*/
- (void)setContentPositionAdjustment:(UIOffset)adjustment forSegmentType:(UISegmentedControlSegment)leftCenterRightOrAlone barMetrics:(UIBarMetrics)barMetrics NS_AVAILABLE_IOS(5_0) UI_APPEARANCE_SELECTOR;
- (UIOffset)contentPositionAdjustmentForSegmentType:(UISegmentedControlSegment)leftCenterRightOrAlone barMetrics:(UIBarMetrics)barMetrics NS_AVAILABLE_IOS(5_0) UI_APPEARANCE_SELECTOR;

```




