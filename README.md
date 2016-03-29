### 移动端6位密码输入框

> 做移动端项目时经常遇到6位密码框逐次输入的效果，即输入当前格子后，会自动获取下个格子焦点，直至用户输完6位密码后，自动提交后台。

**实现原理：**使用6个格子模拟框框，一个input[type='password']定位于最上方，通过设置间距与letter-spacing值，达到值与框一一对应的效果。运用input方法，获取密码框val值的长度，与6相匹配，验证成功则密码输入完毕。

#### HTML

``` HMTL
<div class="passContainer">
    <!-- 密码框  注意调整letter-spacing -->
    <input type="password" class="password">    
    <!-- 使用6个div模拟6个框框 -->
    <div class="passItem"></div>
    <div class="passItem"></div>
    <div class="passItem"></div>
    <div class="passItem"></div>
    <div class="passItem"></div>
    <div class="passItem"></div>
</div>
```

#### CSS

``` CSS
.passContainer {
            border: 1px solid #ccc;
            border-radius: 16px;
            width: 300px;
            height: 50px;
            overflow: hidden;
            padding: 0;
            position: relative;
        }
        .passItem {
            width: 16.66666%;
            height: 100%;
            float: left;
            margin: 0;
            box-sizing: border-box;
        }
        .passItem:not(:last-child) {
            border-right: inherit;
        }

        input {
            width: 100%;
            height: 100%;
            background-color: transparent;
            background: transparent;
            position: absolute;
            border: none;
            padding: 0 10px;
            outline: none;
            font-size: 40px;
            font-family: "courier new", sans-serif;
            letter-spacing: 0.62em;
            text-align: left;
            text-overflow: hidden;
        }
```


#### JAVASCRIPT

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