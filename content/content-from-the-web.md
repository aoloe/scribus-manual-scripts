On May 2 2018, Greg Pittman wrote to the mailing list:

> I recently was working on a script, part of which included getting an image from the web. It was challenging. Here is what ended up working:
>
> ```py
>	imagefr = scribus.createImage(175, 14, 20, 7)
>        logo = cStringIO.StringIO(urllib.urlopen("https://website/image.jpg").read())
>        img = Image.open(logo)
>        img.save('/tmp/savedimage.jpg')
>        scribus.loadImage('/tmp/savedimage.jpg', imagefr)
>        scribus.setScaleImageToFrame(1,1,imagefr)
> ```

he wrote that he needed `import PIL, urllib, cStringIO` but there must be ways to simplify it.
