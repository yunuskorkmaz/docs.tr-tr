---
title: SQL-CLR Tür Eşlemesi
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 336732e0fe7ca8955702d325309db6a8e61b1722
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174543"
---
# <a name="sql-clr-type-mapping"></a>SQL-CLR Tür Eşlemesi
LINQ'dan SQL'e, ilişkisel bir veritabanının veri modeli seçtiğiniz programlama dilinde ifade edilen bir nesne modeliyle eşlenir. Uygulama çalıştığında, LINQ to SQL nesne modelindeki dil tümleşik sorgularını SQL'e çevirir ve yürütme için veritabanına gönderir. Veritabanı sonuçları döndürdüğünde, LINQ to SQL sonuçları kendi programlama dilinizde çalışabileceğiniz nesnelere geri çevirir.  
  
 Nesne modeli ve veritabanı arasında veri çevirmek için bir *tür eşleme* tanımlanmalıdır. LINQ to SQL, belirli bir SQL Server türüyle her ortak dil çalışma zamanı (CLR) türünü eşleştirmek için bir tür eşlemi kullanır. Öznitelik tabanlı eşleme yle nesne modelinin içinde tür eşlemeleri ve veritabanı yapısı ve tablo ilişkileri gibi diğer eşleme bilgilerini tanımlayabilirsiniz. Alternatif olarak, dış eşleme dosyasıyla nesne modelinin dışındaki eşleme bilgilerini belirtebilirsiniz. Daha fazla bilgi için [bkz.](attribute-based-mapping.md) [External Mapping](external-mapping.md)  
  
 Bu konu aşağıdaki noktaları tartışır:  
  
- [Varsayılan Tür Eşleme](#DefaultTypeMapping)  
  
- [Tür Eşleme Çalışma Zamanı Davranış Matrisi](#BehaviorMatrix)  
  
- [CLR ve SQL Yürütme Arasındaki Davranış Farkları](#BehaviorDiffs)  
  
- [Enum Haritalama](#EnumMapping)  
  
- [Sayısal Haritalama](#NumericMapping)  
  
- [Metin ve XML Eşleme](#TextMapping)  
  
- [Tarih ve Saat Eşleme](#DateMapping)  
  
- [İkili Haritalama](#BinaryMapping)  
  
- [Çeşitli Haritalama](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>
## <a name="default-type-mapping"></a>Varsayılan Tür Eşleme  
 Nesne İlişkisel Tasarımcısı (O/R Designer) veya SQLMetal komut satırı aracıyla nesne modelini veya harici eşleme dosyasını otomatik olarak oluşturabilirsiniz. Bu araçlar için varsayılan tür eşlemeleri, SQL Server veritabanıiçindeki sütunlarla eşlemek için hangi CLR türlerinin seçildiğini tanımlar. Bu araçları kullanma hakkında daha fazla bilgi için [nesne modeli oluşturma konusuna](creating-the-object-model.md)bakın.  
  
 Yöntem, <xref:System.Data.Linq.DataContext.CreateDatabase%2A> nesne modelindeki veya dış eşleme dosyasındaki eşleme bilgilerini temel alan bir SQL Server veritabanı oluşturmak için de kullanabilirsiniz. Yöntem için <xref:System.Data.Linq.DataContext.CreateDatabase%2A> varsayılan tür eşlemeleri, nesne modelindeki CLR türlerine eşlemek için hangi SQL Server sütuntürününün oluşturulduğunu tanımlar. Daha fazla bilgi için [bkz: Dinamik bir veritabanı oluşturma.](how-to-dynamically-create-a-database.md)  
  
<a name="BehaviorMatrix"></a>
## <a name="type-mapping-run-time-behavior-matrix"></a>Tür Eşleme Çalışma Zamanı Davranış Matrisi  
 Aşağıdaki diyagram, veriler veritabanından alındığı veya veritabanına kaydedildiğinde belirli tür eşlemelerinin beklenen çalışma zamanı davranışını gösterir. Serileştirme dışında, LINQ to SQL bu matriste belirtilmeyen clr veya SQL Server veri türleri arasında eşlemi desteklemez. Serileştirme desteği hakkında daha fazla bilgi için Ikili [Serileştirme'ye](#BinarySerialization)bakın.  

![SQL Server - SQL CLR veri türü eşleme tablosu](./media/sql-clr-type-mapping.png)

> [!NOTE]
> Bazı tür eşlemeleri, veritabanına veya veritabanından çeviri yaparken taşma veya veri kaybı özel durumlarına neden olabilir.  
  
### <a name="custom-type-mapping"></a>Özel Tür Eşleme  
 LINQ'dan SQL'e, O/R Designer, SQLMetal ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A> yöntem tarafından kullanılan varsayılan tür eşlemeleriyle sınırlı değildir. Bunları bir DBML dosyasında açıkça belirterek özel tür eşlemeleri oluşturabilirsiniz. Sonra nesne modeli kodu ve eşleme dosyası oluşturmak için bu DBML dosyasını kullanabilirsiniz. Daha fazla bilgi için [SQL-CLR Özel Tür Eşlemeleri'ne](sql-clr-custom-type-mappings.md)bakın.  
  
<a name="BehaviorDiffs"></a>
## <a name="behavior-differences-between-clr-and-sql-execution"></a>CLR ve SQL Yürütme Arasındaki Davranış Farkları  
 CLR ve SQL Server arasındaki kesinlik ve yürütme farklılıkları nedeniyle, hesaplamalarınızı nerede gerçekleştirdiğinize bağlı olarak farklı sonuçlar alabilir veya farklı davranışlar yaşayabilirsiniz. LINQ'dan SQL sorgularına yapılan hesaplamalar aslında Transact-SQL'e çevrilmiş ve daha sonra SQL Server veritabanında yürütülür. LINQ-SQL sorguları dışında gerçekleştirilen hesaplamalar CLR bağlamında yürütülür.  
  
 Örneğin, CLR ve SQL Server arasındaki davranış farklılıkları şunlardır:  
  
- SQL Server, bazı veri türlerini CLR'deki eşdeğer türdeki verilerden farklı şekilde sıralar. Örneğin, SQL Server türünden `UNIQUEIDENTIFIER` veriler, clr türünden <xref:System.Guid?displayProperty=nameWithType>farklı olarak sıralanır.  
  
- SQL Server bazı dize karşılaştırma işlemlerini CLR'den farklı işler. SQL Server'da dize karşılaştırma davranışı sunucudaki harmanlama ayarlarına bağlıdır. Daha fazla bilgi için Microsoft SQL Server Books Online'daki [Collations ile Çalışma'ya](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms187582(v=sql.105)) bakın.  
  
- SQL Server, bazı eşlenen işlevler için CLR'den farklı değerler döndürebilir. Örneğin, sql server iki dizeyi yalnızca beyaz boşlukta farklılık gösterirse eşit olarak değerlendirdiği için eşitlik işlevleri farklı olacaktır; oysa CLR onları eşit olarak kabul eder.  
  
<a name="EnumMapping"></a>
## <a name="enum-mapping"></a>Enum Haritalama  
 LINQ'dan SQL'e <xref:System.Enum?displayProperty=nameWithType> CLR türüyle SQL Server türlerine eşleme iki şekilde destek sağlar:  
  
- SQL sayısal türlerine eşleme `SMALLINT` `INT`( `BIGINT``TINYINT`, , , , )  
  
     Bir CLR <xref:System.Enum?displayProperty=nameWithType> türünü SQL sayısal türüyle eşlediğinizde, CLR'nin <xref:System.Enum?displayProperty=nameWithType> temel tamsayı değerini SQL Server veritabanı sütununun değeriyle eşlersiniz. Örneğin, adlandırılmış <xref:System.Enum?displayProperty=nameWithType> `DaysOfWeek` `Tue` bir üye, altta yatan bir tamsayı değeri 3 olan bir üye içeriyorsa, bu üye 3 veritabanı değeriyle eşlenir.  
  
- SQL metin türlerine`CHAR` `NCHAR`eşleme ( , , `VARCHAR`, , `NVARCHAR`)  
  
     Bir CLR <xref:System.Enum?displayProperty=nameWithType> türünü BIR SQL metin türüyle eşlediğinizde, SQL veritabanı değeri CLR <xref:System.Enum?displayProperty=nameWithType> üyelerinin adlarına eşlenir. Örneğin, adlandırılmış <xref:System.Enum?displayProperty=nameWithType> `DaysOfWeek` `Tue` bir üye, altta yatan bir tamsayı değeri 3 olan bir `Tue`üye içeriyorsa, bu üye bir veritabanı değeriyle eşleşiyorsa.  
  
> [!NOTE]
> BIR CLR'ye <xref:System.Enum?displayProperty=nameWithType>SQL metin türlerini eşleme <xref:System.Enum> yaparken, eşlenen SQL sütunundaki yalnızca üyelerin adlarını içerir. Diğer değerler -eşlenen <xref:System.Enum>SQL sütununda desteklenmez.  
  
 O/R Designer ve SQLMetal komut satırı aracı otomatik olarak bir <xref:System.Enum> CLR sınıfına SQL türü eşleyemez. O/R Designer ve SQLMetal tarafından kullanılmak üzere bir DBML dosyasını özelleştirerek bu eşlemi açıkça yapılandırmanız gerekir. Özel tür eşleme hakkında daha fazla bilgi için [SQL-CLR Özel Tür Eşlemeleri'ne](sql-clr-custom-type-mappings.md)bakın.  
  
 Numaralandırma amaçlı bir SQL sütunu diğer sayısal ve metin sütunları ile aynı türden olacağından; bu araçlar, aşağıdaki [Sayısal Eşleme](#NumericMapping) ve Metin ve [XML Eşleme](#TextMapping) bölümlerinde açıklandığı gibi, niyetinizi ve varsayılan haritalama nızı tanımaz. DBML dosyasıyla kod oluşturma hakkında daha fazla bilgi için [LINQ'dan SQL'e kod oluşturma bilgisine](code-generation-in-linq-to-sql.md)bakın.  
  
 Yöntem, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> CLR <xref:System.Enum?displayProperty=nameWithType> türünü eşlemek için sayısal türde bir SQL sütunu oluşturur.  
  
<a name="NumericMapping"></a>
## <a name="numeric-mapping"></a>Sayısal Haritalama  
 LINQ'dan SQL'e birçok CLR ve SQL Server sayısal türü eşlenemenizi sağlar. Aşağıdaki tablo, veritabanınıza dayalı bir nesne modeli veya dış eşleme dosyası oluşturmak için O/R Designer ve SQLMetal'in seçtiği CLR türlerini gösterir.  
  
|SQL Sunucu Türü|O/R Designer ve SQLMetal tarafından kullanılan Varsayılan CLR Türü eşlemi|  
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
  
 Sonraki tablo, nesne modelinizde veya <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> dış eşleme dosyanızda tanımlanan CLR türlerine eşlemek için hangi TÜRDE SQL sütununun oluşturulduğunu tanımlamak için yöntem tarafından kullanılan varsayılan tür eşlemelerini gösterir.  
  
|CLR Tipi|Varsayılan SQL Server Type tarafından kullanılan<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
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
  
 Seçebileceğiniz başka sayısal eşlemeler vardır, ancak bazıları veritabanına veya veritabanından çeviri yaparken taşma veya veri kaybı özel durumlarına neden olabilir. Daha fazla bilgi [için, Türü Eşleme Çalışma Zamanı Davranış](#BehaviorMatrix)Matrisi'ne bakın.  
  
### <a name="decimal-and-money-types"></a>Ondalık ve Para Türleri  
 SQL Server `DECIMAL` türünün varsayılan kesinliği (ondalık noktanın sağında ve solunda 18 ondalık basamak) varsayılan olarak eşlenebilen CLR <xref:System.Decimal?displayProperty=nameWithType> türünün hassasiyetinden çok daha küçüktür. Bu, veritabanına veri kaydettiğinizde hassas kayıplara neden olabilir. Ancak, SQL Server `DECIMAL` türü 29 basamaktan büyük bir hassasiyetle yapılandırılırsa tam tersi olabilir. Bir SQL `DECIMAL` Server türü CLR'den <xref:System.Decimal?displayProperty=nameWithType>daha büyük bir hassasiyetle yapılandırıldığında, veritabanından veri alırken hassas kayıp oluşabilir.  
  
 Varsayılan olarak `MONEY` `SMALLMONEY` CLR <xref:System.Decimal?displayProperty=nameWithType> türüyle eşleştirilmiş olan SQL Server ve türleri, veritabanına veri kaydederken taşmaya veya veri kaybı istisnalarına neden olabilecek çok daha küçük bir duyarlıkla sonuçlanır.  
  
<a name="TextMapping"></a>
## <a name="text-and-xml-mapping"></a>Metin ve XML Eşleme  
 Linq ile SQL arasında eşlenebildiğiniz birçok metin tabanlı ve XML türü de vardır. Aşağıdaki tablo, veritabanınıza dayalı bir nesne modeli veya dış eşleme dosyası oluşturmak için O/R Designer ve SQLMetal'in seçtiği CLR türlerini gösterir.  
  
|SQL Sunucu Türü|O/R Designer ve SQLMetal tarafından kullanılan Varsayılan CLR Türü eşlemi|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 Sonraki tablo, nesne modelinizde veya <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> dış eşleme dosyanızda tanımlanan CLR türlerine eşlemek için hangi TÜRDE SQL sütununun oluşturulduğunu tanımlamak için yöntem tarafından kullanılan varsayılan tür eşlemelerini gösterir.  
  
|CLR Tipi|Varsayılan SQL Server Type tarafından kullanılan<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Özel tip `Parse()` uygulama ve`ToString()`|`NVARCHAR(MAX)`|  
  
 Seçebileceğiniz başka metin tabanlı ve XML eşlemeleri vardır, ancak bazıları veritabanına veya veritabanından çeviri yaparken taşmasına veya veri kaybı özel durumuna neden olabilir. Daha fazla bilgi [için, Türü Eşleme Çalışma Zamanı Davranış](#BehaviorMatrix)Matrisi'ne bakın.  
  
### <a name="xml-types"></a>XML Türleri  
 SQL Server `XML` veri türü, Microsoft SQL Server 2005'ten başlayarak kullanılabilir. `XML` SQL Server veri türünü <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>veya <xref:System.String>. Sütun, okunamayan XML parçalarını depolarsa, <xref:System.Xml.Linq.XElement>çalışma zamanı hatalarını önlemek için <xref:System.String> sütunun eşlemesi gerekir. Aşağıdakileri içerecek şekilde <xref:System.String> eşlenen XML parçaları:  
  
- XML elemanlarıdizisi dizisi  
  
- Öznitelikler  
  
- Kamu Tanımlayıcıları (PI)  
  
- Yorumlar  
  
 [Tür Eşleme Çalıştır Zaman Davranış](#BehaviorMatrix)Matrisi'nde gösterildiği gibi <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> SQL Server'ı eşleyebilir <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> eşleyebilirseniz de, yöntemde bu türler için varsayılan SQL Server türü eşleme yoktur.  
  
### <a name="custom-types"></a>Özel Türleri  
 Bir sınıf uygular `Parse()` `ToString()`ve , herhangi bir SQL metin`CHAR`türü `NCHAR` `VARCHAR`( `NVARCHAR` `TEXT`, `NTEXT` `XML`, , , , , , , ) için nesne eşleyebilirsiniz. Nesne, eşlenen veritabanı sütununa döndürülen `ToString()` değeri göndererek veritabanında depolanır. Nesne veritabanı tarafından döndürülen `Parse()` dize çağırArak yeniden oluşturulur.  
  
> [!NOTE]
> LINQ'dan SQL'e serileştirmeyi kullanarak <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>desteklemez.  
  
<a name="DateMapping"></a>
## <a name="date-and-time-mapping"></a>Tarih ve Saat Eşleme  
 LINQ'dan SQL'e birçok SQL Server tarih ve saat türünü eşleyebilirsiniz. Aşağıdaki tablo, veritabanınıza dayalı bir nesne modeli veya dış eşleme dosyası oluşturmak için O/R Designer ve SQLMetal'in seçtiği CLR türlerini gösterir.  
  
|SQL Sunucu Türü|O/R Designer ve SQLMetal tarafından kullanılan Varsayılan CLR Türü eşlemi|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 Sonraki tablo, nesne modelinizde veya <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> dış eşleme dosyanızda tanımlanan CLR türlerine eşlemek için hangi TÜRDE SQL sütununun oluşturulduğunu tanımlamak için yöntem tarafından kullanılan varsayılan tür eşlemelerini gösterir.  
  
|CLR Tipi|Varsayılan SQL Server Type tarafından kullanılan<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Seçebileceğiniz başka tarih ve saat eşlemeleri vardır, ancak bazıları veritabanına veya veritabanından çeviri yaparken taşma veya veri kaybı özel durumlarına neden olabilir. Daha fazla bilgi [için, Türü Eşleme Çalışma Zamanı Davranış](#BehaviorMatrix)Matrisi'ne bakın.  
  
> [!NOTE]
> SQL Server `DATETIME2`türleri `DATETIMEOFFSET` `DATE`, `TIME` , , ve Microsoft SQL Server 2008 ile başlayarak kullanılabilir. LINQ to SQL, .NET Framework sürümü 3.5 SP1 ile başlayan bu yeni türlere eşlemi destekler.  
  
### <a name="systemdatetime"></a>Datetime  
 CLR <xref:System.DateTime?displayProperty=nameWithType> türünün aralığı ve hassasiyeti, `DATETIME` <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemiçin varsayılan tür eşlemeolan SQL Server türünün aralık ve hassasiyetinden daha büyüktür. Microsoft SQL Server 2008'den `DATETIME`başlayarak kullanılabilen , kullanım `DATETIME2`aralığı dışındaki tarihlerle ilgili özel durumları önlemek için. `DATETIME2`CLR'nin <xref:System.DateTime?displayProperty=nameWithType>menzili ve hassasiyeti ile eşleşebilir.  
  
 SQL Server <xref:System.TimeZone>tarihleri, CLR'de zengin bir şekilde desteklenen bir özellik kavramına sahip değildir. <xref:System.TimeZone>değerler, özgün <xref:System.DateTimeKind> bilgilerden bağımsız <xref:System.TimeZone> olarak, dönüşüm olmadan veritabanına olduğu gibi kaydedilir. Değerler <xref:System.DateTime> veritabanından alındığı zaman, değerleri bir <xref:System.DateTime> <xref:System.DateTimeKind> ' ile olduğu <xref:System.DateTimeKind.Unspecified>gibi yüklenir. Desteklenen <xref:System.DateTime?displayProperty=nameWithType> yöntemler hakkında daha fazla bilgi için [System.DateTime Yöntemleri'ne](system-datetime-methods.md)bakın.  
  
### <a name="systemtimespan"></a>Timespan  
 Microsoft SQL Server 2008 ve .NET Framework 3.5 SP1, <xref:System.TimeSpan?displayProperty=nameWithType> CLR `TIME` türünü SQL Server türüyle eşlenemenizi sağlar. Ancak, CLR'nin <xref:System.TimeSpan?displayProperty=nameWithType> desteklediği aralıkla SQL Server `TIME` türünün desteklediği aralık arasında büyük bir fark vardır. SQL'e `TIME` 0'dan küçük veya 23:59:59.99999999 saatten az olan değerleri eşleme, taşma özel durumlarına neden olur. Daha fazla bilgi için [System.TimeSpan Yöntemleri'ne](system-timespan-methods.md)bakın.  
  
 Microsoft SQL Server 2000 ve SQL Server 2005'te veritabanı alanlarını <xref:System.TimeSpan>. Ancak, <xref:System.TimeSpan> <xref:System.TimeSpan> değerler çıkarmadan <xref:System.DateTime> döndürülebildiği veya bir ifadeye gerçek veya bağlı değişken olarak girilebildiği için, üzerinde olan işlemler desteklenir.  
  
<a name="BinaryMapping"></a>
## <a name="binary-mapping"></a>İkili Haritalama  
 CLR türüne eş oluşturabilen birçok <xref:System.Data.Linq.Binary?displayProperty=nameWithType>SQL Server türü vardır. Aşağıdaki tablo, veritabanınıza dayalı bir nesne modeli veya dış eşleme <xref:System.Data.Linq.Binary?displayProperty=nameWithType> dosyası yazarken O/R Designer ve SQLMetal'in CLR türünü tanımlamasına neden olan SQL Server türlerini gösterir.  
  
|SQL Sunucu Türü|O/R Designer ve SQLMetal tarafından kullanılan Varsayılan CLR Türü eşlemi|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)``FILESTREAM` özniteliği ile|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 Sonraki tablo, nesne modelinizde veya <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> dış eşleme dosyanızda tanımlanan CLR türlerine eşlemek için hangi TÜRDE SQL sütununun oluşturulduğunu tanımlamak için yöntem tarafından kullanılan varsayılan tür eşlemelerini gösterir.  
  
|CLR Tipi|Varsayılan SQL Server Type tarafından kullanılan<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Seçebileceğiniz başka ikili eşlemeler vardır, ancak bazıları veritabanına veya veritabanından çeviri yaparken taşma veya veri kaybı özel durumlarına neden olabilir. Daha fazla bilgi [için, Türü Eşleme Çalışma Zamanı Davranış](#BehaviorMatrix)Matrisi'ne bakın.  
  
### <a name="sql-server-filestream"></a>SQL Sunucu FILESTREAM  
 Microsoft `FILESTREAM` SQL `VARBINARY(MAX)` Server 2008'den başlayarak sütunlar için öznitelik kullanılabilir; .NET Framework sürümü 3.5 SP1'den başlayarak LINQ ile SQL'e eşleyebilirsiniz.  
  
 `VARBINARY(MAX)` Nesnelere `FILESTREAM` öznitelik <xref:System.Data.Linq.Binary> ile sütuneşleyebilir olsanız <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> da, yöntem öznitelik ile `FILESTREAM` otomatik olarak sütun oluşturmak mümkün değildir. Hakkında `FILESTREAM`daha fazla bilgi için [FILESTREAM Genel Bakış'a](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb933993(v=sql.105))bakın.  
  
<a name="BinarySerialization"></a>
### <a name="binary-serialization"></a>İkili Serileştirme  
 Bir sınıf arabirimi <xref:System.Runtime.Serialization.ISerializable> uygularsa, bir nesneyi herhangi bir`BINARY` `VARBINARY`SQL `IMAGE`ikili alanına serileştirebilirsiniz ( , , ). Nesne, <xref:System.Runtime.Serialization.ISerializable> arabirimin nasıl uygulandığına göre seri hale getirilir ve deserialize edilir. Daha fazla bilgi için [Ikili Serileştirme'ye](../../../../../standard/serialization/binary-serialization.md)bakın.
  
<a name="MiscMapping"></a>
## <a name="miscellaneous-mapping"></a>Çeşitli Haritalama  
 Aşağıdaki tablo, henüz belirtilmemiş bazı çeşitli türler için varsayılan tür eşlemelerini gösterir. Aşağıdaki tablo, veritabanınıza dayalı bir nesne modeli veya dış eşleme dosyası oluşturmak için O/R Designer ve SQLMetal'in seçtiği CLR türlerini gösterir.  
  
|SQL Sunucu Türü|O/R Designer ve SQLMetal tarafından kullanılan Varsayılan CLR Türü eşlemi|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 Sonraki tablo, nesne modelinizde veya <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> dış eşleme dosyanızda tanımlanan CLR türlerine eşlemek için hangi TÜRDE SQL sütununun oluşturulduğunu tanımlamak için yöntem tarafından kullanılan varsayılan tür eşlemelerini gösterir.  
  
|CLR Tipi|Varsayılan SQL Server Type tarafından kullanılan<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ'dan SQL'e bu çeşitli türler için başka tür eşlemeleri desteklemez.  Daha fazla bilgi [için, Türü Eşleme Çalışma Zamanı Davranış](#BehaviorMatrix)Matrisi'ne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelik Tabanlı Eşleme](attribute-based-mapping.md)
- [Dış Eşleme](external-mapping.md)
- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
- [SQL-CLR Tür Uyumsuzlukları](sql-clr-type-mismatches.md)
