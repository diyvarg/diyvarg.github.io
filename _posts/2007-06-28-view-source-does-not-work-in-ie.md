---
title: Не работает View - Source в IE        -- _POSTS
tags: [ie, javascript]
src: http://mindberg.blogspot.ru/2007/06/view-source-ie.html
layout: default
---
Ситуация: иногда бывает, что IE не может или не хочет отобразить код страниц. Т.е. вызов View – Source  не работает как предполагается.

# header

Use `git status` to list all new or modified files that haven't yet been committed.

<hr/>

Some basic Git commands are:
```
git status
git add
git commit
```

<hr/>

{% highlight ruby %}
def cat
  puts 'I love cats'
end
{% endhighlight %}



<hr/>

Решение:
<ol>
  <li>Создать папку, например, Z:\Projects\IE View Source</li>
  <li>Создать в ней файл: ViewSource.htm со следующим кодом:</li>

  ```html
  <html>
    <body>
      <script language="JavaScript" defer>
        var win = external.menuArguments;
        var szsource = win.document.documentElement.outerHTML;
        var wincounter = 0;
        var mywin = null;
        do
        {
          mywin = window.open("about:blank", "Source" + wincounter++,        
                              "toolbar=no,location=no,menubar=yes,status=yes,scrollbars=yes,resizable=yes");
        }
        while(mywin == null);
        mywin.document.open("text/plain");
        mywin.document.write(szsource);
        mywin.document.close();
        mywin.document.title = "Source for: " + win.location.href;
      </script>
    </body>
  </html>
  ```
</ol>  
<ol start="3"> 
  <li>Запустить regedit; в ветке  HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\MenuExt создать Key с именем 
View Source. В Default записать: Z:\Projects\IE View Source\ViewSource.htm</li>
  <li>Открыть IE, в контекстном меню выбрать View Source.</li>
</ol>
Подробнее, см. MSDN: "Adding Entries to the Standard Context Menu"

P.S.
Все сказанное выше не поможет, если IE запущен в режиме Run As с включенным Run this Program with restricted access.
