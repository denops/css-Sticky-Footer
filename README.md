# css-Sticky-Footer
css Sticky Footer
一，描述：CSS的简单在于它易学，CSS的困难在于寻找更好的解决方案。在CSS的世界里，似乎没有完美这种说法。所以，现在介绍的CSS绝对底部，
只是目前个人见过的方案中比较完美的吧。
二，问题：先说我们为什么会使用到这个CSS底部布局解决方案:

当做一个页面时，如果页面内容很少，不足于填充一屏的窗口区域，按普通的布局，就会出现下面图片中的样子(也就是底部内容并没有位于窗口的底部，而留下了大量空白。
对于追未完美的设计师来说，这是不美观的。网上有一些解决方案，但会出现当改变窗口高度时，底部和正文重叠的BUG。尽管没有多少人会有事没事儿的去改变窗口高度，
但设计嘛，追求的就是尽善尽美;

代码写法

HTML代码:

<div id="wrap">
    <div id="main" class="clearfix">
        <div id="content">
        </div>
        <div id="side">
        </div>
    </div>
</div>
<div id="footer">
</div>

CSS代码:

下面是主要的CSS代码，让你的底部可以位于窗口的最下面:

html, body, #wrap {height: 100%;}
body > #wrap {height: auto; min-height: 100%;}
#main {padding-bottom: 150px;}  /* 必须使用和footer相同的高度 */
#footer {position: relative;margin-top: -150px;	height: 150px;clear:both;} /* footer高度的负值 */

说明: 需要注意的就是#main的padding值、footer的高度和负margin值，需要保持一致。

就是这么简单，不过还没完。如果你的主体是使用悬浮布局，还得解决一些浏览器的兼容问题，这里使用的重点是为了Goolge Chrome。

对#main部份进行著名的Clearfix Hack:

.clearfix:after {content: ".";
	display: block;
	height: 0;
	clear: both;
	visibility: hidden;}
.clearfix {display: inline-block;}
/* Hides from IE-mac \*/
* html .clearfix { height: 1%;}
.clearfix {display: block;}
/* End hide from IE-mac */
注: 该方案测试于两栏悬浮布局，兼容各大主流浏览器，包括Google Chrome。
甚至，创造该CSS的人还专门成立一个网站介绍这个CSS底部布局方案。不知道他有没有去申请专利:)http://www.cssstickyfooter.com/using-sticky-footer-code.html
