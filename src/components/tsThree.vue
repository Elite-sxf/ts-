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

//属性装饰器
function nameDesc(target:any,key:string) {

}
class nameTesc {
    @nameDesc
    name = "我是谁";
}
let n = new nameTesc();
n.name = 'asd';

//装饰器实例  貌似是一个提出来的公共方法
const info:any = undefined;

function methodDecorator (msg:string) {
    return function (target:any, key: string , descriptor: PropertyDescriptor) {
        console.log(descriptor);
        const fn = descriptor.value;
        descriptor.value = function() {
            try {
                fn()
            } catch (error) {
                console.log(msg);
                
            }
        }
    }
}
class exMethod {
    @methodDecorator('没有name')
    getName() {
        return info.name
    }
    @methodDecorator('age')
    getAge() {
        return info.age
    }
}
const e = new exMethod();
e.getName();
e.getAge();
</script>

<style>

</style>