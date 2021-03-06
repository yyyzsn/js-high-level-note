###Welcome to use MarkDown

### selectAPI选择符    

> 下面两个参数：css选择符       
 
- [x]   操作的对象是document元素对象     
 
document.querySelector('.fl')-- 返回找到的第一个元素---一个对象          
document.querySelectorAll('#top')--返回匹配的所有元素---一个伪数组  
        
- [x]   操作的对象是Element元素对象      
  
var aLIs=oul.querySelectorAll('li').length;  
  
- [x]   querySelector和querySelectorAll都不是动态查询，文档结构动态改变时，querySelector和querySelectorAll对应的结果不会再次改变；---不会引起性能问题
而getElementById、getElementsByClassName等则是动态查询的，文档改变时，他们对应的值也会改变---会引起性能问题	   
  

####   验证操作对象oul是否符合后面参数中给定的选择符，符合返回true，反之返回false          

>  需要注意的是：该方法有浏览器兼容性问题--修改前缀      

console.log(oul.webkitMatchesSelector('ul'));   //true    


###   element.classList属性

ex:<div class="bd user disabled div containClass removeClass toggle1Class">

- [x]  element.classList的length属性 
	oDiv.classList.length;         

- [x]  add(class1, class2, ...)-----在元素中添加一个或多个类名         
	oDiv.classList.add('addClass');          

- [x] contains(class)----返回布尔值，判断指定的类名是否存在。----true - 元素包已经包含了该类名,false - 元素中不存在该类名         
	var bool=oDiv.classList.contains('containClass');            

- [x] remove(class1, class2, ...)---移除元素中一个或多个类名。         
	oDiv.classList.remove('removeClass');         

- [x] toggle(class, true|false)----	在元素中切换类名。
	第一个参数为要在元素中移除的类名，并返回 false。          
	如果该类名不存在则会在元素中添加类名，并返回 true。          
	
	第二个是可选参数，是个布尔值用于设置元素是否强制添加或移除类，不管该类名是否存在。例如：         
	移除一个 class: element.classList.toggle("classToRemove", false);          
	添加一个 class: element.classList.toggle("classToAdd", true); 
	
	oDiv.classList.toggle('toggle1Class');
### 焦点管理
> 焦点管理的范围：判断一个页面是否获得了焦点，--获得焦点的元素是哪个元素
- [x] document.activeElement----引用DOM中获得焦点的元素，返回获得焦点的元素
- [x] document.hasFocus()---判断某个元素是否获得焦点，返回true或者false

### document.readyState 属性返回当前文档的状态
	返回的可能值有两个：
		loading--文档加载中；
		complete--文档加载完毕。
### document.head--对文档head的引用----h5新增属性
	 document.body;  //引用文档的body元素
	 document.head;  //引用文档的head元素（h5新增属性）
	 //引用文档head属性的另一种方式
	 document.getElementsByTagName('head')[0];  
###  document.charset---文档字符集属性
	console.log(document.charset); //UTF-8  

### 自定义数据属性 data-
- [x] 法1         
//获取自定义属性值       
console.log(oDiv.getAttribute('data-src'));  //src       
//设置自定义属性值       
oDiv.setAttribute('data-src','src1');       
console.log(oDiv.getAttribute('data-src'));  //src1       

- [x] 法2               
//获取自定义属性值(dataset时，直接使用“name”，不要使用“data-name”)       
console.log(oDiv.dataset.name);  //name       
//设置自定义属性值       
console.log(oDiv.dataset.name="name1");  //name1       

- [x] 此外,新增自定义属性                   
oDiv.dataset.age=12;       
console.log(oDiv.dataset.age); //12	       
- [x] 删除，设置成null，或者delete                  
oDiv.dataset.name=null;       
delete oDiv.dataset.src; 
### innerHTML性能问题
	每设置一次innerHTML，则会创建一次HTML解析器，该解析器是在浏览器级别上

### 锚点设置的三种方式
- [x] a标签的href属性
    对应的锚点内容的展示方式：
    1.a--id
    2.a--name
    3.element--id
- [x] css样式element:target
   ```
    <a href="#div1">div1</a>
    <div style="width: 100px;height: 3000px;background: pink"></div>
    <div id="div1" style="width: 100px;height: 100px;border: 1px solid #ccc;">div1</div>

    样式：
    div:target{
        background: red;
    }
   ```
- [x] js-scrollIntoView()
    obj.scrollIntoView();

### 父.contains(子)  //A.contains(B):判断A是否是B的父元素，如果是返回true,反之，返回false

### innerText属性
    innerText属性可以过滤掉原有父元素中子元素的HTML标签，只留下相应的文本
    oCon.innerText=oCon.innerText;
    注：设置innerText属性,只会生成当前节点的一个子文本节点，
        并且为了确保只生成一个子文本节点，会对子文本节点中的内容进行重新编码，类似 < 会转化成 &lt；

### outerText属性


### innerHTML属性
   获取：调用它的的节点的子节点
   设置：调用它的的节点的子节点

### outerHTML属性

    获取：作用范围扩大到包括调用它的的节点及该节点的子节点
    设置：设置的内容完全替代调用它的节点

### style对象---获取／设置行内样式
    cssText：同时设置一个元素的多个行内样式
    ex：obj.style.cssText="width:100px;height:100px;border: 1px solid #ccc;";

### offsetParent
        body的相对父级是 null
        td 的相对父级是  table
        offsetParent  当前元素最近的定位父元素，没有定位父元素，则一路找到body


### 获取元素距离视口的距离（元素到视口的左偏移量）
    ```
    function getLeft(element) {
            var left=element.offsetLeft;
            var current=element.offsetParent;  //body 的相对父级为 null
            while (current!=null){
                left+=current.offsetLeft;
                current=current.offsetParent;
            }
            return left;

    }
    ```

### element.getBoundingClientRect():返回一个对象，该对象5个属性：top，bottom，left，right, width, height
    top:    元素距离页面视口 顶边 的距离
    bottom: 元素 底边 距离页面视口 顶边 的距离
    left:   元素距离页面视口 左边 的距离
    right:  元素 右边 距离页面视口 左边 的距离
    width： 元素的宽度
    height：元素的高度

### 遍历body的所有子元素
    document.querySelector('body').getElementsByTagName('*');