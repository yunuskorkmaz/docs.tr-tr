---
title: Kurallı Tarih ve Saat İşlevleri
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: 3dd6c0da3f9851df7bb9725d9d6c08fef5a0d3d3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251090"
---
# <a name="date-and-time-canonical-functions"></a>Kurallı Tarih ve Saat İşlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Tarih ve saat kurallı işlevleri içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tabloda tarih ve saat [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri gösterilmektedir. `datetime`bir <xref:System.DateTime> değerdir.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|Belirtilen `number` nanosaniye düzeyini `expression`öğesine ekler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddMicroseconds(expression,number)`|İçin belirtilen `number` mikrosaniye sayısını öğesine ekler. `expression`<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddMilliseconds(expression,number)`|İçin belirtilen `number` milisaniyeyi öğesine ekler. `expression`<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddSeconds(expression,number)`|Belirtilen `number` saniye sayısını `expression`öğesine ekler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddMinutes(expression,number)`|Belirtilen `number` dakika sayısını `expression`öğesine ekler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddHours(expression,number)`|Belirtilen `number` saat sayısını `expression`öğesine ekler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddDays(expression,number)`|Belirtilen `number` gün sayısını `expression`öğesine ekler.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddMonths(expression,number)`|İçin belirtilen `number` ayları ekler. `expression`<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddYears(expression,number)`|İçin belirtilen `number` yılları öğesine ekler. `expression`<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`CreateDateTime(year,month,day,hour,minute,second)`|Sunucunun saat dilimindeki `DateTime` sunucunun geçerli tarih ve saati olarak yeni bir değer döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `year`, `month`, `day`, ,`hour` :`Int16`ve . `minute` `Int32`<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|Sunucunun geçerli tarih `DateTimeOffset` ve saati olarak Eşgüdümlü Evrensel Saat (UTC) ile ilişkili olarak yeni bir değer döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTimeOffset`.|  
|`CreateTime(hour,minute,second)`|Geçerli saat olarak `Time` yeni bir değer döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `hour`ve `minute`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Time`.|  
|`CurrentDateTime()`|Sunucunun saat `DateTime` dilimindeki sunucunun geçerli tarih ve saati olarak bir değer döndürür.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`CurrentDateTimeOffset()`|Geçerli tarih, saat ve sapmayı bir `DateTimeOffset`olarak döndürür.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|Sunucu, <xref:System.DateTime> saat dilimindeki sunucunun geçerli tarih ve saati olarak bir değer döndürür.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`Day(expression)`|1 ile 31 arasında bir `expression` `Int32` gün bölümünü döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|1 ile 366 arasında bir `expression` `Int32` gün bölümünü döndürür. Bu, artık bir yılın son günü için 366 döndürülür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `DateTime` Veya .`DateTimeOffset`<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffNanoseconds(startExpression,endExpression)`|`startExpression` İle`endExpression`arasında, nanosaniye cinsinden farkı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, veya`DateTimeOffset`. `Time` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMilliseconds(startExpression,endExpression)`|`startExpression` Ve`endExpression`arasında milisaniye cinsinden farkı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, veya`DateTimeOffset`. `Time` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMicroseconds(startExpression,endExpression)`|`startExpression` Ve`endExpression`arasında, mikrosaniye cinsinden farkı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, veya`DateTimeOffset`. `Time` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffSeconds(startExpression,endExpression)`|`startExpression` Ve`endExpression`arasındaki farkı saniye cinsinden döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, veya`DateTimeOffset`. `Time` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMinutes(startExpression,endExpression)`|`startExpression` Ve`endExpression`arasındaki farkı dakika cinsinden döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, veya`DateTimeOffset`. `Time` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffHours(startExpression,endExpression)`|`startExpression` Ve`endExpression`arasında, saat cinsinden farkı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, veya`DateTimeOffset`. `Time` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffDays(startExpression,endExpression)`|`startExpression` Ve`endExpression`arasında, gün cinsinden farkı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya .`DateTimeOffset` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMonths(startExpression,endExpression)`|`startExpression` Ve`endExpression`arasında, ay cinsinden farkı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya .`DateTimeOffset` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffYears(startExpression,endExpression)`|`startExpression` Ve`endExpression`arasında, yıl cinsinden farkı döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya .`DateTimeOffset` **Note:** `startExpression` ve`endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`GetTotalOffsetMinutes(datetimeoffset)`|GMT 'den öteye kaydırılacağı dakika `datetimeoffset` sayısını döndürür. Bu genellikle + 780 ile-780 (+ veya-13 saat) arasında olur. **Not:**  Bu işlev yalnızca SQL Server 2008 ' de desteklenir. <br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`Hour(expression)`|0 ile 23 arasında bir `expression` `Int32` saat bölümünü döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|0 ile 999 arasında bir `expression` `Int32` milisaniye bölümünü döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`Minute(expression)`|0 ile 59 arasında bir `expression` `Int32` dakika bölümünü döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `DateTime, Time` Veya .`DateTimeOffset`<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|1 ile 12 arasında bir `expression` `Int32` ay bölümünü döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `DateTime` Veya .`DateTimeOffset`<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|0 ile 59 `Int32` arasında saniye `expression` kısmını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|`expression`Zaman değerleri kesilme ile değerini döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `DateTime` Veya .`DateTimeOffset`<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`Year(expression)`|' Nin `expression` `Int32` yıl`YYYY`kısmını döndürür.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Bu işlevler, verilen `null` `null` giriş durumunda döndürülür.  
  
 Eşdeğer işlevsellik, Microsoft SQL Istemci tarafından yönetilen sağlayıcıda bulunur. Daha fazla bilgi için bkz. [Entity Framework işlevleri Için SqlClient](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](canonical-functions.md)
