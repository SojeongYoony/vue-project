<!-- 
    script테그의 setup옵션은 필수 키워드이다. 변수를 선언하고 싶으면 여기다가 함. 
     ** vite.config.js가 읽을때 setup 키워드로 읽으므로 다른거 쓰면 안됨.
-->

<script setup>
    const greeting = 'Hello Yoon';
    // 함수를 변수에 저장하여 쓰든, 함수형태로 쓰든 자유임.  
    function handleClick(){
        console.log('clicked');
    }

    function handleKeyDown(){
        console.log('tyefef');
    }
</script>

<template>
<!-- page도 component고 쪼꼬만 UI component다 마치 Class, vue/react 개념 
    App.vue가 엄마 component 그리고 다른 애들은 App.vue의 자식들 -->
<!-- 선언된 변수를 {{}}을 이용하여 javascript의 변수를 가져올 수 있다. ** react에서는 {}하나다. -->
    <h1>{{ greeting }}</h1>
    <button @click="handleClick">click button</button>
    <input @keydown="handleKeyDown" />
</template>