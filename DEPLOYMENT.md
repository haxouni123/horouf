# HOROUF - حروف - Deployment Guide

## متطلبات النشر

1. حساب [Netlify](https://netlify.com)
2. حساب [Supabase](https://supabase.com)

## خطوات النشر على Netlify

### 1. إعداد Supabase

1. قم بإنشاء مشروع جديد على [Supabase](https://app.supabase.com)
2. انتقل إلى **Settings > API**
3. انسخ `Project URL` و `anon public` key

### 2. إعداد متغيرات البيئة

في جذر المشروع، أنشئ ملف `.env` وضع فيه:

```
env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=your-anon-key-here
```

استبدل القيم بالقيم من الخطوة السابقة.

### 3. نشر على Netlify

**الطريقة الأولى: عبر CLI**
```
bash
npm install -g netlify-cli
netlify login
netlify deploy --prod --dir=dist
```

**الطريقة الثانية: عبر Git**
1. ارفع الكود إلى GitHub
2. اربط المشروع بـ Netlify
3. أضف متغيرات البيئة في إعدادات Netlify
4. Netlify سيبني المشروع تلقائياً

### 4. إضافة مفاتيح API في Netlify

في إعدادات الموقع على Netlify:
- انتقل إلى **Site settings > Environment variables**
- أضف:
  - `VITE_SUPABASE_URL` = رابط مشروعك من Supabase
  - `VITE_SUPABASE_PUBLISHABLE_KEY` = مفتاح anon من Supabase

---

## ملاحظات مهمة

### الباك إند (Backend)
- الـ Backend الموجود في `backend-fastapi` يحتاج استضافة منفصلة
- يمكن استخدام Render أو Railway أو PythonAnywhere

### ميزات التطبيق
- يعمل بدون Supabase في وضع العرض التوضيحي (Demo Mode)
- لكن المصادقة والـ database يتطلبان Supabase

---

## Troubleshooting

### خطأ في البناء
```
bash
# تأكد من تثبيت المتطلبات
npm install

#_BUILD محلياً للتأكد
npm run build
```

### مشاكل التوجيه
تأكد من وجود ملف `public/_redirects` و `netlify.toml`

### مشاكل PWA
تأكد أن الـ Service Worker يعمل بشكل صحيح في الإنتاج
