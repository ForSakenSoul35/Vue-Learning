1. Vue不支持IE8以下的浏览器
2. 使用Vue 引入Vue
3. 新建Vue实例
4. v-for v-on,v-model指令
5. mvp和mvvm架构
6. 前端组件化  
前端每个页面都可以分割成一个个组件
每个组件都是页面上的一个区域
7. v-bind 指令 
8. 全局组件 局部组件
9. 简单组件传值
父组件向子组件传值:  
 - 父组件 使用v-bind指令传值 子组件使用props属性接收值
子组件向父组件传值: 
 - 子组件 使用$emit的方式 向外触发 一个指定的事件 this.$emit('delete',this.index) // 参数1 为指定的事件名,参数2 为事件处理函数接收的参数
 - 父组件 使用@事件名 监听指定的事件,并分配事件处理函数
 10. v-bind 指令简写 v-bind:content === :content
 11. 生命周期钩子
 - beforecreate
 - created
 - beforeMount
 - Mounted
 - beforeDestory
 - destoryed
 - beforeUpdate
 - Updated
 12. 模版语法
 - 插值表达式
 - v-html v-text
 13. 条件渲染
 v-show v-if区别
 使用：
    <div v-if="show"></div>
    <div v-show="show"></div>
v-if v-show都是用来控制DOM元素
DOM元素的显示都是由v-show v-if 后跟的变量决定
当变量为true时，表示显示DOM元素，两个指令是一致的
当变量为flase时，表示隐藏DOM，v-if指令是直接将DOM元素移除，在DOM树中是看不到DOM元素的
而v-show指令，是通过将DOM元素的display属性设置为none，来实现让DOM元素隐藏的
建议使用v-show指令，因为不会重复操作DOM元素。
更多应用：使用else
<div v-if ="show">helloworld</div>
<div v-else>byeworld</div>
上述代码的意思是 当show变量的值为true时，显示v-if所在的DOM元素
当show的值为false 显示v-else所在的元素。
要注意的是 v-if和v-else要紧邻着使用，否则会报错

更多应用：if...else if...else...
<div v-if="show === 'a' ">显示a</div>
<div v-if-else ="show === 'b'">显示b</div>
<div v-else>不显示a要不显示b</div>
这三个指令也需要紧邻着使用
14. key值 使用key属性来标示不同的DOM元素
15. 列表渲染
渲染对象
<div v-for="(item,key,index) of obj">{{item}}</div>
可以修改对象的原有属性的值
添加属性：
遍历对象 不能动态处理对象，比如直接添加对象的属性，但是可以直接修改掉对象的引用
16. Vue set方法
对象使用set方法
Vue.set(vm.obj,"id","123")// 改变对象的属性
Vue的实例方法 Vue的原型方法

vm.$set(vm.obj,"id","123")

数组使用set方法
Vue.set(vm.list,1,"a")//  修改数组list的 下标为1 的数据
vm.$set(vm.list,1,"a")


修改数组： 操作原数组的方法  ，修改数组的引用  Vue的set方法
16.组件细节
- 在有些HTML标签中，子标签必须是特定的标签 比如 table中必须有tbody ,select中必须有option
在特殊情况下 又想在这些子标签中使用子组件。
解决方案：
<table>
  <tbody>
    <tr is = "row "></tr>
    <tr is = "row "></tr>
    <tr is = "row "></tr>
  </tbody>
</table>
- 全局组件定义 data 
Vue.component('row',{
  data: function(){
    return {
      content:"this is content"
    }
  }
})
17. ref

 