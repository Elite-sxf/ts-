<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />
    <span class="item">{{msg}}</span>
    <span class="item">{{num}}</span>
    <span class="item">{{flag ? "是":"否"}}</span>
    <span class="item">{{obj.a}}+{{obj.b}}</span>
    <span class="item">枚举 {{gender.male}}--{{gender.femal}}</span>

    <ul>
      <li v-for="i in arr" :key="i">{{i}}</li>
    </ul>
  </header>

  <RouterView />
</template>

<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'

const msg:String = "这是一个字符串";
const num:Number = 0;
const flag:Boolean = false;
const arr: Array<number> = [0,1,2,3,4];
let obj : {
  a: string,
  b: string
}
obj = {
  a: '1',
  b: '2'
}

//类型断言
let txt:string = "sssssssssssssss";
// const len = (<string>txt).length
const len = (txt as string).length
console.log(len);



  //枚举
enum gender {
  male = 2,
  femal
}

function handleVoid() {
  // console.log("void");
}
handleVoid()

//接口
interface city {
  name: string,
  area: string,
  // lv?: Number  //可选属性 之后定义的属性可以不声明此项
  // readonly lv: 99999  // 只读  只能是这个值
  lv: Number
}
let jap:city = {
  name: '小鬼子',
  area: "asia",
  lv: 999
}
console.log(jap);

//索引签名  可以随意定义多个变量
interface names {
  [props: string] : number
}

let mans:names = {
  name: 0,
  123: 1
}
console.log(mans);

</script>


<style scoped>
.item{
  margin: 0 20px;
  font-size: 20px;
}
*{
  list-style: none;
}
header {
  line-height: 1.5;
  max-height: 100vh;
  display: block !important;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
