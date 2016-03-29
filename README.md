### 移动端6位密码输入框
> 移动端开发时经常遇到6位密码框输入，输入当前格子后，自己获取下个格子焦点并跳转

``` javascript
$('.password').on('input', function(){
            var v = $(this).val();
            var l = v.length;
            if(l==6){
                $(this).blur();
                alert('输入完毕');
            }
        })
```