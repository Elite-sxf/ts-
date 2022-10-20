<template>

</template>

<script setup lang="ts">
const arr:Array<number> = [1,2,3,4,5];
let getArray = <s>(array:Array<number>)=> {
    let a:Array<number> =  array.map((item) => {
        return item
    })
    return a
}
let newArr = getArray<string>(arr)
console.log(newArr);
//这种写法不严谨 所以用到泛型约束
// function getIndex(arr:Array<number>,item:number):number {
//     // return arr.findIndex(i => i===item)
//     return arr[item]

// }
const obj = {
    a:'1',
    b:'2'
}
function getIndex<T,K extends keyof T>(arr:T,item:K) {
    // return arr.findIndex(i => i===item)
    return arr[item]

}
console.log('泛型约束',getIndex(obj,'a'));


///泛型
interface haveLenth {
    length: number
}
function getLength<T extends haveLenth>(value:T):number {
    return value.length
}
console.log(getLength<string>('sxf'));

//泛型接口的
interface fanxing<t1=number,t2=string> {
    name: t1,
    age: t2
}
let p:fanxing<string,number> = {
    name:"sadsad",
    age:4
}
//条件类型
type isFlag<T> = T extends String ? string : number 
function isStrOrNum<T extends String | Number>(v:T) {
    // throw ""
    return console.log(v);
}
isStrOrNum(1)

//映射
type Iname = "Person" | "Hobby";
type Iinfo = {
    name: string,
    age: number
}
//前一项为属性名 ，后一项为每个里面的属性
type newType = Record<Iname, Iinfo>
let newInfo: newType = {
    Person: {
        name: 'wo',
        age:6
    },
    Hobby:  {
        name: 'dog',
        age:1
    },
}
//第一个参数为接口 第二个为接口上的某个属性
type newType2 = Pick<fanxing, "name">
let newInfo2:newType2 = {
    name: 1
}
</script>

<style>

</style>