---
title: CLR yöntemini kurallı işlev ile eşleme
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 31e6bfaf86ffb6721491a8d6681d713075a628f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551585"
---
# <a name="clr-method-to-canonical-function-mapping"></a>CLR yöntemini kurallı işlev ile eşleme
Entity Framework, dize işlemleri ve matematik işlevleri gibi birçok veritabanı sistemleri arasında ortak olan işlevselliği uygulamak kurallı işlevler sunmaktadır. Bu, geliştiricilerin veritabanı sistemleri geniş bir hedef sağlar. Sorgulama teknoloji ve LINQ to Entities, gibi bunlar kurallı çağrılır, işlevleri için kullanılan sağlayıcısı doğru karşılık gelen depolama işleviyle çevrilir. Bu veri kaynakları arasında tutarlı sorgu deneyimi sağlayan veri kaynaklarında yaygın bir biçimde ifade edilmesi işlev çağrılarını sağlar. Bit düzeyinde AND, OR değil ve bir sayısal tür işleneni olduğunda XOR işleçleri için kurallı işlevler ayrıca eşlendi. Boole işlenenleri, bit düzeyinde AND, OR, NOT, için ve işlem mantıksal AND, OR, XOR işleçler ve işlenenleri XOR işlemlerini. Daha fazla bilgi için [kurallı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
 LINQ senaryoları için Entity Framework sorguları kurallı işlevler aracılığıyla temel alınan veri kaynağında yöntemlere eşleme belirli CLR yöntemlerini içerir. Kurallı bir işleve açıkça eşleştirilmemiş yöntemi çağrıları bir LINQ to Entities sorgusunda çalışma zamanı'nda neden olacak <xref:System.NotSupportedException> oluşturulan özel durum.  
  
## <a name="systemstring-method-static-mapping"></a>System.String yöntemi (statik) eşleme  
  
|System.String yöntemi (statik)|Kurallı işlevi|  
|-------------------------------------|------------------------|  
|System.String Concat(String `str0`, String `str1`)|Concat (`str0`, `str1`)|  
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat (Concat (`str0`, `str1`), `str2`)|  
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat (Concat (Concat (`str0`, `str1`), `str2`), `str3`)|  
|Boole eşittir (dize `a`, dize `b`)|= işleci|  
|Boole IsNullOrEmpty (dize `value`)|(IsNull (`value`)) veya uzunluğu (`value`) = 0|  
|Boole op_Equality (dize `a`, dize `b`)|= işleci|  
|Boole op_Inequality (dize `a` , dize `b`)|!= operator|  
|Microsoft.VisualBasic.Strings.Trim (dize `str`)|Trim (`str`)|  
|Microsoft.VisualBasic.Strings.LTrim (dize `str`)|LTrim (`str`)|  
|Microsoft.VisualBasic.Strings.RTrim (dize `str`)|RTrim (`str`)|  
|Microsoft.VisualBasic.Strings.Len (dize `expression`)|Uzunluk (`expression`)|  
|Microsoft.VisualBasic.Strings.Left (dize `str`, Int32 `Length`)|Sol (`str`, `Length`)|  
|Microsoft.VisualBasic.Strings.Mid (dize `str`, Int32 `Start`, Int32 `Length`)|Alt dize (`str`, `Start`, `Length`)|  
|Microsoft.VisualBasic.Strings.Right (dize `str`, Int32 `Length`)|Right(`str`, `Length`)|  
|Microsoft.VisualBasic.Strings.UCase (dize `Value`)|ToUpper (`Value`)|  
|Microsoft.VisualBasic.Strings.LCase (dize)|ToLower (`Value`)|  
  
## <a name="systemstring-method-instance-mapping"></a>System.String eşleme yöntemi (örnek)  
  
|System.String yöntemi (örnek)|Kurallı işlevi|Notlar|  
|---------------------------------------|------------------------|-----------|  
|Boolean içerir (dize `value`)|`this` GİBİ ' %`value`%'|Varsa `value` bu eşler için IndexOf sonra bir sabit değil (`this`, `value`) > 0|  
|Boole EndsWith (dize `value`)|`this` GİBİ `'` % `value`'|Varsa `value` bu sağa eşler sonra bir sabit değil (`this`, uzunluğu (`value`)) = `value`.|  
|Boole StartsWith (dize `value`)|`this` GİBİ '`value`%'|Varsa `value` bu eşler için IndexOf sonra bir sabit değil (`this`, `value`) = 1.|  
|Uzunluğu|Uzunluk (`this`)||  
|Int32 IndexOf (dize `value`)|IndexOf (`this`, `value`) - 1||  
|System.String Insert(Int32 `startIndex`, String `value`)|Concat (Concat (alt dize (`this`, 1, `startIndex`), `value`), alt dize (`this`, `startIndex`+ 1, uzunluk (`this`)- `startIndex`))||  
|System.String Remove(Int32 `startIndex`)|Alt dize (`this`, 1, `startIndex`)||  
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat (alt dize (`this`, 1, `startIndex`), alt dize (`this`, `startIndex`  +  `count` + 1, uzunluk (`this`)-(`startIndex` + `count`)))|Kaldır (`startIndex`, `count`), yalnızca desteklenen `count` 0'a eşit veya daha büyük bir tamsayıdır.|  
istem. Dize değiştirin (String `oldValue`, dize `newValue`)|Değiştir (`this`, `oldValue`, `newValue`)||  
|System.String Substring(Int32 `startIndex`)|Alt dize (`this`, `startIndex` + 1, uzunluk (`this`)- `startIndex`)||  
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Alt dize (`this`, `startIndex` + 1, `length`)||  
|System.String ToLower()|ToLower (`this`)||  
|System.String ToUpper()|ToUpper (`this`)||  
|System.String Trim()|Trim (`this`)||  
|System.String TrimEnd(Char[] `trimChars`)|RTrim (`this`)||  
|System.String TrimStart(Char[]`trimChars`)|LTrim (`this`)||  
|Boole eşittir (dize `value`)|= işleci||  
  
## <a name="systemdatetime-method-static-mapping"></a>System.DateTime yöntemi (statik) eşleme  
  
|System.DateTime yöntemi (statik)|Kurallı işlevi|Notlar|  
|---------------------------------------|------------------------|-----------|  
|Boole eşittir (DateTime `t1`, DateTime `t2`)|= işleci||  
|System.DateTime.Now|CurrentDateTime()||  
|System.DateTime.UtcNow|CurrentUtcDateTime()||  
|Boole op_Equality (DateTime `d1`, DateTime `d2`)|= işleci||  
|Boole op_GreaterThan (DateTime `t1`, DateTime `t2`)|> işleci||  
|Boole op_GreaterThanOrEqual (DateTime `t1`, DateTime `t2`)|>= işleci||  
|Boole op_Inequality (DateTime `t1`, DateTime `t2`)|!= operator||  
|Boole op_LessThan (DateTime `t1`, DateTime `t2`)|< işleci||  
|Boole op_LessThanOrEqual (DateTime `t1`, DateTime `t2`)|<= işleci||  
|Microsoft.VisualBasic.DateAndTime.DatePart (_<br /><br /> ByVal `Interval` DateInterval, olarak \_<br /><br /> ByVal `DateValue` DateTime, olarak \_<br /><br /> İsteğe bağlı ByVal `FirstDayOfWeekValue` FirstDayOfWeek olarak VbSunday, = \_<br /><br /> İsteğe bağlı ByVal `FirstWeekOfYearValue` FirstWeekOfYear olarak VbFirstJan1 = \_<br /><br /> ) Tamsayı olarak||Daha fazla bilgi için DatePart işlevi bölümüne bakın.|  
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||  
|Microsoft.VisualBasic.DateAndTime.Year (DateTime `TimeValue`)|Year()||  
|Microsoft.VisualBasic.DateAndTime.Month (DateTime `TimeValue`)|Month()||  
icrosoft. VisualBasic.DateAndTime.Day (DateTime `TimeValue`)|Day()||  
|Microsoft.VisualBasic.DateAndTime.Hour (DateTime `TimeValue`)|Hour()||  
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minute()||  
|Microsoft.VisualBasic.DateAndTime.Second (DateTime `TimeValue`)|Second()||  
  
## <a name="systemdatetime-method-instance-mapping"></a>System.DateTime eşleme yöntemi (örnek)  
  
|System.DateTime yöntemi (örnek)|Kurallı işlevi|  
|-----------------------------------------|------------------------|  
|Boole eşittir (DateTime `value`)|= işleci|  
|Gün|Gün (`this`)|  
|Saat|Saat (`this`)|  
|Milisaniye|Milisaniye (`this`)|  
|Dakika|Dakika (`this`)|  
|Ay|Ay (`this`)|  
|Saniye|İkinci (`this`)|  
|Yıl|Yıl (`this`)|  
  
## <a name="systemdatetimeoffset-method-instance-mapping"></a>System.DateTimeOffset eşleme yöntemi (örnek)  
 Eşleme için gösterilen `get` yöntemleri listelenen özellikleri.  
  
|System.DateTimeOffset yöntemi (örnek)|Kurallı işlevi|Notlar|  
|-----------------------------------------------|------------------------|-----------|  
|Gün|Gün (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Saat|Saat (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Milisaniye|Milisaniye (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Dakika|Dakika (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Ay|Ay (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Saniye|İkinci (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Yıl|Yıl (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
  
> [!NOTE]
>  <xref:System.DateTimeOffset.Equals%2A> Yöntemi döndürür `true` , karşılaştırılan <xref:System.DateTimeOffset> nesneler eşit; `false` Aksi takdirde. <xref:System.DateTimeOffset.CompareTo%2A> Yöntemi, 0, 1 ya da bağlı olarak -1 döndürür karşılaştırılan <xref:System.DateTimeOffset> nesnedir eşit, büyük veya küçük değerinden, sırasıyla.  
  
## <a name="systemdatetimeoffset-method-static-mapping"></a>System.DateTimeOffset yöntemi (statik) eşleme  
 Eşleme için gösterilen `get` yöntemleri listelenen özellikleri.  
  
|System.DateTimeOffset yöntemi (statik)|Kurallı işlevi|Notlar|  
|---------------------------------------------|------------------------|-----------|  
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|SQL Server 2005 karşı desteklenmiyor.|  
  
## <a name="systemtimespan-method-instance-mapping"></a>System.TimeSpan eşleme yöntemi (örnek)  
 Eşleme için gösterilen `get` yöntemleri listelenen özellikleri.  
  
|System.TimeSpan yöntemi (örnek)|Kurallı işlevi|Notlar|  
|-----------------------------------------|------------------------|-----------|  
|saat|Saat (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Milisaniye|Milisaniye (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Dakika|Dakika (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|saniye|İkinci (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
  
> [!NOTE]
>  <xref:System.TimeSpan.Equals%2A> Yöntemi döndürür `true` , karşılaştırılan <xref:System.TimeSpan> nesneler eşit; `false` Aksi takdirde. <xref:System.TimeSpan.CompareTo%2A> Yöntemi, 0, 1 ya da bağlı olarak -1 döndürür karşılaştırılan <xref:System.TimeSpan> nesnedir eşit, büyük veya küçük değerinden, sırasıyla.  
  
### <a name="datepart-function"></a>DatePart işlevi  
 `DatePart` İşlevi değerine bağlı olarak birkaç farklı kurallı işlevler birine eşlendi `Interval`. Aşağıdaki tablo kurallı işlev ile eşleme için desteklenen değerlerini görüntüler `Interval`:  
  
|Aralık değeri|Kurallı işlevi|  
|--------------------|------------------------|  
|DateInterval.Year|Year()|  
|DateInterval.Month|Month()|  
|DateInterval.Day|Day()|  
|DateInterval.Hour|Hour()|  
|DateInterval.Minute|Minute()|  
|DateInterval.Second|Second()|  
  
## <a name="mathematical-function-mapping"></a>Matematiksel işlev eşlemesi  
  
|CLR yöntemi|Kurallı işlevi|  
|----------------|------------------------|  
|System.Decimal.Ceiling (ondalık `d`)|Ceiling (`d`)|  
|System.Decimal.Floor (ondalık `d`)|Katı (`d`)|  
|System.Decimal.Round (ondalık `d`)|Yuvarlak (`d`)|  
|System.Math.Ceiling (ondalık `d`)|Ceiling (`d`)|  
|System.Math.Floor (ondalık `d`)|Katı (`d`)|  
|System.Math.Round (ondalık `d`)|Yuvarlak (`d`)|  
|System.Math.Ceiling (çift `a`)|Ceiling (`a`)|  
|System.Math.Floor (çift `a`)|Katı (`a`)|  
|System.Math.Round (çift `a`)|Yuvarlak (`a`)|  
|System.Math.Round (çift değer, Int16 basamak)|Round (değer, basamak)|  
|System.Math.Round (çift değer, Int32 basamak)|Round (değer, basamak)|  
|System.Math.Round (ondalık değeri, Int16 basamak)|Round (değer, basamak)|  
|System.Math.Round (ondalık değeri, Int32, basamak)|Round (değer, basamak)|  
|System.Math.Abs (Int16 değeri)|Abs(Value)|  
|System.Math.Abs (Int32 değeri)|Abs(Value)|  
|System.Math.Abs (Int64 değeri)|Abs(Value)|  
|System.Math.Abs (bayt değeri)|Abs(Value)|  
|System.Math.Abs (çoklu değer)|Abs(Value)|  
|System.Math.Abs (çift değer)|Abs(Value)|  
|System.Math.Abs (ondalık değeri)|Abs(Value)|  
|System.Math.Truncate (çift değer, Int16 basamak)|(Değer, basamak) Kes|  
|System.Math.Truncate (çift değer, Int32 basamak)|(Değer, basamak) Kes|  
|System.Math.Truncate (ondalık değeri, Int16 basamak)|(Değer, basamak) Kes|  
|System.Math.Truncate (ondalık değeri, Int32 basamak)|(Değer, basamak) Kes|  
|System.Math.Power (değer Int32, Int64 üs)|Güç (değeri, üs)|  
|System.Math.Power (Int32 değeri, üs çift)|Güç (değeri, üs)|  
|System.Math.Power (Int32 değeri, ondalık üs)|Güç (değeri, üs)|  
|System.Math.Power (Int64 değeri, Int64 üs)|Güç (değeri, üs)|  
|System.Math.Power (Int64 değeri, üs çift)|Güç (değeri, üs)|  
|System.Math.Power (Int64 değeri, ondalık üs)|Güç (değeri, üs)|  
|System.Math.Power (çift değer, Int64 üs)|Güç (değeri, üs)|  
|System.Math.Power (çift üs değerini çift)|Güç (değeri, üs)|  
|System.Math.Power (Double değeri, ondalık üs)|Güç (değeri, üs)|  
|System.Math.Power (ondalık değeri, Int64 üs)|Güç (değeri, üs)|  
|System.Math.Power (ondalık değeri, üs çift)|Güç (değeri, üs)|  
|System.Math.Power (ondalık değeri, ondalık üs)|Güç (değeri, üs)|  
  
## <a name="bitwise-operator-mapping"></a>Bit düzeyinde işleci eşleştirme  
  
|Bit düzeyinde işleci|Boole olmayan işlenenleri için kurallı işlevi|Boole işlenenleri için kurallı işlevi|  
|----------------------|--------------------------------------------------|---------------------------------------------|  
|Bit düzeyinde AND işleci|BitWiseAnd|op1 ve op2|  
|Bit düzeyinde OR işleci|BitWiseOr|op1 veya op2|  
|Bit düzeyinde NOT işleci|BitWiseNot|Not(OP)|  
|Bit düzeyinde XOR işleci|BitWiseXor|((op1 ve NOT(op2)) veya (NOT(op1) ve op2))|  
  
## <a name="other-mapping"></a>Diğer eşleme  
  
|Yöntem|Kurallı işlevi|  
|------------|------------------------|  
|Guid.NewGuid()|NewGuid()|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
