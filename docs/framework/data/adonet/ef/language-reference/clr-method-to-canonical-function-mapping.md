---
title: Kurallı işlev eşlemesi için CLR yöntemi
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 07d488eb8caba8309857ef7fba42e67e155363e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="clr-method-to-canonical-function-mapping"></a>Kurallı işlev eşlemesi için CLR yöntemi
Entity Framework dize düzenlemesi ve matematik işlevleri gibi birçok veritabanı sistemler arasında ortak olan işlevselliğini uygulayan kurallı işlevler kümesini sağlar. Bu, çok çeşitli veritabanı sistemleri hedeflemek geliştiricilere sağlar. LINQ to Entities, gibi bir sorgulama teknolojisi gelen bunlar kurallı çağrıldığında işlevleri için kullanılan sağlayıcısı için doğru karşılık gelen depolama işlevi çevrilir. Bu veri kaynakları arasında tutarlı bir sorgu deneyimi sağlayan ortak bir formda arasında veri kaynaklarına, ifade işlev çağrılarını sağlar. Bit düzeyinde AND, OR değil ve işlenen sayısal bir tür olduğunda XOR işleçleri kurallı işlevleri de eşleniyor. Boole işlenenler, bit düzeyinde AND, OR, NOT, için ve XOR işleçleri mantıksal AND, OR değil, işlem ve bunların işlenenler XOR işlemlerini. Daha fazla bilgi için bkz: [kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
 LINQ senaryoları için Entity Framework sorguları kurallı işlevler aracılığıyla temel alınan veri kaynağında yöntemlerine eşleme belirli CLR yöntemlerini içerir. Çalışma zamanı'nda açıkça kurallı bir işleve eşlenmemiş tüm yöntem çağrılarını bir LINQ to Entities sorgusunda sonuçlanır <xref:System.NotSupportedException> oluşturulan özel durum.  
  
## <a name="systemstring-method-static-mapping"></a>System.String yöntemi (statik) eşleme  
  
|System.String yöntemi (statik)|Kurallı işlevi|  
|-------------------------------------|------------------------|  
|System.String Concat(String `str0`, String `str1`)|Concat (`str0`, `str1`)|  
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat (Concat (`str0`, `str1`), `str2`)|  
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat (Concat (Concat (`str0`, `str1`), `str2`), `str3`)|  
|Boole eşittir (dize `a`, dize `b`)|= işleci|  
|Boolean IsNullOrEmpty (dize `value`)|(IsNull (`value`)) veya uzunluğu (`value`) = 0|  
|Boole op_Equality (dize `a`, dize `b`)|= işleci|  
|Boolean op_Inequality (dize `a` , dize `b`)|!= operator|  
|Microsoft.VisualBasic.Strings.Trim (dize `str`)|Trim (`str`)|  
|Microsoft.VisualBasic.Strings.LTrim (dize `str`)|LTrim (`str`)|  
|Microsoft.VisualBasic.Strings.RTrim (dize `str`)|RTrim (`str`)|  
|Microsoft.VisualBasic.Strings.Len (dize `expression`)|Uzunluğu (`expression`)|  
|Microsoft.VisualBasic.Strings.Left (dize `str`, Int32 `Length`)|Sol (`str`, `Length`)|  
|Microsoft.VisualBasic.Strings.Mid (dize `str`, Int32 `Start`, Int32 `Length`)|Substring (`str`, `Start`, `Length`)|  
|Microsoft.VisualBasic.Strings.Right (dize `str`, Int32 `Length`)|Sağ (`str`, `Length`)|  
|Microsoft.VisualBasic.Strings.UCase (dize `Value`)|ToUpper (`Value`)|  
|Microsoft.VisualBasic.Strings.LCase (dize)|ToLower (`Value`)|  
  
## <a name="systemstring-method-instance-mapping"></a>System.String eşleme yöntemi (örneği)  
  
|System.String yöntemi (örneği)|Kurallı işlevi|Notlar|  
|---------------------------------------|------------------------|-----------|  
|Boole değeri içeren (dize `value`)|`this` GİBİ ' %`value`%'|Varsa `value` bu IndexOf için eşler sonra bir sabit değil (`this`, `value`) > 0|  
|Boolean EndsWith (dize `value`)|`this` GİBİ `'` % `value`'|Varsa `value` bu sağa eşler sonra bir sabit değil (`this`, uzunluğu (`value`)) = `value`.|  
|Boolean StartsWith (dize `value`)|`this` GİBİ '`value`%'|Varsa `value` bu IndexOf için eşler sonra bir sabit değil (`this`, `value`) = 1.|  
|uzunluğu|Uzunluğu (`this`)||  
|Int32 IndexOf (dize `value`)|IndexOf (`this`, `value`) - 1||  
|System.String Insert(Int32 `startIndex`, String `value`)|Concat (Concat (Substring (`this`, 1, `startIndex`), `value`), Substring (`this`, `startIndex`+ 1, uzunluğu (`this`)- `startIndex`))||  
|System.String Remove(Int32 `startIndex`)|Substring (`this`, 1, `startIndex`)||  
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat (Substring (`this`, 1, `startIndex`), Substring (`this`, `startIndex`  +  `count` + 1, uzunluğu (`this`)-(`startIndex` + `count`)))|Kaldır (`startIndex`, `count`), yalnızca desteklenen `count` 0 değerine eşit veya daha büyük bir tamsayıdır.|  
istem. Dize Değiştir (dize `oldValue`, dize `newValue`)|Değiştir (`this`, `oldValue`, `newValue`)||  
|System.String Substring(Int32 `startIndex`)|Substring (`this`, `startIndex` + 1, uzunluğu (`this`)- `startIndex`)||  
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Substring (`this`, `startIndex` + 1, `length`)||  
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
|Boolean op_GreaterThan (DateTime `t1`, DateTime `t2`)|> işleci||  
|Boolean op_GreaterThanOrEqual (DateTime `t1`, DateTime `t2`)|>= işleci||  
|Boolean op_Inequality (DateTime `t1`, DateTime `t2`)|!= operator||  
|Boolean op_LessThan (DateTime `t1`, DateTime `t2`)|< işleci||  
|Boolean op_LessThanOrEqual (DateTime `t1`, DateTime `t2`)|<= işleci||  
|Microsoft.VisualBasic.DateAndTime.DatePart (_<br /><br /> ByVal `Interval` DateInterval, olarak \_<br /><br /> ByVal `DateValue` DateTime, olarak \_<br /><br /> İsteğe bağlı ByVal `FirstDayOfWeekValue` FirstDayOfWeek olarak VbSunday, = \_<br /><br /> İsteğe bağlı ByVal `FirstWeekOfYearValue` yılın ilk haftası olarak VbFirstJan1 = \_<br /><br /> ) Tamsayı olarak||Daha fazla bilgi için DatePart işlevi bölümüne bakın.|  
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||  
|Microsoft.VisualBasic.DateAndTime.Year (DateTime `TimeValue`)|Year()||  
|Microsoft.VisualBasic.DateAndTime.Month (DateTime `TimeValue`)|Month()||  
icrosoft. VisualBasic.DateAndTime.Day (DateTime `TimeValue`)|Day()||  
|Microsoft.VisualBasic.DateAndTime.Hour (DateTime `TimeValue`)|Hour()||  
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minute()||  
|Microsoft.VisualBasic.DateAndTime.Second (DateTime `TimeValue`)|Second()||  
  
## <a name="systemdatetime-method-instance-mapping"></a>System.DateTime eşleme yöntemi (örneği)  
  
|System.DateTime yöntemi (örneği)|Kurallı işlevi|  
|-----------------------------------------|------------------------|  
|Boole eşittir (DateTime `value`)|= işleci|  
|Gün|Gün (`this`)|  
|Saat|Saat (`this`)|  
|Milisaniye|Milisaniye (`this`)|  
|Dakika|Dakika (`this`)|  
|Ay|Ay (`this`)|  
|Saniye|İkinci (`this`)|  
|Yıl|Yıl (`this`)|  
  
## <a name="systemdatetimeoffset-method-instance-mapping"></a>System.DateTimeOffset eşleme yöntemi (örneği)  
 Gösterilen eşleme `get` listelenen özellikler yöntemleri.  
  
|System.DateTimeOffset yöntemi (örneği)|Kurallı işlevi|Notlar|  
|-----------------------------------------------|------------------------|-----------|  
|Gün|Gün (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Saat|Saat (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Milisaniye|Milisaniye (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Dakika|Dakika (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Ay|Ay (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Saniye|İkinci (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Yıl|Yıl (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
  
> [!NOTE]
>  <xref:System.DateTimeOffset.Equals%2A> Yöntemi döndürür `true` varsa karşılaştırılan <xref:System.DateTimeOffset> nesneleri eşit; `false` Aksi takdirde. <xref:System.DateTimeOffset.CompareTo%2A> Yöntemi, 0, 1 ya da bağlı olarak mı yoksa -1 döndürür karşılaştırılan <xref:System.DateTimeOffset> nesnesidir eşit, büyük veya küçük daha sırasıyla.  
  
## <a name="systemdatetimeoffset-method-static-mapping"></a>System.DateTimeOffset yöntemi (statik) eşleme  
 Gösterilen eşleme `get` listelenen özellikler yöntemleri.  
  
|System.DateTimeOffset yöntemi (statik)|Kurallı işlevi|Notlar|  
|---------------------------------------------|------------------------|-----------|  
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|SQL Server 2005 karşı desteklenmiyor.|  
  
## <a name="systemtimespan-method-instance-mapping"></a>System.TimeSpan eşleme yöntemi (örneği)  
 Gösterilen eşleme `get` listelenen özellikler yöntemleri.  
  
|System.TimeSpan yöntemi (örneği)|Kurallı işlevi|Notlar|  
|-----------------------------------------|------------------------|-----------|  
|Saatleri|Saat (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|milisaniye|Milisaniye (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|dakika|Dakika (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
|Saniye|İkinci (`this`)|SQL Server 2005 karşı desteklenmiyor.|  
  
> [!NOTE]
>  <xref:System.TimeSpan.Equals%2A> Yöntemi döndürür `true` varsa karşılaştırılan <xref:System.TimeSpan> nesneleri eşit; `false` Aksi takdirde. <xref:System.TimeSpan.CompareTo%2A> Yöntemi, 0, 1 ya da bağlı olarak mı yoksa -1 döndürür karşılaştırılan <xref:System.TimeSpan> nesnesidir eşit, büyük veya küçük daha sırasıyla.  
  
### <a name="datepart-function"></a>DatePart işlevi  
 `DatePart` İşlevi değerine bağlı olarak birkaç farklı kurallı işlevler birine eşlendiği `Interval`. Aşağıdaki tabloda desteklenen değerler için kurallı işlev eşleme görüntüler `Interval`:  
  
|Aralık değeri|Kurallı işlevi|  
|--------------------|------------------------|  
|DateInterval.Year|Year()|  
|DateInterval.Month|Month()|  
|DateInterval.Day|Day()|  
|DateInterval.Hour|Hour()|  
|DateInterval.Minute|Minute()|  
|DateInterval.Second|Second()|  
  
## <a name="mathematical-function-mapping"></a>Matematik işlev eşlemesi  
  
|CLR yöntemi|Kurallı işlevi|  
|----------------|------------------------|  
|System.Decimal.Ceiling (ondalık `d`)|Tavan (`d`)|  
|System.Decimal.Floor (ondalık `d`)|Floor (`d`)|  
|System.Decimal.Round (ondalık `d`)|Yuvarlak (`d`)|  
|System.Math.Ceiling (ondalık `d`)|Tavan (`d`)|  
|System.Math.Floor (ondalık `d`)|Floor (`d`)|  
|System.Math.Round (ondalık `d`)|Yuvarlak (`d`)|  
|System.Math.Ceiling (çift `a`)|Tavan (`a`)|  
|System.Math.Floor (çift `a`)|Floor (`a`)|  
|System.Math.Round (çift `a`)|Yuvarlak (`a`)|  
|System.Math.Round (Double değeri, Int16 basamak)|Round (değer, basamak)|  
|System.Math.Round (Double değeri, Int32 basamak)|Round (değer, basamak)|  
|System.Math.Round (ondalık değer, Int16 basamak)|Round (değer, basamak)|  
|System.Math.Round (Int32, Decimal değeri basamak)|Round (değer, basamak)|  
|System.Math.Abs (Int16 değeri)|Abs(Value)|  
|System.Math.Abs (Int32 değeri)|Abs(Value)|  
|System.Math.Abs (Int64 değeri)|Abs(Value)|  
|System.Math.Abs (bayt değeri)|Abs(Value)|  
|System.Math.Abs (tek değer)|Abs(Value)|  
|System.Math.Abs (çift değer)|Abs(Value)|  
|System.Math.Abs (ondalık değeri)|Abs(Value)|  
|System.Math.Truncate (Double değeri, Int16 basamak)|(Değer, basamak) kesme|  
|System.Math.Truncate (Double değeri, Int32 basamak)|(Değer, basamak) kesme|  
|System.Math.Truncate (ondalık değer, Int16 basamak)|(Değer, basamak) kesme|  
|System.Math.Truncate (ondalık değeri, Int32 basamak)|(Değer, basamak) kesme|  
|System.Math.Power (Int32 değeri, Int64 üs)|Güç (değer, üs)|  
|System.Math.Power (Int32 değeri, çift üs)|Güç (değer, üs)|  
|System.Math.Power (Int32 değeri, ondalık üs)|Güç (değer, üs)|  
|System.Math.Power (bir Int64 değeri, Int64 üs)|Güç (değer, üs)|  
|System.Math.Power (Int64 değeri, çift üs)|Güç (değer, üs)|  
|System.Math.Power (bir Int64 değeri, ondalık üs)|Güç (değer, üs)|  
|System.Math.Power (Double değeri, Int64 üs)|Güç (değer, üs)|  
|System.Math.Power (çift değer, çift üs)|Güç (değer, üs)|  
|System.Math.Power (Double değeri, ondalık üs)|Güç (değer, üs)|  
|System.Math.Power (ondalık değer, Int64 üs)|Güç (değer, üs)|  
|System.Math.Power (ondalık değer, çift üs)|Güç (değer, üs)|  
|System.Math.Power (ondalık değeri, ondalık üs)|Güç (değer, üs)|  
  
## <a name="bitwise-operator-mapping"></a>Bit düzeyinde işleci eşleştirme  
  
|Bit düzeyinde işleci|Boole olmayan işlenenler için kurallı işlevi|Boole işlenenler için kurallı işlevi|  
|----------------------|--------------------------------------------------|---------------------------------------------|  
|Bit düzeyinde AND işleci|BitWiseAnd|op1 ve op2|  
|Bit düzeyinde OR işleci|BitWiseOr|op1 veya op2|  
|Bitwise NOT işleci|BitWiseNot|Not(OP)|  
|Bit düzeyinde XOR işleci|BitWiseXor|((op1 ve NOT(op2)) OR (NOT(op1) ve op2))|  
  
## <a name="other-mapping"></a>Diğer eşleme  
  
|Yöntem|Kurallı işlevi|  
|------------|------------------------|  
|Guid.NewGuid()|NewGuid()|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
