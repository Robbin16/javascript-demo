- 数组
  - a.at(-1)从后往前一位 a.at(0) === a[0]
  - 数组也是一种对象，只是对象上 key 变成了数字，增加了数组的若干方法，以及 length 属性
  - 如果你把数组当成对象来用，比如 arr.text = 1 ;出现数组空洞 arr[0] = 0; arr[1000] = 1000;倒序插入数组 arr[1000] = 1000;arr[999] = 999;这种 V8 底层根据数组所做的优化将不生效，仅仅是当成普通对象来处理
  - pop 和 push 比 shift 和 unshift 要快，因为 shift 需要先清理第 0 项数据，再把 1 到 length-1 的项往前移，再修改 length 属性，pop 只需要删除最后一项，然后修改 length 属性即可
  - 数组循环 for 最古老也是最好，for of 没法拿到下标，由于数组是对象的一种，因此可以用 for in 但是，有些类数组除了有数字下标和 length 外，还有其他下标，for in 会把所有下标都循环出来。for 和 for of 则不会。for 和 for of 在数组中要比 for in 快 10-100 倍。
  - length 的本质是最大下标加 1 比如: let arr = []; arr[999] = 999; arr.length // 1000 将 length 变小可以截断数组，将数组清空可以 arr.length = 0
  - []创建数组简洁，new Array(2)的意思是创建 length 为 2 的空数组会有歧义，不建议使用。
  - splice 删除和插入数组 arr.splice(1,2,"c","d") //["a","b","c","d"] => ["a","c","d","d"] arr.splice(3,0,"e","f") //["a","b","c","d"]=> ["a","b","c","e","f","d"] arr.splice(-1,3,"g","z") //["a","b","c","d"] => ["a","b","c","g","z"]
  - slice 字面意思切片，就是返回新的子数组。arr.slice(1,3) // ["a","b","c","d"] => ["b","c"] arr.slice()返回 arr 浅拷贝副本
  - concat 追加元素并返回新数组，arr.concat[a,"f","g"] a=["a"] // ["a","b","c","d"] => ["a","b","c","d","a","f","g"] concat 追加类数组除非类数组 likeArr[Symbol.isConcatSpreadable] = true 才会展开追加否则将整个类数组视为一个元素追加
