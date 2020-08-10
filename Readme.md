## Template to PDF in Django

- First You need to install a module ** xhtml2pdf **
``` python

  pip install xhtml2pdf

```

- If your installation is success then import the module in views.py

``` python
  from xhtml2pdf import pisa
  def getpdfpage(req):
    data = Add_Data.objects.all()
    dat = {'dataa':data}
    response = HttpResponse(content_type="application/pdf")
    response['Content-Disposition'] = 'attachment; filename="Guru_data.pdf"'
    template = get_template('pdfpage.html')
    data = template.render(dat)
    pdfpage = pisa.CreatePDF(data,dest=response,link_callback='showdata')
    if not pdfpage.err:
      return response
    else:
      return HttpResponse('ERROR')
```
- When you are accessing the url getpdfpage your pdf page successfully downloaded
