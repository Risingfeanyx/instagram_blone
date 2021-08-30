#Todo: implement using read/web based url, more automatic, rewrite using curl/more interactive

#The purpose of this hyper-minimal function is twofold; you tell it a filename and descriptor, and it will create a new html page headed with your image, descriptor, and insert a link to the page into your index.html page, so instead  of writing a whole new page in your text editor of choice, you'd run newpage $image.fileformat $descriptor, 
and let it do the rest. 



Here's an example
<img src="image.png">

Replaced using read/asks for descriptions of each image

```
image_2()
{
  clear
  mkdir -p images.$(date +%F)
  echo "<a href="images.$(date +%F)/">$(date +%F)</a>" >> index.html
  cp -v *.{png,jpg,jpeg,gif,tiff} images.$(date +%F)/
  cd images.$(date +%F)
  for i in *
  do 
  read -rp "tell me about $i" descriptor
  echo "<img src=$i /img>" >> index.html
  echo -e "<p><em>  $descriptor  </em></p>" >> index.html
done
  cd ..
}
```
