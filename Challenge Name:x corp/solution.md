### في هذا التحدي، نلاحظ وجود حقل إدخال (input)، بمجرد إدخال أي نص مثل admin والضغط على زر البحث، تظهر الكلمة المدخلة في مصدر الصفحة داخل خاصية alt في وسم <img>، بالشكل التالي:

```
<span> <img style='width:20%;' src='./759511.jpg' alt='admin > 
</span>

```

# هذا يشير إلى وجود ضعف في الفلترة، خصوصًا في طريقة تضمين القيمة داخل خاصية HTML.

# قمنا بتجربة كسر سياق الخاصية alt بإغلاقها باستخدام '، ثم حقننا حدث onload:
```
admin' onload=alert(0) x=
```
# تم تنفيذ الشيفرة بنجاح ✅، مما يعني أن الثغرة Reflected XSS قائمة ويتم تنفيذها داخل وسوم HTML بدون فلترة قوية.



### In this challenge, we are given an input field. When entering any text like admin, then viewing the page source, we find the input embedded inside the alt attribute of an <img> tag:
`<span> <img style='width:20%;' src='./759511.jpg' alt='admin > 
</span>
`
This reveals an input reflection vulnerability with improper context handling.

By breaking out of the alt attribute using a single quote ', then injecting an onload event, we trigger our JavaScript payload:

`admin' onload=alert(0) x=
`
This successfully executes JavaScript, confirming the presence of a Reflected XSS vulnerability.

