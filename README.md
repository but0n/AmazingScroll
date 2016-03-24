# but0n.github.io
>* `HTML` `CSS` `jQuery`
>* Idear from [hooli.xyz](http://hooli.xyz), code by myself.

## Detail
> The code of `hooli` is hard to read, </br>
> Cause they use a lib of `Adobe` or something,</br>
> So I use Firefox to copy one, </br>
> ***
> ###About js
> The most important function as follow
>
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


