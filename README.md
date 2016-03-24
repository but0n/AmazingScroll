# but0n.github.io
>* Tag: `HTML` `CSS` `jQuery`
>* Idear from [hooli.xyz](http://hooli.xyz), code by myself.

## Detail
The codes of `hooli` is hard to read, </br>
Cause they use a kind of library or something from `Adobe`,</br>
So I use Firefox to reason out how does it works,</br>
At last, I write it out.</br>

###About js
> The most important function as follow:

```javascript
function img_transition() {
    var len = $(window).scrollTop();        
    $(".imageBar").each(function(i,e) {
        var delta = 0.7,
            offset_val = len>=aim[i]?aim[i]+y-len+"px":"-100%",
            inner_offset = len>=aim[i]?-(aim[i]+y-len)*delta+"px":"-100%"
        $(e).css({"transform":"translateY("+offset_val+")"})
        $(e).children().eq(0).css({"transform":"translateY("+inner_offset+")"})
    });    
}
```

> init and bind events:

```javascript
$(function() {
    if(x<y) alert("原谅我目前还没有写移动端的布局。。暂时使用横屏浏览吧");
    init_layout();
    $(window).scroll(function() {img_transition()});
    $(window).resize(function(){
        init_layout();
        img_transition();
    });
    init(); 
});
```
```javascript
function init() {
    $(".imageView").each(function(i,e) {
        $(e).css({"background-image":"url(/img/"+i+".jpg)"});
    });
    $(".show").each(function(i,e) {
        $(e).mousemove(function() {
            $(e).children().eq(0).addClass("bluron");
            $(e).children().eq(1).css({"display":"block"});
        });
        $(e).mouseout(function() {
            $(e).children().eq(0).removeClass("bluron");
            $(e).children().eq(1).css({"display":"none"});
        });
    })  
    $(".scrollTip").css({"animation":"pulse 1s infinite"}); 
    $(".show").each(function(i,e) {
        $(e).click(function() {
            if(link[i]) window.open(link[i]);
            else alert("你可以在网上搜索有关 "+$(e).children().eq(1).text()+" 的内容")
        })
    })
}
```

> Init data

```javascript
var aim = [],
    link = [,,,,,,"http://github.com/but0n", "http://instagram.com/but0n"],
    x = window.innerWidth,
    y = window.innerHeight;
```


