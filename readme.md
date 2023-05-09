<!-- {"s_msg":"this file was automatically generated","s_by":"f_generate_markdown.module.js","s_ts_created":"Tue May 09 2023 12:05:04 GMT+0200 (Central European Summer Time)","n_ts_created":1683626704526} -->
# usage
## import module
```javascript
import {
  f_s_html_syntax_highlighted, 
  s_css_syntax_highlight,
  f_add_css,
  f_append_child_with_syntax_highlight

} from "./client.module.js";
// import {f_s_html_syntax_highlighted} from "https://deno.land/x/f_s_html_syntax_highlighted@[version]/mod.js";
```
## convert json or js object to html with classses
```javascript

let s_html_syntax_highlighted = f_s_html_syntax_highlighted(
    {
      n: 23, 
      s: 'hello', 
      a_n: [1,2,3], 
      a_s: ['s', 'u', 'p'], 
      a: null, 
      b: false, 
      o: {
        n: 23, 
        s: 'hello', 
        a_n: [1,2,3], 
        a_s: ['s', 'u', 'p'], 
      }, 
      a_o: [
        {
          n: 2
        },
        {
          n: 3
        },
        {
          n: 4
        },
      ]
    }
)
```
## add the css that comes with the library
```javascript

f_add_css(
  s_css_syntax_highlight
);

```
## optionally add custom css
```javascript


f_add_css(
  `
  .my_custom_theme .s_html_syntax_highlighted .string { color: green; }
  .my_custom_theme .s_html_syntax_highlighted .number { color: darkorange; }
  .my_custom_theme .s_html_syntax_highlighted .boolean { color: blue; }
  .my_custom_theme .s_html_syntax_highlighted .null { color: magenta; }
  .my_custom_theme .s_html_syntax_highlighted .key { color: red; }
`
)
      
```
## create a html element with a class for the theme
```javascript
let o_div = document.createElement("div");
o_div.className = 'theme_dark'//dark or
o_div.className = 'theme_light'//light theme
o_div.className = 'my_custom_theme'//custom 
o_div.innerHTML = s_html_syntax_highlighted
document.body.appendChild(o_div);

```
## add html (with f_o_html_from_o_js)
```javascript
import {f_o_html_from_o_js} from "https://deno.land/x/f_o_html_from_o_js@0.7/mod.js";
document.body.appendChild(
  f_o_html_from_o_js(

    {
      a_o: [
        ...['theme_dark', 'theme_light'].map(function(
          s
        ){
          return {
            class: s, 
            innerHTML: s_html_syntax_highlighted
          }
        })
      ]
      
    }
  )
)
```
## use the function that does all for you
```javascript
f_append_child_with_syntax_highlight(
  document.body,
  {
    s:'test', 
    n:2, 
    b: false, 
    n: null, 
    a: [1,2], 
    o: {n:2, n:3}
  }, 
  'theme_light'
)
```