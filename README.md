<!DOCTYPE html>
<!-- saved from url=(0045)https://cryptodeeptech.ru/reduce-private-key/ -->
<html lang="ru-RU"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
	
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<link rel="profile" href="https://gmpg.org/xfn/11">

	<meta name="robots" content="index, follow, max-image-preview:large, max-snippet:-1, max-video-preview:-1">

	<!-- This site is optimized with the Yoast SEO plugin v19.2 - https://yoast.com/wordpress/plugins/seo/ -->
	<style type="text/css"></style><title>Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»</title>
	<meta name="description" content="How can you reduce the private key knowing only the leak from the &quot;BLOCKCHAIN FOLBIT LEAKS&quot; list, for this we will restore the Bitcoin Wallet.">
	<link rel="canonical" href="https://cryptodeeptech.ru/reduce-private-key/">
	<meta property="og:locale" content="ru_RU">
	<meta property="og:type" content="article">
	<meta property="og:title" content="Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»">
	<meta property="og:description" content="How can you reduce the private key knowing only the leak from the &quot;BLOCKCHAIN FOLBIT LEAKS&quot; list, for this we will restore the Bitcoin Wallet.">
	<meta property="og:url" content="https://cryptodeeptech.ru/reduce-private-key/">
	<meta property="og:site_name" content="«CRYPTO DEEP TECH»">
	<meta property="article:published_time" content="2022-08-08T22:29:25+00:00">
	<meta property="article:modified_time" content="2022-08-25T15:54:25+00:00">
	<meta property="og:image" content="https://habrastorage.org/getpro/habr/upload_files/201/da1/f9f/201da1f9f8e93fbbeae07e8e9af7723e.png">
	<meta name="author" content="Crypto Deep Tech">
	<meta name="twitter:card" content="summary_large_image">
	<meta name="twitter:label1" content="Написано автором">
	<meta name="twitter:data1" content="Crypto Deep Tech">
	<meta name="twitter:label2" content="Примерное время для чтения">
	<meta name="twitter:data2" content="9 минут">
	<script async="" src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/tag.js"></script><script type="application/ld+json" class="yoast-schema-graph">{"@context":"https://schema.org","@graph":[{"@type":"WebSite","@id":"https://cryptodeeptech.ru/#website","url":"https://cryptodeeptech.ru/","name":"«CRYPTO DEEP TECH»","description":"Cryptanalysis and data financial security services","potentialAction":[{"@type":"SearchAction","target":{"@type":"EntryPoint","urlTemplate":"https://cryptodeeptech.ru/?s={search_term_string}"},"query-input":"required name=search_term_string"}],"inLanguage":"ru-RU"},{"@type":"ImageObject","inLanguage":"ru-RU","@id":"https://cryptodeeptech.ru/reduce-private-key/#primaryimage","url":"https://habrastorage.org/getpro/habr/upload_files/201/da1/f9f/201da1f9f8e93fbbeae07e8e9af7723e.png","contentUrl":"https://habrastorage.org/getpro/habr/upload_files/201/da1/f9f/201da1f9f8e93fbbeae07e8e9af7723e.png"},{"@type":"WebPage","@id":"https://cryptodeeptech.ru/reduce-private-key/#webpage","url":"https://cryptodeeptech.ru/reduce-private-key/","name":"Reducing the private key through scalar multiplication using the ECPy + Google Colab library - «CRYPTO DEEP TECH»","isPartOf":{"@id":"https://cryptodeeptech.ru/#website"},"primaryImageOfPage":{"@id":"https://cryptodeeptech.ru/reduce-private-key/#primaryimage"},"datePublished":"2022-08-08T22:29:25+00:00","dateModified":"2022-08-25T15:54:25+00:00","author":{"@id":"https://cryptodeeptech.ru/#/schema/person/0ef8ac0f63991970628a3a6587f9e6c0"},"description":"How can you reduce the private key knowing only the leak from the \"BLOCKCHAIN FOLBIT LEAKS\" list, for this we will restore the Bitcoin Wallet.","breadcrumb":{"@id":"https://cryptodeeptech.ru/reduce-private-key/#breadcrumb"},"inLanguage":"ru-RU","potentialAction":[{"@type":"ReadAction","target":["https://cryptodeeptech.ru/reduce-private-key/"]}]},{"@type":"BreadcrumbList","@id":"https://cryptodeeptech.ru/reduce-private-key/#breadcrumb","itemListElement":[{"@type":"ListItem","position":1,"name":"Главная страница","item":"https://cryptodeeptech.ru/"},{"@type":"ListItem","position":2,"name":"Reducing the private key through scalar multiplication using the ECPy + Google Colab library"}]},{"@type":"Person","@id":"https://cryptodeeptech.ru/#/schema/person/0ef8ac0f63991970628a3a6587f9e6c0","name":"Crypto Deep Tech","sameAs":["https://cryptodeeptech.ru","https://www.youtube.com/channel/UCd8W6qtRSiBn0Q0wy6HuNkQ/"],"url":"https://cryptodeeptech.ru/author/cryptodeeptech/"}]}</script>
	<!-- / Yoast SEO plugin. -->


<link rel="dns-prefetch" href="https://fonts.googleapis.com/">
<link rel="alternate" type="application/rss+xml" title="«CRYPTO DEEP TECH» » Лента" href="https://cryptodeeptech.ru/feed/">
<link rel="alternate" type="application/rss+xml" title="«CRYPTO DEEP TECH» » Лента комментариев" href="https://cryptodeeptech.ru/comments/feed/">
<link rel="stylesheet" id="itng-block-style-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_8f426a1779caff96bb3f2afbcff86bc9.css" media="all">
<link rel="stylesheet" id="wp-block-library-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/style.min.css" media="all">
<style id="global-styles-inline-css">
body{--wp--preset--color--black: #000000;--wp--preset--color--cyan-bluish-gray: #abb8c3;--wp--preset--color--white: #ffffff;--wp--preset--color--pale-pink: #f78da7;--wp--preset--color--vivid-red: #cf2e2e;--wp--preset--color--luminous-vivid-orange: #ff6900;--wp--preset--color--luminous-vivid-amber: #fcb900;--wp--preset--color--light-green-cyan: #7bdcb5;--wp--preset--color--vivid-green-cyan: #00d084;--wp--preset--color--pale-cyan-blue: #8ed1fc;--wp--preset--color--vivid-cyan-blue: #0693e3;--wp--preset--color--vivid-purple: #9b51e0;--wp--preset--gradient--vivid-cyan-blue-to-vivid-purple: linear-gradient(135deg,rgba(6,147,227,1) 0%,rgb(155,81,224) 100%);--wp--preset--gradient--light-green-cyan-to-vivid-green-cyan: linear-gradient(135deg,rgb(122,220,180) 0%,rgb(0,208,130) 100%);--wp--preset--gradient--luminous-vivid-amber-to-luminous-vivid-orange: linear-gradient(135deg,rgba(252,185,0,1) 0%,rgba(255,105,0,1) 100%);--wp--preset--gradient--luminous-vivid-orange-to-vivid-red: linear-gradient(135deg,rgba(255,105,0,1) 0%,rgb(207,46,46) 100%);--wp--preset--gradient--very-light-gray-to-cyan-bluish-gray: linear-gradient(135deg,rgb(238,238,238) 0%,rgb(169,184,195) 100%);--wp--preset--gradient--cool-to-warm-spectrum: linear-gradient(135deg,rgb(74,234,220) 0%,rgb(151,120,209) 20%,rgb(207,42,186) 40%,rgb(238,44,130) 60%,rgb(251,105,98) 80%,rgb(254,248,76) 100%);--wp--preset--gradient--blush-light-purple: linear-gradient(135deg,rgb(255,206,236) 0%,rgb(152,150,240) 100%);--wp--preset--gradient--blush-bordeaux: linear-gradient(135deg,rgb(254,205,165) 0%,rgb(254,45,45) 50%,rgb(107,0,62) 100%);--wp--preset--gradient--luminous-dusk: linear-gradient(135deg,rgb(255,203,112) 0%,rgb(199,81,192) 50%,rgb(65,88,208) 100%);--wp--preset--gradient--pale-ocean: linear-gradient(135deg,rgb(255,245,203) 0%,rgb(182,227,212) 50%,rgb(51,167,181) 100%);--wp--preset--gradient--electric-grass: linear-gradient(135deg,rgb(202,248,128) 0%,rgb(113,206,126) 100%);--wp--preset--gradient--midnight: linear-gradient(135deg,rgb(2,3,129) 0%,rgb(40,116,252) 100%);--wp--preset--duotone--dark-grayscale: url('#wp-duotone-dark-grayscale');--wp--preset--duotone--grayscale: url('#wp-duotone-grayscale');--wp--preset--duotone--purple-yellow: url('#wp-duotone-purple-yellow');--wp--preset--duotone--blue-red: url('#wp-duotone-blue-red');--wp--preset--duotone--midnight: url('#wp-duotone-midnight');--wp--preset--duotone--magenta-yellow: url('#wp-duotone-magenta-yellow');--wp--preset--duotone--purple-green: url('#wp-duotone-purple-green');--wp--preset--duotone--blue-orange: url('#wp-duotone-blue-orange');--wp--preset--font-size--small: 13px;--wp--preset--font-size--medium: 20px;--wp--preset--font-size--large: 36px;--wp--preset--font-size--x-large: 42px;}.has-black-color{color: var(--wp--preset--color--black) !important;}.has-cyan-bluish-gray-color{color: var(--wp--preset--color--cyan-bluish-gray) !important;}.has-white-color{color: var(--wp--preset--color--white) !important;}.has-pale-pink-color{color: var(--wp--preset--color--pale-pink) !important;}.has-vivid-red-color{color: var(--wp--preset--color--vivid-red) !important;}.has-luminous-vivid-orange-color{color: var(--wp--preset--color--luminous-vivid-orange) !important;}.has-luminous-vivid-amber-color{color: var(--wp--preset--color--luminous-vivid-amber) !important;}.has-light-green-cyan-color{color: var(--wp--preset--color--light-green-cyan) !important;}.has-vivid-green-cyan-color{color: var(--wp--preset--color--vivid-green-cyan) !important;}.has-pale-cyan-blue-color{color: var(--wp--preset--color--pale-cyan-blue) !important;}.has-vivid-cyan-blue-color{color: var(--wp--preset--color--vivid-cyan-blue) !important;}.has-vivid-purple-color{color: var(--wp--preset--color--vivid-purple) !important;}.has-black-background-color{background-color: var(--wp--preset--color--black) !important;}.has-cyan-bluish-gray-background-color{background-color: var(--wp--preset--color--cyan-bluish-gray) !important;}.has-white-background-color{background-color: var(--wp--preset--color--white) !important;}.has-pale-pink-background-color{background-color: var(--wp--preset--color--pale-pink) !important;}.has-vivid-red-background-color{background-color: var(--wp--preset--color--vivid-red) !important;}.has-luminous-vivid-orange-background-color{background-color: var(--wp--preset--color--luminous-vivid-orange) !important;}.has-luminous-vivid-amber-background-color{background-color: var(--wp--preset--color--luminous-vivid-amber) !important;}.has-light-green-cyan-background-color{background-color: var(--wp--preset--color--light-green-cyan) !important;}.has-vivid-green-cyan-background-color{background-color: var(--wp--preset--color--vivid-green-cyan) !important;}.has-pale-cyan-blue-background-color{background-color: var(--wp--preset--color--pale-cyan-blue) !important;}.has-vivid-cyan-blue-background-color{background-color: var(--wp--preset--color--vivid-cyan-blue) !important;}.has-vivid-purple-background-color{background-color: var(--wp--preset--color--vivid-purple) !important;}.has-black-border-color{border-color: var(--wp--preset--color--black) !important;}.has-cyan-bluish-gray-border-color{border-color: var(--wp--preset--color--cyan-bluish-gray) !important;}.has-white-border-color{border-color: var(--wp--preset--color--white) !important;}.has-pale-pink-border-color{border-color: var(--wp--preset--color--pale-pink) !important;}.has-vivid-red-border-color{border-color: var(--wp--preset--color--vivid-red) !important;}.has-luminous-vivid-orange-border-color{border-color: var(--wp--preset--color--luminous-vivid-orange) !important;}.has-luminous-vivid-amber-border-color{border-color: var(--wp--preset--color--luminous-vivid-amber) !important;}.has-light-green-cyan-border-color{border-color: var(--wp--preset--color--light-green-cyan) !important;}.has-vivid-green-cyan-border-color{border-color: var(--wp--preset--color--vivid-green-cyan) !important;}.has-pale-cyan-blue-border-color{border-color: var(--wp--preset--color--pale-cyan-blue) !important;}.has-vivid-cyan-blue-border-color{border-color: var(--wp--preset--color--vivid-cyan-blue) !important;}.has-vivid-purple-border-color{border-color: var(--wp--preset--color--vivid-purple) !important;}.has-vivid-cyan-blue-to-vivid-purple-gradient-background{background: var(--wp--preset--gradient--vivid-cyan-blue-to-vivid-purple) !important;}.has-light-green-cyan-to-vivid-green-cyan-gradient-background{background: var(--wp--preset--gradient--light-green-cyan-to-vivid-green-cyan) !important;}.has-luminous-vivid-amber-to-luminous-vivid-orange-gradient-background{background: var(--wp--preset--gradient--luminous-vivid-amber-to-luminous-vivid-orange) !important;}.has-luminous-vivid-orange-to-vivid-red-gradient-background{background: var(--wp--preset--gradient--luminous-vivid-orange-to-vivid-red) !important;}.has-very-light-gray-to-cyan-bluish-gray-gradient-background{background: var(--wp--preset--gradient--very-light-gray-to-cyan-bluish-gray) !important;}.has-cool-to-warm-spectrum-gradient-background{background: var(--wp--preset--gradient--cool-to-warm-spectrum) !important;}.has-blush-light-purple-gradient-background{background: var(--wp--preset--gradient--blush-light-purple) !important;}.has-blush-bordeaux-gradient-background{background: var(--wp--preset--gradient--blush-bordeaux) !important;}.has-luminous-dusk-gradient-background{background: var(--wp--preset--gradient--luminous-dusk) !important;}.has-pale-ocean-gradient-background{background: var(--wp--preset--gradient--pale-ocean) !important;}.has-electric-grass-gradient-background{background: var(--wp--preset--gradient--electric-grass) !important;}.has-midnight-gradient-background{background: var(--wp--preset--gradient--midnight) !important;}.has-small-font-size{font-size: var(--wp--preset--font-size--small) !important;}.has-medium-font-size{font-size: var(--wp--preset--font-size--medium) !important;}.has-large-font-size{font-size: var(--wp--preset--font-size--large) !important;}.has-x-large-font-size{font-size: var(--wp--preset--font-size--x-large) !important;}
</style>
<link rel="stylesheet" id="wp-date-remover-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_e6094661d8923e95b233019ebff7c8f0.css" media="all">
<link rel="stylesheet" id="itng-fonts-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/css" media="all">
<link rel="stylesheet" id="itng-style-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_8de4505c66a21eefd3c1c98b6400e4e1.css" media="all">
<link rel="stylesheet" id="itng-main-style-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_d1cf6f49400112d539e59eee9b75e10d.css" media="all">
<style id="itng-main-style-inline-css">
.custom-logo-link img {width: 400px;}@media screen and (min-width: 992px) {#header-image .header-overlay {
            opacity: 0.01;
        }}
ins,
	.nav-wrapper,
	#menu,
	.main-navigation ul#menu-desktop ul,
	#itng-featured-news .slider-post-wrapper .posted-on a,
	#itng-featured-news #itng-featured-news-list-container .posted-on a,
	#itng-featured-posts .itng-featured-post-date,
	#itng-featured-news #itng-featured-news-carousel-container .posted-on a,
	#colophon,
	[class^=itng-search] form,
	#itng-featured-cat .featured-cat-thumb h2,
	#itng-featured-cat .featured-cat-thumb h3
	{background-color: #008bca}article .entry-meta a,
	article .blog-footer,
	article .blog-footer a,
	.widget a,
	.nav-links a,
	.itng-pagination .nav-links > a,
	.itng-pagination .dots
	{color: #008bca !important}blockquote,
	#itng-content-title span
	{border-color: #008bca}button.top-menu-mobile
	{background-color: #43bdf2 !important}#footer-sidebar .widget-title
	{color: #43bdf2 !important}
</style>
<link rel="stylesheet" id="bootstrap-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_d26191bd0380b0cf97525a613b8b566c.css" media="all">
<link rel="stylesheet" id="owl-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_c8322bd5bffc8e2856f2cbcd03c61d18.css" media="all">
<link rel="stylesheet" id="mag-popup-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_30b593b71d7672658f89bfea0ab360c9.css" media="all">
<link rel="stylesheet" id="font-awesome-css" href="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_c495654869785bc3df60216616814ad1.css" media="all">
<script src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/jquery.min.js" id="jquery-core-js"></script>
<script src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/jquery-migrate.min.js" id="jquery-migrate-js"></script>
<script src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_49cea0a781874a962879c2caca9bc322.js" id="wp-date-remover-js"></script>
<link rel="https://api.w.org/" href="https://cryptodeeptech.ru/wp-json/"><link rel="alternate" type="application/json" href="https://cryptodeeptech.ru/wp-json/wp/v2/posts/355"><meta name="generator" content="WordPress 6.0.1">
<link rel="alternate" type="application/json+oembed" href="https://cryptodeeptech.ru/wp-json/oembed/1.0/embed?url=https%3A%2F%2Fcryptodeeptech.ru%2Freduce-private-key%2F">
<link rel="alternate" type="text/xml+oembed" href="https://cryptodeeptech.ru/wp-json/oembed/1.0/embed?url=https%3A%2F%2Fcryptodeeptech.ru%2Freduce-private-key%2F&amp;format=xml">
		<style type="text/css">
						#header-image {
						background-image: url(https://cryptodeeptech.ru/wp-content/uploads/2022/07/header3.jpg);
						background-size: cover;
						background-repeat: repeat;
						background-position: center center;
				}
							.site-title, .site-description {
				display: none;
				position: absolute;
				clip: rect(1px, 1px, 1px, 1px);
				}
					</style>
		<style id="custom-background-css">
body.custom-background { background-color: #eff3fd; }
</style>
	<link rel="icon" href="https://cryptodeeptech.ru/wp-content/uploads/2022/07/cropped-favicon7-32x32.png" sizes="32x32">
<link rel="icon" href="https://cryptodeeptech.ru/wp-content/uploads/2022/07/cropped-favicon7-192x192.png" sizes="192x192">
<link rel="apple-touch-icon" href="https://cryptodeeptech.ru/wp-content/uploads/2022/07/cropped-favicon7-180x180.png">
<meta name="msapplication-TileImage" content="https://cryptodeeptech.ru/wp-content/uploads/2022/07/cropped-favicon7-270x270.png">
</head>

<body data-rsssl="1" class="post-template-default single single-post postid-355 single-format-standard custom-background wp-custom-logo no-sidebar">
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 0 0" width="0" height="0" focusable="false" role="none" style="visibility: hidden; position: absolute; left: -9999px; overflow: hidden;"><defs><filter id="wp-duotone-dark-grayscale"><fecolormatrix color-interpolation-filters="sRGB" type="matrix" values=" .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 "></fecolormatrix><fecomponenttransfer color-interpolation-filters="sRGB"><fefuncr type="table" tableValues="0 0.49803921568627"></fefuncr><fefuncg type="table" tableValues="0 0.49803921568627"></fefuncg><fefuncb type="table" tableValues="0 0.49803921568627"></fefuncb><fefunca type="table" tableValues="1 1"></fefunca></fecomponenttransfer><fecomposite in2="SourceGraphic" operator="in"></fecomposite></filter></defs></svg><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 0 0" width="0" height="0" focusable="false" role="none" style="visibility: hidden; position: absolute; left: -9999px; overflow: hidden;"><defs><filter id="wp-duotone-grayscale"><fecolormatrix color-interpolation-filters="sRGB" type="matrix" values=" .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 "></fecolormatrix><fecomponenttransfer color-interpolation-filters="sRGB"><fefuncr type="table" tableValues="0 1"></fefuncr><fefuncg type="table" tableValues="0 1"></fefuncg><fefuncb type="table" tableValues="0 1"></fefuncb><fefunca type="table" tableValues="1 1"></fefunca></fecomponenttransfer><fecomposite in2="SourceGraphic" operator="in"></fecomposite></filter></defs></svg><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 0 0" width="0" height="0" focusable="false" role="none" style="visibility: hidden; position: absolute; left: -9999px; overflow: hidden;"><defs><filter id="wp-duotone-purple-yellow"><fecolormatrix color-interpolation-filters="sRGB" type="matrix" values=" .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 "></fecolormatrix><fecomponenttransfer color-interpolation-filters="sRGB"><fefuncr type="table" tableValues="0.54901960784314 0.98823529411765"></fefuncr><fefuncg type="table" tableValues="0 1"></fefuncg><fefuncb type="table" tableValues="0.71764705882353 0.25490196078431"></fefuncb><fefunca type="table" tableValues="1 1"></fefunca></fecomponenttransfer><fecomposite in2="SourceGraphic" operator="in"></fecomposite></filter></defs></svg><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 0 0" width="0" height="0" focusable="false" role="none" style="visibility: hidden; position: absolute; left: -9999px; overflow: hidden;"><defs><filter id="wp-duotone-blue-red"><fecolormatrix color-interpolation-filters="sRGB" type="matrix" values=" .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 "></fecolormatrix><fecomponenttransfer color-interpolation-filters="sRGB"><fefuncr type="table" tableValues="0 1"></fefuncr><fefuncg type="table" tableValues="0 0.27843137254902"></fefuncg><fefuncb type="table" tableValues="0.5921568627451 0.27843137254902"></fefuncb><fefunca type="table" tableValues="1 1"></fefunca></fecomponenttransfer><fecomposite in2="SourceGraphic" operator="in"></fecomposite></filter></defs></svg><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 0 0" width="0" height="0" focusable="false" role="none" style="visibility: hidden; position: absolute; left: -9999px; overflow: hidden;"><defs><filter id="wp-duotone-midnight"><fecolormatrix color-interpolation-filters="sRGB" type="matrix" values=" .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 "></fecolormatrix><fecomponenttransfer color-interpolation-filters="sRGB"><fefuncr type="table" tableValues="0 0"></fefuncr><fefuncg type="table" tableValues="0 0.64705882352941"></fefuncg><fefuncb type="table" tableValues="0 1"></fefuncb><fefunca type="table" tableValues="1 1"></fefunca></fecomponenttransfer><fecomposite in2="SourceGraphic" operator="in"></fecomposite></filter></defs></svg><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 0 0" width="0" height="0" focusable="false" role="none" style="visibility: hidden; position: absolute; left: -9999px; overflow: hidden;"><defs><filter id="wp-duotone-magenta-yellow"><fecolormatrix color-interpolation-filters="sRGB" type="matrix" values=" .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 "></fecolormatrix><fecomponenttransfer color-interpolation-filters="sRGB"><fefuncr type="table" tableValues="0.78039215686275 1"></fefuncr><fefuncg type="table" tableValues="0 0.94901960784314"></fefuncg><fefuncb type="table" tableValues="0.35294117647059 0.47058823529412"></fefuncb><fefunca type="table" tableValues="1 1"></fefunca></fecomponenttransfer><fecomposite in2="SourceGraphic" operator="in"></fecomposite></filter></defs></svg><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 0 0" width="0" height="0" focusable="false" role="none" style="visibility: hidden; position: absolute; left: -9999px; overflow: hidden;"><defs><filter id="wp-duotone-purple-green"><fecolormatrix color-interpolation-filters="sRGB" type="matrix" values=" .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 "></fecolormatrix><fecomponenttransfer color-interpolation-filters="sRGB"><fefuncr type="table" tableValues="0.65098039215686 0.40392156862745"></fefuncr><fefuncg type="table" tableValues="0 1"></fefuncg><fefuncb type="table" tableValues="0.44705882352941 0.4"></fefuncb><fefunca type="table" tableValues="1 1"></fefunca></fecomponenttransfer><fecomposite in2="SourceGraphic" operator="in"></fecomposite></filter></defs></svg><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 0 0" width="0" height="0" focusable="false" role="none" style="visibility: hidden; position: absolute; left: -9999px; overflow: hidden;"><defs><filter id="wp-duotone-blue-orange"><fecolormatrix color-interpolation-filters="sRGB" type="matrix" values=" .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 .299 .587 .114 0 0 "></fecolormatrix><fecomponenttransfer color-interpolation-filters="sRGB"><fefuncr type="table" tableValues="0.098039215686275 1"></fefuncr><fefuncg type="table" tableValues="0 0.66274509803922"></fefuncg><fefuncb type="table" tableValues="0.84705882352941 0.41960784313725"></fefuncb><fefunca type="table" tableValues="1 1"></fefunca></fecomponenttransfer><fecomposite in2="SourceGraphic" operator="in"></fecomposite></filter></defs></svg><div id="page" class="site">
	<a class="skip-link screen-reader-text" href="https://cryptodeeptech.ru/reduce-private-key/#primary">Skip to content</a>

	
	    <header id="masthead" class="site-header style-1">

		    
	        <div id="header-image">
		        <div class="site-branding">
					<a href="https://cryptodeeptech.ru/" class="custom-logo-link" rel="home"><img width="1279" height="319" src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/cropped-header4.png" class="custom-logo" alt="«CRYPTO DEEP TECH»" srcset="https://cryptodeeptech.ru/wp-content/uploads/2022/07/cropped-header4.png 1279w, https://cryptodeeptech.ru/wp-content/uploads/2022/07/cropped-header4-300x75.png 300w, https://cryptodeeptech.ru/wp-content/uploads/2022/07/cropped-header4-1024x255.png 1024w, https://cryptodeeptech.ru/wp-content/uploads/2022/07/cropped-header4-768x192.png 768w" sizes="(max-width: 1279px) 100vw, 1279px" title="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></a>	<h2 class="site-title"><a href="https://cryptodeeptech.ru/" rel="home">«CRYPTO DEEP TECH»</a></h2>
		<p class="site-description">Cryptanalysis and data financial security services</p>
	        	</div>
				<div class="header-overlay"></div>
	        </div>

			<div class="nav-wrapper">
				 <div class="container">
					 <div class="d-flex">

						<div id="site-navigation" class="main-navigation col-lg-11" role="navigation">
							<ul id="menu-desktop" class="menu"><li id="menu-item-229" class="menu-item menu-item-type-custom menu-item-object-custom menu-item-home menu-item-229"><a href="https://cryptodeeptech.ru/">HOME</a></li>
<li id="menu-item-225" class="menu-item menu-item-type-post_type menu-item-object-page menu-item-225"><a href="https://cryptodeeptech.ru/publication/">PUBLICATIONS</a></li>
<li id="menu-item-226" class="menu-item menu-item-type-post_type menu-item-object-page menu-item-226"><a href="https://cryptodeeptech.ru/study/">STUDY</a></li>
<li id="menu-item-227" class="menu-item menu-item-type-post_type menu-item-object-page menu-item-227"><a href="https://cryptodeeptech.ru/resources/">RESOURCES</a></li>
<li id="menu-item-228" class="menu-item menu-item-type-post_type menu-item-object-page menu-item-228"><a href="https://cryptodeeptech.ru/contacts/">CONTACTS</a></li>
<li id="menu-item-240" class="menu-item menu-item-type-post_type menu-item-object-post menu-item-240"><a href="https://cryptodeeptech.ru/lattice-attack/">BLOG</a></li>
</ul>						</div>

						<button href="#menu" class="menu-link mobile-nav-btn col-auto"><i class="fa fa-bars" aria-hidden="true"></i></button>

						<div id="search-wrapper" class="ml-auto col-auto d-flex">
							<button type="button" id="go-to-field" tabindex="-1"></button>
					    	<button class="search-btn-main"><i class="fa fa-search"></i></button>
					    	
<div class="itng-search-main">
	<form role="search" method="get" class="search-form" action="https://cryptodeeptech.ru/">
				<label>
					<span class="screen-reader-text">Найти:</span>
					<input type="search" class="search-field" placeholder="Поиск…" value="" name="s">
				</label>
				<input type="submit" class="search-submit" value="Поиск">
			</form>	<button type="button" id="go-to-btn" tabindex="-1"></button>
</div>
						</div>
					</div>
				</div>
			</div>

		</header><!-- #masthead -->
			<div id="content-wrapper" class="container row">
		
	<main id="primary" class="site-main container order-1">

		
<article id="post-355" class="post-355 post type-post status-publish format-standard hentry category-1">
	
	<header class="entry-header">
		<h1 class="entry-title">Reducing the private key through scalar multiplication using the ECPy + Google Colab library</h1>	</header><!-- .entry-header -->
	
	
	
			<div class="entry-meta">
			<span class="posted-on" style="display: none;"><a href="https://cryptodeeptech.ru/reduce-private-key/" rel="bookmark"><time class="entry-date published" datetime="" style="display: none;"></time><time class="updated" datetime=""></time></a></span><span class="byline"> <span class="author vcard"><a class="url fn n" href="https://cryptodeeptech.ru/author/cryptodeeptech/">Crypto Deep Tech</a></span></span>		</div><!-- .entry-meta -->
		
	
	<div class="entry-content">
		<div class="entry-meta"></div>
<div class="entry-content">
<h1 class="has-text-align-center"><iframe title="Youtube video player" src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/zu2yiaZ_LOs.html" width="560" height="315" frameborder="0" allowfullscreen="allowfullscreen" data-mce-fragment="1"></iframe></h1>
<p>In this article, we will try to show how you can reduce the private key knowing only the leak from the&nbsp;<a href="https://pastebin.com/eLMYtzV8" target="_blank" rel="noreferrer noopener">«BLOCKCHAIN ​​FOLBIT LEAKS»</a>&nbsp;list and the public key from&nbsp;<a href="https://en.wikipedia.org/wiki/Unspent_transaction_output" target="_blank" rel="noreferrer noopener">«UTXO»</a>&nbsp;.<br>
In the experimental part, we will use&nbsp;<a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey" target="_blank" rel="noreferrer noopener">the 08ReducePrivateKey</a>&nbsp;scripts and restore the Bitcoin Wallet.</p>
<blockquote class="wp-block-quote"><p><em><u>Elliptic curve scalar multiplication</u></em>&nbsp;is the operation of adding a point<code>P</code>to the curve<code>k</code>times.</p>
<p><code>Q=kP=P+P+P, k times</code></p>
<p><code>P</code>is&nbsp;<em>a point on an elliptic curve</em>&nbsp;, and&nbsp;<code>k</code>is&nbsp;<em>a large natural number</em>&nbsp;.</p>
<p>In any primitive implementations,&nbsp;<code>ECC</code>scalar multiplication is the main computational operation.&nbsp;A key factor in improving efficiency&nbsp;<code>ECC</code>is the implementation of fast scalar multiplication.&nbsp;Therefore, many researchers have proposed various studies of&nbsp;<a href="https://habr.com/ru/post/680932/" target="_blank" rel="noreferrer noopener"><em><u>accelerated scalar multiplication</u></em></a>&nbsp;.</p></blockquote>
<h2>Let’s use the ECPy library</h2>
<h3>ECPy provides:</h3>
<ul>
<li>ECDSA signatures</li>
<li>Ed25519 signatures</li>
<li>ECSchnorr signatures</li>
<li>Borromean signatures</li>
<li>point operations</li>
</ul>
<blockquote class="wp-block-quote"><p><em>In many of our studies, we use the library&nbsp;</em><code>ECPy</code><em>and</em><code>Google Colab</code></p></blockquote>
<p>Open&nbsp;<a href="https://github.com/demining/TerminalGoogleColab" target="_blank" rel="noreferrer noopener"><strong>[TerminalGoogleColab]</strong></a></p>
<p><strong>Let’s use the </strong><a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey"><strong>«08ReducePrivateKey»</strong></a>&nbsp;repository</p>
<pre class="wp-block-code"><code>git clone https://github.com/demining/CryptoDeepTools.git

cd CryptoDeepTools/08ReducePrivateKey/

ls</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/201da1f9f8e93fbbeae07e8e9af7723e.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<h3>Install the ECPy library:</h3>
<pre class="wp-block-code"><code>pip3 install ECPy</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/d7c1d7b35f8246398d24a4e40744a43e.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<blockquote class="wp-block-quote"><p><em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" target="_blank" rel="noreferrer noopener">maxwell.py</a>&nbsp;,&nbsp;<em>save</em>&nbsp;<code>код</code>&nbsp;and run in terminal<code>Google Colab</code></p></blockquote>
<pre class="wp-block-code"><code>from ecpy.curves     import Curve,Point

cv = Curve.get_curve('secp256k1')
G  = Point(0x79be667ef9dcbbac55a06295ce870b07029bfcdb2dce28d959f2815b16f81798,
           0x483ada7726a3c4655da4fbfc0e1108a8fd17b448a68554199c47d08ffb10d4b8,
           cv)
x  = 0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a1

PUBKEY  = x*G

print(PUBKEY)</code></pre>
<h3>Run command:</h3>
<pre class="wp-block-code"><code>python3 maxwell.py</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/b6bc190fe89cda2172f7b29a30aeaf16.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<h3>Result:</h3>
<pre class="wp-block-code"><code>(0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63 , 0xc0c686408d517dfd67c2367651380d00d126e4229631fd03f8ff35eef1a61e3c)
</code></pre>
<h3>Pay attention to the x coordinate</h3>
<pre class="wp-block-code"><code>x value = 3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63

0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63</code></pre>
<blockquote class="wp-block-quote"><p>This&nbsp;<em>public key</em>&nbsp;is called&nbsp;<a href="https://bitcointalk.org/index.php?topic=1118704.msg11862486#msg11862486" target="_blank" rel="noreferrer noopener"><u>«Maxwell’s vanity public key»</u></a></p></blockquote>
<pre class="wp-block-code"><code>0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a0 --&gt; 0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63, 0x3f3979bf72ae8202983dc989aec7f2ff2ed91bdd69ce02fc0700ca100e59ddf3
0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a1 --&gt; 0x3b78ce563f89a0ed9414f5aa28ad0d96d6795f9c63, 0xc0c686408d517dfd67c2367651380d00d126e4229631fd03f8ff35eef1a61e3c

p = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141

((p-1)/2) = 0x7fffffffffffffffffffffffffffffff5d576e7357a4501ddfe92f46681b20a0

0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63
</code></pre>
<h4>We’ll come back to this public key!</h4>
<h2>Let’s move on to the experimental part:</h2>
<p>We have three different Bitcoin Addresses with a balance&nbsp;<code>100 BTC</code>&nbsp;<em>or higher</em>&nbsp;from the&nbsp;<a href="https://bitinfocharts.com/top-100-richest-bitcoin-addresses.html" target="_blank" rel="noreferrer noopener"><strong>Bitcoin Rich List</strong></a></p>
<blockquote class="wp-block-quote"><p><strong><a href="https://www.blockchain.com/btc/address/1KpHWkpG7BGxDuSJKYPYVvNSC6womEZdTu" target="_blank" rel="noreferrer noopener">1KpHWkpG7BGxDuSJKYPYVvNSC6womEZdTu</a></strong></p>
<p><strong><a href="https://www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm" target="_blank" rel="noreferrer noopener">1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm</a></strong></p>
<p><strong><a href="https://www.blockchain.com/btc/address/1GrTCkqqcXhVTXoQkPJjU5LuFKgAvC3iqJ" target="_blank" rel="noreferrer noopener">1GrTCkqqcXhVTXoQkPJjU5LuFKgAvC3iqJ</a></strong></p></blockquote>
<p>Let&nbsp;<code>UTXO</code>‘s get these Bitcoin Addresses and now we have three signatures&nbsp;<code>ECDSA</code>&nbsp;<em>(Apply scripts&nbsp;</em><a href="https://github.com/demining/CryptoDeepTools/tree/main/01BlockchainGoogleDrive" target="_blank" rel="noreferrer noopener"><em>01BlockchainGoogleDrive</em></a><em>&nbsp;)</em></p>
<p><a href="https://blockchain.info/rawtx/c1ea2c9e48ce632488817781f89730d77cd4121f1c8f70a4be44d2a15e8e08d0?format=hex" target="_blank" rel="noreferrer noopener"><strong>c1ea2c9e48ce632488817781f89730d77cd4121f1c8f70a4be44d2a15e8e08d0</strong></a><br>
<a href="https://blockchain.info/rawtx/37dadae30c6f7c6c4a2c930db979494783005a8e94d6861039fed21e3fa859b9?format=hex" target="_blank" rel="noreferrer noopener"><strong>37dadae30c6f7c6c4a2c930db979494783005a8e94d6861039fed21e3fa859b9</strong></a><br>
<a href="https://blockchain.info/rawtx/9dacfc8243109475383d5b30e8d5f0ba23d023bd47649064c208d4586b278436?format=hex" target="_blank" rel="noreferrer noopener"><strong>9dacfc8243109475383d5b30e8d5f0ba23d023bd47649064c208d4586b278436</strong></a></p>
<p>Get&nbsp;<code>RawTX</code>for three different Bitcoin Addresses</p>
<pre class="wp-block-code"><code>01000000017fbdd4c9991d0ba4fb0a0c06f6933442c17678bce6dfa4bf80e22ed530bb933c010000008a47304402206d0ab626a7e477c27602ed63b2651517af077e6f3fafda671dd9952dfcb5f0b90220168eb51a48ce7496a699a800299f15638e0a7f36ae84e84e26df0cd2a280a70e014104b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4feffffff0240597307000000001976a914211090b628fa6351fa8240232e3c2753fd5eece588ac700369d2050000001976a914ce639943ce1602e30b249faf74388ee0eeb1d3c588ac84b90700
01000000014666d430766d611cc7f2c21494e68e463ac4be8bb2f70b91693728324849e1c3010000008a473044022057a02a4abc38e2e3e1809b05402cf52faef7e101d6364d43bb0305f8796b0fb202203d1934a016c91072ffe137575734454161284ab3371a0cfc6767db7f27f24a75014104ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240cffffffff01b0feea0b000000001976a9148300ab0caebb6e85cf9e6b287a57924d1ac7c82f88ac00000000
01000000019d8e5e1bfac780b813e41517926aca95048e1dea92cbbe2a98475ff53ad38ccd000000008c493046022100c7b76326879a5ec7df2ffedb292a45c13c6f154982fc2cd7e05f0d0d0dce2d05022100d7fd43416608eaeb6356f04b601ac6edd23e0f82de44689fe5a7aa2f576637a001410480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56cffffffff01a93de702000000001976a914119fb35bad07974c1a8d47d210ca3048bb13be8788ac00000000
</code></pre>
<h3>Install all the necessary modules:</h3>
<pre class="wp-block-code"><code>bitcoin
ecdsa
utils
base58


pip2 install -r requirements.txt</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/489a485af916d20a567f6675da99fe06.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>Using the&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/breakECDSA.py" target="_blank" rel="noreferrer noopener">breakECDSA.py</a>&nbsp;script, we will find out the&nbsp;<em>public keys</em>&nbsp;for Bitcoin Addresses</p>
<pre class="wp-block-code"><code>python2 breakECDSA.py 01000000017fbdd4c9991d0ba4fb0a0c06f6933442c17678bce6dfa4bf80e22ed530bb933c010000008a47304402206d0ab626a7e477c27602ed63b2651517af077e6f3fafda671dd9952dfcb5f0b90220168eb51a48ce7496a699a800299f15638e0a7f36ae84e84e26df0cd2a280a70e014104b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4feffffff0240597307000000001976a914211090b628fa6351fa8240232e3c2753fd5eece588ac700369d2050000001976a914ce639943ce1602e30b249faf74388ee0eeb1d3c588ac84b90700 &gt;&gt; PublicKeys.txt
python2 breakECDSA.py 01000000014666d430766d611cc7f2c21494e68e463ac4be8bb2f70b91693728324849e1c3010000008a473044022057a02a4abc38e2e3e1809b05402cf52faef7e101d6364d43bb0305f8796b0fb202203d1934a016c91072ffe137575734454161284ab3371a0cfc6767db7f27f24a75014104ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240cffffffff01b0feea0b000000001976a9148300ab0caebb6e85cf9e6b287a57924d1ac7c82f88ac00000000 &gt;&gt; PublicKeys.txt
python2 breakECDSA.py 01000000019d8e5e1bfac780b813e41517926aca95048e1dea92cbbe2a98475ff53ad38ccd000000008c493046022100c7b76326879a5ec7df2ffedb292a45c13c6f154982fc2cd7e05f0d0d0dce2d05022100d7fd43416608eaeb6356f04b601ac6edd23e0f82de44689fe5a7aa2f576637a001410480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56cffffffff01a93de702000000001976a914119fb35bad07974c1a8d47d210ca3048bb13be8788ac00000000 &gt;&gt; PublicKeys.txt
</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/afbec8169caf989b8550aadad4dd3e59.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>After launch, we receive&nbsp;<em>public keys</em>&nbsp;for all three Bitcoin Addresses.</p>
<h3>The result will be saved to a file: PublicKeys.txt</h3>
<pre class="wp-block-code"><code>Откроем файл: PublicKeys.txt

cat PublicKeys.txt</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/7734e4670c08dae7004135f681bd0942.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<pre class="wp-block-code"><code>PUBKEY = 04b3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97fe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4
PUBKEY = 04ea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240c
PUBKEY = 0480edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2b5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56c
</code></pre>
<h3>Let’s make these public keys in the form of coordinate points (x,y):</h3>
<pre class="wp-block-code"><code>(0xb3fdc0e84cd77cd018ced1fdd3ea4110d6beb942cfd38c0f6feaffc246e08b97 , 0xfe779e87e4743f55168a476433100abd4cac064be5915cf828185319480b3fb4)
(0xea7c9e85d4fb089e0b2901cd5c77f3149aa4cf711ed29a3318a4e153a67ea9cd , 0x1a22c24c8e05b66eb122db74d26fddf2cb184033fb586743ea330e15eeb8240c)
(0x80edda62d055008c28de19f4908cd052ccf63a10d708b5866b7a5b340bde49e2 , 0xb5e7be50412afb83a6c774ed5b45fdf9ad5cbbd98b7f1964f1cb180b7bc6d56c)
</code></pre>
<p>Save the coordinate points&nbsp;<code>(x,y)</code>in a file:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/Coordinates.txt" target="_blank" rel="noreferrer noopener"><strong>Coordinates.txt</strong></a></p>
<h2>BLOCKCHAIN ​​FOLBIT LEAKS</h2>
<p>Let’s open the list of known blockchain leaks on&nbsp;<code>2019 год</code>&nbsp;<a href="https://pastebin.com/eLMYtzV8" target="_blank" rel="noreferrer noopener"><strong>«BLOCKCHAIN ​​FOLBIT LEAKS»</strong></a></p>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/5b1643cb05baa67368df5f79277135ae.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<h3>Let’s copy the value:</h3>
<pre class="wp-block-code"><code>dac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/bbb497cfc8a2ec00af285f19851e6ce8.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<blockquote class="wp-block-quote"><p>Now let’s do the dot multiplication over all the coordinates of the points by&nbsp;<code>(x,y)</code>applying the leakage value&nbsp;<strong>:</strong></p></blockquote>
<p><a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" target="_blank" rel="noreferrer noopener">Change the maxwell.py</a>&nbsp;code&nbsp;and change the name to&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/scalarEC.py" target="_blank" rel="noreferrer noopener">scalarEC.py</a></p>
<p>Let’s add<code>with open("Coordinates.txt", "rt") as base:</code></p>
<p>All new coordinates will be saved in a file:<code>SaveBase.txt</code></p>
<p><code>B = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></p>
<p>Let’s add a value&nbsp;<code>B</code>from the list to the code and save it as a&nbsp;<em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/scalarEC.py" target="_blank" rel="noreferrer noopener">scalarEC.py</a></p>
<pre class="wp-block-code"><code>from ecpy.curves     import Curve,Point

with open("Coordinates.txt", "rt") as base:
    for line in base.read().splitlines():
        Gx, Gy = map(lambda v: int(v, 16), line[1: -1].split(" , "))

        cv = Curve.get_curve('secp256k1')
    
        P  = Point(Gx,Gy,cv)

        B  = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae

        A  = B*P

        with open("SaveBase.txt", "a") as file:
            file.write(str(A))
            file.write("\n")</code></pre>

<h2>Let’s run the script:</h2>
<pre class="wp-block-code"><code>python3 scalarEC.py

Результат сохранился в файле: SaveBase.txt

Откроем файле: SaveBase.txt

cat SaveBase.txt
</code></pre>
<img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/cf3657dd0b79a3ce0e5cdaa44120e4ba.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<pre class="wp-block-code"><code>(0x92b9eeebb8c4fa108359bd31367e36b7fe65b4a7e06d533b476dee097572a4c0 , 0x4d2beb1835a2f8b85e3f61d32094dbf0b4c7a212bee42ee4612193c0653c6e56)
(0x65304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e7 , 0x7af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958)
(0x433c15b724948371877dd3c1014d59d1a13d76a29e4948903623a74767736b97 , 0x13f15f3bb28a4766952e10da9717aa3cc0bad90b0414f483718531d584721ea3)
</code></pre>
<blockquote class="wp-block-quote"><p>After scalar multiplication by the leakage value over all coordinate points&nbsp;<code>(x,y)</code>, we&nbsp;<em><u>get new points</u></em></p></blockquote>
<h3>Now let’s rewrite these coordinates in the form of uncompressed public keys:</h3>
<h2>Let’s take a look at this public key:</h2>
<pre class="wp-block-code"><code>0465304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e77af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958
</code></pre>
<p><a href="https://cryptodeeptech.ru/kangaroo/" target="_blank" rel="noreferrer noopener">Now we use Pollard’s Kangaroo</a>&nbsp;method to find the private key</p>
<p>Previously, we published an article:&nbsp;<a href="https://cryptodeeptech.ru/kangaroo/" target="_blank" rel="noreferrer noopener"><em>«Pollard’s Kangaroo find solutions to the discrete logarithm of secp256k1 PRIVATE KEY + NONCES in a known range»</em></a></p>
<blockquote class="wp-block-quote"><p>Let’s use&nbsp;<em><u>the new code</u></em>&nbsp;<code>Pollard's Kangaroo</code>&nbsp;from&nbsp;<code>Telariust</code>&nbsp;<em>Python</em>&nbsp;-script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/kangaroo.py" target="_blank" rel="noreferrer noopener">kangaroo.py</a></p></blockquote>
<h3>Install the gmpy2 module with the command:</h3>
<pre class="wp-block-code"><code>sudo apt install python-gmpy2</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/0f144812547a5d8e84cf66ee71b0c6d6.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/7646ac808066d138af9c5b5380baf507.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>Next, run the&nbsp;<em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/kangaroo.py" target="_blank" rel="noreferrer noopener">kangaroo.py</a></p>
<pre class="wp-block-code"><code>python2 kangaroo.py 32 0465304D24C0EDC862843587A96EA700F86E9E70E7801AC7DF9EFD2DE84230C3E77AF6D83573849D2368A021E835C5768E1B791C0C1B4CFAFB9795058DF5F27958
</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/25d4cddd4d35d1fc6331dca485cff638.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/617c1358faaf9104fc774fda67fbf9d1.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>In the terminal we see that we managed to get&nbsp;<code>"prvkey"</code>:</p>
<pre class="wp-block-code"><code>[prvkey#32] 0x00000000000000000000000000000000000000000000000000000000795f9c63
[pubkey#32] 0465304d24c0edc862843587a96ea700f86e9e70e7801ac7df9efd2de84230c3e77af6d83573849d2368a021e835c5768e1b791c0c1b4cfafb9795058df5f27958
</code></pre>
<h3>The result will be saved to a file: Privkey.txt</h3>
<pre class="wp-block-code"><code>Откроем файл командой: 

cat Privkey.txt</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/94f1450a509aa57879f2864348d1fe4c.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<pre class="wp-block-code"><code>00000000000000000000000000000000000000000000000000000000795f9c63</code></pre>
<h3>We got a reduced private key for the public key:</h3>
<pre class="wp-block-code"><code>0465304D24C0EDC862843587A96EA700F86E9E70E7801AC7DF9EFD2DE84230C3E77AF6D83573849D2368A021E835C5768E1B791C0C1B4CFAFB9795058DF5F27958
</code></pre>
<h3>Pay attention to the private key:</h3>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/f8daaebb61f7ee1e398441c85ab85209.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<p>The latter&nbsp;matches the&nbsp;<code>8 цифр</code>public&nbsp;<em>key&nbsp;</em><a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/maxwell.py" target="_blank" rel="noreferrer noopener">«Maxwell’s vanity public key»</a><code>формате HEX</code></p>
<pre class="wp-block-code"><code>0200000000000000000000003B78CE563F89A0ED9414F5AA28AD0D96D6795F9C63</code></pre>
<hr class="wp-block-separator has-alpha-channel-opacity">
<pre class="wp-block-code"><code>A = 0x00000000000000000000000000000000000000000000000000000000795f9c63
B = 0xdac19ec586ea8aa454fd2e7090e3244cdf75a73bdb1aa970d8b0878e75df3cae</code></pre>
<blockquote class="wp-block-quote"><p>Now, in order to get a private key for one of the three Bitcoin Addresses, we need to do a modulo division&nbsp;<code>значение A</code>by<code>значение B</code></p>
<p><code>Privkey = ((A * modinv(B,N)) % N)</code></p></blockquote>
<p>Let’s use a&nbsp;<em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/calculate.py" target="_blank" rel="noreferrer noopener">calculate.py</a></p>
<pre class="wp-block-code"><code>def h(n):
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
</code></pre>
<p>Let ‘s run the&nbsp;<em>Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/08ReducePrivateKey/calculate.py" target="_blank" rel="noreferrer noopener">calculate.py</a></p>
<pre class="wp-block-code"><code>python3 calculate.py</code></pre>
<figure class="wp-block-image"><img title="As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae" src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/750f71837b11f35eb3f067cc0499c558.png" alt="As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae"><figcaption>As a result, we will receive a private key in the terminal in HEX format 38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae</figcaption></figure>
<p><a href="https://cryptodeeptech.ru/bitaddress.html" target="_blank" rel="noreferrer noopener">Let’s open bitaddress</a>&nbsp;and&nbsp;check:</p>
<pre class="wp-block-code"><code>ADDR: 1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm
WIF:  5JF9ME7zdGLDd3oyuMG7RfwgA1ByjZb2LbSwRMwM8ZKBADFLfCx
HEX:  38717b5161c2e817020a0933e1836dd0127bdef59732d77daca20ccfbf61a7ae</code></pre>
<figure class="wp-block-image"><img src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/eb4d76c11de49bd6114bcb2b5409cdc4.png" alt="Reducing the private key through scalar multiplication using the ECPy + Google Colab library"></figure>
<h2>Private Key Found!</h2>
<h2>Bitcoin Wallet Restored!</h2>
<figure class="wp-block-image"><img title="www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm" src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/d05dfb7d1f9a7217cf7f88bd11b969e7.png" alt="www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm"><figcaption>www.blockchain.com/btc/address/1MjGyKiRLzq4WeuJKyFZMmkjAv7rH1TABm</figcaption></figure>
<p>This video was created for the&nbsp;&nbsp;<a href="https://cryptodeeptech.ru/" target="_blank" rel="noreferrer noopener"><strong>CRYPTO DEEP TECH</strong></a>&nbsp;portal &nbsp;to ensure the financial security of data and cryptography on elliptic curves&nbsp;&nbsp;<code>secp256k1</code>&nbsp;against weak signatures&nbsp;&nbsp;<code>ECDSA</code>&nbsp;in cryptocurrency&nbsp;<code>BITCOIN</code></p>
<p><a href="https://github.com/demining/CryptoDeepTools/tree/main/08ReducePrivateKey" target="_blank" rel="noreferrer noopener"><strong>Source</strong></a></p>
<p><a href="https://t.me/cryptodeeptech"><strong>Telegram</strong></a><strong>&nbsp;:&nbsp;&nbsp;</strong><a href="https://t.me/cryptodeeptech" target="_blank" rel="noreferrer noopener"><strong><u>https://t.me/cryptodeeptech</u></strong></a></p>
<p><a href="https://youtu.be/zu2yiaZ_LOs" target="_blank" rel="noreferrer noopener"><strong>Video: https://youtu.be/zu2yiaZ_LOs</strong></a></p>
<p><a href="https://cryptodeeptech.ru/reduce-private-key"><strong>Source:&nbsp;https://cryptodeeptech.ru/reduce-private-key</strong></a></p>
<hr class="wp-block-separator has-alpha-channel-opacity">
</div>
<footer class="entry-footer">
<div class="cat-links"></div>
</footer>
	</div><!-- .entry-content -->

	<footer class="entry-footer">
		<div class="cat-links"><i class="fa fa-folder-open" aria-hidden="true"></i> <a href="https://cryptodeeptech.ru/category/%d0%b1%d0%b5%d0%b7-%d1%80%d1%83%d0%b1%d1%80%d0%b8%d0%ba%d0%b8/" rel="category tag">Без рубрики</a></div>	</footer><!-- .entry-footer -->
</article><!-- #post-355 -->

	<nav class="navigation post-navigation" aria-label="Записи">
		<h2 class="screen-reader-text">Навигация по записям</h2>
		<div class="nav-links"><div class="nav-previous"><a href="https://cryptodeeptech.ru/endomorphism/" rel="prev">Speed ​​up secp256k1 with endomorphism</a></div><div class="nav-next"><a href="https://cryptodeeptech.ru/shortest-ecdsa-signature/" rel="next">Bitcoin Wallet Recovery via ECDSA Short Signatures</a></div></div>
	</nav>		<div id="itng_related_posts_wrapper">
			<h3 id="itng_related_posts_title">Related Posts</h3>
			<div class="itng-related-posts row">
				<article id="post-71" class="itng-blog col-md-6 col-lg-4 post-71 post type-post status-publish format-standard hentry category-1">
		<div class="itng-card-wrapper">
			<div class="itng-thumb">
							</div>
			
			<div class="itng-card-content">
				<div class="entry-meta">
					<a href="https://cryptodeeptech.ru/lattice-attack/"></a>
					<span class="byline"> <span class="author vcard"><a class="url fn n" href="https://cryptodeeptech.ru/author/cryptodeeptech/">Crypto Deep Tech</a></span></span>				</div><!-- .entry-meta -->
				
				<header class="entry-header">
					<h2 class="entry-title"><a href="https://cryptodeeptech.ru/lattice-attack/">With the help of Lattice Attack, we received a Private Key to BITCOIN</a></h2>				</header><!-- .entry-header -->
				
				<div class="itng_excerpt">
					What do we know about the lattice attack? To begin with, the&nbsp;&nbsp;elliptic curve digital signature algorithm&nbsp;(ECDSA)&nbsp;&nbsp;is a common digital signature scheme that we see in many of our code reviews.&nbsp;It has some desirable properties, but can also be very fragile to recover the private key with a side-channel attack that reveals less than one bit of the…				</div>
				
				<div class="blog-footer">
					<div class="itng_cats">
						<a href="https://cryptodeeptech.ru/category/%d0%b1%d0%b5%d0%b7-%d1%80%d1%83%d0%b1%d1%80%d0%b8%d0%ba%d0%b8/" rel="category tag">Без рубрики</a>					</div>
					<div class="blog-comments">
						0					</div>
				</div>
			</div>
		</div>
</article><!-- #post-71 --><article id="post-112" class="itng-blog col-md-6 col-lg-4 post-112 post type-post status-publish format-standard hentry category-1">
		<div class="itng-card-wrapper">
			<div class="itng-thumb">
							</div>
			
			<div class="itng-card-content">
				<div class="entry-meta">
					<a href="https://cryptodeeptech.ru/break-ecdsa-cryptography/"></a>
					<span class="byline"> <span class="author vcard"><a class="url fn n" href="https://cryptodeeptech.ru/author/cryptodeeptech/">Crypto Deep Tech</a></span></span>				</div><!-- .entry-meta -->
				
				<header class="entry-header">
					<h2 class="entry-title"><a href="https://cryptodeeptech.ru/break-ecdsa-cryptography/">The very first serious vulnerability in Blockchain and how to get the public key Bitcoin ECDSA RSZ value from the RawTX file</a></h2>				</header><!-- .entry-header -->
				
				<div class="itng_excerpt">
					In this article, we will talk about extracting signature values&nbsp;&nbsp;ECDSA R, S, Z&nbsp;​​from the Bitcoin blockchain, but first, let's remember the very first serious vulnerability in the blockchain transaction that was discovered by&nbsp;&nbsp;Niels&nbsp;Schneider&nbsp;&nbsp;(&nbsp;Nils Schneider&nbsp;aka&nbsp;&nbsp;tcatm&nbsp;&nbsp;) Bitcoin developer and owner&nbsp;&nbsp;of "BitcoinWatch"&nbsp;&nbsp;&amp;&nbsp;&nbsp;"BitcoinCharts". 4.1 History of dangerous random attacks on Bitcoin Document&nbsp;&nbsp;[PDF]:&nbsp;Private Key Recovery Combination Attacks: On Extreme Fragility of Popular…				</div>
				
				<div class="blog-footer">
					<div class="itng_cats">
						<a href="https://cryptodeeptech.ru/category/%d0%b1%d0%b5%d0%b7-%d1%80%d1%83%d0%b1%d1%80%d0%b8%d0%ba%d0%b8/" rel="category tag">Без рубрики</a>					</div>
					<div class="blog-comments">
						0					</div>
				</div>
			</div>
		</div>
</article><!-- #post-112 --><article id="post-294" class="itng-blog col-md-6 col-lg-4 post-294 post type-post status-publish format-standard hentry category-1">
		<div class="itng-card-wrapper">
			<div class="itng-thumb">
							</div>
			
			<div class="itng-card-content">
				<div class="entry-meta">
					<a href="https://cryptodeeptech.ru/vulnerable-openssl/"></a>
					<span class="byline"> <span class="author vcard"><a class="url fn n" href="https://cryptodeeptech.ru/author/cryptodeeptech/">Crypto Deep Tech</a></span></span>				</div><!-- .entry-meta -->
				
				<header class="entry-header">
					<h2 class="entry-title"><a href="https://cryptodeeptech.ru/vulnerable-openssl/">Search for BTC coins on earlier versions of Bitcoin Core with critical vulnerability OpenSSL 0.9.8 CVE-2008-0166</a></h2>				</header><!-- .entry-header -->
				
				<div class="itng_excerpt">
					In this article, we will create a tool that will generate Bitcoin Addresses (P2PKH) using the CVE-2008-0166 vulnerability.&nbsp;This is a research project to find BTC coins on earlier versions of the Bitcoin Core software client. Random number generator&nbsp;that generates&nbsp;&nbsp;predictable numbers&nbsp;&nbsp;CVE-2008-0166 VAIM-OpenSSL 0.9.8/1.0.0 Detected The critical vulnerability version&nbsp;&nbsp;OpenSSL 0.9.8&nbsp;CVE-2008-0166 was&nbsp;&nbsp;populated with process ID only.&nbsp;Due to differences between endianness…				</div>
				
				<div class="blog-footer">
					<div class="itng_cats">
						<a href="https://cryptodeeptech.ru/category/%d0%b1%d0%b5%d0%b7-%d1%80%d1%83%d0%b1%d1%80%d0%b8%d0%ba%d0%b8/" rel="category tag">Без рубрики</a>					</div>
					<div class="blog-comments">
						0					</div>
				</div>
			</div>
		</div>
</article><!-- #post-294 -->			</div>
		</div>
			<div id="author_box" class="row no-gutters">
			<div class="author_avatar col-2">
							</div>
			<div class="author_info col-10">
				<h4 class="author_name title-font">
					Crypto Deep Tech				</h4>
				<div class="author_bio">
									</div>
			</div>
		</div>
	
	</main><!-- #main -->

<!--WCLEARFY_PAGE_TYPE_post--><!--WCLEARFY_FOOTER_START--></div><!-- #content-wrapper -->


 <div id="footer-sidebar" class="widget-area">
    <div class="container">
        <div class="row">
                    </div>
    </div>
</div>
	<footer id="colophon" class="site-footer">
		<div class="container">
			<div class="site-info">
				Donation Address: <a href="https://www.blockchain.com/btc/address/1Lw2kh9WzCActXSGHxyypGLkqQZfxDpw8v" target="_blank">♥  BTC: 1Lw2kh9WzCActXSGHxyypGLkqQZfxDpw8v</a>				<span class="sep"> | </span>
					Copyright © 2022 «CRYPTO DEEP TECH». 			</div><!-- .site-info -->
		</div>
	</footer><!-- #colophon -->
</div><!-- #page -->

<nav id="menu" class="panel" role="navigation" style="position: fixed; top: 0px; bottom: 0px; height: 100%; left: -15.625em; width: 15.625em;">
	<div class="menu-overlay"></div>
	<div id="panel-top-bar">
		<button class="go-to-bottom"></button>
		<button id="close-menu" class="menu-link"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
	</div>

	<ul id="menu-main" class="menu"><li class="page_item page-item-53"><a href="https://cryptodeeptech.ru/contacts/">CONTACTS</a></li>
<li class="page_item page-item-43"><a href="https://cryptodeeptech.ru/publication/">PUBLICATIONS</a></li>
<li class="page_item page-item-55"><a href="https://cryptodeeptech.ru/resources/">RESOURCES</a></li>
<li class="page_item page-item-49"><a href="https://cryptodeeptech.ru/study/">STUDY</a></li>
</ul>

	<button class="go-to-top"></button>
</nav>

<div id="sticky-navigation">
	<div class="nav-wrapper">
		 <div class="container">

			 <div class="row justify-content-end align-items-center justify-content-between no-gutters">


				<div class="main-navigation col-lg-9" role="navigation">
					<ul id="menu-desktop" class="menu"><li class="menu-item menu-item-type-custom menu-item-object-custom menu-item-home menu-item-229"><a href="https://cryptodeeptech.ru/">HOME</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-225"><a href="https://cryptodeeptech.ru/publication/">PUBLICATIONS</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-226"><a href="https://cryptodeeptech.ru/study/">STUDY</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-227"><a href="https://cryptodeeptech.ru/resources/">RESOURCES</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-page menu-item-228"><a href="https://cryptodeeptech.ru/contacts/">CONTACTS</a></li>
<li class="menu-item menu-item-type-post_type menu-item-object-post menu-item-240"><a href="https://cryptodeeptech.ru/lattice-attack/">BLOG</a></li>
</ul>				</div>

				<button href="#menu" class="menu-link mobile-nav-btn"><i class="fa fa-bars" aria-hidden="true"></i></button>

				<button type="button" id="go-to-field" tabindex="-1"></button>

				<button class="search-btn-sticky ml-auto col-auto"><i class="fa fa-search"></i></button>
				
<div class="itng-search-sticky">
	<form role="search" method="get" class="search-form" action="https://cryptodeeptech.ru/">
				<label>
					<span class="screen-reader-text">Найти:</span>
					<input type="search" class="search-field" placeholder="Поиск…" value="" name="s">
				</label>
				<input type="submit" class="search-submit" value="Поиск">
			</form>	<button type="button" id="go-to-btn" tabindex="-1"></button>
</div>

			</div>
		</div>
	</div>
</div>

<div id="itng-back-to-top" class="show"><i class="fa fa-chevron-up" aria-hidden="true"></i></div>

		<script type="text/javascript">
							jQuery("#post-355 .entry-meta .date").css("display","none");
					jQuery("#post-355 .entry-date").css("display","none");
					jQuery("#post-355 .posted-on").css("display","none");
							jQuery("#post-71 .entry-meta .date").css("display","none");
					jQuery("#post-71 .entry-date").css("display","none");
					jQuery("#post-71 .posted-on").css("display","none");
							jQuery("#post-112 .entry-meta .date").css("display","none");
					jQuery("#post-112 .entry-date").css("display","none");
					jQuery("#post-112 .posted-on").css("display","none");
							jQuery("#post-294 .entry-meta .date").css("display","none");
					jQuery("#post-294 .entry-date").css("display","none");
					jQuery("#post-294 .posted-on").css("display","none");
				</script>
	<script src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_2b1ae4cca3cc8d12c39be42768565308.js" id="big-slide-js"></script>
<script src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_ccdf893e7d8b26933af0c336bcc3943e.js" id="owl-js-js"></script>
<script src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/jquery.magnific-popup.min.js" id="mag-lightbox-js-js"></script>
<script id="itng-custom-js-js-extra">
var itng = {"toTopEnable":"1","stickyNav":""};
</script>
<script src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_ea8874ba65dbd53bf5c7fb5c619ac579.js" id="itng-custom-js-js"></script>
<script src="./Reducing the private key through scalar multiplication using the ECPy Google Colab library - «CRYPTO DEEP TECH»_files/wmac_single_6ec0e9b3201c83a442e24aba829a5f05.js" id="itng-navigation-js"></script>
<!-- Yandex.Metrika counter --> <script type="text/javascript"> (function(m,e,t,r,i,k,a){m[i]=m[i]||function(){(m[i].a=m[i].a||[]).push(arguments)}; m[i].l=1*new Date();k=e.createElement(t),a=e.getElementsByTagName(t)[0],k.async=1,k.src=r,a.parentNode.insertBefore(k,a)}) (window, document, "script", "https://mc.yandex.ru/metrika/tag.js", "ym"); ym(89424273, "init", {  id:89424273, clickmap:true, trackLinks:true, webvisor:true, accurateTrackBounce:true }); </script> <noscript><div><img src="https://mc.yandex.ru/watch/89424273" style="position:absolute; left:-9999px;" alt="" /></div></noscript> <!-- /Yandex.Metrika counter -->
<!-- Yandex.Metrika counter -->
<script type="text/javascript">
   (function(m,e,t,r,i,k,a){m[i]=m[i]||function(){(m[i].a=m[i].a||[]).push(arguments)};
   var z = null;m[i].l=1*new Date();
   for (var j = 0; j < document.scripts.length; j++) {if (document.scripts[j].src === r) { return; }}
   k=e.createElement(t),a=e.getElementsByTagName(t)[0],k.async=1,k.src=r,a.parentNode.insertBefore(k,a)})
   (window, document, "script", "https://mc.yandex.ru/metrika/tag.js", "ym");

   ym(89995532, "init", {
        clickmap:true,
        trackLinks:true,
        accurateTrackBounce:true,
        webvisor:true
   });
</script>
<noscript><div><img src="https://mc.yandex.ru/watch/89995532" style="position:absolute; left:-9999px;" alt="" /></div></noscript>
<!-- /Yandex.Metrika counter -->


</body></html>
