---
title: Kurallı Tarih ve Saat İşlevleri
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: 9b7650990232face3a7c3673a6fb789912acf15c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148288"
---
# <a name="date-and-time-canonical-functions"></a>Kurallı Tarih ve Saat İşlevleri

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Tarih ve saat kurallı işlevleri içerir.  
  
## <a name="remarks"></a>Açıklamalar  

 Aşağıdaki tabloda tarih ve saat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri gösterilmektedir. `datetime` bir <xref:System.DateTime> değerdir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|Belirtilen `number` nanosaniye düzeyini öğesine ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` , `DateTimeOffset` , veya `Time` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`AddMicroseconds(expression,number)`|`number`İçin belirtilen mikrosaniye sayısını öğesine ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` , `DateTimeOffset` , veya `Time` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`AddMilliseconds(expression,number)`|`number`İçin belirtilen milisaniyeyi öğesine ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` , `DateTimeOffset` , veya `Time` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`AddSeconds(expression,number)`|Belirtilen `number` saniye sayısını öğesine ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` , `DateTimeOffset` , veya `Time` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`AddMinutes(expression,number)`|Belirtilen `number` dakika sayısını öğesine ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` , `DateTimeOffset` , veya `Time` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`AddHours(expression,number)`|Belirtilen `number` saat sayısını öğesine ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` , `DateTimeOffset` , veya `Time` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`AddDays(expression,number)`|Belirtilen `number` gün sayısını öğesine ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`AddMonths(expression,number)`|`number`İçin belirtilen ayları ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`AddYears(expression,number)`|`number`İçin belirtilen yılları öğesine ekler `expression` .<br /><br /> **Arguments**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset` .<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`CreateDateTime(year,month,day,hour,minute,second)`|Sunucunun `DateTime` saat dilimindeki sunucunun geçerli tarih ve saati olarak yeni bir değer döndürür.<br /><br /> **Arguments**<br /><br /> `year`, `month` , `day` , `hour` , `minute` : `Int16` ve `Int32` .<br /><br /> `second`: `Double`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `DateTime`.|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|`DateTimeOffset`Sunucunun geçerli tarih ve saati olarak Eşgüdümlü Evrensel Saat (UTC) ile ilişkili olarak yeni bir değer döndürür.<br /><br /> **Arguments**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `DateTimeOffset`.|  
|`CreateTime(hour,minute,second)`|`Time`Geçerli saat olarak yeni bir değer döndürür.<br /><br /> **Arguments**<br /><br /> `hour` ve `minute` : `Int32` .<br /><br /> `second`: `Double`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Time`.|  
|`CurrentDateTime()`|Sunucunun `DateTime` saat dilimindeki sunucunun geçerli tarih ve saati olarak bir değer döndürür.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `DateTime`.|  
|`CurrentDateTimeOffset()`|Geçerli tarih, saat ve sapmayı bir olarak döndürür `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|Sunucu, <xref:System.DateTime> saat dilimindeki sunucunun geçerli tarih ve saati olarak bir değer döndürür.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `DateTime`.|  
|`Day(expression)`|`expression` `Int32` 1 ile 31 arasında bir gün bölümünü döndürür.<br /><br /> **Arguments**<br /><br /> A `DateTime` ve `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|`expression` `Int32` 1 ile 366 arasında bir gün bölümünü döndürür. Bu, artık bir yılın son günü için 366 döndürülür.<br /><br /> **Arguments**<br /><br /> `DateTime`Veya `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffNanoseconds(startExpression,endExpression)`|İle arasında, nanosaniye cinsinden farkı döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` , `DateTimeOffset` veya `Time` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffMilliseconds(startExpression,endExpression)`|Ve arasında milisaniye cinsinden farkı döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` , `DateTimeOffset` veya `Time` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffMicroseconds(startExpression,endExpression)`|Ve arasında, mikrosaniye cinsinden farkı döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` , `DateTimeOffset` veya `Time` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffSeconds(startExpression,endExpression)`|Ve arasındaki farkı saniye cinsinden döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` , `DateTimeOffset` veya `Time` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffMinutes(startExpression,endExpression)`|Ve arasındaki farkı dakika cinsinden döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` , `DateTimeOffset` veya `Time` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffHours(startExpression,endExpression)`|Ve arasında, saat cinsinden farkı döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` , `DateTimeOffset` veya `Time` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffDays(startExpression,endExpression)`|Ve arasında, gün cinsinden farkı döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` veya `DateTimeOffset` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffMonths(startExpression,endExpression)`|Ve arasında, ay cinsinden farkı döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` veya `DateTimeOffset` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`DiffYears(startExpression,endExpression)`|Ve arasında, yıl cinsinden farkı döndürür `startExpression` `endExpression` .<br /><br /> **Arguments**<br /><br /> `startExpression`, `endExpression` : `DateTime` veya `DateTimeOffset` . **Note:** `startExpression` `endExpression`aynı türde olmalıdır.   <br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`GetTotalOffsetMinutes(datetimeoffset)`|`datetimeoffset`GMT 'den öteye kaydırılacağı dakika sayısını döndürür. Bu genellikle + 780 ile-780 (+ veya-13 saat) arasında olur. **Note:**  Bu işlev yalnızca SQL Server 2008 ' de desteklenir. <br /><br /> **Arguments**<br /><br /> Bir `DateTimeOffset`.<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`Hour(expression)`|`expression` `Int32` 0 ile 23 arasında bir saat bölümünü döndürür.<br /><br /> **Arguments**<br /><br /> A `DateTime, Time` ve `DateTimeOffset` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|`expression` `Int32` 0 ile 999 arasında bir milisaniye bölümünü döndürür.<br /><br /> **Arguments**<br /><br /> A `DateTime, Time` ve `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .|  
|`Minute(expression)`|`expression` `Int32` 0 ile 59 arasında bir dakika bölümünü döndürür.<br /><br /> **Arguments**<br /><br /> `DateTime, Time`Veya `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|`expression` `Int32` 1 ile 12 arasında bir ay bölümünü döndürür.<br /><br /> **Arguments**<br /><br /> `DateTime`Veya `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|`expression` `Int32` 0 ile 59 arasında saniye kısmını döndürür.<br /><br /> **Arguments**<br /><br /> A `DateTime, Time` ve `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|`expression`Zaman değerleri kesilme ile değerini döndürür.<br /><br /> **Arguments**<br /><br /> `DateTime`Veya `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Türü `expression` .|  
|`Year(expression)`|' Nin yıl kısmını döndürür `expression` `Int32` `YYYY` .<br /><br /> **Arguments**<br /><br /> A `DateTime` ve `DateTimeOffset` .<br /><br /> **Dönüş Değeri**<br /><br /> Bir `Int32` .<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Bu işlevler, `null` verilen giriş durumunda döndürülür `null` .  
  
 Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur. Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)
