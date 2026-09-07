# OmniPost — public pages

These are the public pages required by social platforms (TikTok, Meta) before they
approve a developer application: an app description, a privacy policy, terms of
service, and an OAuth redirect page.

**Live site:** https://waelsaballyl.github.io/omnipost-site/

- [App description](https://waelsaballyl.github.io/omnipost-site/)
- [Privacy Policy](https://waelsaballyl.github.io/omnipost-site/privacy.html)
- [Terms of Service](https://waelsaballyl.github.io/omnipost-site/terms.html)
- [OAuth redirect](https://waelsaballyl.github.io/omnipost-site/oauth/callback.html)

All three policy pages are written in English. The notes below are the author's own
setup instructions, in Arabic.

---

# موقع OmniPost العام

هذا المجلد هو الجزء اللي لازم يكون **على الإنترنت**. الأداة نفسها تبقى على جهازك —
هذي بس الصفحات اللي المنصات تطلبها قبل ما توافق على تطبيقك.

## وش فيه

| الملف | وش يسوّي | مين يطلبه |
|---|---|---|
| `index.html` | صفحة تعريف بالأداة | تيك توك · ميتا · لينكدإن |
| `privacy.html` | سياسة الخصوصية | كل المنصات — إلزامي |
| `terms.html` | شروط الاستخدام | كل المنصات — إلزامي |
| `oauth/callback.html` | جسر يرجّع كود التفويض لأداتك المحلية | تيك توك · ميتا (يرفضون `http://127.0.0.1`) |

الجسر ملف ثابت بدون سيرفر: يقرأ الكود من الرابط ويحوّلك مباشرة إلى
`http://127.0.0.1:8000` على جهازك. ما فيه أي سكربت خارجي ولا تتبّع، والكود ما يمرّ
على أحد غير جهازك.

## النشر على GitHub Pages (مجاني)

1. سوِّ مستودعاً جديداً على GitHub باسم `omnipost-site` واجعله **Public**.
2. ارفع محتويات هذا المجلد في جذر المستودع:

```bash
cd site
git init
git add .
git commit -m "OmniPost public pages"
git branch -M main
git remote add origin https://github.com/<اسم-حسابك>/omnipost-site.git
git push -u origin main
```

3. في المستودع: **Settings ← Pages** ← تحت *Source* اختر `Deploy from a branch`،
   الفرع `main` والمجلد `/ (root)` ← **Save**.
4. انتظر دقيقتين، وبيصير عندك:

```
https://<اسم-حسابك>.github.io/omnipost-site/
https://<اسم-حسابك>.github.io/omnipost-site/privacy.html
https://<اسم-حسابك>.github.io/omnipost-site/terms.html
https://<اسم-حسابك>.github.io/omnipost-site/oauth/callback.html
```

هذي الأربعة هي اللي تحتاجها في كل منصة. GitHub يعطيك HTTPS تلقائياً.

## توثيق الملكية

تيك توك وميتا يطلبون تثبت إنك تملك الروابط. الطريقة: يعطونك ملف توقيع، ترفعه في جذر
المستودع (جنب `index.html`)، تعمل `git push`، وتضغط تحقّق عندهم.

## قبل ما ترفع

بدّل الإيميل في `privacy.html` و`terms.html` إذا تبي إيميلاً غير `wael78041@gmail.com`.

## اختبار محلي

```bash
cd site
python -m http.server 8899
```

ثم افتح <http://127.0.0.1:8899>.
