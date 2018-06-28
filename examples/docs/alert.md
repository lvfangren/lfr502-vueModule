<style>
.dome-alert .w-alert:not(:first-child){
  margin-top: 10px;
}
</style>
<script>
 export default {
    methods: {
      hello() {
        alert('Hello World!');
      }
    }
  }
</script>
# Alert 警告
----
用于页面中展示重要的提示信息。
### 基本用法
页面中的非浮层元素，不会自动消失。
<div class="dome-alert demo-block">
  <h2>alerts</h2>
</div>

::: demo
```html

<div>
  <h2>alerts</h2>
</div>

```
:::



<div class="demo-block">
  <p>独自饮酒醉</p>
</div>

::: demo
```html
  <div>
    <p>独自饮酒醉</p>
  </div>
```
:::
