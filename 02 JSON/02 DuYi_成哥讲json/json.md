#json

---
---

##简介：

JSON是一种传输数据的格式（以对象为样板，本质上就是对象，但用途有区别，对象就是本地用的，json是用来传输的）

JSON.parse();  string — > json

JSON.stringify(); json — > string


##异步加载json

**js加载的缺点：**加载工具方法没必要阻塞文档，过得js加载会影响页面效率，一旦网速不好，那么整个网站将等待js加载而不进行后续渲染等工作。

有些工具方法需要按需加载，用到再加载，不用不加载。

**javascript 异步加载 的 三种方案**

- 1 defer 异步加载，但要等到dom文档全部解析完才会被执行。只有IE能用，也可以将代码写到内部。
- 2 async 异步加载，加载完就执行，async只能加载外部脚本，不能把js写在script 标签里。
- 1.2 执行时也不阻塞页面
- 3 创建script，插入到DOM中，加载完毕后callBack，

##js加载时间线

js时间线

- 1、创建Document对象，开始解析web页面。解析HTML元素和他们的文本内容后添加Element对象和Text节点到文档中。这个阶段document.readyState = 'loading'。

- 2、遇到link外部css，创建线程加载，并继续解析文档。

- 3、遇到script外部js，并且没有设置async、defer，浏览器加载，并阻塞，等待js加载完成并执行该脚本，然后继续解析文档。

- 4、遇到script外部js，并且设置有async、defer，浏览器创建线程加载，并继续解析文档。
对于async属性的脚本，脚本加载完成后立即执行。（异步禁止使用document.write()）

- 5、遇到img等，先正常解析dom结构，然后浏览器异步加载src，并继续解析文档。

- 6、当文档解析完成，document.readyState = 'interactive'。

- 7、文档解析完成后，所有设置有defer的脚本会按照顺序执行。（注意与async的不同,但同样禁止使用document.write()）;

- 8、document对象触发DOMContentLoaded事件，这也标志着程序执行从同步脚本执行阶段，转化为事件驱动阶段。

- 9、当所有async的脚本加载完成并执行后、img等加载完成后，document.readyState = 'complete'，window对象触发load事件。

- 10、从此，以异步响应方式处理用户输入、网络事件等。


		window.onload = function () {}    dom加载完
		
		$(document).ready(function(){})   dom解析完
