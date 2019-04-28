---
title: Kurallı Tarih ve Saat İşlevleri
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: 1e54fa3d763fa08d7bafd9b002f0458ec3a6293d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606016"
---
# <a name="date-and-time-canonical-functions"></a>Kurallı Tarih ve Saat İşlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Tarih ve saat kurallı işlevler içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tablo tarih ve saati gösterir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevler. `datetime` olan bir <xref:System.DateTime> değeri.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|Belirtilen ekler `number` nanosaniye için `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`AddMicroseconds(expression,number)`|Belirtilen ekler `number` milisaniyeye, `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`AddMilliseconds(expression,number)`|Belirtilen ekler `number` için milisaniye `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`AddSeconds(expression,number)`|Belirtilen ekler `number` sayısının `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`AddMinutes(expression,number)`|Belirtilen ekler `number` dakika için `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`AddHours(expression,number)`|Belirtilen ekler `number` sayısının `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`AddDays(expression,number)`|Belirtilen ekler `number` gün için `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`AddMonths(expression,number)`|Belirtilen ekler `number` için aylık `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`AddYears(expression,number)`|Belirtilen ekler `number` için yıllık `expression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`CreateDateTime(year,month,day,hour,minute,second)`|Yeni bir `DateTime` değeri geçerli tarih ve saat sunucusunun saat diliminde sunucunun olarak.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `year`, `month`, `day`, `hour`, `minute`: `Int16` ve `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|Yeni bir `DateTimeOffset` geçerli tarih ve saat sunucunun göre Eşgüdümlü Evrensel Saat (UTC) olarak değeri.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTimeOffset`.|  
|`CreateTime(hour,minute,second)`|Yeni bir `Time` değeri olarak geçerli saati.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `hour` ve `minute`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Time`.|  
|`CurrentDateTime()`|Döndürür bir `DateTime` değeri geçerli tarih ve saat sunucusunun saat diliminde sunucunun olarak.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`CurrentDateTimeOffset()`|Geçerli tarih ve saat olarak uzaklığı döndürür bir `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|Döndürür bir <xref:System.DateTime> değeri geçerli tarih ve saat ZGİLERİ saat diliminde sunucunun olarak.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`Day(expression)`|Gün kısmını döndürür `expression` olarak bir `Int32` 1 ile 31 arasında.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|Gün kısmını döndürür `expression` olarak bir `Int32` 1 ile 366 artık yıl son günü için döndürülen burada 366 arasında.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime` veya `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffNanoseconds(startExpression,endExpression)`|Arasındaki farkı, nanosaniye cinsinden döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMilliseconds(startExpression,endExpression)`|Arasındaki fark, milisaniye cinsinden döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMicroseconds(startExpression,endExpression)`|Mikrosaniye, fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffSeconds(startExpression,endExpression)`|Arasındaki farkı saniye cinsinden döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMinutes(startExpression,endExpression)`|Arasındaki farkı dakika cinsinden döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffHours(startExpression,endExpression)`|Arasındaki saat farkı döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffDays(startExpression,endExpression)`|Arasındaki farkı gün cinsinden döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya `DateTimeOffset`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMonths(startExpression,endExpression)`|Arasındaki fark, ay içinde döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya `DateTimeOffset`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffYears(startExpression,endExpression)`|Yıl, farkı arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya `DateTimeOffset`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır. <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`GetTotalOffsetMinutes(datetimeoffset)`|Dakika sayısını döndüren `datetimeoffset` GMT uzaklığı. Bu, genellikle +780 arasında-780. (+ veya - 13 SA). **Not:**  Bu işlev, yalnızca SQL Server 2008'de desteklenir. <br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`Hour(expression)`|Saat bölümünü döndürür `expression` olarak bir `Int32` 0 ile 23 arasında.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|Milisaniye bölümünü döndürür `expression` olarak bir `Int32` 0 ile 999 arasında.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`Minute(expression)`|Dakika kısmını döndürür `expression` olarak bir `Int32` 0 ile 59 arasında.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime, Time` veya `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|Ay kısmını döndürür `expression` olarak bir `Int32` 1 ile 12 arasında.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime` veya `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|Saniyeyi döndürür kısmı `expression` olarak bir `Int32` 0 ile 59 arasında.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|Döndürür `expression`, kesirli kısmı saat değerleri ile.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime` veya `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Türünü `expression`.|  
|`Year(expression)`|Yıl kısmını döndürür `expression` olarak bir `Int32` `YYYY`.<br /><br /> **Bağımsız Değişkenler**<br /><br /> A `DateTime` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Bu işlevler döndüreceği `null` verildiyse `null` giriş.  
  
 Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer bir işlevselliği kullanılabilir. Daha fazla bilgi için [Entity Framework işlevleri için SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
