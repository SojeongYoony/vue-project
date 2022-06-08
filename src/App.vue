<!-- 
    script테그의 setup옵션은 필수 키워드이다. 변수를 선언하고 싶으면 여기다가 함. 
     ** vite.config.js가 읽을때 setup 키워드로 읽으므로 다른거 쓰면 안됨.
-->

<script setup>

    // ref 함수를 사용하기 위해서는 import 필수
    import { ref, computed } from "vue";

    const greeting = 'Hello Yoon';
    // 함수를 변수에 저장하여 쓰든, 함수형태로 쓰든 자유임.  
    function handleClick(){
        console.log('clicked');
    }

    function handleKeyDown(){
        console.log('tyefef');
    }

    // ref 함수에 초기값을 넘겨준다. : 화면에 변형이 일어나는 변수값은 ref를 써준다.
    // * ref type의 count 변수 선언, 초기화
    const count = ref(0)
    const increment = () => {
        count.value++
        console.log(count.value);
    }

    // script는 페이지가 처음 로딩 될때 한번만 실행된다.
    // 그래서 computed를 안쓰면 재 계산이 안된다.
    const seen = computed(()=> count.value % 10 === 0)

    // @sign 붙은 친구들은 event 함수이므로 callback 함수이다. 
    // 따라서 특정 이벤트가 실행될때마다 함수를 호출하지만
    // if는 이벤트가 아니어서 호출이 안됨. ---> v-if="test" 실행 안됐음.
    // * if boolean 값만 받는다.
    // const test = ()=>{
    //     count.value % 10 === 0
    // }
</script>

<template>
<!-- page도 component고 쪼꼬만 UI component다 마치 Class, vue/react 개념 
    App.vue가 엄마 component 그리고 다른 애들은 App.vue의 자식들 -->
<!-- 선언된 변수를 {{}}을 이용하여 javascript의 변수를 가져올 수 있다. ** react에서는 {}하나다. -->
    <h1>{{ greeting }}</h1>
    <!-- v-on:click 의 줄임말 @click -->
    <button v-on:click="handleClick">click button1</button>
    <br />
    <button @click="handleClick">click button2</button>
    <br />
    <input @keydown="handleKeyDown" />

    <br />
    <h3> clicked {{count}} times </h3>
    <button @click="increment">button</button>
    <p v-if="seen"> {{count}}번 누름 </p>

</template>