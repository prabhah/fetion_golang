fetion golang 接口
======

## 原理
模拟wap飞信登陆，无需输入验证码，适合用作定期发送短信、命令行操作等。

新版本wap飞信只支持动态密码登录，所以请先到如下地址获取动态密码：
登录地址：http://f.10086.cn/im5/login/login.action

## 安装

```bash
go get -u github.com/prabhah/fetion_golang
```


## 使用
```go

package main

import (
	"fmt"
	"github.com/prabhah/fetion_golang"
)

func main() {
	mobileNumber := "手机号"
	password := "动态密码"
	f := fetion.NewFetion(mobileNumber, password)
	err := f.Login()
	if err != nil {
		fmt.Println(err)
		return
	}
	defer f.Logout()
	f.BuildUserDb()
    users := []string{"手机号1", "手机号2"}
    msg := "Hello 世界"
    f.SendSms(msg, users)
	f.SendOneself("发送成功")
}
```
