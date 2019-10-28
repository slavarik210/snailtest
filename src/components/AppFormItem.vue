<template>
  <div>
    <div class="test-item" v-if="type == 'text'">
        <h1>Введите имя</h1>   
        <input 
            :placeholder="label" 
            :type="type" 
            :name="prop"
        >
        <p  
            v-if="isName" 
            :style='`color: red`'
            >
            Необходимо заполнить имя
        </p>
    </div>
    <div class="test-item" v-if="type == 'dropdown'">
        <h1>Укажите возраст</h1>   
        <select :name="prop">
            <option value="" disabled selected hidden>{{label}}</option>
            <option  v-for="item in data">{{item}}</option>
        </select>
        <p 
            v-if="isAge" 
            :style='`color: red`'
            >
            Необходимо указать возраст
        </p>
    </div>
    <div 
        class="test-item" 
        v-if="type == 'textarea'"
        >
        <p>Напишите отзыв</p>   
        <textarea :name="prop" :placeholder="`${label} По желанию`"/>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import Component from 'vue-class-component'
import AppForm from '@/components/AppForm.vue'

@Component({
    components: {
        AppForm
    },
    props: {
        prop: String,
        type: String,
        label: String,
        data: Array,
        isName: Boolean | undefined,
        isAge: Boolean | undefined
    }
})
export default class AppFormItem extends Vue {

    
}
</script>

<style scoped lang="scss">

</style>