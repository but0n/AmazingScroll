# AmazingScroll [![js](https://img.shields.io/badge/js-ES6.svg)](#)
## [demo](https://but0n.github.io/AmazingScroll/)
 - Tag: `HTML` `CSS` `jQuery`
 - Idea from [hooli.xyz](http://hooli.xyz), code by myself.

## Details
The website of hooli is funny, </br>
But the source code is not readable, </br>
They probably used some kind of framework from `Adobe`,</br>
So I try to use the built-in debugging tools of browser to figure out how does it works,</br>
At last, I figure out the solution and wrote this demo </br>

### Behind the scenes
 - The core function as follow:

```javascript
function img_transition() {
    var len = $(window).scrollTop();        
    $(".imageBar").each((i,e) => {
        var delta = 0.7,
            offset_val = len>=aim[i]?aim[i]+y-len+"px":"-100%",
            inner_offset = len>=aim[i]?-(aim[i]+y-len)*delta+"px":"-100%"
        $(e).css({"transform":"translateY("+offset_val+")"})
        $(e).children().eq(0).css({"transform":"translateY("+inner_offset+")"})
    });    
}
```

 - init and bind events:

```javascript
$(() => {
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
    $(".imageView").each((i,e) => {
        $(e).css({"background-image":"url(/img/"+i+".jpg)"});
    });
    $(".show").each((i,e) => {
        $(e).mousemove(() => {
            $(e).children().eq(0).addClass("bluron");
            $(e).children().eq(1).css({"display":"block"});
        });
        $(e).mouseout(() => {
            $(e).children().eq(0).removeClass("bluron");
            $(e).children().eq(1).css({"display":"none"});
        });
    })  
    $(".scrollTip").css({"animation":"pulse 1s infinite"});
    $(".show").each((i,e) => {
        $(e).click(() => {
            if(link[i]) window.open(link[i]);
            else alert("你可以在网上搜索有关 "+$(e).children().eq(1).text()+" 的内容")
        })
    })
}
```

 - Statements

```javascript
var aim = [],
    link = [,,,,,,"http://github.com/but0n", "http://instagram.com/but0n"],
    x = window.innerWidth,
    y = window.innerHeight;
```
