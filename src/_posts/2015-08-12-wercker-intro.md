---
title: آشنایی با سرویس Wercker
tags: [اتوماسیون, ورکر, قلاب‌وب, راهنما]
category: معرفی
uuid: 64345752-3e17-404f-a228-b511414da94f
---
من خیلی به اتوماسیون علاقه‌مند هستم. دوست دارم سرویس‌های وب رو به کمک قلاب‌ها به هم وصل کنم و چیزهای جدید بسازم که خود به خود فعال بشوند و کاری رو به اتمام برسانند. سرویس Wercker بدرد اینکار می‌خورد.

بگذارید با مثالی آغاز بکنم. سرویس صفحات گیت‌هاب از وبسایت‌های جکیل پشتیبانی می‌کند. یعنی اگر
من سورس کد وبسایت مبتنی بر جکیل را روی گیت‌هاب هاست کنم، دیگر نیازی نیست که خودم بعد از هر تغییر یا مطلب جدید سایت را از نو بسازم و بارگذاری کنم. گیت‌هاب اینکار را برای من به شکل خودکار انجام می‌دهد. اما چون من وبلاگم فارسی است و نیز از تعدادی کتابخانه روبی استفاده کرده‌ام که گیت‌هاب آنها را
پشتیبانی نمی‌کند − مثلا برای تاریخ شمسی − بنابراین نمی‌توانم از این امکان گیت‌هاب استفاده کنم.
تا پیش از این مجبور بودم خودم وبسایت را روی لپ‌تاپم بسازم و بعد خروجی را در گیت‌هاب بارگذاری کنم.

این کار خیلی خسته‌کننده‌ بود.

از جایی که می‌دانستم گیت‌هاب Webhook یا قلاب‌های وبی دارد (از ترجمه بهتر استقبال می‌کنم) می‌خواستم یک برنامه کوچک بنویسم و روی سروری شخصی بارگذاری کنم تا همواره گوش بایستد و به پیام‌های گیت‌هاب گوش کند.
مثلا اگر کامیت جدیدی اتفاق افتاد بیاید و سورس را دانلود بکند و وبسایت را بسازد و در انتها خروجی را به کمک توکنی[^1] که خودم به او داده‌ام روی شاخه صحیح در گیت‌هاب بارگذاری کند.

در همین افکار بودم و خودم را برای اینکار آماده می‌کردم که با ‬[سرویس ورکر](https://app.wercker.com/) آشنا شدم که دقیقا همین کار را مجانی انجام می‌دهد. طرز کار هم خیلی شبیه به سایت‌های مشابه مثل travis-ci یا
heroku است.
یعنی ما یک اکانت در سایت سرویس دهنده − اینجا ورکر − می‌سازیم و یک فایل تنظیمات هم در مخزن گیت‌هاب
قرار می‌دهیم که حاوی تنظیمات ضروری است. به زبان ساده در این فایل تنظیمات به ورکر می‌گوییم هر وقت
که گیت‌هاب تو را خبر کرد چه کاری باید انجام بدهی. در این فایل گام‌های لازم را شرح می‌دهیم.

به طور کلی گام‌های اساسی دو تا بیشتر نیستند. اولی گام ساخت خروجی است و دومی گام دیپلوی یا بارگزاری آن است. گام اول باید حاوی دستورات بیلد پروژه باشد. در گام دوم خروجی را برداشته و در مثال من روی گیت‌هاب کپی می‌کنیم.

این هم فایل تنظیمات ورکر سایت من است:

~~~yaml
box: ruby
build:
  steps:
    # Install dependencies
    - bundle-install

    # Execute jeykyll doctor command to validate the
    # site against a list of known issues.
    - script:
        name: jekyll doctor
        code: bundle exec jekyll doctor

    - script:
        name: generate site
        code: bundle exec jekyll build --trace --destination ./_site

    - create-file:
        name: generate robots.txt
        filename: ./_site/robots.txt
        content: |-
          User-agent: *
          Allow: /
          Sitemap: http://mehdix.ir/sitemap.xml
deploy:
  steps:
    - lukevivier/gh-pages:
        token: $GITHUB_TOKEN
        basedir: _site
        domain: mehdix.ir
~~~

یک حسن ورکر این است که می‌توان گام‌ها را با دیگران به اشتراک گذاشت. مثلا در مثال بالا من برای
بارگذاری خروجی روی گیت‌هاب از اسکریپتی که دیگری نوشته است − lukevivier/gh-pages − استفاده
کرده‌ام. همانطور که پیشتر اشاره کردم ورکر هم از الگوهای پذیرفته شده در میان برنامه‌های مدرن توسعه وب پیروی می‌کند. از جمله دادن نشان[^2] برای نمایش آخرین وضعیت. مثلا وضعیت آخرین عملیات اتوماسیون من در نشان زیر پیداست − کلیک روی این نشان به صفحه پروژه روی ورکر منتهی می‌شود:
[![wercker status](https://app.wercker.com/status/7cdfaf1d4ea865468f4965954ed95247/s "wercker status")](https://app.wercker.com/project/bykey/7cdfaf1d4ea865468f4965954ed95247)

این مقدمه کوتاهی بود بر سرویس ورکر جهت اتوماسیون عملیات‌های تحت وب. اگر کار جالبی با ورکر انجام دادید خبر بدهید.

[^1]: Token
[^2]: Badge
