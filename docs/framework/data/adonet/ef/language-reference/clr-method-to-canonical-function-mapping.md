---
title: CLR Yöntemini Kurallı İşlev ile Eşleme
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 6f14ad8d9e8f919fe820447cc991b102319b38d5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251219"
---
# <a name="clr-method-to-canonical-function-mapping"></a>CLR Yöntemini Kurallı İşlev ile Eşleme

Entity Framework, dize işleme ve matematik işlevleri gibi birçok veritabanı sisteminde ortak olan işlevleri uygulayan kurallı bir işlevler kümesi sağlar. Bu, geliştiricilerin çok çeşitli veritabanı sistemlerini hedeflemesini sağlar. LINQ to Entities gibi bir sorgulama teknolojisinden çağrıldığında, bu kurallı işlevler kullanılan sağlayıcı için doğru ilgili depo işlevine çevrilir. Bu, işlev etkinleştirmeleri veri kaynakları genelinde ortak bir biçimde ifade etmesine olanak tanır ve veri kaynakları arasında tutarlı bir sorgu deneyimi sağlar. Bit düzeyinde AND, OR, NOT ve XOR işleçleri, işlenen sayısal bir tür olduğunda kurallı işlevlere de eşlenir. Boolean işlenenleri için bit düzeyinde AND, OR, NOT ve XOR işleçleri işlenenlerinin mantıksal ve veya, DEĞIL ve XOR işlemlerini hesaplar. Daha fazla bilgi için bkz. [kurallı işlevler](canonical-functions.md).

LINQ senaryolarında Entity Framework yapılan sorgular, belirli CLR yöntemlerinin kurallı işlevler aracılığıyla temel alınan veri kaynağındaki yöntemlere eşlenmesini içerir. Kurallı bir işleve açıkça eşlenmemiş bir LINQ to Entities sorgusunda yapılan herhangi bir yöntem çağrısı, çalışma zamanı <xref:System.NotSupportedException> özel durumu oluşmasına neden olur.

## <a name="systemstring-method-static-mapping"></a>System. String yöntemi (statik) eşleme

|System. String yöntemi (statik)|Kurallı işlev|
|-------------------------------------|------------------------|
|System. String Concat (dize `str0`, dize `str1`)|Concat (`str0`, `str1`)|
|System. String Concat (dize `str0`, dize `str1`, dize `str2`)|Concat (Concat (`str0`, `str1`), `str2`)|
|System. String Concat (dize `str0`, dize `str1`, dize `str2`, dize `str03`)|Concat (`str0`Concat (, `str1`), `str2`), `str3`)|
|Boole eşittir (dize `a`, dize `b`)|= işleci|
|Boolean IsNullOrEmpty (dize `value`)|(IsNull (`value`)) veya length (`value`) = 0|
|Boolean op_Equality (dize `a`, dize `b`)|= işleci|
|Boolean op_Inequality (dize `a` , dize `b`)|!= operator|
|Microsoft. VisualBasic. Strings. Trim (dize `str`)|Trim (`str`)|
|Microsoft. VisualBasic. Strings. LTrim (dize `str`)|LTrim (`str`)|
|Microsoft. VisualBasic. Strings. RTrim (dize `str`)|RTrim (`str`)|
|Microsoft. VisualBasic. Strings. Len (dize `expression`)|Length (`expression`)|
|Microsoft. VisualBasic. Strings. Left (dize `str`, Int32 `Length`)|Sol (`str`, `Length`)|
|Microsoft. VisualBasic. Strings. mid (dize `str`, Int32 `Start`, Int32 `Length`)|Alt dize`str`( `Start`, `Length`,)|
|Microsoft. VisualBasic. Strings. Right (dize `str`, Int32 `Length`)|Sağ (`str`, `Length`)|
|Microsoft. VisualBasic. Strings. UCase (dize `Value`)|ToUpper (`Value`)|
|Microsoft. VisualBasic. Strings. LCase (dize değeri)|ToLower (`Value`)|

## <a name="systemstring-method-instance-mapping"></a>System. String yöntemi (örnek) eşleme

|System. String yöntemi (örnek)|Kurallı işlev|Notlar|
|---------------------------------------|------------------------|-----------|
|Boolean Contains (dize `value`)|`this`'%`value`% ' GİBİ|Bir sabit değilse, bu, IndexOf (`this`, `value`) > 0 ' a eşlenir `value`|
|Boole EndsWith (dize `value`)|`this`LIKE `'` '% `value`|Bir sabit değilse, bu, sağa (`this`, length (`value`)) = `value`ile eşlenir. `value`|
|Boole StartsWith (dize `value`)|`this`'`value`% ' GİBİ|Bir sabit değilse, bu, IndexOf (`this`, `value`) = 1 ile eşlenir. `value`|
|Uzunluklu|Length (`this`)||
|Int32 IndexOf (dize `value`)|IndexOf (`this`, `value`)-1||
|System. String ekleme (Int32 `startIndex`, String `value`)|Concat (Concat (alt dize`this`(, 1 `startIndex`,) `value`,), alt`this`dize `startIndex`(, + 1,`this`Uzunluk ( `startIndex`)-))||
|System. String Kaldır (Int32 `startIndex`)|Alt dize`this`(, 1 `startIndex`,)||
|System. String Kaldır (Int32 `startIndex`, Int32 `count`)|Concat (alt dize`this`(, 1 `startIndex`,), alt`this`dize `startIndex` (,`this` `count`  +  + 1, uzunluk ()`startIndex`-( + `count`)))|Remove (`startIndex`, `count` )yalnızca0'danbüyükveyabunaeşitbirtamsayıisedesteklenir.`count`|
|System. String Replace (dize `oldValue`, dize `newValue`)|Değiştir (`this`, `oldValue`, `newValue`)||
|System. String alt dizesi ( `startIndex`Int32)|Alt dize`this`( `startIndex` , + 1, length`this`() `startIndex`-)||
|System. String alt dize ( `startIndex`Int32, `length`Int32)|Alt dize`this`( `startIndex` , + 1 `length`,)||
|System. String ToLower ()|ToLower (`this`)||
|System. String ToUpper ()|ToUpper (`this`)||
|System. String Trim ()|Trim (`this`)||
|System. String TrimEnd (Char [] `trimChars`)|RTrim (`this`)||
|System. String Kırbir başlangıç (Char [`trimChars`])|LTrim (`this`)||
|Boole eşittir (dize `value`)|= işleci||

## <a name="systemdatetime-method-static-mapping"></a>System. DateTime yöntemi (statik) eşleme

|System. DateTime yöntemi (statik)|Kurallı işlev|Notlar|
|---------------------------------------|------------------------|-----------|
|Boolean eşittir (DateTime `t1`, DateTime `t2`)|= işleci||
|System. DateTime. Now|CurrentDateTime ()||
|System. DateTime. UtcNow|CurrentUtcDateTime()||
|Boolean op_Equality (DateTime `d1`, DateTime `d2`)|= işleci||
|Boolean op_GreaterThan (DateTime `t1`, DateTime `t2`)|> işleci||
|Boolean op_GreaterThanOrEqual (DateTime `t1`, DateTime `t2`)|> = işleci||
|Boolean op_Inequality (DateTime `t1`, DateTime `t2`)|!= operator||
|Boolean op_LessThan (DateTime `t1`, DateTime `t2`)|< işleci||
|Boolean op_LessThanOrEqual (DateTime `t1`, DateTime `t2`)|< = işleci||
|Microsoft. VisualBasic. DateAndTime. DatePart (_<br /><br /> ByVal `Interval` olarak DateInterval,\_<br /><br /> Tarih `DateValue` saat olarak ByVal,\_<br /><br /> İsteğe bağlı `FirstDayOfWeekValue` ByVal as FirstDayOfWeek = vbpazar,\_<br /><br /> FirstWeekOfYear için isteğe bağlı ByVal `FirstWeekOfYearValue` = vbFirstJan1\_<br /><br /> ) Tamsayı olarak||Daha fazla bilgi için DatePart Işlevi bölümüne bakın.|
|Microsoft. VisualBasic. DateAndTime. Şimdi|CurrentDateTime ()||
|Microsoft. VisualBasic. DateAndTime. Year (DateTime `TimeValue`)|Year ()||
|Microsoft. VisualBasic. DateAndTime. month (TarihSaat `TimeValue`)|Month ()||
|Microsoft. VisualBasic. DateAndTime. Day (TarihSaat `TimeValue`)|Gün ()||
|Microsoft. VisualBasic. DateAndTime. Hour (DateTime `TimeValue`)|Saat ()||
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minute ()||
|Microsoft. VisualBasic. DateAndTime. second (TarihSaat `TimeValue`)|Second ()||

## <a name="systemdatetime-method-instance-mapping"></a>System. DateTime yöntemi (örnek) eşleme

|System. DateTime yöntemi (örnek)|Kurallı işlev|
|-----------------------------------------|------------------------|
|Boole eşittir (TarihSaat `value`)|= işleci|
|Gün|Gün (`this`)|
|Saat|Saat (`this`)|
|Milisaniy|Milisaniyelik`this`()|
|Dakika|Minute (`this`)|
|Başından|Month (`this`)|
|Saniye|Second (`this`)|
|Yıl|Year (`this`)|

## <a name="systemdatetimeoffset-method-instance-mapping"></a>System. DateTimeOffset yöntemi (örnek) eşleme

Listelenen özelliklerde `get` yöntemler için gösterilen eşleme.

|System. DateTimeOffset yöntemi (örnek)|Kurallı işlev|Notlar|
|-----------------------------------------------|------------------------|-----------|
|Gün|Gün (`this`)|SQL Server 2005 ' de desteklenmez.|
|Saat|Saat (`this`)|SQL Server 2005 ' de desteklenmez.|
|Milisaniy|Milisaniyelik`this`()|SQL Server 2005 ' de desteklenmez.|
|Dakika|Minute (`this`)|SQL Server 2005 ' de desteklenmez.|
|Başından|Month (`this`)|SQL Server 2005 ' de desteklenmez.|
|Saniye|Second (`this`)|SQL Server 2005 ' de desteklenmez.|
|Yıl|Year (`this`)|SQL Server 2005 ' de desteklenmez.|

> [!NOTE]
> `true` Karşılaştırılan <xref:System.DateTimeOffset.Equals%2A> nesnelereşitse<xref:System.DateTimeOffset> , yöntemi döndürür; `false` Aksi takdirde. Yöntemi, karşılaştırılan <xref:System.DateTimeOffset> nesnenin sırasıyla eşit, büyük veya küçük olmasına bağlı olarak 0, 1 veya-1 döndürür. <xref:System.DateTimeOffset.CompareTo%2A>

## <a name="systemdatetimeoffset-method-static-mapping"></a>System. DateTimeOffset yöntemi (statik) eşleme

Listelenen özelliklerde `get` yöntemler için gösterilen eşleme.

|System. DateTimeOffset yöntemi (statik)|Kurallı işlev|Notlar|
|---------------------------------------------|------------------------|-----------|
|System. DateTimeOffset. Now ()|CurrentDateTimeOffset()|SQL Server 2005 ' de desteklenmez.|

## <a name="systemtimespan-method-instance-mapping"></a>System. TimeSpan yöntemi (örnek) eşleme

Listelenen özelliklerde `get` yöntemler için gösterilen eşleme.

|System. TimeSpan yöntemi (örnek)|Kurallı işlev|Notlar|
|-----------------------------------------|------------------------|-----------|
|Saatlerinin|Saat (`this`)|SQL Server 2005 ' de desteklenmez.|
|Milisaniye|Milisaniyelik`this`()|SQL Server 2005 ' de desteklenmez.|
|Dakika|Minute (`this`)|SQL Server 2005 ' de desteklenmez.|
|Saniyeden|Second (`this`)|SQL Server 2005 ' de desteklenmez.|

> [!NOTE]
> `true` Karşılaştırılan <xref:System.TimeSpan.Equals%2A> nesnelereşitse<xref:System.TimeSpan> , yöntemi döndürür; `false` Aksi takdirde. Yöntemi, karşılaştırılan <xref:System.TimeSpan> nesnenin sırasıyla eşit, büyük veya küçük olmasına bağlı olarak 0, 1 veya-1 döndürür. <xref:System.TimeSpan.CompareTo%2A>

### <a name="datepart-function"></a>DatePart Işlevi

İşlevi, değerine bağlı olarak çeşitli farklı kurallı işlevlerden birine eşlenir. `Interval` `DatePart` Aşağıdaki tabloda, desteklenen değerleri `Interval`için kurallı işlev eşlemesi görüntülenmektedir:

|Aralık değeri|Kurallı işlev|
|--------------------|------------------------|
|Tarih aralığı. yıl|Year ()|
|Tarih aralığı. ay|Month ()|
|Tarih aralığı. gün|Gün ()|
|Tarih aralığı. saat|Saat ()|
|Tarih aralığı. dakika|Minute ()|
|Tarih aralığı. saniye|Second ()|

## <a name="mathematical-function-mapping"></a>Matematik Işlevi eşleme

|CLR yöntemi|Kurallı işlev|
|----------------|------------------------|
|System. Decimal. tavan (ondalık `d`)|Tavan (`d`)|
|System. Decimal. Floor (ondalık `d`)|Floor (`d`)|
|System. Decimal. Round (ondalık `d`)|Round (`d`)|
|System. Math. tavan (ondalık `d`)|Tavan (`d`)|
|System. Math. Floor (ondalık `d`)|Floor (`d`)|
|System. Math. Round (ondalık `d`)|Round (`d`)|
|System. Math. tavan (çift `a`)|Tavan (`a`)|
|System. Math. Floor (Double `a`)|Floor (`a`)|
|System. Math. Round (Double `a`)|Round (`a`)|
|System. Math. Round (Double değeri, Int16 basamakları)|Round (değer, basamak)|
|System. Math. Round (Double değeri, Int32 rakamları)|Round (değer, basamak)|
|System. Math. Round (ondalık değer, Int16 basamakları)|Round (değer, basamak)|
|System. Math. Round (Decimal değeri, Int32, basamaklar)|Round (değer, basamak)|
|System. Math. ABS (Int16 değeri)|ABS (değer)|
|System. Math. ABS (Int32 değeri)|ABS (değer)|
|System. Math. ABS (Int64 değeri)|ABS (değer)|
|System. Math. ABS (bayt değeri)|ABS (değer)|
|System. Math. ABS (tek değer)|ABS (değer)|
|System. Math. ABS (Double değeri)|ABS (değer)|
|System. Math. ABS (ondalık değeri)|ABS (değer)|
|System. Math. truncate (Double değeri, Int16 basamakları)|Kes (değer, basamak)|
|System. Math. truncate (Double değeri, Int32 rakamları)|Kes (değer, basamak)|
|System. Math. truncate (ondalık değer, Int16 basamakları)|Kes (değer, basamak)|
|System. Math. truncate (Decimal değeri, Int32 rakamları)|Kes (değer, basamak)|
|System. Math. Power (Int32 değeri, Int64 üs)|Güç (değer, üs)|
|System. Math. Power (Int32 değeri, Double üs)|Güç (değer, üs)|
|System. Math. Power (Int32 değeri, Decimal üs)|Güç (değer, üs)|
|System. Math. Power (Int64 değeri, Int64 üs)|Güç (değer, üs)|
|System. Math. Power (Int64 değeri, Çift üs)|Güç (değer, üs)|
|System. Math. Power (Int64 değeri, Decimal üs)|Güç (değer, üs)|
|System. Math. Power (Double değeri, Int64 üs)|Güç (değer, üs)|
|System. Math. Power (Double değeri, Double üs)|Güç (değer, üs)|
|System. Math. güç (Double değeri, Decimal üs)|Güç (değer, üs)|
|System. Math. Power (Decimal değeri, Int64 üs)|Güç (değer, üs)|
|System. Math. Power (Decimal değeri, Double üs)|Güç (değer, üs)|
|System. Math. Power (Decimal değeri, Decimal üs)|Güç (değer, üs)|

## <a name="bitwise-operator-mapping"></a>Bit düzeyinde Işleç eşleme

|Bit düzeyinde işleç|Boole olmayan işlenenler için kurallı işlev|Boole işlenenleri için kurallı işlev|
|----------------------|--------------------------------------------------|---------------------------------------------|
|Bit düzeyinde AND işleci|Bitwiseve|OP1 ve OP2|
|Bit düzeyinde OR işleci|Bitwiseveya|OP1 veya OP2|
|Bit düzeyinde NOT işleci|BitWiseNot|NOT (OP)|
|Bit düzeyinde XOR işleci|BitWiseXor|((OP1 ve NOT (OP2)) veya (NOT (OP1) ve OP2))|

## <a name="other-mapping"></a>Diğer eşleme

|Yöntem|Kurallı işlev|
|------------|------------------------|
|Guid. NewGuid ()|NewGuid ()|

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities](linq-to-entities.md)
