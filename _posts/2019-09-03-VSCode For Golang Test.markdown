---
layout: post
title:  "VSCode For Golang Test"
date:   2019-09-03 10:57:00
categories: VSCode
tags: 開發工具
excerpt: VSCode For Golang Test
mathjax: true
---

![/images/202010061826.png](/images/202010061826.png)

話說現在寫Golang可以透過VSCode來自己生測試碼，想想過去那個寫PHP還要自己寫一堆測試碼的日子實在有夠…!@#$%^&*()

不過，給值還是要自己寫的

如果你是習慣用TDD來開發的工程師，以下的方式你可能會覺得不好適應

首先，我們先找一段要產生Unit Test的Go Function，像這樣將所有的程式碼給反白起來

![](/images/202010061830.jpg)

右鍵->Go:Generate Unit Tests For Function

之後，他就會在你程式碼所在的資料夾，產生一個[檔名]_test.go的檔案

![](/images/202010061831.jpg)

然後你就可以在註解的TODO: Add test cases裡面，加上你代入參數的"值"，好比這樣

![](/images/202010061832.jpg)


```
{
		{
			name: "一般測試",
			args: args{
				params: &homekeeper.DailyPunchclockData{
					Employee: &homekeeper.EmployeeOnChain{
						Identify:  "00190",
						FirstName: "Peter",
						LastName:  "Cheng",
					},
					Punchclock: &homekeeper.Punchclock{
						Begin: &homekeeper.TimeStruct{
							Year:   "2019",
							Month:  "08",
							Day:    "28",
							Hour:   "09",
							Minute: "24",
							Second: "00",
						},
						End: &homekeeper.TimeStruct{
							Year:   "2019",
							Month:  "08",
							Day:    "28",
							Hour:   "20",
							Minute: "05",
							Second: "00",
						},
					},
				},
			},
			want: &beans.Response{
				Status:  true,
				Channel: "PunchClock",
				Message: "PunchClock/UploadDailyPunchclockData</UseService>{\"employee\":{\"$class\":\"\",\"identify\":\"00190\",\"firstName\":\"Peter\",\"lastName\":\"Cheng\"},\"punchclock\":{\"begin\":{\"year\":\"2019\",\"month\":\"08\",\"day\":\"28\",\"hour\":\"09\",\"minute\":\"24\",\"second\":\"00\"},\"end\":{\"year\":\"2019\",\"month\":\"08\",\"day\":\"28\",\"hour\":\"20\",\"minute\":\"05\",\"second\":\"00\"}}}",
			},
		},
	}
```

這時，你可以點Function上方的run test，就可以運行Unit test

![](/images/202010061833.jpg)

如果你要一次運行資料夾內包含子資料夾裡面的全部測試碼，可以在該資料夾下輸入以下指令
```
go test ./...
```

![](/images/202010061834.jpg)

如果你需要一次運行所有$GOPATH資料夾下包含子資料夾的全部則試碼，可以直接下以下指令
```
go test ...
```