腾讯信鸽推送 go sdk
===================
说明
-------------------
项目里要用到信鸽，找的其他go sdk使用感觉太麻烦，所以在的基础上完善了一个，目前实现的接口包括(安卓与ios接口分开)：

- 单个设备推送
- 帐号/别名推送
- 帐号/别名列表推送

总结
-------------------
经多次测试，在生产环境下信鸽延时很严重，最长1分钟才可能收到，而且有时经常出现掉推送包的可能. IOS还是用APNS原生要靠谱些

参考链接
-------------------
http://developer.xg.qq.com/wiki/xg/%E6%9C%8D%E5%8A%A1%E7%AB%AFAPI%E6%8E%A5%E5%85%A5/Rest%20API%20%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97/Rest%20API%20%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97.html


Demo Code:
func test_pushmsg_xg(c <-chan int) {
  cli := xinge.NewClient(22002*****, "a2bbd4b3a8ae5195d7e4c97b753*****")
  cli.PushSingleIosAccount("4de86b5aceb579c4a7689fc79ab46d0fb******", "你有一个新的未读消息", 6, nil)
  <-c
}

func main() {
	c_Block = make(chan int)
	fmt.Println("start test...")
	go test_pushmsg_xg(c_Block)
	c_Block <- 1
	fmt.Println("test end.")
	return
}
--------------------