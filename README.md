   1.vue源码解读流程 1.new Vue 调用的是 Vue.pr 件，初始化渲染函数。初始化状态就是数据。把数据添加到观察者中实现双数据绑定。 

   2.双数据绑定原理是：obersve()方法判断value没有没有__ob___属性并且是不是Obersve实例化的，
   value是不是Vonde实例化的，如果不是则调用Obersve 去把数据添加到观察者中，为数据添加__ob__属性， Obersve 则调用defineReactive方法，该方法是连接Dep和wacther方法的一个通道，利用Object.definpropty() 中的get和set方法 监听数据。get方法中是new Dep调用depend()。为dep添加一个wacther类，watcher中有个方法是更新视图的是run调用update去更新vonde 然后更新视图。 然后set方法就是调用dep中的notify 方法调用wacther中的run 更新视图
 3.vue从字符串模板怎么到真实的dom呢？是通过$mount挂载模板，就是获取到html，然后通过paseHTML这个方法转义成ast模板，他大概算法是 while(html) 如果匹配到开始标签，结束标签，或者是属性，都会截取掉html，然后收集到一个对象中，知道循环结束 html被截取完。最后变成一个ast对象，ast对象好了之后，在转义成vonde 需要渲染的函数，比如_c('div'  s(''))  等这类的函数，编译成vonde 虚拟dom。然后到updata更新数据 调用__patch__ 把vonde 通过diff算法变成正真正的dom元素。

