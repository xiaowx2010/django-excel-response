django-excel-response
=====================

>Fork by https://bitbucket.org/tarkatronic/django-excel-response, add supported for RawQuerySet.


This is http://djangosnippets.org/snippets/1151/ uploaded to pypi.
Author is Tarken.

A subclass of HttpResponse which will transform a QuerySet,
or sequence of sequences, into either an Excel spreadsheet or
CSV file formatted for Excel, depending on the amount of data.
All of this is done in-memory and on-the-fly, with no disk writes,
thanks to the StringIO library.

Installation
============



    pip install django-excel-response xlwt


Usage
=====



    from excel_response import ExcelResponse

    def excelview(request):
        objs = SomeModel.objects.all()
        return ExcelResponse(objs)


or

    from excel_response import ExcelResponse

    def excelview(request):
        data = [
            ['Column 1', 'Column 2'],
            [1,2]
            [23,67]
        ]
        return ExcelResponse(data, 'my_data')
        
or

    from excel_response import ExcelResponse
    def export_excel(request):
        objs = TranOrder.objects.raw(u"select '' as id, `usage` as 用途, model as 配置, count as 数量 from tran_order")
        return ExcelResponse(objs, u'文件名'.encode('gb2312'))
