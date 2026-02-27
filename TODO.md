# خطة نشر المشروع على Netlify

## المعلومات المجمعة

### حالة المشروع:
- ✅ مشروع Vite + React + TypeScript
- ✅ ملف `netlify.toml` موجود ومعد مسبقاً
- ✅ ملف `public/_redirects` موجود
- ✅ يدعم PWA (Vite PWA)

### ما يحتاج إعدادات:
1. Supabase - للـ Authentication و Database
2. متغيرات البيئة في Netlify

---

## خطوات النشر

### الخطوة 1: إنشاء حساب Supabase
- اذهب إلى [supabase.com](https://supabase.com)
- أنشئ مشروع جديد
- احتفظ بـ `Project URL` و `anon public key`

### الخطوة 2: إعداد متغيرات البيئة
أنشئ ملف `.env` في جذر المشروع:
```
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=your-anon-key
```

### الخطوة 3: النشر على Netlify

**الطريقة الأولى: عبر GitHub (الأسهل)**
1. ارفع المشروع إلى GitHub
2. اذهب إلى [netlify.com](https://netlify.com)
3. اضغط "Add new site" > "Import an existing project"
4. اختر GitHub واختر المشروع
5. أضف متغيرات البيئة:
   - `VITE_SUPABASE_URL` = رابط Supabase
   - `VITE_SUPABASE_PUBLISHABLE_KEY` = المفتاح العام
6. اضغط "Deploy"

**الطريقة الثانية: عبر Netlify CLI**
```
bash
npm install -g netlify-cli
netlify login
netlify deploy --prod --dir=dist
```

### الخطوة 4: (اختياري) نشر الـ Backend
الـ Backend في `backend-fastapi` يحتاج استضافة منفصلة مثل:
- Render.com
- Railway.app
- PythonAnywhere

---

## ملاحظات مهمة
- التطبيق يعمل في وضع Demo بدون Supabase
- لكن ميزات تسجيل الدخول تحتاج Supabase
