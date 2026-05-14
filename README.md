<div dir="rtl" align="right">

<h1>🎬 Khayam YouTube Downloader</h1>

<p>یک بات قدرتمند و کاملاً خودکار برای دانلود ویدیوهای یوتیوب در پیام‌رسان بله — با قابلیت جستجو، تنظیمات شخصی‌سازی شده و ارسال مستقیم فایل — همه چیز رایگان و بدون نیاز به سرور اختصاصی.</p>

<hr>

<h2>✨ این پروژه چه کاری انجام می‌دهد؟</h2>

<ul>
<li>✅ دانلود ویدیو از یوتیوب با ارسال لینک به بات</li>
<li>✅ جستجوی هوشمند در یوتیوب و نمایش نتایج</li>
<li>✅ انتخاب کیفیت از ۴۸۰p تا ۴K و حتی استخراج فقط صدا (MP3)</li>
<li>✅ دانلود خودکار زیرنویس‌های فارسی و انگلیسی</li>
<li>✅ ذخیره فایل در کانال بله و ارسال مستقیم با file_id</li>
<li>✅ دکمه تأیید قبل از شروع دانلود</li>
<li>✅ بررسی وضعیت دانلود با تایمر داخلی</li>
<li>✅ محدودیت نرخ درخواست برای استفاده منصفانه (۵ دقیقه)</li>
<li>✅ حذف خودکار فایل‌های قدیمی از ریپازیتوری</li>
<li>✅ پشتیبانی از ۸ روش مختلف برای عبور از محدودیت‌های دانلود</li>
</ul>

<hr>

<h2>🚀 چگونه از این پروژه استفاده کنم؟</h2>

<p><strong>🔴🔴🔴 قبل از هر کاری:</strong> شما باید ریپازیتوری را <strong>فورک (Fork)</strong> کنید و فایل <code>gateway.php</code> را روی هاست خود آپلود نمایید. 🔴🔴🔴</p>

<h3>مرحله ۱: فورک کردن ریپازیتوری</h3>

<ol>
<li>روی دکمه <strong>"Use this template"</strong> در بالای صفحه کلیک کنید.</li>
<li>نام دلخواه برای ریپوی خود انتخاب کنید.</li>
<li>روی <strong>"Create repository"</strong> کلیک کنید.</li>
</ol>

<h3>مرحله ۲: تنظیم Secrets در گیت‌هاب</h3>

<p>به <strong>Settings &gt; Secrets and variables &gt; Actions</strong> بروید و این مقادیر را اضافه کنید:</p>

<table>
<thead>
<tr>
<th>نام Secret</th>
<th>توضیح</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>BALE_BOT_TOKEN</code></td>
<td>توکن بات بله (از @BotFather بگیرید)</td>
</tr>
<tr>
<td><code>GITHUB_PAT</code></td>
<td>توکن شخصی گیت‌هاب با دسترسی <code>repo</code> و <code>workflow</code></td>
</tr>
<tr>
<td><code>CHANNEL_ID</code></td>
<td>شناسه کانال بله (اختیاری — برای آرشیو فایل‌ها)</td>
</tr>
</tbody>
</table>

<h3>مرحله ۳: تنظیم Webhook بات بله</h3>

<p>فایل <code>gateway.php</code> را روی هاست خود آپلود کنید. سپس Webhook را تنظیم کنید:</p>

<pre><code>https://tapi.bale.ai/bot&lt;TOKEN&gt;/setWebhook?url=&lt;آدرس فایل gateway.php شما&gt;
</code></pre>

<h3>مرحله ۴: استفاده از بات</h3>

<p>کاربران با ارسال <code>/start</code> می‌توانند از بات استفاده کنند:</p>

<ul>
<li><strong>🎥 دانلود ویدیو</strong> → ارسال لینک یوتیوب → تأیید تنظیمات → دریافت فایل</li>
<li><strong>🔍 جستجوی یوتیوب</strong> → نوشتن عبارت جستجو → انتخاب از نتایج</li>
<li><strong>⚙️ تنظیمات</strong> → تغییر کیفیت و فعال/غیرفعال کردن زیرنویس</li>
<li><strong>📊 وضعیت سرور</strong> → مشاهده وضعیت و زمان باقی‌مانده تا درخواست بعدی</li>
</ul>

<hr>

<h2>📋 ساختار فایل‌ها</h2>

<table>
<thead>
<tr>
<th>فایل</th>
<th>وظیفه</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>.github/workflows/yt-dl.yml</code></td>
<td>اکشن اصلی دانلود ویدیو و آپلود در کانال</td>
</tr>
<tr>
<td><code>.github/workflows/yt-search.yml</code></td>
<td>اکشن جستجو در یوتیوب</td>
</tr>
<tr>
<td><code>gateway.php</code></td>
<td>واسط بین بات بله و GitHub Actions</td>
</tr>
</tbody>
</table>

<hr>

<h2>🔧 تنظیمات پیکربندی در gateway.php</h2>

<pre><code>define('RATE_LIMIT_SECONDS', 300);      // فاصله بین دو دانلود (۵ دقیقه)
define('STATUS_CHECK_SECONDS', 180);    // فاصله بین دو بررسی وضعیت (۳ دقیقه)
</code></pre>

<table>
<thead>
<tr>
<th>کیفیت</th>
<th>مقدار داخلی</th>
</tr>
</thead>
<tbody>
<tr>
<td>بهترین کیفیت</td>
<td><code>best</code></td>
</tr>
<tr>
<td>4K (2160p)</td>
<td><code>2160</code></td>
</tr>
<tr>
<td>2K (1440p)</td>
<td><code>1440</code></td>
</tr>
<tr>
<td>Full HD (1080p)</td>
<td><code>1080</code></td>
</tr>
<tr>
<td>HD (720p)</td>
<td><code>720</code></td>
</tr>
<tr>
<td>SD (480p)</td>
<td><code>480</code></td>
</tr>
<tr>
<td>فقط صدا</td>
<td><code>audio</code></td>
</tr>
</tbody>
</table>

<hr>

<h2>📝 نکات مهم</h2>

<table>
<thead>
<tr>
<th>موضوع</th>
<th>توضیح</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>محدودیت نرخ درخواست</strong></td>
<td>هر کاربر هر ۵ دقیقه فقط یک دانلود می‌تواند انجام دهد</td>
</tr>
<tr>
<td><strong>بررسی وضعیت</strong></td>
<td>هر ۳ دقیقه یکبار می‌توان وضعیت را بررسی کرد</td>
</tr>
<tr>
<td><strong>مدت نگهداری فایل</strong></td>
<td>فایل‌ها حداکثر ۵ دقیقه در ریپازیتوری باقی می‌مانند</td>
</tr>
<tr>
<td><strong>آرشیو در کانال</strong></td>
<td>در صورت تنظیم <code>CHANNEL_ID</code>، فایل‌ها در کانال بله ذخیره می‌شوند</td>
</tr>
<tr>
<td><strong>زیرنویس‌ها</strong></td>
<td>به صورت خودکار فارسی و انگلیسی دانلود و در فایل <code>subtitle.zip</code> قرار می‌گیرند</td>
</tr>
<tr>
<td><strong>تقسیم فایل</strong></td>
<td>فایل‌های بزرگتر از ۴۵ مگابایت به چند پارت تقسیم می‌شوند</td>
</tr>
</tbody>
</table>

<hr>

<h2>🛠️ تکنولوژی‌های استفاده شده</h2>

<ul>
<li><strong>yt-dlp</strong> — موتور اصلی دانلود و جستجو</li>
<li><strong>FFmpeg</strong> — پردازش و تبدیل ویدیو و صدا</li>
<li><strong>Cloudflare WARP</strong> — عبور از محدودیت‌های شبکه</li>
<li><strong>GitHub Actions</strong> — اجرای خودکار و رایگان</li>
<li><strong>PHP</strong> — gateway بین بات بله و گیت‌هاب</li>
<li><strong>SQLite</strong> — مدیریت محدودیت نرخ درخواست و تنظیمات کاربران</li>
</ul>

<hr>

<h2>⚖️ قوانین استفاده</h2>

<ul>
<li>این پروژه صرفاً برای استفاده <strong>شخصی و آموزشی</strong> طراحی شده است.</li>
<li>شما مسئولیت هرگونه استفاده از این ابزار را بر عهده دارید.</li>
<li>لطفاً به حقوق مالکیت فکری و قوانین کپی‌رایت یوتیوب احترام بگذارید.</li>
</ul>

<hr>

<h2>🤝 مشارکت و پیشنهادات</h2>

<p>اگر ایده، پیشنهاد یا مشکلی دارید، خوشحال می‌شوم آن را بشنوم:</p>

<ul>
<li><strong>Issue</strong> باز کنید برای گزارش مشکلات یا ارائه ایده‌های جدید</li>
<li><strong>Pull Request</strong> بفرستید برای بهبود کد</li>
<li><strong>Star</strong> ⭐ بزنید اگر این پروژه برایتان مفید بوده است</li>
</ul>

<hr>

<h2>📞 ارتباط با من</h2>

<p>ساخته شده با ❤️ توسط <strong>Khashayar</strong></p>

<p>
<a href="https://khashayar.one" target="_blank">🌐 وبسایت شخصی</a>
<br>
<a href="https://ble.ir/GeminiPrompt" target="_blank">🥷 چنل من داخل بله</a>
</p>

<hr>

<p><strong>نسخه:</strong> ۴.۰ | <strong>آخرین بروزرسانی:</strong> اردیبهشت ۱۴۰۵</p>

</div>
