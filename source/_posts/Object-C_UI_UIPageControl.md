
---
title: Object-C_UI_UIPageControl
date: 2018/3/14 20:18:24
categories:
- Object-C
- UI
---
# UIPageControl
#### 1、继承

**父类暴露的方法和属性都可以使用**

```objc
NS_CLASS_AVAILABLE_IOS(2_0) @interface UIPageControl : UIControl
```

#### 2、创建
```objc
UIPageControl *sl_pageControl = [[UIPageControl alloc] initWithFrame:CGRectMake(0, 0, 100, 50)];
sl_pageControl.center = self.view.center;
sl_pageControl.backgroundColor = [UIColor brownColor];
[self.view addSubview:sl_pageControl];
```
#### 3、常用属性
```objc
sl_pageControl.numberOfPages = 5;   // 设置圆点个数

// 设置圆点的颜色
sl_pageControl.currentPageIndicatorTintColor = [UIColor redColor];  // 选中颜色
sl_pageControl.pageIndicatorTintColor = [UIColor greenColor];  // 未选中的颜色

sl_pageControl.currentPage = 3;    // 设置默认显示的圆点位置(默认从0开始)

sl_pageControl.hidesForSinglePage = YES;    // 当圆点个数仅省一个的时候，设置是否隐藏

```

#### 4、其他属性或方法
```objc
@property(nonatomic) BOOL defersCurrentPageDisplay;    // if set, clicking to a new page won't update the currently displayed page until -updateCurrentPageDisplay is called. default is NO
- (void)updateCurrentPageDisplay;                      // update page display to match the currentPage. ignored if defersCurrentPageDisplay is NO. setting the page value directly will update immediately

- (CGSize)sizeForNumberOfPages:(NSInteger)pageCount;   // returns minimum size required to display dots for given page count. can be used to size control if page count could change
```




