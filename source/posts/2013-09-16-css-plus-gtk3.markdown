---
layout: post
title: "CSS+Gtk3"
date: 2013-09-16 14:00
comments: true
categories: [gtk, python]
---

Remix GTK3 Apps with the magical CSS  <!--more-->

I assumed you know Gtk2 and write Gtk apps in any language, I show you how to  theme your GTK3 apps. Please note CSS support is available for Gtk3 and not for Gtk2.  

First of all create a window which have some widget on it. In my case I add GtkLabel.  

```
#Example Window

import gi.repository Gtk, Gdk

win=Gtk.Window()
lbl=Gtk.Label("Hello")
lbl.set_name('mylabel') #use as CSS selector i.e #mylabel

win.set_size_request(200,100)
win.connect('delete-event',close)
win.add(lbl)

win.show_all()
Gtk.main()


def close(event,data):
	Gtk.main_quit()
```

Then add CSS using ``GtkStyleContext`` and ``GtkCssProvider`` these classes allows to import ``css`` file or embed css code in app. So first create a css that apply color to label.

```
#mylabel{
	color: #FF0000;
	
}
``` 

Instead of ``mylabel`` you can use widget name i.e ``GtkLabel``. Now its time to attach CSS to GTK apps.

```
style=Gtk.CssProvider()
style.load_from_path('./style.css')
Gtk.StyleContext.add_provider_for_screen(Gdk.Screen.get_default(),style,Gtk.STYLE_PROVIDER_PRIORITY_APPLICATION)
```  

and thats it.  

###Result  
<img src="/images/css_gtk/gtk-css.png" style="height: 200px"/>
