## &#x1F308;Vue2和Vue3的生命周期
#### Vue2的生命周期:
1. **beforeCreate**：实例刚在内存中被创建出来，此时还没有初始化好data和methods属性。
<br/>

2. **created**：实例已经在内存中创建完成，data和methods已经初始化好，可以访问data和methods属性。
<br/>

3. **beforeMount**：在挂载开始之前被调用，相关的render函数首次被调用。
<br/>

4. **mounted**：el被新创建的vm.$el替换，并挂载到实例上去之后调用该钩子。
<br/>

5. **beforeUpdate**：数据更新时调用，发生在虚拟DOM重新渲染和打补丁之前。
<br/>

6. **updated**：由于数据更改导致的虚拟DOM重新渲染和打补丁之后调用。
<br/>

7. **beforeDestroy**：实例销毁之前调用。在这一步，实例仍然完全可用。
<br/>

8. **destroyed**：实例销毁后调用。此时，所有的事件监听器都被移除，所有的子实例也都被销毁。
### Vue3生命周期
1. **beforeCreate**：与Vue 2的beforeCreate生命周期函数相同。
<br/>

2. **created**：与Vue 2的created生命周期函数相同。
<br/>

3. **beforeMount**：与Vue 2的beforeMount生命周期函数相同。
<br/>

4. **mounted**：与Vue 2的mounted生命周期函数相同。
<br/>

5. **beforeUpdate**：与Vue 2的beforeUpdate生命周期函数相同。
<br/>

6. **updated**：与Vue 2的updated生命周期函数相同。
<br/>

7. **beforeUnmount**：在卸载组件之前调用。
<br/>

8. **unmounted**：在卸载组件之后调用。
<br/>

9. **errorCaptured**：在捕获一个来自子孙组件的错误时被调用。

#### 总结：
Vue 3中的beforeDestroy和destroyed被重命名为beforeUnmount和unmounted，以更好地反映组件的卸载过程。此外，Vue 3中引入了errorCaptured生命周期函数，用于捕获来自子孙组件的错误。

