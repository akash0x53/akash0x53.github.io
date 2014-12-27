---
layout: post
title: "RGB Normalization"
date: 2013-04-29 20:16
comments: true
categories: opencv segmentation
---

Segmentation is always a very important and basic task while detecting a particular object. For example, In [this](http://www.pranavmistry.com/projects/sixthsense/images/full/sixthsense12.jpg) picture, Pranav Mistry wearing color markers on his fingers to track the motion of fingers and do some task according to movement of fingers.
<!--more-->
Is it sound easy? Yeah! but detecting an object is not an easy task. Light also play crucial role. For example, if you have unidirectional source of light then it creates shadow and different shades of colors on object as you can see in following picture.  

{% img /images/norm/norm.jpg 500 %}  
Intense light from right side of body whiten the right side of body. Detecting skin or Tshirt from this image is not possible as different shades of colors are there. Some part is highlighted and some in shadowed region. If we choose to detect blue T-shirt using RGB value that range varies from (10,80,200) to (10,70,230) (approximate values) then it will not detect the whole T-shirt. It will partially detect T-shirt and this is not what you want.  

So to reduce the effects of light, Normalization of color space is helpful. Normalization removes highlighted regions, shadows and make that object easier to detect.  
See the following image. Its free from highlighted region, shadow and objects are easily detectable now. For example, human skin, green curtain and Tshirt.
{% img /images/norm/norm2.jpg 500 %}  

####How to convert RGB to Normalized-RGB?  
Now some mathematical work starts here, following equation convert a pixel to normalized pixel.  
{% img /images/norm/eq.png 400 %}

#####Explaination:  
let R,G,B are pixel values,  
to normalized the pixel, divide the individual color component with `total' and multiply by 255. Here 255 is scaling factor. You can use any other scaling factor.As this image is 8 bit scaling value is 255.

let f(10,10)=(100,200,150)  
R=100,  
G=200,  
B=150  

then,  total=(R+G+B)=450  

now,
 R'=(100/450)x255=0.22x255=56.66  
 G'=(200/450)x255=0.44x255=113.33  
 B'=(150/450)x255=0.33x255=85  
then new pixel value is (56,113,85) respective to RGB.  


######Why scaling factor is required?  
In previous example, division results in floating point value that is less than 1.00. Division value 0.22 which then rounded of to 0 that means black color. To avoid this, it must be multiplied by some value.  


#### Python-OpenCV implementation  

This function accepts 8bit image that captured by using OpenCV-python bindings.  


```
def normalized(down):

        norm=np.zeros((600,800,3),np.float32)
        norm_rgb=np.zeros((600,800,3),np.uint8)
              
        b=rgb[:,:,0]
        g=rgb[:,:,1]
        r=rgb[:,:,2]
        
        sum=b+g+r
        
        norm[:,:,0]=b/sum*255.0
        norm[:,:,1]=g/sum*255.0
        norm[:,:,2]=r/sum*255.0
        
        norm_rgb=cv2.convertScaleAbs(norm)
        return norm_rgb
```

