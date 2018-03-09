
---
title: Object-C_UI_根视图控制器和tag值
date: 2018/2/26 17:38:25
categories:
- Object-C
- UI
---
# 根视图控制器和tag值
#### 1、初始创建根试图控制器
```objc
    self.window = [[UIWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
    [self.window setBackgroundColor:[UIColor whiteColor]];
    [self.window makeKeyAndVisible];
    [self.window setRootViewController:[RootViewController new]];
```
#### 2、添加并调用tag值
```objc
// 添加：
[secondView setTag:1111];
// 调用
[self.window viewWithTag:1111];
```
#### 3、UIWindow关于Level

>   UIKIT_EXTERN const UIWindowLevel UIWindowLevelNormal;
    UIKIT_EXTERN const UIWindowLevel UIWindowLevelAlert;
    UIKIT_EXTERN const UIWindowLevel UIWindowLevelStatusBar

*上面三个值分别是0.0,2000.0,1000.0*
**大部分在App上使用的都是UIWindowLevelNormal，这也是每个Window被创建出来时的默认值**

#### 4、获取keyWindow
```objc
UIWindow *keyWindow = [[UIApplication sharedApplication] keyWindow];
```




