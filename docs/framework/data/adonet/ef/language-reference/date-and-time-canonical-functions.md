---
title: "Tarih ve saat kurallı işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3ded6b669a5232246e2878ea26d3116774aea532
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="date-and-time-canonical-functions"></a>Tarih ve saat kurallı işlevleri
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]Tarih ve saat kurallı işlevler içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki tablo tarih ve saati gösterir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kurallı işlevleri. `datetime`olan bir <xref:System.DateTime> değeri.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|`AddNanoseconds(` `expression`, `number``)`|Belirtilen ekler `number` nanosaniye için `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddMicroseconds(` `expression`, `number``)`|Belirtilen ekler `number` milisaniyeye, `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddMilliseconds(` `expression`, `number``)`|Belirtilen ekler `number` için milisaniye olarak `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddSeconds(` `expression`, `number``)`|Belirtilen ekler `number` saniye için `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddMinutes(` `expression`, `number``)`|Belirtilen ekler `number` dakika için `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddHours(` `expression`, `number``)`|Belirtilen ekler `number` için saat `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, veya `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddDays(` `expression`, `number``)`|Belirtilen ekler `number` gün için `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddMonths(` `expression`, `number``)`|Belirtilen ekler `number` için aylık `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`AddYears(` `expression`, `number``)`|Belirtilen ekler `number` için yıllık `expression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `expression`: `DateTime` veya `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`CreateDateTime(` `year`, `month`, `day`, `hour`, `minute`, `second``)`|Yeni bir döndürür `DateTime` değeri geçerli tarih ve saat sunucunun saat diliminde sunucunun olarak.<br /><br /> **Bağımsız değişkenler**<br /><br /> `year`, `month`, `day`, `hour`, `minute`: `Int16` ve `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`CreateDateTimeOffset(` `year`, `month`, `day`, `hour`, `minute`, `second`, `tzoffset``)`|Yeni bir döndürür `DateTimeOffset` değeri olarak geçerli tarih ve saat sunucunun göre Eşgüdümlü Evrensel Saat (UTC).<br /><br /> **Bağımsız değişkenler**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTimeOffset`.|  
|`CreateTime(` `hour`, `minute`, `second``)`|Yeni bir döndürür `Time` değeri geçerli saati olarak.<br /><br /> **Bağımsız değişkenler**<br /><br /> `hour`ve `minute`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Dönüş değeri**<br /><br /> A `Time`.|  
|`CurrentDateTime()`|Döndürür bir `DateTime` değeri geçerli tarih ve saat sunucunun saat diliminde sunucunun olarak.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`CurrentDateTimeOffset()`|Geçerli tarih, saat ve uygun şekilde döndüren bir `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|Döndürür bir <xref:System.DateTime> değeri geçerli tarih ve saat ZGİLERİ saat diliminde sunucunun olarak.<br /><br /> **Dönüş değeri**<br /><br /> A `DateTime`.|  
|`Day(` `expression` `)`|Gün kısmını döndürür `expression` olarak bir `Int32` 1 ile 31 arasında.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(` `expression` `)`|Gün kısmını döndürür `expression` olarak bir `Int32` 1 ile 366 artık yıl son gündür döndürülen burada 366 arasında.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime` veya `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffNanoseconds(` `startExpression`, `endExpression``)`|Nanosaniye, fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMilliseconds(` `startExpression`, `endExpression``)`|Milisaniye cinsinden fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMicroseconds(` `startExpression`, `endExpression``)`|Mikrosaniye, fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffSeconds(` `startExpression`, `endExpression``)`|Saniye cinsinden fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMinutes(` `startExpression`, `endExpression``)`|Dakika cinsinden fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffHours(` `startExpression`, `endExpression``)`|Saat olarak fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, veya `Time`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffDays(` `startExpression`, `endExpression``)`|Gün cinsinden fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya `DateTimeOffset`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffMonths(` `startExpression`, `endExpression``)`|Ay içinde fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya `DateTimeOffset`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`DiffYears(` `startExpression`, `endExpression``)`|Yıllarda fark arasında döndürür `startExpression` ve `endExpression`.<br /><br /> **Bağımsız değişkenler**<br /><br /> `startExpression`, `endExpression`: `DateTime` veya `DateTimeOffset`. **Not:** `startExpression` ve `endExpression` aynı türde olmalıdır.   <br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`GetTotalOffsetMinutes(` `datetimeoffset` `)`|Dakika sayısını döndürür `datetimeoffset` GMT uzaklığı. Bu, genellikle +780 ve-780 arasında. (+ veya - 13 SA). **Not:** bu işlev yalnızca SQL Server 2008'de desteklenir. <br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`Hour (` `expression` `)`|Saat bölümünü döndürür `expression` olarak bir `Int32` 0 ile 23 arasında.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(` `expression` `)`|Milisaniye bölümünü döndürür `expression` olarak bir `Int32` 0-999 arasında.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.|  
|`Minute(` `expression` `)`|Dakika kısmını döndürür `expression` olarak bir `Int32` 0 ile 59 arasında.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime, Time` veya `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month``(``expression``)`|Ay bölümünü döndürür `expression` olarak bir `Int32` 1 ile 12 arasında.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime` veya `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(` `expression` `)`|Saniyeyi döndürür kısmı `expression` olarak bir `Int32` 0 ile 59 arasında.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime, Time` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(` `expression` `)`|Döndürür `expression`, kesilmiş saat değerleri ile.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime` veya `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Türü `expression`.|  
|`Year(` `expression` `)`|Yıl kısmını döndürür `expression` olarak bir `Int32``YYYY`.<br /><br /> **Bağımsız değişkenler**<br /><br /> A `DateTime` ve `DateTimeOffset`.<br /><br /> **Dönüş değeri**<br /><br /> Bir `Int32`.<br /><br /> **Örnek**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Bu işlevler döndürülecek `null` verildiyse `null` giriş.  
  
 Microsoft SQL istemci yönetilen sağlayıcısında eşdeğer işlevselliği kullanılabilir. Daha fazla bilgi için bkz: [SqlClient Entity Framework işlevleri için](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
