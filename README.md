# jQueryStudy
撸jQuery API记录

# DOM
## .addClass()
    $('p').last().addClass('new') 
    等价于：
    $('p:last').addClass('new')
    $('p').addClass(function(index, currentClass) {
        var addedClass;
        if (currentClass == 'red') {
            addedClass = 'new';
        }
        return addedClass;
    });//API文档里面可以生效，改变red属性的p为new，但实际测试没有生效？
    
## .Attr(),取值，改变值，赋值 三大功能
    <img id="greatphoto" src="brush-seller.jpg" alt="brush seller" />
    <script>
        $('#greatphoto').attr('alt') //brush seller;
        $('#greatphoto').attr('alt','BEIJING') // <img id="greatphoto" src="brush-seller.jpg" alt="BEIJING" />
        $('#greatphoto').attr('title','Photo') //img 里面新增 title='Photo'
        $('#greatphoto').attr({
    	    title:'Photo',
    	    alt: 'Beijing Brush Seller'
        }) //可同时操作几个值
    </script>
    <div>Zero-th <span></span></div>
    <div>First <span></span></div>
    <div>Second <span></span></div>
    <script type="text/javascript">
    $("div").attr("id", function(arr) {
            return "div-id" + arr;
        }) //给每个div加上id
        .each(function() {
            $("span").html("(ID = '<b>" + this.id + "</b>')");
        });
    </script>
## .hasClass('class name') 用于判断是否含有Class
## .html() 能拿到绑定标签的内容，包括标签
## .val()能拿到绑定标签的内容，不包括标签
    <div class="demo-container">
     <div class="demo-box">Demonstration Box</div>
    </div>
    <script type="text/javascript">
        $('div.demo-container').html(); //<div class="demo-box">Demonstration Box</div>
        $('div.demo-container').html('<p>9128749137</p>'); //可替代原本的内容，替代，不是添加
    </script>
## .prop(),区分于.attr(),用于检查属性的值是否生效，多用于checkbox;
    <input id="check1" type="checkbox" checked="checked">
    <label for="check1">Check me</label>
    <p></p>
    <script type="text/javascript">
    	$('#check1').change(function(){
    		$('p').html('.attr("checked"): <b>'+$(this).attr('checked')+'</b><br>'+
    			".prop('checked'): <b>"+$(this).prop('checked')+'</b><br>'+
    				".is(':checked'): <b>"+$(this).is(':checked'))+ "</b>";
    	});
    	//禁用复选框
    	$('#check1').prop('disabled',true);
    </script>

#  CSS
##  .offset() 
    //用于获取当前元素相对document的偏移值，提供 top，left 两个参数；
    <p>1111</p>
    <p>2222</p>
    <span></span>
    <script type="text/javascript">
    	$('p:last').offset({left:100,top:100}); //第二个P元素会偏移

       var r=$('p:last').offset();
    	$('span').html('left: '+r.left+'top: '+r.top); //能在span中显示第二个P元素的偏移值；
    </script>
##  .position() 
    //区别于上面offst，.position()能获得相对于父元素的偏移值。
## .scrollLeft()
    //获取滚动条向左移动的水平位置，（加参数）或者设置滚动条向左移动的水平位置
    （只传数字，默认加px单位）
## .scrollTop() 
    //同上
    （只传数字，默认加px单位）
## .height() .width()
    //获取元素的高/宽，或者加数字改变元素高/宽 （只传数字，默认加px单位）
    //注意.height('value')设置的容器宽度是根据CSS box-sizing属性来定的,   将这个属性值改成border-box，将造成这个函数改变这个容器的outerHeight，而不是原来的内容高度。 
## .innerHeight() .innerWidth()
    //区别：
    <style>
    p {
      height: 30px;
       border: 1px solid black;
        padding: 2px;
    
    }
    </style>
    <p>Hello</p>
    <span></span>
    <br>
    <span></span>
    
    <script>
    var p = $("p:first");
    $("span:first").text("innerHeight:" + p.innerHeight()); //34
    $("span:last").text("Height:" + p.height());//30
    //innerHeight不包含margin
    //innerHeight不能检测 document 和 windows 的高，需要用 .height()

    </script>
