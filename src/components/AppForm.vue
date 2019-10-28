<template >
  <form
    id="test"
    @submit="checkForm"
    novalidate="true"
    >
    <div>
    <slot :isName="isName" :isAge="isAge"></slot>
    </div>
    <p>
      <input
        type="submit"
        value="Отправить"
      >
    </p>
  </form>
</template>

<script>
import Vue from 'vue'
import Component from 'vue-class-component'
import AppFormItem from '@/components/AppFormItem.vue'

@Component({
  
  components: {
    AppFormItem
  },
  props: {
    value: Object,
    rules: Object
  }
})
export default class AppForm extends Vue {
  isName = false
  isAge = false

  mounted () {
    console.log(this.value)
    console.log(this.test)
  }

  checkForm (sumbit) {
    // this.rules.name.valitator(sumbit.target.elements.name.value)
    if (this.rules.name.find(el => el.validator(sumbit.target.elements.name.value))) {
      this.isName = false
      if( sumbit.target.elements.count.selectedIndex > 0) {
        this.isAge = false
        alert('good') 
        return true
      } else {
        console.log('error')
        this.isAge = true
      }
    } else {
      console.log('error')
      this.isName = true
    }
    console.log(sumbit.target.elements.count.selectedIndex)
    sumbit.preventDefault()
  }
}
</script>

<style scoped lang="scss">

</style>
