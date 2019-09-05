---
title: SQL Server İşlevleri ile Kurallı Kavramsal Model Eşlemesi
ms.date: 03/30/2017
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
ms.openlocfilehash: f997fbf39f3dee07cc0d58a39fca779f55236606
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251672"
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>SQL Server İşlevleri ile Kurallı Kavramsal Model Eşlemesi
Bu konu başlığı altında, kavramsal model kurallı işlevlerinin karşılık gelen SQL Server işlevlerine nasıl eşlendiğini açıklar.  
  
## <a name="date-and-time-functions"></a>Tarih ve Saat İşlevleri  
 Aşağıdaki tabloda, tarih ve saat işlevleri eşleme açıklanmaktadır:  
  
|Kurallı işlevler|SQL Server işlevleri|  
|-------------------------|--------------------------|  
|[AddDays(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[Addyıllar (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime (yıl, ay, gün, saat, dakika, saniye)](./language-reference/date-and-time-canonical-functions.md)|SQL Server 2000 ve SQL Server 2005 için, sunucuda `datetime` biçimlendirilen bir değer oluşturulur. SQL Server 2008 ve sonraki sürümlerinde, sunucuda bir `datetime2` değer oluşturulur.|  
|[CreateDateTimeOffset (yıl, ay, gün, saat, dakika, saniye, tzfark)](./language-reference/date-and-time-canonical-functions.md)|Sunucuda `datetimeoffset` biçimlendirilen bir değer oluşturulur.<br /><br /> SQL Server 2000 veya SQL Server 2005 ' de desteklenmez.|  
|[CreateTime (saat, dakika, saniye)](./language-reference/date-and-time-canonical-functions.md)|Sunucuda `time` biçimlendirilen bir değer oluşturulur.<br /><br /> SQL Server 2000 veya SQL Server 2005 ' de desteklenmez.|  
|[CurrentDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTime()`SQLServer 2008.<br /><br /> `GetDate()`SQLServer 2000 ve SQLServer 2005 ' de.|  
|[CurrentDateTimeOffset()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTimeOffset()`SQL Server 2008.<br /><br /> SQL Server 2000 veya SQL Server 2005 ' de desteklenmez.|  
|[CurrentUtcDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysUtcDateTime()`SQLServer 2008. `GetUtcDate()`SQL Server 2000 ve SQL Server 2005.|  
|[DayOfYear (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Gün (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[Diffmikrosaniye (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[Diffnanosaniye (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[Diffyıllar (startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes (DateTimeOffset)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Saat (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Milisaniyelik (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minute (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Kes (ifade)](./language-reference/date-and-time-canonical-functions.md)|SQL Server 2000 ve SQL Server 2005 için sunucuda kesilmiş `datetime` bir biçimlendirilen değer oluşturulur. SQL Server 2008 ve sonraki sürümlerinde, sunucuda kesilmiş `datetime2` veya `datetimeoffset` değer oluşturulur.|  
|[Yıl (ifade)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>Toplama İşlevleri  
 Aşağıdaki tabloda, toplam işlevleri eşleştirmesi açıklanmaktadır:  
  
|Kurallı işlevler|SQL Server işlevleri|  
|-------------------------|--------------------------|  
|[Ort (ifade)](./language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](./language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count (ifade)](./language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min (ifade)](./language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max (ifade)](./language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev (ifade)](./language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[STDSAPMAS (ifade)](./language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum (ifade)](./language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var (ifade)](./language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP (ifade)](./language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>Matematik işlevleri  
 Aşağıdaki tabloda, matematik işlevleri eşleştirmesi açıklanmaktadır:  
  
|Kurallı işlevler|SQL Server işlevleri|  
|-------------------------|--------------------------|  
|[ABS (değer)](./language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[Tavan (değer)](./language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Floor (değer)](./language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Güç (değer)](./language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round (değer)](./language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[Kesilemedi](./language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>Dize İşlevleri  
 Aşağıdaki tabloda, eşleşen dize işlevleri açıklanmaktadır:  
  
|Kurallı işlevler|SQL Server işlevleri|  
|-------------------------|--------------------------|  
|[Contains (dize, hedef)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat (dize1, dize2)](./language-reference/string-canonical-functions.md)|dize1 + dize2|  
|[EndsWith (dize, hedef)](./language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **Göz önünde** `false` `target` İşlevi, sabituzunluklubirdizesütunundadepolanıyorsavebirsabitisedöndürür.`string` `CHARINDEX` Bu durumda tüm dize, sondaki boşlukları doldurarak aranır. Olası bir geçici çözüm, aşağıdaki örnekte olduğu gibi, dizeyi `EndsWith` işleve geçirmeden önce sabit uzunluklu dizedeki verileri kırpmektir:`EndsWith(TRIM(string), target)`|  
|[IndexOf (hedef, dize2)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Sol (dize1, uzunluk)](./language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[Uzunluk (dize)](./language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim (dize)](./language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Right (dize1, uzunluk)](./language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim (dize)](./language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Replace (dize1, dize2, string3)](./language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Ters (dize)](./language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim (dize)](./language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith (dize, hedef)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Alt dize (dize, başlangıç, uzunluk)](./language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower (dize)](./language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper (dize)](./language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>Bit düzeyinde Işlevler  
 Aşağıdaki tabloda bit düzeyinde işlevler eşleme açıklanmaktadır:  
  
|Kurallı işlevler|SQL Server işlevleri|  
|-------------------------|--------------------------|  
|[Bitwiseve (değer1, değer2)](./language-reference/bitwise-canonical-functions.md)|Değer1 & değer2|  
|[Bitwıenot (değer)](./language-reference/bitwise-canonical-functions.md)|~ değer|  
|[BitWiseOr (değer1, değer2)](./language-reference/bitwise-canonical-functions.md)|Değer1 &#124; değer2|  
|[BitWiseXor (değer1, değer2)](./language-reference/bitwise-canonical-functions.md)|Değer1 ^ değer2|
