---
title: گربه‌ی کوانتومی
category: تفریح
tags: ترجمه پچ بازی
uuid: 706b7c28-7f75-47e6-a49d-d576d11ce4af
---
مدتی پیش به طور اتفاقی به یک بازی ساده به سبک ماجراجویی متنی برخوردم و از بازی کردنش خیلی لذت بردم. تصمیم گرفتم بازی را فارسی کنم که منجر به فارسی‌سازی موتور بازی هم شد. در ادامه می‌نویسم که ماجرا چه بود.

> می‌توانید [اینجا](assets/instead/instead-em.html?cat.zip) بازی کنید

اسم بازی The Returning of the Quantum Cat است که نسخه انگلیسی آن را می‌توانید مستقیم روی [itch.io] بازی کنید. نام موتور بازی [INSTEAD] است و به زبان C نوشته شده و روی پلتفرم‌های مختلف مانند لینوکس و ویندوز و اندروید قابل اجراست.

# خلاصه بازی
یک هکر و فیزیکدان کهنه‌کار از جهان بریده و به جنگلبانی مشغول است تا اینکه روزی گربه‌ی محبوبش پس از ظاهر شدن یک فرد غریبه‌ی مشکوک غیب می‌شود و او باید گربه‌اش را نجات بدهد...


{: .center}
![](assets/pimg/qcat3.png)


# سبک ماجراجویی متنی
این قبیل بازی‌ها را به نام Interactive fiction یا IF می‌شناسند. در این سبک بازیکن داستان را «می‌خواند» و پیش می‌رود و هر از گاهی سوالاتی را پاسخ می‌دهد یا با اشیاء و افراد وارد تعامل می‌شود و بازی پیش می‌رود. گاهی بازی می‌تواند کاملا متنی باشد و در آنصورت تنها تخیل بازیکن است که باید بازی را تصور کند. البته گاهی هم کاغذ و مداد کمک می‌کند.

# ترجمه
نسخه اصلی داستان بازی را یک برنامه‌نویس روس به روسی نوشته و کسی هم آنرا به انگلیسی برگردانده. من از روی نسخه انگلیسی بازی را به فارسی ترجمه آزاد گردم. یعنی در قید و بند اینکه هر کلمه و جمله را واو به واو به فارسی برگردانم نبودم. حدسم اینست که مترجم انگلیسی هم نبوده است! ترجمه را ببینید و دوست داشتید در کم و کیف آن در کامنتدونی اظهار نظر کنید. متن بازی روی [گیتهاب] است.

# ساختار یک بازی
بازی از فضاهای مختلف تشکیل شده. بازیکن از یک نقطه شروع می‌کند و پس از تعامل با برخی اشیاء‌ (مثلا برداشتن آن) و یا صحبت با افراد می‌تواند به نقاط جدیدی برود و بین آنها به پس و پیش حرکت کند. طبق معمول هم یک خورجین دارد که وسایلش را می‌ریزد آن تو.

# بازی با Lua
سبک کار موتور این بازی به این صورت است که یک اسکریپت به [زبان برنامه‌نویسی لوئا] را می‌خواند و بازی را از روی آن می‌سازد (مثلا فضاهای بازی یا همان اتاق‌ها). لوئا بین بازی‌سازان خیلی محبوب است چرا که هم بسیار ساده است و هم سبک و براحتی در برنامه‌های C می‌توان جاسازی‌اش کرد. از طرفی کار بازیسازان را راحت می‌کند چرا که نیاز نیست از پیچیده‌گی‌های موتور بازی سردربیاورند. شما براحتی می‌تونید با تغییر متن بازی (ترجمه و بازی با هم مخلوط هستند) بازی را تغییر بدهید، اتاق‌هایی به آن اضافه کنید، عکس‌ها را دستکاری کنید و مانند اینها.

# فارسی‌سازی موتور بازی
بعد از ترجمه مقداری از بازی متوجه شدم که موتور بازی راست به چپ را اصلا نمی‌فهمد. با مقدار زیادی تقلا توانستم سردربیاورم که مشکل کجاست و آنرا رفع کردم. مقدار زیادی تغییرات در موتور بازی داده‌ام که بتواند متن‌ها را از راست به چپ رندر کند. برخلاف برنامه‌های سطح بالاتر که معمولا با اشیاء سر و کار داریم و ایونت‌ها را می‌توان هندل کرد، در برنامه‌های گرافیکی معمولا از این خبرها نیست و باید بسیاری چیزها را محاسبه و رندر کرد. مثلا وقتی بازیکن روی یک لغت کلیک می‌کند چه اتفاقی می‌افتد؟ یک روال در جایی از برنامه مختصات نقطه کلیک شده را پیدا می‌کند بعد می‌گردد ببیند که آنچا چیزی نوشته شده است یانه؟ اگر چیزی نوشته شده که از قضا قرار است که بازیکن با آن تعامل بکند می‌رود و روالی را صدا می‌زند که تعامل را انجام دهد و الی آخر. یا مثلا وقتی موس را حرکت می‌دهیم و رنگ یک کلمه تغییر می‌کند چه می‌شود؟ اینبار هم با اعمال شاقه جای لغت پیدا شده و فورا به رنگ دیگری نقاشی می‌شود. این‌ها چیزی است که همین الان در گوشی شما یا در فایرفاکس یا کروم و مانند اینها دارد هر لحظه اجرا می‌شود و ذهن ما اصلا متوجه این همه پیچیدگی نمی‌شود و فریب می‌خورد. در یک برنامه سطح بالا ما اصلا به این موارد برخورد نمی‌کنیم.

# دانلود بازی و لانچر اندروید
یک برنامه‌نویس روس دیگر برای موتور بازی یک [لانچر] اندروید نوشته است. لانچر به جاوا نوشته شده ولی برنامه سی کامپایل شده و توابع وابسته آنرا را روی اندروید اجرا می‌کند. فعلا نسخه آخر برنامه و موتور بازی با تغییرات من منتشر نشده (موتور بازی باید با یک فلگ کامپایل شود تا راست به چپ ساپورت کند، به خاطر Backward Compatibility). اگر دوست دارید بازی را با ترجمه فارسی بازی کنید پکیج بازی و فایل زیپ خود بازی را دانلود کنید و امتحانش کنید.

- [دانلود فایل زیپ بازی]
- [دانلود فایل apk لانچر بازی]

در عکس‌های زیر هم اگر لود شده باشد می‌بینید که چطور باید فایل زیپ را در اپ اندروید باز کرد.

{: .center}
![](assets/pimg/qcat1.png)

{: .center}
![](assets/pimg/qcat2.png)
 
# شاید وقتی دیگر
اول قصد داشتم حسابی در مورد SDL و SDL_ttf و HarfBuzz و JNI اینها هم بنویسم که همگی را برای رفع عیب موتور بکار گرفته‌ام و بلکه هنگام نوشتن خودم آنها را بهتر بفهمم. ولی فعلا به انتشار پکیج بازی اکتفا می‌کنم.

[itch.io]: https://instead.itch.io/quantumcat
[INSTEAD]: http://instead3.syscall.ru/en/
[گیتهاب]: https://github.com/mehdisadeghi/returning-the-quantum-cat/
[زبان برنامه‌نویسی لوئا]: http://tylerneylon.com/a/learn-lua/
[لانچر]: https://github.com/btimofeev/instead-launcher-android/
[دانلود فایل زیپ بازی]: assets/instead-cat-fa.zip
[دانلود فایل apk لانچر بازی]: assets/instead-launcher.apk