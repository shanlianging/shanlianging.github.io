
---
title: Object-C_UI_UISwitch
date: 2018/3/09 20:13:18
categories:
- Object-C
- UI
---
# UISwitch
#### 1、继承

**父类暴露的方法和属性都可以使用**

```objc
NS_CLASS_AVAILABLE_IOS(2_0) __TVOS_PROHIBITED @interface UISwitch : UIControl <NSCoding>
```

#### 2、创建

```objc
UISwitch *sl_switch = [[UISwitch alloc] initWithFrame:CGRectMake(0, 0, 100, 100)];  // 这样创建，大小固定，如果需要改变大小，需要重写视图
sl_switch.center = self.view.center;
[self.view addSubview:sl_switch];
```

#### 3、属性

```objc
sl_switch.tintColor = [UIColor redColor]; // 设置动画切换的颜色（边框颜色也会跟着改变）
sl_switch.onTintColor = [UIColor magentaColor];   // 打开状态显示的颜色
sl_switch.thumbTintColor = [UIColor blackColor];  // 滑块的颜色
[sl_switch setOn:YES];    // 设置滑块的开关状态
NSLog(@"%d",sl_switch.isOn);  获取滑块的状态
```

#### 4、其他属性和方法
```objc
@property(nullable, nonatomic, strong) UIImage *onImage NS_AVAILABLE_IOS(6_0) UI_APPEARANCE_SELECTOR;
@property(nullable, nonatomic, strong) UIImage *offImage NS_AVAILABLE_IOS(6_0) UI_APPEARANCE_SELECTOR;

- (void)setOn:(BOOL)on animated:(BOOL)animated; // does not send action
```




