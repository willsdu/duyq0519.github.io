---
layout: post
title: 'golang标准库heap,list,ring'
date: 2018-10-23
categories: 数据库
cover: https://image.mmschool.club/github/sun.jpg
tags: golang stdlib
---

## list
```
//创建，初始化
l := list.New()
//在list后面插入一个元素4，--[4]
e4 := l.PushBack(4)
//在list前面插入一个元素1  --[1,4]
e1 := l.PushFront(1)
//在e1后面插入一个元素2   --[1,2,4]
e2 := l.InsertAfter(2, e1)
//在e4前面插入一个元素3   --[1,2,3,4]
e3 := l.InsertBefore(4, e4)
log.Printf("e2 %v, e3 %v", e2.Value, e3.Value)
list2 := list.New()
list2.PushBack(5)
list2.PushBack(6)
list0 := list.New()
list0.PushBack(-2)
list0.PushBack(-1)
//在后追加一个list
l.PushBackList(list2)
Iterator(l)
//在前面追加一个list
l.PushFrontList(list0)
Iterator(l)
l.Remove(l.Back())
Iterator(l)
```
遍历函数
```
func Iterator(l *list.List) {
	v := ""
	for e := l.Front(); e != nil; e = e.Next() {
		v += fmt.Sprintf("%v,", e.Value)
	}
	log.Printf("length %d, value %s", l.Len(), strings.TrimRight(v, ","))
}
```
为了使用完所有的函数，使用list写个冒泡排序
```
func RaiseList(s *list.List) {
	//来一次排序，使用冒泡排序
	last := s.Back()
	for i := s.Len() - 1; i > 0; i-- {
		max := s.Front()
		current := s.Front()
		for j := 1; j <= i; j++ {
			current = current.Next()
			if Less(max, current) {
				max = current
			}
		}
		if i == s.Len()-1 {
			s.MoveToBack(max)
		} else {
			s.MoveBefore(max, last)
		}
		last = max
	}
}
func Less(i, j *list.Element) bool {
	iValue := i.Value.(int)
	jValue := j.Value.(int)
	return iValue < jValue
}
```
写完测试发现，当list数据超过20000时，冒泡排序的性能下降非常快。然后为了用完函数，又写了list反转功能，写完还是有个MoveToFront没有用到，算了。
```
func reverse(s *list.List) {
	left := s.Front()
	right := s.Back()
	for i := 0; i < s.Len()/2; i++ {
		mark := left.Next()
		s.MoveAfter(left, right)
		s.MoveBefore(right, mark)
		right = left.Prev()
		left = mark
		Iterator(s)
	}
}
```

## ring
## heap