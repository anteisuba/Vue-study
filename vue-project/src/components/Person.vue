<template>
    <div class="person">
        <h2>汽车信息:一辆{{car.brand}}车价值{{car.price}}w</h2>

        <button @click="changePrice">修改汽车价格</button>


        <button @click="changeName">修改汽车姓名</button>
        <button @click="changeCar">修改</button>
        <br>
        <h2>游戏列表:</h2>
        <ul>
            <li v-for="g  in games" v-bind:key="g.id">{{ g.name }}</li>

        </ul>

        <button @click="changeFirstGame">修改第一个游戏的名字</button>

        <h2>当前求和为{{ sum }}</h2>
        <button @click="changeSum">点我sum+1</button>

        <h2>姓名{{ person.name }}</h2>
        <h2>年龄{{ person.age }}</h2>

        <button @click="changeName2">修改名字</button>
        <button @click="changeAge2">修改年龄</button>
        

    </div>
</template>



<script lang="ts" setup name="Person234">
    import {ref} from 'vue'
    import { reactive,toRefs } from "vue";
    //数据
    let car = reactive({brand:'奔驰',price:100})

    let sum = ref(0)

    let games = ref([
        {id:'bilandangan01',name:'hoshino'},
        {id:'bilandangan02',name:'ayase'},
        {id:'bilandangan03',name:'hina'}
    ])

    let person = reactive({
        name:'张三',
        age:18
    })
    //解构响应式
    let {name,age} = toRefs(person)
    console.log(toRefs(person));
    




    //方法
    function changePrice() {
        car.price += 10;

        
    }
    function changeName() {
        car.brand='宝马'

    }
    function changeFirstGame() {
        games.value[0].name = 'shiroko'
        games.value[1].name = 'miya'
        games.value[2].name = 'sara'
    }

    function changeSum() {
        sum.value += 1

    }

    function changeCar() {
        //reactive这么写页面可以更新
        Object.assign(car,{brand:'奥迪',price:5})

        //ref为
        //car.value = {brand:'奥迪',price:5}
    }
    function changeName2() {
        name.value += '~'
        console.log(name.value,person.name);
        
        
    }

    function changeAge2() {
        age.value += 2
    }


</script>



<style scoped>
.person {
    background-color: skyblue;
    box-shadow: 0 0 10px;
    border-radius: 10px;
    padding: 20px;

}

button {
    margin: 0 5px;
}

li{
    font-size:20px
}
</style>