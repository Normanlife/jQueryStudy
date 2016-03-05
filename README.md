# jQueryStudy
撸jQuery API记录

#DOM
#.addClass()
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
    
#.Attr(),取值，改变值，赋值 三大功能
    <img id="greatphoto" src="brush-seller.jpg" alt="brush seller" />
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
#.hasClass('class name') 用于判断是否含有Class
#.html() 能拿到绑定标签的内容，包括标签
#.val()能拿到绑定标签的内容，不包括标签
<div class="demo-container">
  <div class="demo-box">Demonstration Box</div>
</div>
<script type="text/javascript">
    $('div.demo-container').html(); //<div class="demo-box">Demonstration Box</div>
    $('div.demo-container').html('<p>9128749137</p>'); //可替代原本的内容，替代，不是添加
</script>
#.prop(),区分于.attr(),用于检查属性的值是否生效，多用于checkbox
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
