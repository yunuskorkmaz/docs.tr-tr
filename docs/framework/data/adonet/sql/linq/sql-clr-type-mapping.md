---
title: SQL CLR türü eşlemesi
ms.date: 03/30/2017
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 5437529d9293951ad34abda435b538b4f404c600
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365533"
---
# <a name="sql-clr-type-mapping"></a>SQL CLR türü eşlemesi
LINQ-SQL, tercih ettiğiniz programlama dilini ifade edilen bir nesne modeli ilişkisel veritabanı veri modelinin eşler. Uygulama çalıştırıldığında LINQ-SQL dil ile tümleşik sorgu nesne modelinde SQL'e çevirir ve bunları yürütme için veritabanı gönderir. LINQ-SQL veritabanı sonuçları döndürdüğünde, geri kendi programlama dilinde çalışabileceğiniz nesneleri sonuçları çevirir.  
  
 Nesne modeli ve veritabanı arasında veri çevirmek için bir *türü eşlemesi* tanımlanması gerekir. LINQ-SQL türü eşlemesi her ortak dil çalışma zamanı (CLR) türü belirli bir SQL Server türü ile eşleşecek şekilde kullanır. Tür eşlemeleri ve öznitelik tabanlı eşleme ile nesne modeli içindeki veritabanı yapısı ve tablo ilişkileri gibi diğer eşleme bilgilerini tanımlayabilirsiniz. Alternatif olarak, bir dış eşleme dosyası ile nesne modeli dışında eşleme bilgilerini belirtebilirsiniz. Daha fazla bilgi için bkz: [öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) ve [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 Bu konu, aşağıdaki noktaları ele alınmıştır:  
  
-   [Varsayılan türü eşlemesi](#DefaultTypeMapping)  
  
-   [Çalışma zamanı davranışını matris eşleme türü](#BehaviorMatrix)  
  
-   [CLR ve SQL yürütmesi arasındaki davranış farklılıkları](#BehaviorDiffs)  
  
-   [Enum eşleme](#EnumMapping)  
  
-   [Sayısal eşleme](#NumericMapping)  
  
-   [Metin ve XML eşleme](#TextMapping)  
  
-   [Tarih ve saat eşleme](#DateMapping)  
  
-   [İkili eşleme](#BinaryMapping)  
  
-   [Çeşitli eşleme](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## <a name="default-type-mapping"></a>Varsayılan türü eşlemesi  
 Nesne modeli veya dış eşleme dosyası otomatik olarak Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) veya SQLMetal komut satırı aracı ile oluşturabilirsiniz. Bu araçlar için varsayılan türü eşlemeleri hangi CLR Türleri SQL Server veritabanı içinde sütunları eşlemek için seçilen tanımlayın. Bu araçları kullanma hakkında daha fazla bilgi için bkz: [nesne modeli oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md).  
  
 Aynı zamanda <xref:System.Data.Linq.DataContext.CreateDatabase%2A> nesne modeli veya dış eşleme dosyası eşleme bilgilerini temel bir SQL Server veritabanı oluşturmak için yöntem. İçin varsayılan türü eşlemelerini <xref:System.Data.Linq.DataContext.CreateDatabase%2A> yöntemi tanımlayın hangi tür sütunlar için CLR eşlemek için oluşturulan SQL sunucusu nesne modelinde türleri. Daha fazla bilgi için bkz: [nasıl yapılır: dinamik olarak bir veritabanı oluşturmak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
<a name="BehaviorMatrix"></a>   
## <a name="type-mapping-run-time-behavior-matrix"></a>Çalışma zamanı davranışını matris eşleme türü  
 Aşağıdaki diyagramda, veri kaynağından alınan belirli türü eşlemeleri beklenen çalışma zamanı davranışını gösterir veya veritabanına kaydedilir. Seri hale getirme hariç olmak üzere, bu Matris belirtilmemiş türler herhangi bir CLR veya SQL Server veri arasında eşleme LINQ-SQL desteklemez. Seri hale getirme desteği hakkında daha fazla bilgi için bkz: [ikili seri hale getirme](#BinarySerialization).  
  
> [!NOTE]
>  Bazı türü eşlemeleri taşması veya veri kaybı durumlar için veya veritabanından çevrilirken neden olabilir.  
  
### <a name="custom-type-mapping"></a>Özel tür eşleme  
 İle LINQ-SQL, SQLMetal, O/R tasarımcısı tarafından kullanılan varsayılan türü eşlemeleri bununla sınırlı değildir ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A> yöntemi. Açıkça bunları DBML dosyasında belirterek özel tür eşlemeleri oluşturabilirsiniz. Ardından nesne modeli kodu ve eşleme dosyasını oluşturmak için bu DBML dosyasını kullanabilirsiniz. Daha fazla bilgi için bkz: [SQL CLR özel türü eşlemeleri](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>   
## <a name="behavior-differences-between-clr-and-sql-execution"></a>CLR ve SQL yürütmesi arasındaki davranış farklılıkları  
 Farklılıkları nedeniyle duyarlık ve yürütme CLR ve SQL Server arasında farklı sonuçlar almak veya burada, hesaplamalar bağlı olarak farklı davranışlarla karşılaşabilirsiniz. SQL sorguları LINQ gerçekleştirilen hesaplamalar gerçekte Transact-SQL çevrilen ve sonra SQL Server veritabanı üzerinde yürütülür. SQL sorguları LINQ dışında gerçekleştirilen hesaplamalar CLR bağlamı içinde çalıştırılır.  
  
 Örneğin, bazı CLR ve SQL Server arasındaki davranış farklılıkları şunlardır:  
  
-   Bazı veri türleri, SQL Server CLR veri eşdeğer türü farklı bir biçimde sıralar. Örneğin, SQL Server veri türündeki `UNIQUEIDENTIFIER` CLR veri türü'den farklı sıralı <xref:System.Guid?displayProperty=nameWithType>.  
  
-   SQL Server bazı dize karşılaştırma işlemlerini CLR farklı şekilde işler. SQL Server harmanlama ayarları sunucuda dize karşılaştırma davranışı bağlıdır. Daha fazla bilgi için bkz: [harmanlamaları ile çalışma](http://go.microsoft.com/fwlink/?LinkId=115330) Microsoft SQL Server Books Online.  
  
-   SQL Server CLR daha eşlenen bazı işlevler için farklı değerler döndürebilir. Örneğin, SQL Server yalnızca sondaki boşluk farklıysa eşit olacak şekilde iki dizeyi algıladığından eşitlik işlevlerini farklılık gösterir; CLR eşit olmaması için göz önünde bulundurur ise.  
  
<a name="EnumMapping"></a>   
## <a name="enum-mapping"></a>Enum eşleme  
 LINQ-SQL destekleyen CLR eşleme <xref:System.Enum?displayProperty=nameWithType> iki yolla SQL Server türlerine türü:  
  
-   SQL sayısal türler için eşleme (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)  
  
     Bir CLR eşlediğinizde <xref:System.Enum?displayProperty=nameWithType> türü sayısal bir SQL türü için CLR temel tamsayı değerini harita <xref:System.Enum?displayProperty=nameWithType> için SQL Server veritabanı sütununun değeri. Örneğin, bir <xref:System.Enum?displayProperty=nameWithType> adlı `DaysOfWeek` adlı bir üye içeriyor `Tue` temel tamsayı değerini 3 ile bu üye 3 veritabanı değerine eşler.  
  
-   SQL metin türler için eşleme (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)  
  
     Bir CLR eşlediğinizde <xref:System.Enum?displayProperty=nameWithType> SQL metin türüne, SQL veritabanı değeri türü, CLR adlarına eşlendiği <xref:System.Enum?displayProperty=nameWithType> üyeleri. Örneğin, bir <xref:System.Enum?displayProperty=nameWithType> adlı `DaysOfWeek` adlı bir üye içeriyor `Tue` temel tamsayı değerini 3 ile bu üye veritabanı değerine eşleyen `Tue`.  
  
> [!NOTE]
>  SQL metin türleri bir CLR eşlerken <xref:System.Enum?displayProperty=nameWithType>, yalnızca adlarını dahil <xref:System.Enum> eşlenen SQL sütun üyeleri. Diğer değerler desteklenmez <xref:System.Enum>-SQL sütun eşlenmiş.  
  
 O/R Tasarımcısı ve SQLMetal komut satırı aracı, otomatik olarak bir SQL türü bir CLR eşlenemiyor <xref:System.Enum> sınıfı. Bu eşleme SQLMetal ve O/R tasarımcısı tarafından kullanılmak üzere DBML dosyasını özelleştirerek açıkça yapılandırmanız gerekir. Özel tür eşlemesi hakkında daha fazla bilgi için bkz: [SQL CLR özel türü eşlemeleri](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-custom-type-mappings.md).  
  
 Numaralandırma için hedeflenen SQL sütun diğer sayısal ve metin sütunları aynı türde olduğundan; Bu araçlar, hedefi ve varsayılan eşleme için aşağıda açıklandığı gibi tanımaz [sayısal eşleme](#NumericMapping) ve [metin ve XML eşleme](#TextMapping) bölümler. DBML dosyasıyla kod oluşturma hakkında daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi, bir SQL sütun bir CLR eşlemek için sayısal türde oluşturur <xref:System.Enum?displayProperty=nameWithType> türü.  
  
<a name="NumericMapping"></a>   
## <a name="numeric-mapping"></a>Sayısal eşleme  
 LINQ-SQL birçok CLR ve SQL Server sayısal türler eşlemenize olanak sağlar. Aşağıdaki tabloda, O/R Tasarımcısı ve SQLMetal bir nesne modeli veya dış eşleme dosyası, veritabanını temel alan oluştururken seçin CLR Türleri gösterilmektedir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
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
  
 Sonraki tabloda tarafından kullanılan varsayılan türü eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi SQL sütun türünü tanımlamak için nesne modeli veya dış eşleme dosyası içinde tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
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
  
 Seçebileceğiniz birçok diğer sayısal eşlemeleri vardır, ancak bazı taşması veya veri kaybı özel durumlar için veya veritabanından çevrilirken neden olabilir. Daha fazla bilgi için bkz: [türü eşleme çalıştırma zamanı davranışı matris](#BehaviorMatrix).  
  
### <a name="decimal-and-money-types"></a>Ondalık ve para türleri  
 SQL Server'ın varsayılan duyarlık `DECIMAL` türü (18 ondalık basamak sola ve ondalık konumun sağında) CLR duyarlık çok daha küçük olan <!--zz <xref:System.Decima?displayProperty=nameWithType>l --> `Decimal` onu ile varsayılan olarak eşleştirilmiş türü. Veritabanına veri kaydettiğinizde bu duyarlık kaybına neden olabilir. Ancak, yalnızca karşıtı durum SQL Server `DECIMAL` türü duyarlık 29 basamağa büyük ile yapılandırılır. Bir SQL Server zaman `DECIMAL` türü, CLR daha büyük bir duyarlılık ile yapılandırılmış <xref:System.Decimal?displayProperty=nameWithType>, verileri veritabanından alırken duyarlık kaybı oluşabilir.  
  
 SQL Server `MONEY` ve `SMALLMONEY` de CLR ile eşleştirilmiş türleri <xref:System.Decimal?displayProperty=nameWithType> türü varsayılan olarak, veriler veritabanına kaydedilirken taşması veya veri kaybı durumlar sonucunda bir kadar küçük duyarlık sahip.  
  
<a name="TextMapping"></a>   
## <a name="text-and-xml-mapping"></a>Metin ve XML eşleme  
 Ayrıca vardır birçok metin tabanlı ve LINQ-SQL ile eşleyebilirsiniz XML türleri. Aşağıdaki tabloda, O/R Tasarımcısı ve SQLMetal bir nesne modeli veya dış eşleme dosyası, veritabanını temel alan oluştururken seçin CLR Türleri gösterilmektedir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan türü eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi SQL sütun türünü tanımlamak için nesne modeli veya dış eşleme dosyası içinde tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Özel tür uygulama `Parse()` ve `ToString()`|`NVARCHAR(MAX)`|  
  
 Birçok diğer metin tabanlı vardır ve XML eşlemeleri seçtiğiniz, ancak bazı taşması veya veri kaybı özel durumlar için veya veritabanından çevrilirken neden olabilir. Daha fazla bilgi için bkz: [türü eşleme çalıştırma zamanı davranışı matris](#BehaviorMatrix).  
  
### <a name="xml-types"></a>XML türleri  
 SQL Server `XML` veri türü olan Microsoft SQL Server 2005'ten başlayarak kullanılabilir. SQL Server eşleyebilirsiniz `XML` veri türü için <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, veya <xref:System.String>. Sütun halinde okunamıyor XML parçaları depolar, <xref:System.Xml.Linq.XElement>, sütunu eşlenmelidir <xref:System.String> çalışma zamanı hataları önlemek için. Eşlenmelidir XML parçaları <xref:System.String> şunları içerir:  
  
-   Bir dizi XML öğeleri  
  
-   Öznitelikler  
  
-   Ortak tanımlayıcıları (PI)  
  
-   Açıklamalar  
  
 Harita ancak <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> gösterildiği gibi SQL Server [türü eşleme çalıştırma zamanı davranışı matris](#BehaviorMatrix), <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi şu türler için hiçbir varsayılan SQL Server türü eşleme sahiptir.  
  
### <a name="custom-types"></a>Özel türler  
 Bir sınıf uyguluyorsa `Parse()` ve `ToString()`, herhangi bir SQL metin türüne nesne eşleyebilirsiniz (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`). Nesne tarafından döndürülen değer göndererek veritabanında depolanan `ToString()` eşlenen veritabanı sütunu için. Nesne çağırarak oluşturulduğunu `Parse()` veritabanı tarafından döndürülen dize üzerinde.  
  
> [!NOTE]
>  LINQ-SQL desteklemiyor serileştirme kullanarak <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.  
  
<a name="DateMapping"></a>   
## <a name="date-and-time-mapping"></a>Tarih ve saat eşleme  
 İle LINQ-SQL birçok SQL Server tarih ve saat türlerini eşleyebilirsiniz. Aşağıdaki tabloda, O/R Tasarımcısı ve SQLMetal bir nesne modeli veya dış eşleme dosyası, veritabanını temel alan oluştururken seçin CLR Türleri gösterilmektedir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan türü eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi SQL sütun türünü tanımlamak için nesne modeli veya dış eşleme dosyası içinde tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Seçebileceğiniz birçok diğer tarih ve saat eşlemeleri vardır, ancak bazı taşması veya veri kaybı özel durumlar için veya veritabanından çevrilirken neden olabilir. Daha fazla bilgi için bkz: [türü eşleme çalıştırma zamanı davranışı matris](#BehaviorMatrix).  
  
> [!NOTE]
>  SQL Server türleri `DATETIME2`, `DATETIMEOFFSET`, `DATE`, ve `TIME` Microsoft SQL Server 2008 ile başlayarak kullanılabilir. LINQ-SQL .NET Framework sürüm 3.5 SP1 ile başlayarak bu yeni türler için eşleme destekler.  
  
### <a name="systemdatetime"></a>System.Datetime  
 Aralık ve CLR kesinliğini <xref:System.DateTime?displayProperty=nameWithType> türü aralık ve SQL Server'ın duyarlık büyük olan `DATETIME` türü, hangi olan varsayılan türünü eşlemek için <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi. Tarih aralığı dışında ilgili özel durumları önlemeye yardımcı olmak için `DATETIME`, kullanmak `DATETIME2`, Microsoft SQL Server 2008 ile başlayarak kullanılabilir olduğu. `DATETIME2` Aralık ve CLR kesinliğini eşleştirebilirsiniz <xref:System.DateTime?displayProperty=nameWithType>.  
  
 SQL Server tarihleri kavramına sahip <xref:System.TimeZone>, CLR zengin desteklenen bir özellik. <xref:System.TimeZone> değerleri veritabanı olarak kaydedilir <xref:System.TimeZone> özgün bakılmaksızın dönüştürme <xref:System.DateTimeKind> bilgi. Zaman <xref:System.DateTime> değerleri veritabanından alınır, değerlerine içine olarak yüklenen bir <xref:System.DateTime> ile bir <xref:System.DateTimeKind> , <xref:System.DateTimeKind.Unspecified>. Hakkında daha fazla bilgi için desteklenen <xref:System.DateTime?displayProperty=nameWithType> yöntemleri bkz [System.DateTime yöntemleri](../../../../../../docs/framework/data/adonet/sql/linq/system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  
 Microsoft SQL Server 2008 ve .NET Framework 3.5 SP1 CLR eşlemenize olanak <xref:System.TimeSpan?displayProperty=nameWithType> türü SQL Server `TIME` türü. Ancak, aralık arasında büyük farklar yoktur, CLR <xref:System.TimeSpan?displayProperty=nameWithType> destekler ve hangi SQL Server `TIME` yazın destekler. Değerler 0'den küçük ya da 23:59:59.9999999 saatten büyük SQL eşleme `TIME` taşma özel duruma neden olur. Daha fazla bilgi için bkz: [System.TimeSpan yöntemleri](../../../../../../docs/framework/data/adonet/sql/linq/system-timespan-methods.md).  
  
 Microsoft SQL Server 2000 ve SQL Server 2005'te veritabanı alanlarına eşlenemiyor <xref:System.TimeSpan>. Ancak, üzerinde işlem <xref:System.TimeSpan> olduğundan desteklenmektedir <xref:System.TimeSpan> değerleri gelen döndürülmesi <xref:System.DateTime> çıkarma veya değişmez değer veya bağlı bir değişken olarak bir ifade halinde sunulan.  
  
<a name="BinaryMapping"></a>   
## <a name="binary-mapping"></a>İkili eşleme  
 CLR türü eşleyebilirsiniz birçok SQL Server tür vardır <xref:System.Data.Linq.Binary?displayProperty=nameWithType>. O/R Tasarımcısı ve SQLMetal bir CLR tanımlamak neden SQL Server türleri aşağıdaki tabloda gösterilmektedir <xref:System.Data.Linq.Binary?displayProperty=nameWithType> , veritabanını temel alan bir nesne modeli veya dış eşleme dosyası oluşturma zaman yazın.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)` ile `FILESTREAM` özniteliği|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan türü eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi SQL sütun türünü tanımlamak için nesne modeli veya dış eşleme dosyası içinde tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Seçebileceğiniz birçok diğer ikili eşlemeleri vardır, ancak bazı taşması veya veri kaybı özel durumlar için veya veritabanından çevrilirken neden olabilir. Daha fazla bilgi için bkz: [türü eşleme çalıştırma zamanı davranışı matris](#BehaviorMatrix).  
  
### <a name="sql-server-filestream"></a>SQL Server FILESTREAM  
 `FILESTREAM` İçin öznitelik `VARBINARY(MAX)` sütunları Microsoft SQL Server 2008 ile başlayarak kullanılabilir; kendisine LINQ-SQL .NET Framework sürüm 3.5 SP1 ile başlayarak ile eşleyebilirsiniz.  
  
 Harita ancak `VARBINARY(MAX)` sütunlarla `FILESTREAM` özniteliğini <xref:System.Data.Linq.Binary> nesneleri <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi, sütunlarla otomatik olarak oluşturamıyor `FILESTREAM` özniteliği. Hakkında daha fazla bilgi için `FILESTREAM`, bkz: [FILESTREAM genel bakış](http://go.microsoft.com/fwlink/?LinkId=115291) üzerinde Microsoft SQL Server Books Online.  
  
<a name="BinarySerialization"></a>   
### <a name="binary-serialization"></a>İkili seri hale getirme  
 Bir sınıf uyguluyorsa <xref:System.Runtime.Serialization.ISerializable> arabirimi, herhangi bir SQL ikili alan bir nesneyi serileştirebilen (`BINARY`, `VARBINARY`, `IMAGE`). Nesne seri hale getirilmiş ve göre nasıl seri <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulanır. Daha fazla bilgi için bkz: [ikili seri hale getirme](http://go.microsoft.com/fwlink/?LinkId=115581).  
  
<a name="MiscMapping"></a>   
## <a name="miscellaneous-mapping"></a>Çeşitli eşleme  
 Aşağıdaki tabloda değil henüz belirtilmiş olan çeşitli bazı türleri için varsayılan türü eşlemeler gösterilmektedir. Aşağıdaki tabloda, O/R Tasarımcısı ve SQLMetal bir nesne modeli veya dış eşleme dosyası, veritabanını temel alan oluştururken seçin CLR Türleri gösterilmektedir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 Sonraki tabloda tarafından kullanılan varsayılan türü eşlemeleri gösterir <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi SQL sütun türünü tanımlamak için nesne modeli veya dış eşleme dosyası içinde tanımlanan CLR türlerine eşlemek için oluşturulur.  
  
|CLR türü|Varsayılan SQL Server tarafından kullanılan türü <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ-SQL bu çeşitli türleri için başka bir tür eşlemeleri desteklemez.  Daha fazla bilgi için bkz: [türü eşleme çalıştırma zamanı davranışı matris](#BehaviorMatrix).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelik Tabanlı Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Dış Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [SQL-CLR Tür Uyumsuzlukları](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)
