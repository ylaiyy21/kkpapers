kkpapers jquery分页工具
======================

###1.引入pager.js和pager.css文件
```html
	<script type="text/javascript" src="kkpager.js"></script>
	<link rel="stylesheet" type="text/css" href="kkpager.css" />
```
	
###2.页面引用
```html
		<div class="kkpager"></div>
```
###3.javaScrpt
```html
	var pageSize = 9;
	var pageCount = 0;
	var total = 0;
	var pageIndex = 1;

	function selPageList(){
		selPageinfo(1);
		showPageList(1);
	}

	function selPageinfo(page_index){
		var data = getAjaxToData(url,params,'post','json');
		total = data.pageInfo.totalRowNum;
		pageCount = Math.ceil(total/(pageSize+1));
		
	}

	function showPageList(pno) {
			var config = {
				pno : pno,
				total : pageCount,
				totalRecords : total,
				isShowFirstPageBtn  : false,
				isShowLastPageBtn   : false,
				mode : 'click',
				click : function(n){
					console.log('page:'+n);
					 this.selectPage(n);
					 selPageinfo(n);
					 return false;
				}
			};
			kkpager.init(config);
			// 创建分页
			kkpager.generPageHtml(config);
	};
```
###原文地址：https://github.com/pgkk/kkpager