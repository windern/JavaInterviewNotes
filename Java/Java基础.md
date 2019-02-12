# 一、数据类型

## 包装类型

boolean/1
byte/8
short/16
char/16
int/32
float/32
long/64
double/64

自动拆装箱

## 缓存池

new Integer(123)和Integer.valueOf(123)，valueOf运用了cache缓存池

Integer a = 123;//自动用了装箱，valueOf

基本类型对应的缓存池如下：
- boolean values true and false
- byte values all bytes -128 and 127
- short values between -128 and 127
- int values between -128 and 127
- char values 127 char，0-127， range \u0000 and \u007F

## todo
## Integer如何自动valueOf自动拆装箱的，自动拆装箱如何做到的
### char需要进一步了解编码格式\u代表什么