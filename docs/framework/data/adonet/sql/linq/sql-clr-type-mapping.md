---
title: SQL-CLR tür eşlemesi
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: d5c0072d8561efa1211de191a1f2b6f3a1e55b7b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532447"
---
# <a name="sql-clr-type-mapping"></a>SQL-CLR tür eşlemesi
LINQ to SQL'de, ilişkisel veritabanı veri modeli, kendi seçtiğiniz programlama dilinde ifade nesne modeli eşlenir. Uygulama çalışırken, LINQ to SQL nesne modeli dil ile tümleşik sorgu SQL'e çevirir ve bunları yürütme için veritabanı gönderir. Veritabanı sonuçları döndürdüğünde, LINQ to SQL geri kendi programlama dilinde çalışabileceğiniz nesneleri sonuçları çevirir.  
  
 Nesne modeli ve veritabanı arasında veri çevirmek için bir *tür eşlemesi* tanımlanması gerekir. LINQ to SQL her ortak dil çalışma zamanı (CLR) türü belirli bir SQL Server türü ile eşleşecek şekilde tür eşlemesi kullanır. Tür eşlemeleri ve öznitelik tabanlı eşleme ile nesne modeli içinde veritabanı yapısı ve tablo ilişkileri gibi diğer eşleme bilgilerini tanımlayabilirsiniz. Alternatif olarak, bir dış eşleme dosyası ile nesne modelini dış eşleme bilgilerini belirtebilirsiniz. Daha fazla bilgi için [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) ve [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Bu konu, aşağıdaki noktaları açıklar:  
  
-   [Varsayılan tür eşlemesi](#DefaultTypeMapping)  
  
-   [Çalışma zamanı davranışını matris eşleme türü](#BehaviorMatrix)  
  
-   [CLR ve SQL yürütmesi arasındaki davranış farklılıkları](#BehaviorDiffs)  
  
-   [Enum eşleme](#EnumMapping)  
  
-   [Sayısal eşleme](#NumericMapping)  
  
-   [Metin ve XML eşleme](#TextMapping)  
  
-   [Tarih ve saat eşleme](#DateMapping)  
  
-   [İkili eşleme](#BinaryMapping)  
  
-   [Çeşitli eşleme](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## <a name="default-type-mapping"></a>Varsayılan tür eşlemesi  
 Nesne modeli veya dış eşleme dosyası otomatik olarak Object Relational Designer (O/R Tasarımcısı) veya SQLMetal komut satırı aracı ile oluşturabilirsiniz. Bu araçlar için varsayılan tür eşlemeleri hangi CLR türleri, SQL Server veritabanı içindeki sütunlara eşlemek için seçilir tanımlayın. Bu araçları kullanma hakkında daha fazla bilgi için bkz. [nesne modeli oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md).  
  
 Ayrıca <xref:System.Data.Linq.DataContext.CreateDatabase%2A> nesne modeli veya dış eşleme dosyası eşleme bilgileri temel SQL Server veritabanı oluşturmak için yöntemi. İçin varsayılan türü eşlemelerini <xref:System.Data.Linq.DataContext.CreateDatabase%2A> yöntemi tanımlayan nesne modelinde sütunları CLR ile eşlemek için oluşturulan SQL Server'ın hangi tür türleri. Daha fazla bilgi için [nasıl yapılır: dinamik olarak veritabanı oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>   
## <a name="type-mapping-run-time-behavior-matrix"></a>Çalışma zamanı davranışını matris eşleme türü  
 Aşağıdaki diyagramda, veri hizmetinden alınan belirli türde eşlemeler beklenen çalışma zamanı davranışını gösterir veya veritabanına kaydedilir. Seri hale getirme hariç olmak üzere, LINQ to SQL bu Matristeki belirtilmemiş türler herhangi bir CLR veya SQL Server veri arasında eşleme desteklemez. Serileştirme desteği hakkında daha fazla bilgi için bkz. [ikili serileştirme](#BinarySerialization).  
 
![SQL Server için SQL CLR veri türü eşlemesi tablosu](media/sql-clr-type-mapping.png)

> [!NOTE]
>  Bazı tür eşlemeleri için veya veritabanından çevrilirken taşması veya veri kaybı durumlar neden olabilir.  
  
### <a name="custom-type-mapping"></a>Özel tür eşlemesi  
 LINQ to SQL ile siz SQLMetal, O/R tasarımcısı tarafından kullanılan varsayılan türü eşlemeleri sınırlı değildir ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A> yöntemi. Özel tür eşlemeleri açıkça bunları bir DBML dosyasına belirterek oluşturabilirsiniz. Ardından nesne modeli kod ve eşleme dosyasını oluşturmak için bu DBML dosyasını kullanabilirsiniz. Daha fazla bilgi için [SQL-CLR özel tür eşlemeleri](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>   
## <a name="behavior-differences-between-clr-and-sql-execution"></a>CLR ve SQL yürütmesi arasındaki davranış farklılıkları  
 CLR ve SQL Server arasındaki duyarlık ve yürütme farklar nedeniyle, farklı sonuçlar almak veya burada, hesaplamalar bağlı olarak farklı davranışlarla karşılaşabilirsiniz. LINQ to SQL sorguları hesaplamaların gerçekten Transact-SQL çevrilir ve sonra SQL Server veritabanı üzerinde yürütülür. SQL sorguları dışında LINQ hesaplamaların CLR bağlamı içinde yürütülür.  
  
 Örneğin, bazı CLR ve SQL Server arasındaki davranış farklılıkları şunlardır:  
  
-   Bazı veri türleri, SQL Server CLR içinde veri eşdeğer türü farklı sıralar. Örneğin, SQL Server veri türü `UNIQUEIDENTIFIER` CLR veri türünde farklı sıralı <xref:System.Guid?displayProperty=nameWithType>.  
  
-   SQL Server CLR farklı bazı dize karşılaştırma işlemleri gerçekleştirir. SQL Server harmanlama ayarları sunucuda dizesi karşılaştırma davranışı bağlıdır. Daha fazla bilgi için [harmanlamaları ile çalışma](https://go.microsoft.com/fwlink/?LinkId=115330) Microsoft SQL Server Books Online.  
  
-   SQL Server CLR daha eşlenen bazı işlevler için farklı değerler döndürebilecek. Örneğin, SQL Server yalnızca sondaki boşluk farklıysa eşit olacak şekilde iki dizeyi varsaydığı eşitlik işlevleri değişir; CLR bunları eşit olmaması göz önünde bulundurur ise.  
  
<a name="EnumMapping"></a>   
## <a name="enum-mapping"></a>Enum eşleme  
 LINQ to SQL destekleyen CLR eşleme <xref:System.Enum?displayProperty=nameWithType> iki yolla SQL Server türlerine türü:  
  
-   SQL sayısal türler için eşleme (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)  
  
     Bir CLR eşlediğinizde <xref:System.Enum?displayProperty=nameWithType> türü SQL sayısal tür için CLR temel tamsayı değerini harita <xref:System.Enum?displayProperty=nameWithType> için SQL Server veritabanı sütununun değeri. Örneğin, bir <xref:System.Enum?displayProperty=nameWithType> adlı `DaysOfWeek` adlı bir üyeyi içeren `Tue` bir arka plandaki tamsayı değeriyle 3, 3'ün bir veritabanı değere üyenin eşler.  
  
-   SQL metin türleriyle eşleme (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)  
  
     Bir CLR eşlediğinizde <xref:System.Enum?displayProperty=nameWithType> SQL metin türü, SQL veritabanı değer türüne CLR adlarına eşlenen <xref:System.Enum?displayProperty=nameWithType> üyeleri. Örneğin, bir <xref:System.Enum?displayProperty=nameWithType> adlı `DaysOfWeek` adlı bir üyeyi içeren `Tue` arka plandaki tamsayı değerini 3 ile bu üye veritabanı değerine eşleyen `Tue`.  
  
> [!NOTE]
>  Bir CLR SQL metin türleri eşlerken <xref:System.Enum?displayProperty=nameWithType>, yalnızca adları dahil <xref:System.Enum> eşlenen SQL sütunda üyeleri. Diğer değerleri desteklenmez <xref:System.Enum>-SQL sütunu.  
  
 O/R Tasarımcısı ve SQLMetal komut satırı aracı, otomatik olarak bir SQL türü için bir CLR eşlenemez <xref:System.Enum> sınıfı. SQLMetal ve O/R tasarımcısı tarafından kullanılmak üzere bir DBML dosyasını özelleştirerek bu eşleme açıkça yapılandırmanız gerekir. Özel tür eşlemesi hakkında daha fazla bilgi için bkz: [SQL-CLR özel tür eşlemeleri](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
 Sabit listesi için hedeflenen SQL sütun, aynı türde diğer sayısal ve metin sütunları olacağından; Bu araçlar, hedefi ve varsayılan eşleme için aşağıda açıklandığı gibi tanımaz [sayısal eşleme](#NumericMapping) ve [metin ve XML eşleme](#TextMapping) bölümler. DBML dosyasıyla kod oluşturma hakkında daha fazla bilgi için bkz. [LINQ to SQL'de kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi oluşturur bir CLR eşlemek için sayısal tür içeren bir SQL sütun <xref:System.Enum?displayProperty=nameWithType> türü.  
  
<a name="NumericMapping"></a>   
## <a name="numeric-mapping"></a>Sayısal eşleme  
 LINQ to SQL CLR ve SQL Server birçok sayısal türler eşlemenize olanak tanır. Aşağıdaki tabloda, O/R Tasarımcısı ve SQLMetal bir nesne modeli veya dış eşleme dosyası, veritabanını temel alan oluştururken seçtiğiniz CLR türlerini gösterir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR tür eşlemesi|  
|---------------------|-----------------------------------------------------------------|  
|`BIT`|<xref:System.Boolean?displayProperty=nameWithType>|  
|`TINYINT`|<xref:System.Int16?displayProperty=nameWithType>|  
|`INT`|<xref:System.Int32?displayProperty=nameWithType>|  
|`BIGINT`|<xref:System.Int64?displayProperty=nameWithType>|  
|`SMALLMONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`MONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`DECIMAL`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`NUMERIC`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`REAL/FLOAT(24)`|<xref:System.Single?displayProperty=nameWithType>|  
|`FLOAT/FLOAT(53)`|<xref:System.Double?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan tür eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> SQL sütun türünü tanımlamak için yöntemi, nesne modeli veya dış eşleme dosyasında tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|`BIT`|  
|<xref:System.Byte?displayProperty=nameWithType>|`TINYINT`|  
|<xref:System.Int16?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.Int32?displayProperty=nameWithType>|`INT`|  
|<xref:System.Int64?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.SByte?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.UInt16?displayProperty=nameWithType>|`INT`|  
|<xref:System.UInt32?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.UInt64?displayProperty=nameWithType>|`DECIMAL(20)`|  
|<xref:System.Decimal?displayProperty=nameWithType>|`DECIMAL(29,4)`|  
|<xref:System.Single?displayProperty=nameWithType>|`REAL`|  
|<xref:System.Double?displayProperty=nameWithType>|`FLOAT`|  
  
 Seçebileceğiniz çok sayıda diğer sayısal eşlemeler bulunur, ancak bazı taşması veya veri kaybı, özel durumlar için veya veritabanından çevrilirken neden olabilir. Daha fazla bilgi için [türü eşleme çalıştırma zamanı davranışını matris](#BehaviorMatrix).  
  
### <a name="decimal-and-money-types"></a>Ondalık ve para türleri  
 SQL Server'ın varsayılan duyarlık `DECIMAL` türü (18 ondalık basamak sola ve Ondalık ayırıcının sağında) CLR duyarlıklı çok daha küçük olan <xref:System.Decimal?displayProperty=nameWithType> bunu ile varsayılan olarak eşleştirilir türü. Bu durum, veri veritabanına kaydederken duyarlık kaybına neden olabilir. Ancak tersi oluşabilir SQL Server `DECIMAL` türü, 29 basamak duyarlılığındadır büyüktür ile yapılandırılır. SQL Server olduğunda `DECIMAL` türü, CLR daha büyük kesinliği ile yapılandırılmış <xref:System.Decimal?displayProperty=nameWithType>, verileri veritabanından alırken duyarlık kaybı meydana gelebilir.  
  
 SQL Server `MONEY` ve `SMALLMONEY` ayrıca CLR ile eşleştirilmiş durumda türleri <xref:System.Decimal?displayProperty=nameWithType> türü varsayılan olarak, verileri veritabanına kaydedilirken taşması veya veri kaybı durumlar sonucunda çok daha küçük kesinliği, vardır.  
  
<a name="TextMapping"></a>   
## <a name="text-and-xml-mapping"></a>Metin ve XML eşleme  
 Ayrıca birçok metin tabanlı ve vardır XML türleri, LINQ to SQL ile eşleyebilirsiniz. Aşağıdaki tabloda, O/R Tasarımcısı ve SQLMetal bir nesne modeli veya dış eşleme dosyası, veritabanını temel alan oluştururken seçtiğiniz CLR türlerini gösterir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR tür eşlemesi|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan tür eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> SQL sütun türünü tanımlamak için yöntemi, nesne modeli veya dış eşleme dosyasında tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Özel tür uygulama `Parse()` ve `ToString()`|`NVARCHAR(MAX)`|  
  
 Birçok diğer metin tabanlı vardır ve XML eşlemeleri seçebilirsiniz, ancak bazı taşması veya veri kaybı, özel durumlar için veya veritabanından çevrilirken neden olabilir. Daha fazla bilgi için [türü eşleme çalıştırma zamanı davranışını matris](#BehaviorMatrix).  
  
### <a name="xml-types"></a>XML türleri  
 SQL Server `XML` veri türü olan Microsoft SQL Server 2005'te başlangıç kullanılabilir. SQL Server eşleyebilirsiniz `XML` veri türü için <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, veya <xref:System.String>. Sütun içine okunamayan parçalarını depolar, <xref:System.Xml.Linq.XElement>, sütuna eşlenmiş olmalıdır <xref:System.String> çalışma zamanı hataları önlemek için. Eşlenmesi gerekir XML parçalarının <xref:System.String> şunları içerir:  
  
-   Bir dizisi XML öğesi  
  
-   Öznitelikler  
  
-   Ortak tanımlayıcıları (PI)  
  
-   Açıklamalar  
  
 Olsa da <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> gösterildiği gibi SQL Server [türü eşleme çalıştırma zamanı davranışını matris](#BehaviorMatrix), <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi olan bu tür için varsayılan SQL Server türü eşleme yok.  
  
### <a name="custom-types"></a>Özel türler  
 Bir sınıf uyguluyorsa `Parse()` ve `ToString()`, herhangi bir SQL metin türü nesne eşleyebilirsiniz (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`). Nesne tarafından döndürülen değer göndererek veritabanında depolanan `ToString()` eşlenen veritabanı sütun. Nesne çağırarak reconstructed `Parse()` üzerinde veritabanı tarafından döndürülen dize.  
  
> [!NOTE]
>  LINQ to SQL desteklemiyor serileştirme kullanarak <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>   
## <a name="date-and-time-mapping"></a>Tarih ve saat eşleme  
 LINQ to SQL ile birçok SQL Server tarih ve saat türlerinin eşleyebilirsiniz. Aşağıdaki tabloda, O/R Tasarımcısı ve SQLMetal bir nesne modeli veya dış eşleme dosyası, veritabanını temel alan oluştururken seçtiğiniz CLR türlerini gösterir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR tür eşlemesi|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan tür eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> SQL sütun türünü tanımlamak için yöntemi, nesne modeli veya dış eşleme dosyasında tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Seçebileceğiniz çok sayıda diğer tarih ve saat eşlemeler bulunur, ancak bazı taşması veya veri kaybı, özel durumlar için veya veritabanından çevrilirken neden olabilir. Daha fazla bilgi için [türü eşleme çalıştırma zamanı davranışını matris](#BehaviorMatrix).  
  
> [!NOTE]
>  SQL Server türleri `DATETIME2`, `DATETIMEOFFSET`, `DATE`, ve `TIME` Microsoft SQL Server 2008 ile başlayan kullanılabilir. LINQ to SQL .NET Framework sürüm 3.5 SP1 ile başlayarak bu yeni türler için eşleme destekler.  
  
### <a name="systemdatetime"></a>System.Datetime  
 Aralık ve duyarlık CLR <xref:System.DateTime?displayProperty=nameWithType> türü, aralık ve duyarlık SQL Server'ın büyük `DATETIME` türü, hangi olan varsayılan eşleme türü için <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi. Tarih aralığının dışında ilgili özel durumları önlemeye yardımcı olmak için `DATETIME`, kullanın `DATETIME2`, Microsoft SQL Server 2008 ile başlayan kullanılabilir olduğu. `DATETIME2` Aralık ve duyarlık CLR eşleşebilir <xref:System.DateTime?displayProperty=nameWithType>.  
  
 SQL Server tarihleri sahip kavramı <xref:System.TimeZone>, CLR içinde desteklenen zengin bir özellik. <xref:System.TimeZone> değerleri olmadan olarak kaydedilir <xref:System.TimeZone> dönüştürme, orijinal bakılmaksızın <xref:System.DateTimeKind> bilgileri. Zaman <xref:System.DateTime> değerleri veritabanından alınır, değerlerine içine olarak yüklenen bir <xref:System.DateTime> ile bir <xref:System.DateTimeKind> , <xref:System.DateTimeKind.Unspecified>. Hakkında daha fazla bilgi için desteklenen <xref:System.DateTime?displayProperty=nameWithType> yöntemleri bkz [System.DateTime yöntemleri](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  
 Microsoft SQL Server 2008 ve .NET Framework 3.5 SP1 CLR eşlemenize izin <xref:System.TimeSpan?displayProperty=nameWithType> türü SQL Server'a `TIME` türü. Ancak, aralığın arasında büyük bir fark yoktur, CLR <xref:System.TimeSpan?displayProperty=nameWithType> destekler ve hangi SQL Server `TIME` yazın destekler. SQL değerleri 0'den küçük ya da 23:59:59.9999999 saatten büyük eşleme `TIME` taşma özel duruma neden olur. Daha fazla bilgi için [System.TimeSpan yöntemleri](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md).  
  
 Microsoft SQL Server 2000 ve SQL Server 2005'te veritabanı alanlarıyla eşleyemezsiniz <xref:System.TimeSpan>. Ancak, işlemleri <xref:System.TimeSpan> desteklenmez <xref:System.TimeSpan> değerleri sağlayıcıdan döndürülen <xref:System.DateTime> çıkarma veya değişmez değer veya ilişkili bir değişkeni olarak bir ifade içinde tanıtılan.  
  
<a name="BinaryMapping"></a>   
## <a name="binary-mapping"></a>İkili eşleme  
 CLR türüne eşleyebilirsiniz çok sayıda SQL Server türü vardır <xref:System.Data.Linq.Binary?displayProperty=nameWithType>. O/R Tasarımcısı ve SQLMetal bir CLR tanımlamak için neden SQL Server türleri aşağıdaki tabloda gösterilmektedir <xref:System.Data.Linq.Binary?displayProperty=nameWithType> veritabanınızda temel bir nesne modeli veya dış eşleme dosyası derleme yazın.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR tür eşlemesi|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)` ile `FILESTREAM` özniteliği|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan tür eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> SQL sütun türünü tanımlamak için yöntemi, nesne modeli veya dış eşleme dosyasında tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Seçebileceğiniz çok sayıda diğer ikili eşlemeler bulunur, ancak bazı taşması veya veri kaybı, özel durumlar için veya veritabanından çevrilirken neden olabilir. Daha fazla bilgi için [türü eşleme çalıştırma zamanı davranışını matris](#BehaviorMatrix).  
  
### <a name="sql-server-filestream"></a>SQL Server FILESTREAM  
 `FILESTREAM` Özniteliğini `VARBINARY(MAX)` sütunları Microsoft SQL Server 2008 ile başlayan kullanılabilir; için LINQ to SQL .NET Framework sürüm 3.5 SP1 ile başlayarak ile eşleyebilirsiniz.  
  
 Olsa da `VARBINARY(MAX)` sütunlarla `FILESTREAM` özniteliğini <xref:System.Data.Linq.Binary> nesneleri <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi, sütunları otomatik olarak oluşturamıyor `FILESTREAM` özniteliği. Hakkında daha fazla bilgi için `FILESTREAM`, bkz: [FILESTREAM genel bakış](https://go.microsoft.com/fwlink/?LinkId=115291) üzerinde Microsoft SQL Server Books Online.  
  
<a name="BinarySerialization"></a>   
### <a name="binary-serialization"></a>İkili seri hale getirme  
 Bir sınıf uyguluyorsa <xref:System.Runtime.Serialization.ISerializable> arabirimi, herhangi bir SQL ikili alan bir nesneyi serileştirip serileştiremeyeceğini (`BINARY`, `VARBINARY`, `IMAGE`). Nesne serileştirilmiş ve seri durumdan göre nasıl <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulanır. Daha fazla bilgi için [ikili serileştirme](https://go.microsoft.com/fwlink/?LinkId=115581).  
  
<a name="MiscMapping"></a>   
## <a name="miscellaneous-mapping"></a>Çeşitli eşleme  
 Aşağıdaki tabloda değil henüz belirtilmiş olan çeşitli bazı türleri için varsayılan tür eşlemeleri gösterir. Aşağıdaki tabloda, O/R Tasarımcısı ve SQLMetal bir nesne modeli veya dış eşleme dosyası, veritabanını temel alan oluştururken seçtiğiniz CLR türlerini gösterir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR tür eşlemesi|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan tür eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> SQL sütun türünü tanımlamak için yöntemi, nesne modeli veya dış eşleme dosyasında tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ to SQL herhangi bir türü eşlemeleri için bu çeşitli türleri desteklemez.  Daha fazla bilgi için [türü eşleme çalıştırma zamanı davranışını matris](#BehaviorMatrix).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelik Tabanlı Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Dış Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [SQL-CLR Tür Uyumsuzlukları](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)
