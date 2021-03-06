---
layout: page
title: "JavaScript ob_get_contents function"
comments: true
sharing: true
footer: true
sidebar: false
alias:
- /functions/view/ob_get_contents:895
- /functions/view/ob_get_contents
- /functions/view/895
- /functions/ob_get_contents:895
- /functions/895
---
<!-- Generated by Rakefile:build -->
A JavaScript equivalent of PHP's ob_get_contents

{% codeblock outcontrol/ob_get_contents.js lang:js https://raw.github.com/kvz/phpjs/master/functions/outcontrol/ob_get_contents.js raw on github %}
function ob_get_contents () {
  // http://kevin.vanzonneveld.net
  // +   original by: Brett Zamir (http://brett-zamir.me)
  // *     example 1: ob_get_contents();
  // *     returns 1: 'some buffer contents'

  this.php_js = this.php_js || {};
  var phpjs = this.php_js,
    ini = phpjs.ini,
    obs = phpjs.obs;
  if (!obs || !obs.length) {
    return (ini && ini.output_buffering && (typeof ini.output_buffering.local_value !== 'string' || ini.output_buffering.local_value.toLowerCase() !== 'off')) ? '' : false; // If output was already buffered, it would be available in obs
  }
  return obs[obs.length - 1].buffer; // Retrieve most recently added buffer contents
}
{% endcodeblock %}

 - [view on github](https://github.com/kvz/phpjs/blob/master/functions/outcontrol/ob_get_contents.js)
 - [edit on github](https://github.com/kvz/phpjs/edit/master/functions/outcontrol/ob_get_contents.js)

### Example 1
This code
{% codeblock lang:js example %}
ob_get_contents();
{% endcodeblock %}

Should return
{% codeblock lang:js returns %}
'some buffer contents'
{% endcodeblock %}


### Other PHP functions in the outcontrol extension
{% render_partial _includes/custom/outcontrol.html %}
