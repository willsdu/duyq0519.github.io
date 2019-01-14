---
layout: post
title: 'golang 处理价格'
date: 2018-10-23
categories: 数据库
cover: https://image.mmschool.club/github/sun.jpg
tags: golang
---


1. topic One

```

//People people
type People struct {
	Name string
}

func (p *People) Hello() string {
	return fmt.Sprintf("your name is %s", p.Name)
}

//Man 日期
type Man interface {
	Hello() string
}

var (
	_ Man = &People{}
)

func main() {
	m := &People{Name: "duyq"}
	log.Printf(Man.Hello(m))
	SyncOnce()
}

```

sync 各函数的使用