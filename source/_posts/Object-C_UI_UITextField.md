
---
title: Object-C_UI_UITextField
date: 2018/3/06 20:07:33
categories:
- Object-C
- UI
---
# UITextField
### 1、属性
#### 1、继承

**父类暴露的方法和属性都可以使用**

```objc
NS_CLASS_AVAILABLE_IOS(2_0) @interface UITextField : UIControl <UITextInput, NSCoding, UIContentSizeCategoryAdjusting>
```

#### 2、创建

```objc
UITextField *sl_textField = [[UITextField alloc] initWithFrame:CGRectMake(0, 0, 100, 50)];
sl_textField.backgroundColor = [UIColor redColor];
[self.view addSubview:sl_textField];

```

#### 3、常用设置
```objc

sl_textField.text = @"文字";   // 设置预显示文本
sl_textField.placeholder = @"占位符";  // 占位符
// 设置文本框样式
sl_textField.borderStyle = UITextBorderStyleRoundedRect;   // 设置圆角
// 是否允许输入
sl_textField.enabled = NO; // 不允许
// 是否开始输入的时候清空输入框内容
sl_textField.clearsOnBeginEditing = YES; // 清空
// 是否文字以圆点格式显示（密码模式）
sl_textField.secureTextEntry = YES; // 是
```

#### 4、键盘相关
```objc

// 弹出键盘的类型（枚举）
sl_textField.keyboardType = UIKeyboardTypeNumberPad;   // 数字键盘
sl_textField.keyboardType = UIKeyboardTypeTwitter; // 为Twitter优化的键盘，，容易输入@ #符号

// 键盘右下角return按钮类型（枚举值）
sl_textField.returnKeyType = UIReturnKeyDone;  // Done类型

// 代替标准的系统键盘
sl_textField.inputView = mainView; // mainView为自己创建的一个UIView
// 编辑时显示在系统该键盘或用户自定义的inputView上的视图
sl_textField.inputAccessoryView = keyLable; // keyLable为自己创建的一个UILabel


sl_textField.clearButtonMode = UITextFieldViewModeAlways;  // 一直出现：UITextFieldViewModeAlways
sl_textField.rightViewMode = UITextFieldViewModeWhileEditing;  // 编辑时出现：UITextFieldViewModeWhileEditing
// 从不出现：UITextFieldViewModeNever
// 除了编辑外都出现：UITextFieldViewUnlessEditing
```

#### 5、响应者
```
[sl_textField resignFirstResponder];   // 取消第一响应者
[sl_textField becomeFirstResponder];    // 成为第一响应者
```
#### 6、键盘的收回
```
// 遵循<UITextFieldDelegate>协议
- (BOOL)textFieldShouldReturn:(UITextField *)textField {
NSLog(@"%ld",textField.tag);

LTView *l1 = [self.view viewWithTag:101];
LTView *l2 = [self.view viewWithTag:102];
LTView *l3 = [self.view viewWithTag:103];
LTView *l4 = [self.view viewWithTag:104];

if (textField.superview == l1) {
[l2.textField becomeFirstResponder];
}else if (textField.superview == l2) {
[l3.textField becomeFirstResponder];
}else if (textField.superview == l3) {
[l4.textField becomeFirstResponder];
}else if (textField.superview == l4) {
[textField resignFirstResponder];
}

return YES;
}
```
### 2、常用代理方法
#### 1、当textField将要开始编辑的时候告诉委托人
```
- (BOOL)textFieldShouldBeginEditing:(UITextField *)textField
```
#### 2、当textField已经编辑的时候告诉委托人
```
- (void)textFieldDidBeginEditing:(UITextField *)textField
```
#### 3、当textField将要完成编辑的时候告诉委托人
```
- (BOOL)textFieldShouldEndEditing:(UITextField *)textField
```
#### 4、当textField已经完成编辑的时候告诉委托人
```
- (void)textFieldDidEndEditing:(UITextField *)textField
```
#### 5、当点击键盘上回车按键时候告诉委托人
```
- (BOOL)textFieldShouldReturn:(UITextField *)textField
```

> * 以上委托人是delegate





