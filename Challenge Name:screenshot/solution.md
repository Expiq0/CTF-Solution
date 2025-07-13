# حل تحدي CTF: استخراج الفلاج من صورة مشفرة Base64

---

## خطوات الحل | Solution Steps

1. افتح صفحة التحدي واكتب رابط الصورة في الحقل المخصص.  
   Open the challenge page and enter the image URL in the input field.

2. استخدم Burp Suite لالتقاط الطلب المرسل عند إدخال الرابط.  
   Use Burp Suite to intercept the request sent after entering the URL.

3. أعد إرسال الطلب الملتقط من Burp Suite ولاحظ مسار الصورة في الاستجابة.  
   Replay the captured request in Burp Suite and observe the image path in the response.

4. افتح الرابط الكامل للصورة، مثال:  
   `<challenge_url>/screenshot/thumbs/c191cc0fd3c6fbb063e96b12c42a4e49.jpg`  
   Open the full image URL, e.g.:  
   `<challenge_url>/screenshot/thumbs/c191cc0fd3c6fbb063e96b12c42a4e49.jpg`

5. انسخ نص الـ Base64 الموجود في الاستجابة.  
   Copy the Base64 encoded text found in the response.

6. فك تشفير النص باستخدام أدوات فك Base64 (أونلاين أو باستخدام الطرفية).  
   Decode the text using Base64 decoding tools (online or via terminal).

7. افتح الكود الناتج وابحث عن المتغير `$jpeg` الذي يحتوي على الفلاج.  
   Open the decoded code and look for the `$jpeg` variable containing the flag.

---

## الفلاج النهائي | Final Flag

Flag: Server!Host@Flag

نسخ
تحرير
