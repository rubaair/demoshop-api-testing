# DemoShop API Testing

مشروع مصغّر لاختبار واجهة برمجة التطبيقات (API) باستخدام Postman.

**الـ API المستخدم:** SoftwareTestPilot Demo Shop API
`https://www.softwaretestpilot.com/api/public/demoshop`

## الطلبات المشمولة

| # | الطلب | الطريقة | الفحوصات |
|---|-------|---------|----------|
| 1 | Login - success | POST /auth/login | الحالة 200، وجود access_token، حفظ التوكن |
| 2 | Get products | GET /products | الحالة 200، الرد JSON |
| 3 | Add to cart | POST /cart/items | الحالة 201، المنتج في السلة، الإجمالي رقم |
| 4 | Create order | POST /orders | الحالة 200/201، وجود id، حفظ orderId |
| 5 | Get order | GET /orders/{id} | الحالة 200 أو 404، الرد JSON، بنية صحيحة |

## الحالات السلبية

| الطلب | المتوقع |
|-------|---------|
| Login - wrong password | 401 |
| Get product - not found | 404 |
| Add to cart - no token | 401 |

## طريقة التشغيل

1. استورد ملف الـ JSON في Postman (Import)
2. شغّل الـ Collection عن طريق Run collection بالترتيب
3. تأكد أن جميع الفحوصات PASSED

## ملاحظات

- التوكن يُحفظ تلقائيا في متغير `token` بعد تسجيل الدخول.
- رقم الطلب يُحفظ في `orderId` بعد إنشاء الطلب.
- بيانات الـ API التجريبي تُعاد ضبطها تلقائيا ولا تُحفظ بين الطلبات، لذلك قد يرجع Get order الحالة 404، وقد تم توثيق هذا السلوك في الفحص.
