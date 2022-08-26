# Reducing the private key through scalar multiplication using the ECPy + Google Colab library


<meta content="  CRYPTO DEEP TECH In this article, we will try to show how you can reduce the private key knowing only the leak from the  «BLOCKCHAIN ​​FOL..." property="og:description">
<meta content="https://lh3.googleusercontent.com/blogger_img_proxy/ANbyha31eSyRqjCtsPEV5lERNZyvAOXKl5VbbvGRaW2OYbDvgBO5SBLz7pHUUPUT_29RBlQN-61NdVf35zU5wPp2ETSeHuwTFy6gCcIkfCVV1ptTYlxBnw=w1200-h630-n-k-no-nu" property="og:image">
<title>CRYPTO DEEP: Reducing the private key through scalar multiplication using the ECPy + Google Colab library</title>
<style id="page-skin-1" type="text/css"><!--
/*
-----------------------------------------------
Blogger Template Style
Name:     Travel
Designer: Sookhee Lee
URL:      www.plyfly.net
----------------------------------------------- */
/* Content
----------------------------------------------- */
body {
font: normal normal 16px 'Courier New', Courier, FreeMono, monospace;
color: #0097cb;
background: #a7cef7 url(https://themes.googleusercontent.com/image?id=0BwVBOzw_-hbMOWRhNDdjMjMtYWJkMi00ZmQwLTg3OGEtYjhmMWMxZGQzNmNm) no-repeat fixed top center /* Credit: mammamaart (http://www.istockphoto.com/portfolio/mammamaart?platform=blogger) */;
}
html body .region-inner {
min-width: 0;
max-width: 100%;
width: auto;
}
a:link {
text-decoration:none;
color: #4fa8d5;
}
a:visited {
text-decoration:none;
color: #407189;
}
a:hover {
text-decoration:underline;
color: #f85c00;
}
.content-outer .content-cap-top {
height: 5px;
background: transparent url(https://resources.blogblog.com/blogblog/data/1kt/travel/bg_container.png) repeat-x scroll top center;
}
.content-outer {
margin: 0 auto;
padding-top: 20px;
}
.content-inner {
background: #ffffff url(https://resources.blogblog.com/blogblog/data/1kt/travel/bg_container.png) repeat-x scroll top left;
background-position: left -5px;
background-color: #ffffff;
padding: 20px;
}
.main-inner .date-outer {
margin-bottom: 2em;
}
/* Header
----------------------------------------------- */
.header-inner .Header .titlewrapper,
.header-inner .Header .descriptionwrapper {
padding-left: 10px;
padding-right: 10px;
}
.Header h1 {
font: normal normal 60px 'Trebuchet MS',Trebuchet,sans-serif;
color: #000000;
}
.Header h1 a {
color: #000000;
}
.Header .description {
font-size: 130%;
}
/* Tabs
----------------------------------------------- */
.tabs-inner {
margin: 1em 0 0;
padding: 0;
}
.tabs-inner .section {
margin: 0;
}
.tabs-inner .widget ul {
padding: 0;
background: #000000 none repeat scroll top center;
}
.tabs-inner .widget li {
border: none;
}
.tabs-inner .widget li a {
display: inline-block;
padding: 1em 1.5em;
color: #ffffff;
font: normal bold 16px 'Trebuchet MS',Trebuchet,sans-serif;
}
.tabs-inner .widget li.selected a,
.tabs-inner .widget li a:hover {
position: relative;
z-index: 1;
background: #000000 none repeat scroll top center;
color: #ffffff;
}
/* Headings
----------------------------------------------- */
h2 {
font: normal bold 14px 'Trebuchet MS',Trebuchet,sans-serif;
color: #000000;
}
.main-inner h2.date-header {
font: normal normal 14px 'Trebuchet MS',Trebuchet,sans-serif;
color: #666666;
}
.footer-inner .widget h2,
.sidebar .widget h2 {
padding-bottom: .5em;
}
/* Main
----------------------------------------------- */
.main-inner {
padding: 20px 0;
}
.main-inner .column-center-inner {
padding: 10px 0;
}
.main-inner .column-center-inner .section {
margin: 0 10px;
}
.main-inner .column-right-inner {
margin-left: 20px;
}
.main-inner .fauxcolumn-right-outer .fauxcolumn-inner {
margin-left: 20px;
background: #ffffff none repeat scroll top left;
}
.main-inner .column-left-inner {
margin-right: 20px;
}
.main-inner .fauxcolumn-left-outer .fauxcolumn-inner {
margin-right: 20px;
background: #ffffff none repeat scroll top left;
}
.main-inner .column-left-inner,
.main-inner .column-right-inner {
padding: 15px 0;
}
/* Posts
----------------------------------------------- */
h3.post-title {
margin-top: 20px;
}
h3.post-title a {
font: normal bold 20px 'Trebuchet MS',Trebuchet,sans-serif;
color: #000000;
}
h3.post-title a:hover {
text-decoration: underline;
}
.main-inner .column-center-outer {
background: rgba(0,0,0,0) none repeat scroll top left;
_background-image: none;
}
.post-body {
line-height: 1.4;
position: relative;
}
.post-header {
margin: 0 0 1em;
line-height: 1.6;
}
.post-footer {
margin: .5em 0;
line-height: 1.6;
}
#blog-pager {
font-size: 140%;
}
#comments {
background: #cccccc none repeat scroll top center;
padding: 15px;
}
#comments .comment-author {
padding-top: 1.5em;
}
#comments h4,
#comments .comment-author a,
#comments .comment-timestamp a {
color: #000000;
}
#comments .comment-author:first-child {
padding-top: 0;
border-top: none;
}
.avatar-image-container {
margin: .2em 0 0;
}
/* Comments
----------------------------------------------- */
#comments a {
color: #000000;
}
.comments .comments-content .icon.blog-author {
background-repeat: no-repeat;
background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAASCAYAAABWzo5XAAAAAXNSR0IArs4c6QAAAAZiS0dEAP8A/wD/oL2nkwAAAAlwSFlzAAALEgAACxIB0t1+/AAAAAd0SU1FB9sLFwMeCjjhcOMAAAD+SURBVDjLtZSvTgNBEIe/WRRnm3U8RC1neQdsm1zSBIU9VVF1FkUguQQsD9ITmD7ECZIJSE4OZo9stoVjC/zc7ky+zH9hXwVwDpTAWWLrgS3QAe8AZgaAJI5zYAmc8r0G4AHYHQKVwII8PZrZFsBFkeRCABYiMh9BRUhnSkPTNCtVXYXURi1FpBDgArj8QU1eVXUzfnjv7yP7kwu1mYrkWlU33vs1QNu2qU8pwN0UpKoqokjWwCztrMuBhEhmh8bD5UDqur75asbcX0BGUB9/HAMB+r32hznJgXy2v0sGLBcyAJ1EK3LFcbo1s91JeLwAbwGYu7TP/3ZGfnXYPgAVNngtqatUNgAAAABJRU5ErkJggg==);
}
.comments .comments-content .loadmore a {
border-top: 1px solid #000000;
border-bottom: 1px solid #000000;
}
.comments .comment-thread.inline-thread {
background: rgba(0,0,0,0);
}
.comments .continue {
border-top: 2px solid #000000;
}
/* Widgets
----------------------------------------------- */
.sidebar .widget {
border-bottom: 2px solid #000000;
padding-bottom: 10px;
margin: 10px 0;
}
.sidebar .widget:first-child {
margin-top: 0;
}
.sidebar .widget:last-child {
border-bottom: none;
margin-bottom: 0;
padding-bottom: 0;
}
.footer-inner .widget,
.sidebar .widget {
font: normal normal 16px 'Courier New', Courier, FreeMono, monospace;
color: #666666;
}
.sidebar .widget a:link {
color: #666666;
text-decoration: none;
}
.sidebar .widget a:visited {
color: #436590;
}
.sidebar .widget a:hover {
color: #666666;
text-decoration: underline;
}
.footer-inner .widget a:link {
color: #4fa8d5;
text-decoration: none;
}
.footer-inner .widget a:visited {
color: #407189;
}
.footer-inner .widget a:hover {
color: #4fa8d5;
text-decoration: underline;
}
.widget .zippy {
color: #000000;
}
.footer-inner {
background: transparent none repeat scroll top center;
}
/* Mobile
----------------------------------------------- */
body.mobile  {
background-size: 100% auto;
}
body.mobile .AdSense {
margin: 0 -10px;
}
.mobile .body-fauxcolumn-outer {
background: transparent none repeat scroll top left;
}
.mobile .footer-inner .widget a:link {
color: #666666;
text-decoration: none;
}
.mobile .footer-inner .widget a:visited {
color: #436590;
}
.mobile-post-outer a {
color: #000000;
}
.mobile-link-button {
background-color: #4fa8d5;
}
.mobile-link-button a:link, .mobile-link-button a:visited {
color: #ffffff;
}
.mobile-index-contents {
color: #0097cb;
}
.mobile .tabs-inner .PageList .widget-content {
background: #000000 none repeat scroll top center;
color: #ffffff;
}
.mobile .tabs-inner .PageList .widget-content .pagelist-arrow {
border-left: 1px solid #ffffff;
}

--></style>
<style id="template-skin-1" type="text/css"><!--
body {
min-width: 860px;
}
.content-outer, .content-fauxcolumn-outer, .region-inner {
min-width: 860px;
max-width: 860px;
_width: 860px;
}
.main-inner .columns {
padding-left: 0px;
padding-right: 260px;
}
.main-inner .fauxcolumn-center-outer {
left: 0px;
right: 260px;
/* IE6 does not respect left and right together */
_width: expression(this.parentNode.offsetWidth -
parseInt("0px") -
parseInt("260px") + 'px');
}
.main-inner .fauxcolumn-left-outer {
width: 0px;
}
.main-inner .fauxcolumn-right-outer {
width: 260px;
}
.main-inner .column-left-outer {
width: 0px;
right: 100%;
margin-left: -0px;
}
.main-inner .column-right-outer {
width: 260px;
margin-right: -260px;
}
#layout {
min-width: 0;
}
#layout .content-outer {
min-width: 0;
width: 800px;
}
#layout .region-inner {
min-width: 0;
width: auto;
}
body#layout div.add_widget {
padding: 8px;
}
body#layout div.add_widget a {
margin-left: 32px;
}
--></style>
<style>
    body {background-image:url(https\:\/\/themes.googleusercontent.com\/image?id=0BwVBOzw_-hbMOWRhNDdjMjMtYWJkMi00ZmQwLTg3OGEtYjhmMWMxZGQzNmNm);}
    
@media (max-width: 200px) { body {background-image:url(https\:\/\/themes.googleusercontent.com\/image?id=0BwVBOzw_-hbMOWRhNDdjMjMtYWJkMi00ZmQwLTg3OGEtYjhmMWMxZGQzNmNm&options=w200);}}
@media (max-width: 400px) and (min-width: 201px) { body {background-image:url(https\:\/\/themes.googleusercontent.com\/image?id=0BwVBOzw_-hbMOWRhNDdjMjMtYWJkMi00ZmQwLTg3OGEtYjhmMWMxZGQzNmNm&options=w400);}}
@media (max-width: 800px) and (min-width: 401px) { body {background-image:url(https\:\/\/themes.googleusercontent.com\/image?id=0BwVBOzw_-hbMOWRhNDdjMjMtYWJkMi00ZmQwLTg3OGEtYjhmMWMxZGQzNmNm&options=w800);}}
@media (max-width: 1200px) and (min-width: 801px) { body {background-image:url(https\:\/\/themes.googleusercontent.com\/image?id=0BwVBOzw_-hbMOWRhNDdjMjMtYWJkMi00ZmQwLTg3OGEtYjhmMWMxZGQzNmNm&options=w1200);}}
/* Last tag covers anything over one higher than the previous max-size cap. */
@media (min-width: 1201px) { body {background-image:url(https\:\/\/themes.googleusercontent.com\/image?id=0BwVBOzw_-hbMOWRhNDdjMjMtYWJkMi00ZmQwLTg3OGEtYjhmMWMxZGQzNmNm&options=w1600);}}
  </style>
<link href="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/authorization.css" media="all" onload="if(media!=&#39;all&#39;)media=&#39;all&#39;" rel="stylesheet"><noscript><link href='https://www.blogger.com/dyn-css/authorization.css?targetBlogID=6212855055824365162&amp;zx=71240175-dc4e-419c-95af-1311f8bf1dab' rel='stylesheet'/></noscript>
<meta name="google-adsense-platform-account" content="ca-host-pub-1556223355139109">
<meta name="google-adsense-platform-domain" content="blogspot.com">

<script src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/cb=gapi.loaded_2" async=""></script><script type="text/javascript" src="https://pagead2.googlesyndication.com/pagead/js/google_top_exp.js"></script><style>.gc-bubbleDefault{background-color:transparent!important;text-align:left;padding:0!important;margin:0!important;border:0!important;table-layout:auto!important}.gc-reset{background-color:transparent!important;border:0!important;padding:0!important;margin:0!important;text-align:left}.pls-bubbleTop{border-bottom:1px solid #ccc!important}.pls-contentLeft,.pls-topTail,.pls-vertShimLeft{background-image:url(//ssl.gstatic.com/s2/oz/images/stars/po/bubblev1/border_3.gif)!important}.pls-topTail{background-repeat:repeat-x!important;background-position:bottom!important}.pls-vertShim{background-color:#fff!important;text-align:right}.tbl-grey .pls-vertShim{background-color:#f5f5f5!important}.pls-vertShimLeft{background-repeat:repeat-y!important;background-position:100%!important;height:4px}.pls-vertShimRight{height:4px}.pls-confirm-container .pls-vertShim{background-color:#fff3c2!important}.pls-contentWrap{background-color:#fff!important;position:relative!important;vertical-align:top}.pls-contentLeft{background-repeat:repeat-y;background-position:100%;vertical-align:top}.pls-dropRight{background-image:url(//ssl.gstatic.com/s2/oz/images/stars/po/bubblev1/bubbleDropR_3.png)!important;background-repeat:repeat-y!important;vertical-align:top}.pls-dropBL,.pls-dropTR .pls-dropBR,.pls-tailleft,.pls-vert,.pls-vert img{vertical-align:top}.pls-dropBottom{background-image:url(//ssl.gstatic.com/s2/oz/images/stars/po/bubblev1/bubbleDropB_3.png)!important;background-repeat:repeat-x!important;width:100%;vertical-align:top}.pls-topLeft{background:inherit!important;text-align:right;vertical-align:bottom}.pls-topRight{background:inherit!important;text-align:left;vertical-align:bottom}.pls-bottomLeft{background:inherit!important;text-align:right}.pls-bottomRight{background:inherit!important;text-align:left;vertical-align:top}.pls-tailbottom,.pls-tailleft,.pls-tailright,.pls-tailtop{display:none;position:relative}.pls-dropBL,.pls-dropBR,.pls-dropTR,.pls-tailbottom,.pls-tailleft,.pls-tailright,.pls-tailtop{background-image:url(//ssl.gstatic.com/s2/oz/images/stars/po/bubblev1/bubbleSprite_3.png)!important;background-repeat:no-repeat}.tbl-grey .pls-dropBL,.tbl-grey .pls-dropBR,.tbl-grey .pls-dropTR,.tbl-grey .pls-tailbottom,.tbl-grey .pls-tailleft,.tbl-grey .pls-tailright,.tbl-grey .pls-tailtop{background-image:url(//ssl.gstatic.com/s2/oz/images/stars/po/bubblev1/bubbleSprite-grey.png)!important}.pls-tailbottom{background-position:-23px 0}.pls-confirm-container .pls-tailbottom{background-position:-23px -10px}.pls-tailtop{background-position:-19px -20px}.pls-tailright{background-position:0 0}.pls-tailleft{background-position:-10px 0}.pls-tailtop{vertical-align:top}.gc-bubbleDefault td{line-height:0;font-size:0}.pls-tailbottom,.pls-topLeft img,.pls-topRight img{vertical-align:bottom}.bubbleDropTR,.pls-bottomLeft,.pls-bottomLeft img,.pls-dropBottom img,.pls-dropBottomL img,.pls-dropBottomR img{vertical-align:top}.pls-dropTR{background-position:0 -22px}.pls-dropBR{background-position:0 -27px}.pls-dropBL{background-position:0 -16px}.pls-spacerbottom,.pls-spacerleft,.pls-spacerright,.pls-spacertop{position:static!important}.pls-spinner{bottom:0;position:absolute;left:0;margin:auto;right:0;top:0}</style><script async="" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/lazy.min.js"></script></head>
<body class=" variant-flight">
<div class="navbar section" id="navbar" name="Navbar"><div class="widget Navbar" data-version="1" id="Navbar1"><script src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/cb=gapi.loaded_1" async=""></script><script src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/cb=gapi(1).loaded_0" async=""></script><script type="text/javascript">
    function setAttributeOnload(object, attribute, val) {
      if(window.addEventListener) {
        window.addEventListener('load',
          function(){ object[attribute] = val; }, false);
      } else {
        window.attachEvent('onload', function(){ object[attribute] = val; });
      }
    }
  </script>
<div id="navbar-iframe-container"><iframe ng-non-bindable="" frameborder="0" hspace="0" marginheight="0" marginwidth="0" scrolling="no" style="" tabindex="0" vspace="0" width="100%" id="navbar-iframe" name="navbar-iframe" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/navbar.html"></iframe></div>
<script type="text/javascript" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/plusone.js" gapi_processed="true"></script>
<script type="text/javascript">
      gapi.load("gapi.iframes:gapi.iframes.style.bubble", function() {
        if (gapi.iframes && gapi.iframes.getContext) {
          gapi.iframes.getContext().openChild({
              url: 'https://www.blogger.com/navbar.g?targetBlogID\x3d6212855055824365162\x26blogName\x3dCRYPTO+DEEP\x26publishMode\x3dPUBLISH_MODE_BLOGSPOT\x26navbarType\x3dLIGHT\x26layoutType\x3dLAYOUTS\x26searchRoot\x3dhttps://cryptodeep.blogspot.com/search\x26blogLocale\x3den\x26v\x3d2\x26homepageUrl\x3dhttps://cryptodeep.blogspot.com/\x26targetPostID\x3d9146845080846446300\x26blogPostOrPageUrl\x3dhttps://cryptodeep.blogspot.com/2022/08/reducing-private-key-through-scalar.html\x26vt\x3d5064238472975535092',
              where: document.getElementById("navbar-iframe-container"),
              id: "navbar-iframe"
          });
        }
      });
    </script><script type="text/javascript">
(function() {
var script = document.createElement('script');
script.type = 'text/javascript';
script.src = '//pagead2.googlesyndication.com/pagead/js/google_top_exp.js';
var head = document.getElementsByTagName('head')[0];
if (head) {
head.appendChild(script);
}})();
</script>
</div></div>
<div class="body-fauxcolumns">
<div class="fauxcolumn-outer body-fauxcolumn-outer">
<div class="cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left">
<div class="fauxborder-right"></div>
<div class="fauxcolumn-inner">
</div>
</div>
<div class="cap-bottom">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
</div>
</div>
<div class="content">
<div class="content-fauxcolumns">
<div class="fauxcolumn-outer content-fauxcolumn-outer">
<div class="cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left">
<div class="fauxborder-right"></div>
<div class="fauxcolumn-inner">
</div>
</div>
<div class="cap-bottom">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
</div>
</div>
<div class="content-outer">
<div class="content-cap-top cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left content-fauxborder-left">
<div class="fauxborder-right content-fauxborder-right"></div>
<div class="content-inner">
<header>
<div class="header-outer">
<div class="header-cap-top cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left header-fauxborder-left">
<div class="fauxborder-right header-fauxborder-right"></div>
<div class="region-inner header-inner">
<div class="header section" id="header" name="Header"><div class="widget Header" data-version="1" id="Header1">
<div id="header-inner">
<a href="https://cryptodeep.blogspot.com/" style="display: block">
<img alt="CRYPTO DEEP" height="280px; " id="Header1_headerimg" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/A18.png" style="display: block" width="1400px; ">
</a>
<div class="descriptionwrapper">
<p class="description"><span>Financial security of data and secp256k1 elliptic curve cryptography against weak ECDSA signatures in BITCOIN cryptocurrency</span></p>
</div>
</div>
</div></div>
</div>
</div>
<div class="header-cap-bottom cap-bottom">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
</div>
</header>
<div class="tabs-outer">
<div class="tabs-cap-top cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left tabs-fauxborder-left">
<div class="fauxborder-right tabs-fauxborder-right"></div>
<div class="region-inner tabs-inner">
<div class="tabs no-items section" id="crosscol" name="Cross-Column"></div>
<div class="tabs no-items section" id="crosscol-overflow" name="Cross-Column 2"></div>
</div>
</div>
<div class="tabs-cap-bottom cap-bottom">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
</div>
<div class="main-outer">
<div class="main-cap-top cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left main-fauxborder-left">
<div class="fauxborder-right main-fauxborder-right"></div>
<div class="region-inner main-inner">
<div class="columns fauxcolumns">
<div class="fauxcolumn-outer fauxcolumn-center-outer">
<div class="cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left">
<div class="fauxborder-right"></div>
<div class="fauxcolumn-inner">
</div>
</div>
<div class="cap-bottom">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
</div>
<div class="fauxcolumn-outer fauxcolumn-left-outer">
<div class="cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left">
<div class="fauxborder-right"></div>
<div class="fauxcolumn-inner">
</div>
</div>
<div class="cap-bottom">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
</div>
<div class="fauxcolumn-outer fauxcolumn-right-outer">
<div class="cap-top">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
<div class="fauxborder-left">
<div class="fauxborder-right"></div>
<div class="fauxcolumn-inner">
</div>
</div>
<div class="cap-bottom">
<div class="cap-left"></div>
<div class="cap-right"></div>
</div>
</div>
<!-- corrects IE6 width calculation -->
<div class="columns-inner">
<div class="column-center-outer">
<div class="column-center-inner">
<div class="main section" id="main" name="Main"><div class="widget Blog" data-version="1" id="Blog1">
<div class="blog-posts hfeed">

          <div class="date-outer">
        
<h2 class="date-header"><span>Friday, August 26, 2022</span></h2>

          <div class="date-posts">
        
<div class="post-outer">
<div class="post hentry uncustomized-post-template" itemprop="blogPost" itemscope="itemscope" itemtype="http://schema.org/BlogPosting">
<meta content="https://i.ytimg.com/vi/zu2yiaZ_LOs/hqdefault.jpg" itemprop="image_url">
<meta content="6212855055824365162" itemprop="blogId">
<meta content="9146845080846446300" itemprop="postId">
<a name="9146845080846446300"></a>
<h3 class="post-title entry-title" itemprop="name">
Reducing the private key through scalar multiplication using the ECPy + Google Colab library
</h3>
<div class="post-header">
<div class="post-header-line-1"></div>
</div>
<div class="post-body entry-content" id="post-body-9146845080846446300" itemprop="description articleBody">
<p>&nbsp;<a class="url fn n" href="https://cryptodeeptech.ru/author/cryptodeeptech/" style="box-sizing: inherit; color: #d12223; font-family: Lato, sans-serif; font-size: 0.9em; outline: 0px; text-decoration-line: none; text-transform: uppercase;">CRYPTO DEEP TECH</a></p><div class="entry-content" style="background-color: white; border-bottom: 1px solid rgb(238, 238, 238); box-sizing: inherit; color: #333333; font-family: Lato, sans-serif; font-size: 16px; margin: 1em 0px; padding-bottom: 1em;"><div class="entry-meta" style="align-items: center; box-sizing: inherit; display: flex; margin-bottom: 1.5em;"></div><div class="entry-content" style="border-bottom: 1px solid rgb(238, 238, 238); box-sizing: inherit; margin: 1em 0px; padding-bottom: 1em;"><h1 class="has-text-align-center" style="box-sizing: inherit; clear: both; color: #191308; font-size: 3rem; line-height: 1.2; margin: 0.5rem 0px; text-align: center;"><iframe allowfullscreen="allowfullscreen" data-mce-fragment="1" frameborder="0" height="315" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/zu2yiaZ_LOs.html" style="box-sizing: inherit; max-width: 100%;" title="Youtube video player" width="560"></iframe></h1><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">In this article, we will try to show how you can reduce the private key knowing only the leak from the&nbsp;<a href="https://pastebin.com/eLMYtzV8" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">«BLOCKCHAIN ​​FOLBIT LEAKS»</a>&nbsp;list and the public key from&nbsp;<a href="https://en.wikipedia.org/wiki/Unspent_transaction_output" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">«UTXO»</a>&nbsp;.<br style="box-sizing: inherit;">In the experimental part, we will use&nbsp;<a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">the 08ReducePrivateKey</a>&nbsp;scripts and restore the Bitcoin Wallet.</p><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><em style="box-sizing: inherit;"><u style="box-sizing: inherit;">Elliptic curve scalar multiplication</u></em>&nbsp;is the operation of adding a point<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">P</code>to the curve<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">k</code>times.</p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">Q=kP=P+P+P, k times</code></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">P</code>is&nbsp;<em style="box-sizing: inherit;">a point on an elliptic curve</em>&nbsp;, and&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">k</code>is&nbsp;<em style="box-sizing: inherit;">a large natural number</em>&nbsp;.</p><p style="box-sizing: inherit; margin: 0px;">In any primitive implementations,&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">ECC</code>scalar multiplication is the main computational operation.&nbsp;A key factor in improving efficiency&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">ECC</code>is the implementation of fast scalar multiplication.&nbsp;Therefore, many researchers have proposed various studies of&nbsp;<a href="https://habr.com/ru/post/680932/" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><em style="box-sizing: inherit;"><u style="box-sizing: inherit;">accelerated scalar multiplication</u></em></a>&nbsp;.</p></blockquote><h2 style="box-sizing: inherit; clear: both; color: #191308; font-size: 2rem; line-height: 1.2; margin: 0.5rem 0px;">Let’s use the ECPy library</h2><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">ECPy provides:</h3><ul style="box-sizing: border-box; list-style-image: initial; list-style-position: initial; margin: 0px 0px 1rem 3em; padding-left: 0.1em;"><li style="box-sizing: inherit; margin: 0.5em 0px;">ECDSA signatures</li><li style="box-sizing: inherit; margin: 0.5em 0px;">Ed25519 signatures</li><li style="box-sizing: inherit; margin: 0.5em 0px;">ECSchnorr signatures</li><li style="box-sizing: inherit; margin: 0.5em 0px;">Borromean signatures</li><li style="box-sizing: inherit; margin: 0.5em 0px;">point operations</li></ul><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin: 0px;"><em style="box-sizing: inherit;">In many of our studies, we use the library&nbsp;</em><code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">ECPy</code><em style="box-sizing: inherit;">and</em><code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">Google Colab</code></p></blockquote><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Open&nbsp;<a href="https://github.com/demining/TerminalGoogleColab" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">[TerminalGoogleColab]</span></a></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><span style="box-sizing: inherit; font-weight: bolder;">Let’s use the&nbsp;</span><a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey" style="background-color: transparent; box-sizing: inherit; color: black;"><span style="box-sizing: inherit; font-weight: bolder;">«08ReducePrivateKey»</span></a>&nbsp;repository</p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">git clone https://github.com/demining/CryptoDeepTools.git

cd CryptoDeepTools/08ReducePrivateKey/

ls</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/201da1f9f8e93fbbeae07e8e9af7723e.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Install the ECPy library:</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">pip3 install ECPy</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/d7c1d7b35f8246398d24a4e40744a43e.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin: 0px;"><em style="box-sizing: inherit;">Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">maxwell.py</a>&nbsp;,&nbsp;<em style="box-sizing: inherit;">save</em>&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">код</code>&nbsp;and run in terminal<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">Google Colab</code></p></blockquote><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">from ecpy.curves     import Curve,Point

cv = Curve.get_curve('secp256k1')
G  = Point(0x79be667ef9dcbbac55a06295ce870b07029bfcdb2dce28d959f2815b16f81798,
           0x483ada7726a3c4655da4fbfc0e1108a8fd17b448a68554199c47d08ffb10d4b8,
           cv)
x  = 0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a1

PUBKEY  = x*G

print(PUBKEY)</code></pre><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Run command:</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">python3 maxwell.py</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/b6bc190fe89cda2172f7b29a30aeaf16.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Result:</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">(0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63 , 0xc0c686408d517dfd67c2367651380d00d126e4229631fd03f8ff35eef1a61e3c)
</code></pre><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Pay attention to the x coordinate</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">x value = 3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63

0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63</code></pre><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin: 0px;">This&nbsp;<em style="box-sizing: inherit;">public key</em>&nbsp;is called&nbsp;<a href="https://bitcointalk.org/index.php?topic=1118704.msg11862486#msg11862486" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><u style="box-sizing: inherit;">«Maxwell’s vanity public key»</u></a></p></blockquote><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a0 --&gt; 0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63, 0x3f3979bf72ae8202983dc989aec7f2ff2ed91bdd69ce02fc0700ca100e59ddf3
0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a1 --&gt; 0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63, 0xc0c686408d517dfd67c2367651380d00d126e4229631fd03f8ff35eef1a61e3c

p = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141

((p-1)/2) = 0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a0

0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63
</code></pre><h4 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.5rem; line-height: 1.2; margin: 0.5rem 0px;">We’ll come back to this public key!</h4><h2 style="box-sizing: inherit; clear: both; color: #191308; font-size: 2rem; line-height: 1.2; margin: 0.5rem 0px;">Let’s move on to the experimental part:</h2><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">We have three different Bitcoin Addresses with a balance&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">100 BTC</code>&nbsp;<em style="box-sizing: inherit;">or higher</em>&nbsp;from the&nbsp;<a href="https://bitinfocharts.com/top-100-richest-bitcoin-addresses.html" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">Bitcoin Rich List</span></a></p><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><span style="box-sizing: inherit; font-weight: bolder;"><a href="https://www.blockchain.com/btc/address/1KpHWkpG7BGxDuSJKYPYVvNSC6womEZdTu" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">1KpHWkpG7BGxDuSJKYPYVvNSC6womEZdTu</a></span></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><span style="box-sizing: inherit; font-weight: bolder;"><a href="https://www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm</a></span></p><p style="box-sizing: inherit; margin: 0px;"><span style="box-sizing: inherit; font-weight: bolder;"><a href="https://www.blockchain.com/btc/address/1GrTCkqqcXhVTXoQkPJjU5LuFKgAvC3iqJ" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">1GrTCkqqcXhVTXoQkPJjU5LuFKgAvC3iqJ</a></span></p></blockquote><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Let&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">UTXO</code>‘s get these Bitcoin Addresses and now we have three signatures&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">ECDSA</code>&nbsp;<em style="box-sizing: inherit;">(Apply scripts&nbsp;</em><a href="https://github.com/demining/CryptoDeepTools/tree/main/01BlockchainGoogleDrive" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><em style="box-sizing: inherit;">01BlockchainGoogleDrive</em></a><em style="box-sizing: inherit;">&nbsp;)</em></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><a href="https://blockchain.info/rawtx/c1ea2c9e48ce632488817781f89730d77cd4121f1c8f70a4be44d2a15e8e08d0?format=hex" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">c1ea2c9e48ce632488817781f89730d77cd4121f1c8f70a4be44d2a15e8e08d0</span></a><br style="box-sizing: inherit;"><a href="https://blockchain.info/rawtx/37dadae30c6f7c6c4a2c930db979494783005a8e94d6861039fed21e3fa859b9?format=hex" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">37dadae30c6f7c6c4a2c930db979494783005a8e94d6861039fed21e3fa859b9</span></a><br style="box-sizing: inherit;"><a href="https://blockchain.info/rawtx/9dacfc8243109475383d5b30e8d5f0ba23d023bd47649064c208d4586b278436?format=hex" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">9dacfc8243109475383d5b30e8d5f0ba23d023bd47649064c208d4586b278436</span></a></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Get&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">RawTX</code>for three different Bitcoin Addresses</p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">01000000017fbdd4c9991d0ba4fb0a0c06f6933442c17678bce6dfa4bf80e22ed530bb933c010000008a47304402206d0ab626a7e477c27602ed63b2651517af077e6f3fafda671dd9952dfcb5f0b90220168eb51a48ce7496a699a800299f15638e0a7f36ae84e84e26df0cd2a280a70e014104b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4feffffff0240597307000000001976a914211090b628fa6351fa8240232e3c2753fd5eece588ac700369d2050000001976a914ce639943ce1602e30b249faf74388ee0eeb1d3c588ac84b90700
01000000014666d430766d611cc7f2c21494e68e463ac4be8bb2f70b91693728324849e1c3010000008a473044022057a02a4abc38e2e3e1809b05402cf52faef7e101d6364d43bb0305f8796b0fb202203d1934a016c91072ffe137575734454161284ab3371a0cfc6767db7f27f24a75014104ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240cffffffff01b0feea0b000000001976a9148300ab0caebb6e85cf9e6b287a57924d1ac7c82f88ac00000000
01000000019d8e5e1bfac780b813e41517926aca95048e1dea92cbbe2a98475ff53ad38ccd000000008c493046022100c7b76326879a5ec7df2ffedb292a45c13c6f154982fc2cd7e05f0d0d0dce2d05022100d7fd43416608eaeb6356f04b601ac6edd23e0f82de44689fe5a7aa2f576637a001410480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56cffffffff01a93de702000000001976a914119fb35bad07974c1a8d47d210ca3048bb13be8788ac00000000
</code></pre><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Install all the necessary modules:</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">bitcoin
ecdsa
utils
base58


pip2 install -r requirements.txt</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/489a485af916d20a567f6675da99fe06.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Using the&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/breakECDSA.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">breakECDSA.py</a>&nbsp;script, we will find out the&nbsp;<em style="box-sizing: inherit;">public keys</em>&nbsp;for Bitcoin Addresses</p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">python2 breakECDSA.py 01000000017fbdd4c9991d0ba4fb0a0c06f6933442c17678bce6dfa4bf80e22ed530bb933c010000008a47304402206d0ab626a7e477c27602ed63b2651517af077e6f3fafda671dd9952dfcb5f0b90220168eb51a48ce7496a699a800299f15638e0a7f36ae84e84e26df0cd2a280a70e014104b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4feffffff0240597307000000001976a914211090b628fa6351fa8240232e3c2753fd5eece588ac700369d2050000001976a914ce639943ce1602e30b249faf74388ee0eeb1d3c588ac84b90700 &gt;&gt; PublicKeys.txt
python2 breakECDSA.py 01000000014666d430766d611cc7f2c21494e68e463ac4be8bb2f70b91693728324849e1c3010000008a473044022057a02a4abc38e2e3e1809b05402cf52faef7e101d6364d43bb0305f8796b0fb202203d1934a016c91072ffe137575734454161284ab3371a0cfc6767db7f27f24a75014104ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240cffffffff01b0feea0b000000001976a9148300ab0caebb6e85cf9e6b287a57924d1ac7c82f88ac00000000 &gt;&gt; PublicKeys.txt
python2 breakECDSA.py 01000000019d8e5e1bfac780b813e41517926aca95048e1dea92cbbe2a98475ff53ad38ccd000000008c493046022100c7b76326879a5ec7df2ffedb292a45c13c6f154982fc2cd7e05f0d0d0dce2d05022100d7fd43416608eaeb6356f04b601ac6edd23e0f82de44689fe5a7aa2f576637a001410480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56cffffffff01a93de702000000001976a914119fb35bad07974c1a8d47d210ca3048bb13be8788ac00000000 &gt;&gt; PublicKeys.txt
</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/afbec8169caf989b8550aadad4dd3e59.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">After launch, we receive&nbsp;<em style="box-sizing: inherit;">public keys</em>&nbsp;for all three Bitcoin Addresses.</p><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">The result will be saved to a file: PublicKeys.txt</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">Откроем файл: PublicKeys.txt

cat PublicKeys.txt</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/7734e4670c08dae7004135f681bd0942.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">PUBKEY = 04b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4
PUBKEY = 04ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240c
PUBKEY = 0480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56c
</code></pre><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Let’s make these public keys in the form of coordinate points (x,y):</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">(0xb3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97 , 0xfe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4)
(0xea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd , 0x1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240c)
(0x80edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2 , 0xb5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56c)
</code></pre><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Save the coordinate points&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">(x,y)</code>in a file:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/Coordinates.txt" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">Coordinates.txt</span></a></p><h2 style="box-sizing: inherit; clear: both; color: #191308; font-size: 2rem; line-height: 1.2; margin: 0.5rem 0px;">BLOCKCHAIN ​​FOLBIT LEAKS</h2><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Let’s open the list of known blockchain leaks on&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">2019 год</code>&nbsp;<a href="https://pastebin.com/eLMYtzV8" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">«BLOCKCHAIN ​​FOLBIT LEAKS»</span></a></p><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/5b1643cb05baa67368df5f79277135ae.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Let’s copy the value:</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">dac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/bbb497cfc8a2ec00af285f19851e6ce8.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin: 0px;">Now let’s do the dot multiplication over all the coordinates of the points by&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">(x,y)</code>applying the leakage value&nbsp;<span style="box-sizing: inherit; font-weight: bolder;">:</span></p></blockquote><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">Change the maxwell.py</a>&nbsp;code&nbsp;and change the name to&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/scalarEC.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">scalarEC.py</a></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Let’s add<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">with open("Coordinates.txt", "rt") as base:</code></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">All new coordinates will be saved in a file:<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">SaveBase.txt</code></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">B = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Let’s add a value&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">B</code>from the list to the code and save it as a&nbsp;<em style="box-sizing: inherit;">Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/scalarEC.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">scalarEC.py</a></p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">from ecpy.curves     import Curve,Point

with open("Coordinates.txt", "rt") as base:
    for line in base.read().splitlines():
        Gx, Gy = map(lambda v: int(v, 16), line[1: -1].split(" , "))

        cv = Curve.get_curve('secp256k1')
    
        P  = Point(Gx,Gy,cv)

        B  = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae

        A  = B*P

        with open("SaveBase.txt", "a") as file:
            file.write(str(A))
            file.write("\n")</code></pre><hr class="wp-block-separator has-alpha-channel-opacity" style="background-color: #cccccc; border-bottom-color: initial; border-bottom-style: solid; border-image: initial; border-left: 0px; border-right: 0px; border-top-color: initial; border-top-style: solid; box-sizing: content-box; height: 0px; margin-bottom: 1rem; margin-top: 1rem; overflow: visible;"><h2 style="box-sizing: inherit; clear: both; color: #191308; font-size: 2rem; line-height: 1.2; margin: 0.5rem 0px;">Let’s run the script:</h2><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">python3 scalarEC.py

Результат сохранился в файле: SaveBase.txt

Откроем файле: SaveBase.txt

cat SaveBase.txt
</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/cf3657dd0b79a3ce0e5cdaa44120e4ba.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">(0x92b9eeebb8c4fa108359bd31367e36b7fe65b4a7e06d533b476dee097572a4c0 , 0x4d2beb1835a2f8b85e3f61d32094dbf0b4c7a212bee42ee4612193c0653c6e56)
(0x65304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e7 , 0x7af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958)
(0x433c15b724948371877dd3c1014d59d1a13d76a29e4948903623a74767736b97 , 0x13f15f3bb28a4766952e10da9717aa3cc0bad90b0414f483718531d584721ea3)
</code></pre><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin: 0px;">After scalar multiplication by the leakage value over all coordinate points&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">(x,y)</code>, we&nbsp;<em style="box-sizing: inherit;"><u style="box-sizing: inherit;">get new points</u></em></p></blockquote><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Now let’s rewrite these coordinates in the form of uncompressed public keys:</h3><h2 style="box-sizing: inherit; clear: both; color: #191308; font-size: 2rem; line-height: 1.2; margin: 0.5rem 0px;">Let’s take a look at this public key:</h2><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">0465304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e77af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958
</code></pre><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><a href="https://cryptodeeptech.ru/kangaroo/" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">Now we use Pollard’s Kangaroo</a>&nbsp;method to find the private key</p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Previously, we published an article:&nbsp;<a href="https://cryptodeeptech.ru/kangaroo/" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><em style="box-sizing: inherit;">«Pollard’s Kangaroo find solutions to the discrete logarithm of secp256k1 PRIVATE KEY + NONCES in a known range»</em></a></p><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin: 0px;">Let’s use&nbsp;<em style="box-sizing: inherit;"><u style="box-sizing: inherit;">the new code</u></em>&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">Pollard's Kangaroo</code>&nbsp;from&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">Telariust</code>&nbsp;<em style="box-sizing: inherit;">Python</em>&nbsp;-script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/kangaroo.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">kangaroo.py</a></p></blockquote><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Install the gmpy2 module with the command:</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">sudo apt install python-gmpy2</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/0f144812547a5d8e84cf66ee71b0c6d6.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/7646ac808066d138af9c5b5380baf507.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Next, run the&nbsp;<em style="box-sizing: inherit;">Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/kangaroo.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">kangaroo.py</a></p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">python2 kangaroo.py 32 0465304D24C0EDC862843587A96EA700F86E9E70E7801AC7DF9EFD2DE84230C3E77AF6D83573849D2368A021E835C5768E1B791C0C1B4CFAFB9795058DF5F27958
</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/25d4cddd4d35d1fc6331dca485cff638.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/617c1358faaf9104fc774fda67fbf9d1.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">In the terminal we see that we managed to get&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">"prvkey"</code>:</p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">[prvkey#32] 0x00000000000000000000000000000000000000000000000000000000795f9c63
[pubkey#32] 0465304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e77af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958
</code></pre><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">The result will be saved to a file: Privkey.txt</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">Откроем файл командой: 

cat Privkey.txt</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/94f1450a509aa57879f2864348d1fe4c.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">00000000000000000000000000000000000000000000000000000000795f9c63</code></pre><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">We got a reduced private key for the public key:</h3><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">0465304D24C0EDC862843587A96EA700F86E9E70E7801AC7DF9EFD2DE84230C3E77AF6D83573849D2368A021E835C5768E1B791C0C1B4CFAFB9795058DF5F27958
</code></pre><h3 style="box-sizing: inherit; clear: both; color: #191308; font-size: 1.6rem; line-height: 1.2; margin: 0.5rem 0px;">Pay attention to the private key:</h3><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/f8daaebb61f7ee1e398441c85ab85209.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">The latter&nbsp;matches the&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">8 цифр</code>public&nbsp;<em style="box-sizing: inherit;">key&nbsp;</em><a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">«Maxwell’s vanity public key»</a><code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">формате HEX</code></p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63</code></pre><hr class="wp-block-separator has-alpha-channel-opacity" style="background-color: #cccccc; border-bottom-color: initial; border-bottom-style: solid; border-image: initial; border-left: 0px; border-right: 0px; border-top-color: initial; border-top-style: solid; box-sizing: content-box; height: 0px; margin-bottom: 1rem; margin-top: 1rem; overflow: visible;"><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">A = 0x00000000000000000000000000000000000000000000000000000000795f9c63
B = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></pre><blockquote class="wp-block-quote" style="border-bottom-color: rgb(0, 139, 202); border-left: 0.2rem solid rgb(0, 139, 202); border-right-color: rgb(0, 139, 202); border-top-color: rgb(0, 139, 202); box-sizing: border-box; margin: 0px 0px 1rem; overflow-wrap: break-word; padding: 0.5rem 0px 0.5rem 2rem;"><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Now, in order to get a private key for one of the three Bitcoin Addresses, we need to do a modulo division&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">значение A</code>by<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">значение B</code></p><p style="box-sizing: inherit; margin: 0px;"><code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">Privkey = ((A * modinv(B,N)) % N)</code></p></blockquote><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Let’s use a&nbsp;<em style="box-sizing: inherit;">Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/calculate.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">calculate.py</a></p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">def h(n):
    return hex(n).replace("0x","")

def extended_gcd(aa, bb):
    lastremainder, remainder = abs(aa), abs(bb)
    x, lastx, y, lasty = 0, 1, 1, 0
    while remainder:
        lastremainder, (quotient, remainder) = remainder, divmod(lastremainder, remainder)
        x, lastx = lastx - quotient*x, x
        y, lasty = lasty - quotient*y, y
    return lastremainder, lastx * (-1 if aa &lt; 0 else 1), lasty * (-1 if bb &lt; 0 else 1)

def modinv(a, m):
    g, x, y = extended_gcd(a, m)
    if g != 1:
        raise ValueError
    return x % m

N = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141

A = 0x00000000000000000000000000000000000000000000000000000000795f9c63
B = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae


print (h(((A) * modinv(B,N)) % N))
</code></pre><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">Let ‘s run the&nbsp;<em style="box-sizing: inherit;">Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/calculate.py" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">calculate.py</a></p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">python3 calculate.py</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/750f71837b11f35eb3f067cc0499c558.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;" title="As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae"><figcaption style="background-color: #f1f1f1; box-sizing: inherit; color: #666666; font-size: 0.9em; font-style: italic; margin-bottom: 1em; margin-top: 0px; padding: 0.24em 0.4em;">As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae</figcaption></figure><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><a href="https://cryptodeeptech.ru/bitaddress.html" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank">Let’s open bitaddress</a>&nbsp;and&nbsp;check:</p><pre class="wp-block-code" style="background-color: #f7f7f7; border-color: rgb(230, 230, 230); box-sizing: inherit; color: #212529; font-family: &quot;Courier 10 Pitch&quot;, courier, monospace; font-size: 14px; line-height: 1.6; margin-bottom: 1rem; margin-top: 0px; max-width: 100%; overflow: auto; padding: 1.6em; text-overflow: ellipsis;"><code style="box-sizing: inherit; color: inherit; display: block; font-family: inherit; font-size: inherit; overflow-wrap: break-word; white-space: pre-wrap; word-break: normal;">ADDR: 1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm
WIF:  5JF9ME7zdGLDd3oyuMG7RfwgA1ByjZb2LbSwRMwM8ZKBADFLfCx
HEX:  38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae</code></pre><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/eb4d76c11de49bd6114bcb2b5409cdc4.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;"></figure><h2 style="box-sizing: inherit; clear: both; color: #191308; font-size: 2rem; line-height: 1.2; margin: 0.5rem 0px;">Private Key Found!</h2><h2 style="box-sizing: inherit; clear: both; color: #191308; font-size: 2rem; line-height: 1.2; margin: 0.5rem 0px;">Bitcoin Wallet Restored!</h2><figure class="wp-block-image" style="box-sizing: inherit; margin: 0px 0px 1em;"><img alt="www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm" src="./CRYPTO DEEP_ Reducing the private key through scalar multiplication using the ECPy Google Colab library_files/d05dfb7d1f9a7217cf7f88bd11b969e7.png" style="border-radius: inherit; border-style: none; box-sizing: inherit; height: auto; max-width: 100%; vertical-align: bottom;" title="www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm"><figcaption style="background-color: #f1f1f1; box-sizing: inherit; color: #666666; font-size: 0.9em; font-style: italic; margin-bottom: 1em; margin-top: 0px; padding: 0.24em 0.4em;">www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm</figcaption></figure><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;">This video was created for the&nbsp;&nbsp;<a href="https://cryptodeeptech.ru/" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">CRYPTO DEEP TECH</span></a>&nbsp;portal &nbsp;to ensure the financial security of data and cryptography on elliptic curves&nbsp;&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">secp256k1</code>&nbsp;against weak signatures&nbsp;&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">ECDSA</code>&nbsp;in cryptocurrency&nbsp;<code style="box-sizing: inherit; color: #e83e8c; font-family: monaco, consolas, &quot;Andale Mono&quot;, &quot;DejaVu Sans Mono&quot;, monospace; font-size: 14px; overflow-wrap: break-word;">BITCOIN</code></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">Source</span></a></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><a href="https://t.me/cryptodeeptech" style="background-color: transparent; box-sizing: inherit; color: black;"><span style="box-sizing: inherit; font-weight: bolder;">Telegram</span></a><span style="box-sizing: inherit; font-weight: bolder;">&nbsp;:&nbsp;&nbsp;</span><a href="https://t.me/cryptodeeptech" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;"><u style="box-sizing: inherit;">https://t.me/cryptodeeptech</u></span></a></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><a href="https://youtu.be/zu2yiaZ_LOs" rel="noreferrer noopener" style="background-color: transparent; box-sizing: inherit; color: black;" target="_blank"><span style="box-sizing: inherit; font-weight: bolder;">Video: https://youtu.be/zu2yiaZ_LOs</span></a></p><p style="box-sizing: inherit; margin-bottom: 1rem; margin-top: 0px;"><a href="https://cryptodeeptech.ru/reduce-private-key" style="background-color: transparent; box-sizing: inherit; color: black;"><span style="box-sizing: inherit; font-weight: bolder;">Source:&nbsp;https://cryptodeeptech.ru/reduce-private-key</span></a></p><hr class="wp-block-separator has-alpha-channel-opacity" style="background-color: #cccccc; border-bottom-color: initial; border-bottom-style: solid; border-image: initial; border-left: 0px; border-right: 0px; border-top-color: initial; border-top-style: solid; box-sizing: content-box; height: 0px; margin-bottom: 1rem; margin-top: 1rem; overflow: visible;"></div><footer class="entry-footer" style="box-sizing: inherit; margin-bottom: 2em;"><div class="cat-links" style="box-sizing: inherit; margin-bottom: 1em;"></div></footer></div><footer class="entry-footer" style="background-color: white; box-sizing: inherit; color: #333333; font-family: Lato, sans-serif; font-size: 16px; margin-bottom: 2em;"><div class="cat-links" style="box-sizing: inherit; margin-bottom: 1em;"><br></div></footer>
---


|  | Donation Address |
| --- | --- |
| ♥ __BTC__ | 1Lw2kh9WzCActXSGHxyypGLkqQZfxDpw8v |
| ♥ __ETH__ | 0xaBd66CF90898517573f19184b3297d651f7b90bf |
