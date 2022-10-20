<template>

</template>

<script setup lang="ts">

// function testTs<T extends new (...args:any[])=>{}>(constructor:T) {
//         return class extends constructor {
//             name = '阿飞';
//             show() {
//                 console.log(this.name,'sdasdadasdasdasd');
//             }
//         }
//     }
// @testTs
// class Person {
//     name: string;
//     constructor(name:string) {
//         this.name = name;
//     }
// }

// let p = new Person("飞哥");
// (p as any).show()

//最终写法
//类的装饰器----------------------------------------
function testTs() {
    return function <T extends new (...args:any[])=>{}>(constructor:T) {
        return class extends constructor {
            name = '阿飞';
            show() {
                console.log(this.name,'sdasdadasdasdasd');
            }
        }
    }
}
const Person = testTs()(class {
    name: string;
    constructor(name:string) {
        this.name = name;
    }
})
let p = new Person("飞哥");
p.show()
</script>

<style>

</style>