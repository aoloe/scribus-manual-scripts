Ale Rimoldi wrote on the mailing list:

> loading from a text file is rather trivial.
>
> i remember having created an external translation workflow for a comic book in the past.
>
> getting the formatting imported (and even more syncing the format) is less trivial or -- depending on what you want to achieve -- needs hard work on the scribus code.

Juraj Fedel wrote a script to read/write attributes and store there the information on external items to be synced:

```py
scribus.newDocument(scribus.PAPER_A4,  (15,15,  20, 20),  scribus.PORTRAIT, 1, scribus.UNIT_POINTS,  scribus.PAGE_1, 0, 1)
txt=scribus.createText(70, 70, 200,  150)
scribus.setText('Hello World!', txt)

attr = scribus.getObjectAttributes(txt)
attr.append({
    'Name':"SourceUrl",
    'Type': "string",
    'Value': "http://example.com/data.txt",
    'Parameter': "",
    'Relationship': "none",
    'RelationshipTo': "",
    'AutoAddTo': "none"
    })
scribus.setObjectAttributes(attr, txt)
attr = scribus.getObjectAttributes(txt)

scribus.saveDocAs("objattr.sla")
pdf = scribus.PDFfile()
pdf.save()
```
