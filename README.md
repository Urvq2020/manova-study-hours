# مانوڤا · ساعة الدراسة — Manova Study Hours

تطبيق صفحة واحدة لتتبّع ساعات منطقة الدراسة في المقهى.
A single-file web app to track study-area hours in the cafe.

**الملف الوحيد المطلوب / the only file you need:** `index.html`

---

## الاستخدام / Usage

### أول تشغيل / First launch
يطلب التطبيق إنشاء **رمز دخول المشرف** مرة واحدة فقط (لأسباب أمنية لا يُشحن التطبيق برمز جاهز).
On first launch the app asks you to **create the admin passcode** once (no passcode ships baked into the code).

> اكتب `1234` إن أردت الرمز المؤقت المقترح.
> Type `1234` if you want the suggested temporary passcode.

### العميل / Member
1. تسجيل الدخول برقم الجوال السعودي `05X XXX XXXX` (يقبل أيضًا `+966…`).
   Sign in with a Saudi mobile `05X XXX XXXX` (`+966…` also accepted).
2. أول مرة: يختار **رقمًا سريعًا** من 4 أرقام. First time: pick a quick 4-digit password.
3. **بدء الجلسة** عند الجلوس، و**إنهاء الجلسة** عند المغادرة — التكلفة تُحسب تلقائيًا.
   Start session on arrival, end on leaving — cost is calculated automatically.
4. يرى: ساعات اليوم، الإجمالي، عدد الزيارات، الرصيد غير المدفوع، وسجل الجلسات.
   Sees: today's hours, total, visits, unpaid balance, and session history.

### المشرف / Admin (رابط «دخول المشرف» أسفل صفحة الدخول)
- إحصائيات: الجلسات النشطة الآن، عدد الأعضاء، إيراد اليوم، إجمالي المستحق.
  Stats: active now, members, today's revenue, total due.
- **الإعدادات**: سعر الساعة (افتراضي 10 ر.س) وطريقة الاحتساب
  (بالدقيقة / تقريب 15 دقيقة «الافتراضي» / 30 دقيقة / ساعة كاملة).
  Settings: hourly rate (default 10 SAR) and billing rounding
  (per-minute / 15 min default / 30 min / full hour).
- **كل الأرقام والساعات**: جدول بكل عضو (الساعات، الزيارات، المستحق، آخر نشاط، مؤقّت حيّ للجلسة الجارية).
  All mobiles & hours: per-member table with hours, visits, due, last activity, live timer.
- لكل عضو: إنهاء جلسته، **تسديد** المستحق، **تصفير الرمز** (لو نسي رقمه)، أو حذفه.
  Per member: end session, mark paid, reset their PIN, or delete.
- **تصدير CSV** لنسخة احتياطية / للمحاسبة. Export CSV for backup / bookkeeping.
- تغيير رمز المشرف من الإعدادات. Change the admin passcode in settings.

---

## ملاحظات مهمة / Important notes

- **كل البيانات محفوظة في هذا المتصفح/الجهاز فقط** (localStorage) — لا يوجد سيرفر.
  All data lives **on this device's browser only** (localStorage) — there is no server.
- استخدم جهازًا واحدًا (آيباد الكاشير مثلًا) كمصدر للحقيقة، وصدّر CSV بانتظام.
  Use one device (e.g. the counter iPad) as the source of truth; export CSV regularly.
- مسح بيانات المتصفح يمحو السجلات. Clearing browser data erases records.
- الأرقام السرية تُخزّن مُعمّاة (SHA-256 + salt) وليست نصًا واضحًا.
  PINs are stored hashed (SHA-256 + salt), never in plain text.
- 5 محاولات خاطئة → قفل 30 ثانية. 5 wrong tries → 30-second lock.
- الحد الأدنى للفاتورة = أول شريحة احتساب (مع تقريب 15 دقيقة: أي جلسة تُحسب 15 دقيقة على الأقل).
  Minimum bill = first rounding bucket (with 15-min rounding: every session bills ≥ 15 minutes).

## النشر / Putting it online
- يعمل مباشرة بفتح `index.html` في أي متصفح حديث (يعمل دون إنترنت، عدا الخط).
  Works by simply opening `index.html` in any modern browser (offline too, except the font).
- لرابط عام: اسحب المجلد إلى [Netlify Drop](https://app.netlify.com/drop) أو ارفعه على GitHub Pages، ثم ضع الرابط في موقعك على rekaz.io.
  For a public link: drag the folder onto Netlify Drop or GitHub Pages, then link it from your rekaz.io site.
