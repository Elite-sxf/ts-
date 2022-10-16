<template>
    <div>
        ts函数接口
    </div>
</template>

<script setup lang="ts">


//定义一个函数接口 a ,b为参数 后加类型  （）后面跟返回值类型
interface IsFunc {
    (a:number ,b:number):number
}
const handleAdd:IsFunc = function(a:number,b:number):number {
    return  a*b
}
console.log(handleAdd);
//接口继承
interface name {
    name:string
}
interface age {
    age?:number
}
interface person extends name,age {
    
}
let xiaoming:person = {
    name:'xioaming',
}
console.log(xiaoming);

const func = (x:number=1,y:number=2):void =>{
    console.log('函数');
    
}
func()

//构造函数
// var gzFunc = new Function("a","b","return a*b")
// console.log(gzFunc(1,3));

</script>

<style>

</style>