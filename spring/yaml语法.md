```yaml
#简单的key:value
key: value
#对象
obj:
  key1: value1
  key2: value2
#对象2
obj2: { key1: value1, key2: value2 }
#列表1
list1:
  - 1
  - 2
  - 3
  - 4
#列表2
list2: [ 1,2,3,4 ]
#调用其他值
refer1: ${key}
#默认值
default: ${key1:default}
#内置random
random: ${random.int}
```