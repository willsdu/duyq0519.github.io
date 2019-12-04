---
layout: post
title: 'golang标准库json包'
date: 2019-04-17
categories: 数据库
cover: https://image.mmschool.club/github/sun.jpg
tags: golang stdlib
---

## 概览
包函数里面提供了大部分函数，在其他的struct中的方法基本上包函数都能找到
```
func Compact(dst *bytes.Buffer, src []byte) error
func HTMLEscape(dst *bytes.Buffer, src []byte)
func Indent(dst *bytes.Buffer, src []byte, prefix, indent string) error
func Marshal(v interface{}) ([]byte, error)
func MarshalIndent(v interface{}, prefix, indent string) ([]byte, error)
func Unmarshal(data []byte, v interface{}) error
func Valid(data []byte) bool
```
方法
```
type Decoder
    func NewDecoder(r io.Reader) *Decoder
    func (dec *Decoder) Buffered() io.Reader
    func (dec *Decoder) Decode(v interface{}) error
    func (dec *Decoder) DisallowUnknownFields()
    func (dec *Decoder) More() bool
    func (dec *Decoder) Token() (Token, error)
    func (dec *Decoder) UseNumber()

type Encoder
    func NewEncoder(w io.Writer) *Encoder
    func (enc *Encoder) Encode(v interface{}) error
    func (enc *Encoder) SetEscapeHTML(on bool)
    func (enc *Encoder) SetIndent(prefix, indent string)
type Delim
    func (d Delim) String() string
type Number
    func (n Number) Float64() (float64, error)
    func (n Number) Int64() (int64, error)
    func (n Number) String() string
type RawMessage
    func (m RawMessage) MarshalJSON() ([]byte, error)
    func (m *RawMessage) UnmarshalJSON(data []byte) error
type Token
```
接口
```
type Marshaler
type Unmarshaler
```
错误
```
type InvalidUnmarshalError
type InvalidUTF8Error
type MarshalerError
type SyntaxError
type UnmarshalFieldError
type UnmarshalTypeError
type UnsupportedTypeError
type UnsupportedValueError
```
## 样例代码