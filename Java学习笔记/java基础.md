1. hashCode,equals,==

   "=="对于Java中的基本数据类型（数值型：byte、short、int、long,字符型：char,浮点型：float、double）来说是比较其值是否相等,对于引用数据类型（对象、接口、数据）比较其引用地址是否相等。

   equals在Object上的实现方式为:
   ```Java
   public boolean equals(Object obj) {
        return (this == obj);
    }
   ```
   
   hashCode有三个特性:1、同一Application内对同一个对象多次hashCode时其值相同。2、两个对象equals值为true，hashCode值也必须相等。3、如果两个对象equals值为false,不要求hashCode不相等。
2. int、char、long各占几个字节
3. int和Interger的区别
   
   jdk5自动装箱、拆箱。Interger.valueof(int)缓存-128-127之间的数字在常量词。int与Interger比较会拆箱。
    