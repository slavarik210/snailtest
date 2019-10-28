<template>
  <div class="home">
    <app-form v-model="form" :rules="rules" v-slot="{isName, isAge}">  
      <app-form-item label="Name" type="text" prop="name" :isName="isName"/>
      <app-form-item label="Count" type="dropdown" prop="count" :data="countList" :isAge="isAge" />
      <app-form-item label="Comment" type="textarea" prop="comment" />
    </app-form>
  </div>
</template>

<script>
import Vue from 'vue'
import Component from 'vue-class-component'
import AppForm from '@/components/AppForm.vue'
import AppFormItem from '@/components/AppFormItem.vue'

@Component({
  components: {
    AppForm,
    AppFormItem
  }
})
export default class Home extends Vue {
  form=  {
      name: "",
      count: null,
      comment: "" 
  }

  countList = ['17', '18', '19']

  rules = {
    name: [
      {
        required: true,
        validator: this.someValidatorFunction,
        message: "Some error",
        trigger: "blur"
      }
    ],
    age: [
      {
          required: true,
          // validator: someValidatorFunction2,
          message: "Some error 2",
          trigger: "change"
      }
    ],
  }
  
  someValidatorFunction (value) {
    if (value) {
      return value 
    }
  }
}
</script>
