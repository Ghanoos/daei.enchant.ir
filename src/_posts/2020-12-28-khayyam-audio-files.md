---
title: ضبط و انتشار ۱۰۶ رباعی خیام
tags: khayyam خیام ساقی رباعیات
uuid: 2c0823a1-b84b-47e1-9bab-b30a0ca5c4b1
---
در گذشته ۱۰۶ رباعی خیام را به فرمت YAML منتشر کرده بودم. طی روزهای گذشته همین‌ها را با میکروفن ضبط کردم و فایل‌های صوتی آنها را منتشر کردم.

هدفم این بود که بتوان رباعی‌ها را علاوه بر خواندن گوش کرد. اکثر این رباعی‌ها و هزاران شعر دیگر در سایت خوب گنجور هم در دسترس است و بسیاری از آنها را هم می‌توان گوش کرد. من هم برای فهم تلفظ صحیح بعضی لغات به کامنت‌های سایت گنجور و نیز فایل‌های صوتی آن مراجعه کردم.

ابیات را با میکروفن [Q2U ساخت SAMSON] در خانه ضبط کرده‌ام. این میکروفن صداهای مزاحم محیط را کمتر ضبط می‌کند. ابیات اول کمی کم‌جان از آب درآمدند ولی مجدد ضبط نکردم، از یک چهارم اول به بعد باید صدا خوب باشد.

برای ضبط از برنامه‌ی Sound Recorder گنوم استفاده کردم. برنامه برای ضبط تعداد زیادی فایل چندان مناسب نیست چرا که نمی‌توان همه فایل‌ها را با هم ذخیره کرد ولی کار را انجام داد. فرمت فایل‌های اصلی flac است اما نسخه ogg که کم‌حجم‌تر است را برای انتشار انتخاب کردم.

برای تبدیل فایل‌های flac به ogg از برنامه‌ی ffmpeg به صورت زیر استفاده کردم:

```
for i in `ls`; do ffmpeg -i $i $i.ogg; done
```

تمامی فایل‌ها را هم پیش از تبدیل با برنامه‌ی EasyTAG به نحو مطلوب تگ‌گذاری کرده‌ام. برنامه‌های مختلف مانند VLC و یا mpv تگ‌ها را موقع پخش به درستی نمایش می‌دهند. برای اینکه تگ عنوان هر فایل را به راحتی به شکل تزایدی تغییر بدهم از برنامه‌ی lltag و bash استفاده کردم:

```
c=1;for i in `ls`; do lltag --yes --tag title="Quatrain No. `printf "%03d" $c`" $i && ((c=c+1)); done
```

برای هر فایل هم یک Album Art که همان تصویر خیام از سایت ویکی‌پدیاست با ذکر منبع به کار گرفته‌ام. همه چیز هم تحت مجوز CC BY-SA 4.0 قرار دارد. یعنی دست بزن اما خیانت مکن :)

البته شاید بگویید به چه درد می‌خورد؟ اول اینکه انتشار آزاد محتوای بیشتر با مجوز درست و تگ حسابی که ضرر ندارد. دیگر اینکه فکر کردم از این ۱۰۶ متن و صوت بتوان به عنوان یک دیتاست کوچک آزمایشی برای پردازش صوت استفاده کرد.


همه‌ی فایل‌ها [روی گیت‌هاب] است. [فایل زیپ] مستقیما قابل دانلود است.


[Q2U ساخت SAMSON]: http://www.samsontech.com/site_media/support/manuals/Q2U_OM_5L_v6.pdf

[روی گیت‌هاب]: https://github.com/mehdisadeghi/khayyam/tree/master/audio

[فایل زیپ]: https://github.com/mehdisadeghi/khayyam/archive/master.zip