>>>
今天看书学到了个小技巧,
toString()接受一个参数，该参数声明的数字转字符串的进制。
所以，如果不会进制转换，就可以用这个

>>>
前端将数据转换成树状结构
http://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=2651555566&idx=1&sn=11ab4e180f7e32773fac3f92c33c21b5&chksm=8025512fb752d839371aed160f0bfdd42c0acd8fe6b321471098318f294bfb7e6de257a35b5f&mpshare=1&scene=1&srcid=#rd

>>>
在当前页面中引入其他页面
    (function load_home() {
      document.getElementById("viewDiv").innerHTML =
        '<object type="text/html" data="new.html" width="100%" height="100%"></object>';
    })()
>>>