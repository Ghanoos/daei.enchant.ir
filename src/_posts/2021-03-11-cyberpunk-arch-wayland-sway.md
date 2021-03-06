---
title: چطور روی آرچ‌لینوکس سایبرپانک بازی می‌کنم
layout: post
tags: بازی لینوکس گرافیک راهنما
---
من چندان اهل بازی کردن نیستم، گه‌گاه بازی‌های دوبعدی بازی می‌کنم و اواخر هم به اصرار [شایگان] کلی Stardew Valley دو نفری بازی کردیم که البته بسیار لذت بخش و حتی آموزنده بود.

{: .center}
![](assets/pimg/StardewValley-2020-09-04-16-54-32.png)

وقتی که بازی سایبرپانک منتشر شد به درخواست شایگان نسخه‌ای سفارش دادم. از جایی که او به خاطر باگ‌های بسیار گزارش شده در بازی فعلا از بازی کردن صرف نظر کرده، تصمیم گرفتم خودم بازی کنم.

به عنوان آدمی که از کوزه شکسته آب می‌خوره، سیستم عامل من ترکیبی از غریب‌ترین نرم‌افزارهای موجوده. بواسطه‌ی آرچ لینوکس بودن که همواره در لبه‌ی تیغ حرکت می‌کنیم. ولی من پا رو از این فراتر گذاشتم و پس از سالها از xorg به Wayland و از GNOME به Sway مهاجرت کردم تا نفسی تازه کنم و در پی تصمیمی که اواخر گرفتم از نرم‌افزارهایی که توسط‌ شرکت‌های بزرگ اداره می‌شوند به طرف نرم‌افزارهای کوچک‌تر و سبک‌تر که توسط گروه‌های کوچک و مستقل اداره می‌شوند حرکت کنم.

بنابراین اصلا فکر نمی‌کردم امکان اجرای یک بازی ویندوزی روی چنین سیستمی وجود داشته باشه. ولی بخت با من یار بود و برنامه‌هایی مثل Wine به قدری پیشرفت کردند که این امکان فراهم شده.

توجه کنید که من اینجا بازی رو مستقیم روی سیستم اجرا می‌کنم و کارت گرافیکی دومی هم ندارم. سی‌پی‌یو من AMD Ryzen 3000 بدون گرافیک توکاره و کارت گرافیکم هم AMD RX580. علت انتخاب گرافیک AMD از ابتدا اطلاع از وجود درایورهای بهتر روی لینوکس بود.

اگر کارت گرافیکی دومی داشتم از GPU Passthrough استفاده می‌کردم. با یک سرچ کوچک [راهنمای خوبی] پیدا کردم که جزئیات کار رو شرح داده. در این روش دو کارت گرافیک نیازه و یکی اختصاصا به یک ماشین مجازی ویندوز داده می‌شه و به این طریق می‌شه با سرعت بالا بازی کرد.

از طرف دیگر اگر کسی بازی رو روی استیم خریداری کرده باشه، استیم می‌تونه مستقیما به کمک [پروتون] و [واین] در پشت صحنه بازی رو اجرا می‌کنه. هرچند از جایی که من از اسیتم بازی رو نخریده بودم امکان اینکار نبود. من برای بازی یک کد دانلود دریافت کرده بودم که بازی رو از [gog store] دانلود کنم. اما این فروشگاه فقط کلاینت ویندوز داره. یه انسان دوست داشتنی برنامه‌ای عالی به نام [مینی گلکسی] برای لینوکس نوشته که اجازه استفاده از اکانت gog روی لینوکس رو فراهم می‌کنه.

اول به کمک مینی گلکسی بازی رو دانلود کردم. این برنامه هیچ فیچری نداره. فقط می‌تونه بازی‌ها رو از اکانت دانلود کنه که من هم همین رو لازم داشتم. بعد از دانلود دیگه به برنامه نیازی نیست مگر برای آپدیت.

برای اجرا نیاز به نصب پروتون بود که از ریپازیتوری کاربران آرچ (aur: arch user repository) نصب کردم:

    $ yay proton-ge-custom-bin

از جایی که من بدون استیم بازی رو می‌خواستم اجرا کنم با جستجوی متوجه شدم که نیاز به رانتایم استیم دارم که در ریپازیتوری اصلی آرچ فراهم بود:

    $ sudo pacman -S steam-native-runtime

(قبلا مجبور شده بودم که mesa-git رو هم نصب کنم ولی الان نیازی نیست چون تغییرات لازم در ریپازیتوری‌های اصلی اعمال و منتشر شده.)

با این تغییرات بازی روی کامپیوترم اجرا شد، البته از ترمینال باز می‌کنم:

    $ proton GOG\ Games/Cyberpunk\ 2077/bin/x64/Cyberpunk2077.exe

{: .center}
![](assets/pimg/ps_20210311210516.png)

بازی معمولا بدون مشکل اجرا می‌شه. من حتی استک صوتی کامپیوتر رو با برنامه‌ی جدیدالتاسیس [پایپ‌وایر] جایگزین کردم و تصورم این بود که اصلا از بازی صدا درنیاد (به هر دلیلی، مثل همیشه!) ولی کار کرد!

گاهی بعد از آپدیت پکیج‌ها پیش آمده که بازی باز نمی‌شه که در این مواقع اول فایل‌های سیو بازی رو از داخل پوشه‌ی پروتون کپی می‌کنم و بعد پوشه رو کامل حذف می‌کنم:

    $ cp -r .local/share/proton-pfx/0/pfx/dosdevices/c:/users/steamuser/Saved\ Games/CD\ Projekt\ Red ~/Backups/
    $ rm -rf .local/share/proton-pfx

و بازی رو دوباره اجرا می‌کنم و می‌بندم و بعد سیوها رو برمی‌گردم سر جای اولشون:

    $ cp -r Backups/Cyberpunk\ 2077/ .local/share/proton-pfx/0/pfx/dosdevices/c:/users/steamuser/Saved\ Games/CD\ Projekt\ Red/
    
بازی باگ کم نداره اوایل چند بار کرش کرد یا آرتیفکت‌هایی در هوا معلق بودند یکبار هم تو یک کوچه گیر کردم و هر کار کردم نتونستم در برم :) ولی در مجموع خیلی راضی هستم.

{: .center}
![](assets/pimg/ps_20210212225630.png)



[شایگان]: https://bekindtozombies.com/
[راهنمای خوبی]: https://github.com/bryansteiner/gpu-passthrough-tutorial/
[پروتون]: https://github.com/ValveSoftware/Proton
[واین]: https://www.winehq.org/
[gog store]: https://www.gog.com/game/cyberpunk_2077
[مینی گلکسی]: https://github.com/sharkwouter/minigalaxy
[پایپ‌وایر]: https://pipewire.org
