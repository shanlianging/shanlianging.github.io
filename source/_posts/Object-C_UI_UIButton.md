
---
title: Object-C_UI_UIButton
date: 2018/3/06 11:28:20
categories:
- Object-C
- UI
---
# UIButton
#### 1、继承
**父类暴露的方法和属性都可以使用**

```objc
NS_CLASS_AVAILABLE_IOS(2_0) @interface UIButton : UIControl <NSCoding>
```

#### 2、初始化

```objc

//    UIButton *button = [[UIButton alloc] initWithFrame:CGRectMake(0, 0, 100, 100)];
//    [self.view addSubview:button];

// 或者
UIButton *button = [UIButton buttonWithType:UIButtonTypeCustom];
button.frame = CGRectMake(0, 0, 100, 100);
[self.view addSubview:button];

```

```objc
typedef NS_ENUM(NSInteger, UIButtonType) {
UIButtonTypeCustom = 0,                         // no button type
UIButtonTypeSystem NS_ENUM_AVAILABLE_IOS(7_0),  // standard system button

UIButtonTypeDetailDisclosure,
UIButtonTypeInfoLight,
UIButtonTypeInfoDark,
UIButtonTypeContactAdd,

UIButtonTypePlain API_AVAILABLE(tvos(11.0)) API_UNAVAILABLE(ios, watchos), // standard system button without the blurred background view

UIButtonTypeRoundedRect = UIButtonTypeSystem   // Deprecated, use UIButtonTypeSystem instead
};
```

#### 3、设置文字标题
```objc
// 普通状态下：UIControlStateNormal
[button setTitle:@"普通" forState:UIControlStateNormal];
// 高亮状态下：UIControlStateHighlighted
[button setTitle:@"高亮" forState:UIControlStateHighlighted];
button.titleLabel.textAlignment = NSTextAlignmentCenter;    // 文字对齐方式
button.titleLabel.font = [UIFont systemFontOfSize:15.0];    // 文字大小
```

```objc
typedef NS_OPTIONS(NSUInteger, UIControlState) {
UIControlStateNormal       = 0,
UIControlStateHighlighted  = 1 << 0,                  // used when UIControl isHighlighted is set
UIControlStateDisabled     = 1 << 1,
UIControlStateSelected     = 1 << 2,                  // flag usable by app (see below)
UIControlStateFocused NS_ENUM_AVAILABLE_IOS(9_0) = 1 << 3, // Applicable only when the screen supports focus
UIControlStateApplication  = 0x00FF0000,              // additional flags available for application use
UIControlStateReserved     = 0xFF000000               // flags reserved for internal framework use
};
```
#### 4、设置图片标题
```objc
// 普通状态下：UIControlStateNormal
[button setImage:[UIImage imageNamed:@"a.png"] forState:UIControlStateNormal];
// 高亮状态下：UIControlStateHighlighted
[button setImage:[UIImage imageNamed:@"b.png"] forState:UIControlStateHighlighted];
```
#### 5、其他属性
```objc
button.contentEdgeInsets = UIEdgeInsetsMake(10, 10, 10, 10);
button.adjustsImageWhenHighlighted = NO;    // 在Highlight状态时是否调整

@property(nonatomic)          UIEdgeInsets contentEdgeInsets UI_APPEARANCE_SELECTOR; // default is UIEdgeInsetsZero. On tvOS 10 or later, default is nonzero except for custom buttons.
@property(nonatomic)          UIEdgeInsets titleEdgeInsets;                // default is UIEdgeInsetsZero
@property(nonatomic)          BOOL         reversesTitleShadowWhenHighlighted; // default is NO. if YES, shadow reverses to shift between engrave and emboss appearance
@property(nonatomic)          UIEdgeInsets imageEdgeInsets;                // default is UIEdgeInsetsZero

```
#### 6、给按钮添加方法
```objc
// text为添加的方法名字
// UIControlEventTouchUpInside：按钮点击进去才会触发，移走不会触发
[button addTarget:self action:@selector(sl_buttonAction:) forControlEvents:UIControlEventTouchUpInside];

- (void)sl_buttonAction:(UIButton *)button {

}

```

```objc
typedef NS_OPTIONS(NSUInteger, UIControlEvents) {
UIControlEventTouchDown                                         = 1 <<  0,      // on all touch downs
UIControlEventTouchDownRepeat                                   = 1 <<  1,      // on multiple touchdowns (tap count > 1)
UIControlEventTouchDragInside                                   = 1 <<  2,
UIControlEventTouchDragOutside                                  = 1 <<  3,
UIControlEventTouchDragEnter                                    = 1 <<  4,
UIControlEventTouchDragExit                                     = 1 <<  5,
UIControlEventTouchUpInside                                     = 1 <<  6,
UIControlEventTouchUpOutside                                    = 1 <<  7,
UIControlEventTouchCancel                                       = 1 <<  8,

UIControlEventValueChanged                                      = 1 << 12,     // sliders, etc.
UIControlEventPrimaryActionTriggered NS_ENUM_AVAILABLE_IOS(9_0) = 1 << 13,     // semantic action: for buttons, etc.

UIControlEventEditingDidBegin                                   = 1 << 16,     // UITextField
UIControlEventEditingChanged                                    = 1 << 17,
UIControlEventEditingDidEnd                                     = 1 << 18,
UIControlEventEditingDidEndOnExit                               = 1 << 19,     // 'return key' ending editing

UIControlEventAllTouchEvents                                    = 0x00000FFF,  // for touch events
UIControlEventAllEditingEvents                                  = 0x000F0000,  // for UITextField
UIControlEventApplicationReserved                               = 0x0F000000,  // range available for application use
UIControlEventSystemReserved                                    = 0xF0000000,  // range reserved for internal framework use
UIControlEventAllEvents                                         = 0xFFFFFFFF
};
```





