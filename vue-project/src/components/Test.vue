<template>
    <div class="test">
        姓:<input type="text" v-model="firstName"><br>
        名:<input type="text" v-model="lastName"><br>
        <button @click="changeFullName">将全名改为li-si</button>
        全名:<span>{{ fullName }}</span>
    </div>
</template>




<script lang="ts" setup>
    import {ref,computed} from 'vue'

    let firstName = ref('zhang')
    let lastName = ref('san')


    //计算属性,且是只读的
    // let fullName = computed(()=>{
    //     console.log(1);
        
    //     return firstName.value + '-' + lastName.value
    // })

    //计算属性,可读可写
    let fullName = computed({
        get(){
            return firstName.value + '-' + lastName.value
        },
        set(val){
            const [str1,str2] = val.split('-')
            firstName.value = str1
            lastName.value = str2
            console.log('set',val);
        }
    })
    
    
    function changeFullName() {
        console.log(fullName.value);
        fullName.value = 'li-si'
        
    }
</script>

<style scoped>
    .test{
        background-color: aqua;
        box-shadow: 0 0 10px;
        border-radius: 10px;
        padding: 20px;
    }

</style>