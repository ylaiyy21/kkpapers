kkpapers jquery��ҳ����

1.����pager.js��pager.css�ļ�

2.ҳ������
	"<div class="kkpager"></div>"
3.javaScrpt
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
			// ������ҳ
			kkpager.generPageHtml(config);
	};

ԭ�ĵ�ַ��https://github.com/pgkk/kkpager