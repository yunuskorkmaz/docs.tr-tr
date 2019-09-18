---
title: SQL-CLR Tür Eşlemesi
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 6710c58a430c35dae41a1a381335019fd3e75192
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053033"
---
# <a name="sql-clr-type-mapping"></a>SQL-CLR Tür Eşlemesi
LINQ to SQL, ilişkisel bir veritabanının veri modeli, tercih ettiğiniz programlama dilinde ifade edilen bir nesne modeliyle eşlenir. Uygulama çalıştığında, LINQ to SQL nesne modelindeki dil ile tümleşik sorguları SQL 'e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde, LINQ to SQL sonuçları kendi programlama dilinizde birlikte çalışleyebileceğiniz nesnelere geri çevirir.  
  
 Nesne modeli ve veritabanı arasında veri çevirmek için, bir *tür eşlemesinin* tanımlanması gerekir. LINQ to SQL, her bir ortak dil çalışma zamanı (CLR) türünü belirli bir SQL Server türü ile eşleştirmek için bir tür eşlemesi kullanır. Öznitelik tabanlı eşleme ile nesne modeli içinde, tür eşlemelerini ve veritabanı yapısı ve tablo ilişkileri gibi diğer eşleme bilgilerini tanımlayabilirsiniz. Alternatif olarak, eşleme bilgilerini bir dış eşleme dosyası ile nesne modeli dışında belirtebilirsiniz. Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md) ve [dış eşleme](external-mapping.md).  
  
 Bu konuda aşağıdaki noktaları ele alınmaktadır:  
  
- [Varsayılan tür eşleme](#DefaultTypeMapping)  
  
- [Tür eşleme çalışma zamanı davranış matrisi](#BehaviorMatrix)  
  
- [CLR ve SQL yürütme arasındaki davranış farklılıkları](#BehaviorDiffs)  
  
- [Sabit listesi eşleme](#EnumMapping)  
  
- [Sayısal eşleme](#NumericMapping)  
  
- [Metin ve XML eşleme](#TextMapping)  
  
- [Tarih ve saat eşleme](#DateMapping)  
  
- [İkili eşleme](#BinaryMapping)  
  
- [Çeşitli eşleme](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>   
## <a name="default-type-mapping"></a>Varsayılan tür eşleme  
 Nesne modeli veya dış eşleme dosyasını Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) veya SQLMetal komut satırı aracı ile otomatik olarak oluşturabilirsiniz. Bu araçların varsayılan tür eşlemeleri, SQL Server veritabanı içindeki sütunlara eşlemek için hangi CLR türlerinin seçili olduğunu tanımlar. Bu araçları kullanma hakkında daha fazla bilgi için bkz. [nesne modeli oluşturma](creating-the-object-model.md).  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> Yöntemi, nesne modelindeki veya dış eşleme dosyasındaki eşleme bilgilerine göre SQL Server veritabanı oluşturmak için de kullanabilirsiniz. <xref:System.Data.Linq.DataContext.CreateDatabase%2A> Yöntemi için varsayılan tür eşlemeleri, nesne modelindeki clr türleriyle eşlemek için hangi SQL Server sütun türlerinin oluşturulacağını tanımlar. Daha fazla bilgi için [nasıl yapılır: Dinamik olarak bir veritabanı](how-to-dynamically-create-a-database.md)oluşturun.  
  
<a name="BehaviorMatrix"></a>   
## <a name="type-mapping-run-time-behavior-matrix"></a>Tür eşleme çalışma zamanı davranış matrisi  
 Aşağıdaki diyagramda, veriler veritabanından alındığında veya veritabanına kaydedildiğinde belirli tür eşleştirmelerin beklenen çalışma zamanı davranışı gösterilmektedir. Serileştirme hariç LINQ to SQL, bu matriste belirtilmemiş herhangi bir CLR veya SQL Server veri türü arasındaki eşlemeyi desteklemez. Serileştirme desteği hakkında daha fazla bilgi için bkz. [Ikili serileştirme](#BinarySerialization).  
 
![SQL CLR veri türüne SQL Server eşleme tablosu](./media/sql-clr-type-mapping.png)

> [!NOTE]
> Bazı tür eşlemelerde veya veritabanına çevrilirken taşma veya veri kaybı özel durumları oluşabilir.  
  
### <a name="custom-type-mapping"></a>Özel tür eşleme  
 LINQ to SQL ile, O/R Tasarımcısı, SqlMetal ve <xref:System.Data.Linq.DataContext.CreateDatabase%2A> yöntemi tarafından kullanılan varsayılan tür eşlemelerle sınırlı değildir. Özel tür eşlemelerini, açıkça bir DBML dosyasında belirterek oluşturabilirsiniz. Ardından, nesne modeli kodu ve eşleme dosyası oluşturmak için bu DBML dosyasını kullanabilirsiniz. Daha fazla bilgi için bkz. [SQL-CLR özel tür eşlemeleri](sql-clr-custom-type-mappings.md).  
  
<a name="BehaviorDiffs"></a>   
## <a name="behavior-differences-between-clr-and-sql-execution"></a>CLR ve SQL yürütme arasındaki davranış farklılıkları  
 CLR ve SQL Server arasındaki duyarlık ve yürütme farklılıkları nedeniyle, hesaplamalarınızı gerçekleştirdiğiniz yere bağlı olarak farklı sonuçlar alabilir veya farklı davranışlar yaşayabilirsiniz. LINQ to SQL sorgularda gerçekleştirilen hesaplamalar aslında Transact-SQL ' e çevrilir ve sonra SQL Server veritabanında yürütülür. LINQ to SQL sorgularının dışında gerçekleştirilen hesaplamalar CLR bağlamı içinde yürütülür.  
  
 Örneğin, CLR ve SQL Server arasındaki davranıştaki bazı farklılıklar aşağıda verilmiştir:  
  
- SQL Server, bazı veri türlerini CLR içindeki eşdeğer türdeki verilerden farklı şekilde sıralar. Örneğin, türündeki `UNIQUEIDENTIFIER` SQL Server veri türü <xref:System.Guid?displayProperty=nameWithType>clr verilerinden farklı şekilde sıralanır.  
  
- SQL Server, bazı dize karşılaştırma işlemlerini CLR 'den farklı işler. SQL Server, dize karşılaştırma davranışı sunucudaki harmanlama ayarlarına bağlıdır. Daha fazla bilgi için bkz. Microsoft SQL Server Çevrimiçi Kitapları [harmanlamalar Ile çalışma](https://go.microsoft.com/fwlink/?LinkId=115330) .  
  
- SQL Server, CLR 'nin bazı eşlenmiş işlevleri için farklı değerler döndürebilir. Örneğin eşitlik işlevleri farklı olur çünkü SQL Server iki dizeyi yalnızca sondaki beyaz boşluğa farklıysa eşit olacak şekilde değerlendirir; Ancak CLR bunları eşit değil olarak kabul eder.  
  
<a name="EnumMapping"></a>   
## <a name="enum-mapping"></a>Sabit listesi eşleme  
 LINQ to SQL, clr <xref:System.Enum?displayProperty=nameWithType> türünün SQL Server türlerine eşlemesini iki şekilde destekler:  
  
- SQL sayısal türlerine eşleme`TINYINT`(, `SMALLINT`, `INT` `BIGINT`,)  
  
     Bir clr <xref:System.Enum?displayProperty=nameWithType> türünü bir SQL sayısal türü ile eşleştirdiğinizde, clr <xref:System.Enum?displayProperty=nameWithType> 'nin temeldeki tamsayı değerini SQL Server veritabanı sütununun değeriyle eşlersiniz. Örneğin, adlandırılmış <xref:System.Enum?displayProperty=nameWithType> `DaysOfWeek` bir, temel alınan tamsayı değeri 3 `Tue` olan adlı bir üye içeriyorsa, bu üye 3 ' ün bir veritabanı değeriyle eşlenir.  
  
- SQL metin türleriyle eşleme`CHAR`(, `NCHAR`, `VARCHAR` `NVARCHAR`,)  
  
     Bir clr <xref:System.Enum?displayProperty=nameWithType> türünü bir SQL metin türüyle eşleştirdiğinizde, SQL veritabanı değeri clr <xref:System.Enum?displayProperty=nameWithType> üyelerinin adlarıyla eşleştirilir. Örneğin <xref:System.Enum?displayProperty=nameWithType> , adlandırılmış `DaysOfWeek` bir, temel alınan tamsayı değeri 3 `Tue` olan adlı bir üye içeriyorsa, `Tue`Bu üye bir veritabanı değeriyle eşlenir.  
  
> [!NOTE]
> SQL metin türlerini bir clr <xref:System.Enum?displayProperty=nameWithType>ile eşlerken, yalnızca eşlenmiş SQL sütunundaki <xref:System.Enum> üyelerin adlarını ekleyin. Diğer değerler, <xref:System.Enum>eşlenmiş SQL sütununda desteklenmez.  
  
 O/R Tasarımcısı ve SQLMetal komut satırı aracı bir SQL türünü otomatik olarak bir clr <xref:System.Enum> sınıfına eşleyemezsiniz. Bir DBML dosyasını O/R Tasarımcısı ve SQLMetal tarafından kullanılmak üzere özelleştirerek bu eşlemeyi açıkça yapılandırmanız gerekir. Özel tür eşlemesi hakkında daha fazla bilgi için bkz. [SQL-CLR özel tür eşlemeleri](sql-clr-custom-type-mappings.md).  
  
 Sabit listesi için tasarlanan bir SQL sütunu diğer sayısal ve metin sütunlarıyla aynı türde olacaktır; Bu araçlar, aşağıdaki [sayısal eşleme](#NumericMapping) ve [metin ve XML eşleme](#TextMapping) bölümlerinde açıklandığı gibi, ' nin amacını ve varsayılan olarak eşleştirilmesini tanımaz. DBML dosyası ile kod üretme hakkında daha fazla bilgi için bkz. [LINQ to SQL kod oluşturma](code-generation-in-linq-to-sql.md).  
  
 Yöntemi bir clr <xref:System.Enum?displayProperty=nameWithType> türünü eşlemek için sayısal türde bir SQL sütunu oluşturur. <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>  
  
<a name="NumericMapping"></a>   
## <a name="numeric-mapping"></a>Sayısal eşleme  
 LINQ to SQL, çok sayıda CLR ve SQL Server sayısal türü eşlemenizi sağlar. Aşağıdaki tabloda, veritabanınıza göre bir nesne modeli veya dış eşleme dosyası oluştururken O/R Tasarımcısı ve SQLMetal Select CLR türleri gösterilmektedir.  
  
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
  
 Sonraki tabloda, nesne modelinizde veya dış eşleme dosyanızda tanımlanan <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> clr türleriyle eşlemek için hangi tür SQL sütunlarının oluşturulduğunu tanımlamak üzere yöntemi tarafından kullanılan varsayılan tür eşlemeleri gösterilmektedir.  
  
|CLR türü|Tarafından kullanılan varsayılan SQL Server türü<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
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
  
 Seçebileceğiniz birçok farklı sayısal eşleşme vardır ancak bazıları taşma veya veritabanına çevrilirken taşma ya da veri kaybı özel durumlarına neden olabilir. Daha fazla bilgi için, [tür eşleme çalışma zamanı davranış matrisine](#BehaviorMatrix)bakın.  
  
### <a name="decimal-and-money-types"></a>Ondalık ve para türleri  
 SQL Server `DECIMAL` türünün varsayılan duyarlığı (ondalık noktanın sol ve sağ tarafında 18 ondalık basamak), varsayılan olarak eşleştirildiği clr <xref:System.Decimal?displayProperty=nameWithType> türünün duyarlığından çok daha küçüktür. Bu, verileri veritabanına kaydettiğinizde duyarlık kaybına neden olabilir. Ancak, SQL Server `DECIMAL` türü 29 ' dan fazla duyarlıkta yapılandırılmışsa yalnızca ters durum oluşabilir. SQL Server `DECIMAL` bir tür CLR <xref:System.Decimal?displayProperty=nameWithType>'den daha büyük bir duyarlıkla yapılandırıldığında, verileri veritabanından alırken duyarlık kaybı oluşabilir.  
  
 CLR `SMALLMONEY` `MONEY` türüiledeeşlenmişolanSQLServervetürler,varsayılanolarakdahaküçükbirduyarlığasahiptirvebu,verileriveritabanınakaydederkentaşmaveyaverikaybıözeldurumlarınanedenolabilir.<xref:System.Decimal?displayProperty=nameWithType>  
  
<a name="TextMapping"></a>   
## <a name="text-and-xml-mapping"></a>Metin ve XML eşleme  
 LINQ to SQL ile eşleyebileceğiniz çok sayıda metin tabanlı ve XML türü de vardır. Aşağıdaki tabloda, veritabanınıza göre bir nesne modeli veya dış eşleme dosyası oluştururken O/R Tasarımcısı ve SQLMetal Select CLR türleri gösterilmektedir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 Sonraki tabloda, nesne modelinizde veya dış eşleme dosyanızda tanımlanan <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> clr türleriyle eşlemek için hangi tür SQL sütunlarının oluşturulduğunu tanımlamak üzere yöntemi tarafından kullanılan varsayılan tür eşlemeleri gösterilmektedir.  
  
|CLR türü|Tarafından kullanılan varsayılan SQL Server türü<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<xref:System.Char?displayProperty=nameWithType>[]|`NVARCHAR(4000)`|  
|Uygulayan `Parse()` özel tür ve`ToString()`|`NVARCHAR(MAX)`|  
  
 Seçebileceğiniz birçok farklı metin tabanlı ve XML eşlemesi vardır, ancak bazıları veritabanına veya veritabanından çevrilirken taşma veya veri kaybı özel durumlarına neden olabilir. Daha fazla bilgi için, [tür eşleme çalışma zamanı davranış matrisine](#BehaviorMatrix)bakın.  
  
### <a name="xml-types"></a>XML türleri  
 SQL Server `XML` veri türü Microsoft SQL Server 2005 ' den başlayarak kullanılabilir. SQL Server `XML` veri türünü, <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>veya ileeşleyebilirsiniz.<xref:System.String> Sütun, okunamayan <xref:System.Xml.Linq.XElement>XML parçalarını depoluyorsa, çalışma zamanı hatalarından kaçınmak için sütunun ile <xref:System.String> eşlenmesi gerekir. Aşağıdakiler dahil olmak üzere <xref:System.String> eşlenmesi gereken XML parçaları:  
  
- Bir dizi XML öğesi  
  
- Öznitelikler  
  
- Ortak tanımlayıcılar (PI)  
  
- Açıklamalar  
  
 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> [Tür eşleme çalışma zamanı davranışı matrisinde](#BehaviorMatrix)gösterildiği gibi SQL Server eşleyebilir, ancak bu tür için yönteminvarsayılanSQLServertüreşlemesiyoktur.<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>  
  
### <a name="custom-types"></a>Özel türler  
 Bir sınıf ve `Parse()` `ToString()`uygularsa, nesneyi herhangi bir SQL metin `NVARCHAR`türüyle `NCHAR` `VARCHAR``CHAR` `NTEXT` `XML`(,, ,,,,)eşleyebilirsiniz.`TEXT` Nesnesi, tarafından döndürülen değer tarafından `ToString()` eşlenen veritabanı sütununa gönderilerek veritabanında depolanır. Nesnesi, veritabanı tarafından döndürülen dizeyi `Parse()` çağırarak yeniden oluşturulur.  
  
> [!NOTE]
> LINQ to SQL, kullanılarak <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>Serileştirmeyi desteklemez.  
  
<a name="DateMapping"></a>   
## <a name="date-and-time-mapping"></a>Tarih ve saat eşleme  
 LINQ to SQL, birçok SQL Server Tarih ve saat türünü eşleyebilirsiniz. Aşağıdaki tabloda, veritabanınıza göre bir nesne modeli veya dış eşleme dosyası oluştururken O/R Tasarımcısı ve SQLMetal Select CLR türleri gösterilmektedir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 Sonraki tabloda, nesne modelinizde veya dış eşleme dosyanızda tanımlanan <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> clr türleriyle eşlemek için hangi tür SQL sütunlarının oluşturulduğunu tanımlamak üzere yöntemi tarafından kullanılan varsayılan tür eşlemeleri gösterilmektedir.  
  
|CLR türü|Tarafından kullanılan varsayılan SQL Server türü<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 Seçebileceğiniz birçok başka tarih ve zaman eşlemesi vardır, ancak bazıları veritabanına veya veritabanından çevrilirken taşma veya veri kaybı özel durumlarına neden olabilir. Daha fazla bilgi için, [tür eşleme çalışma zamanı davranış matrisine](#BehaviorMatrix)bakın.  
  
> [!NOTE]
> SQL Server türler `DATETIME2`,, `DATETIMEOFFSET`ve `DATE` MicrosoftSQLServer2008'denbaşlayarakkullanılabilir`TIME` . LINQ to SQL, .NET Framework sürüm 3,5 SP1 ile başlayarak bu yeni türlere eşlemeyi destekler.  
  
### <a name="systemdatetime"></a>System. DateTime  
 CLR <xref:System.DateTime?displayProperty=nameWithType> türünün aralığı ve duyarlığı, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntem için varsayılan tür eşleme olan SQL Server `DATETIME` türünün aralığından ve duyarlığından daha büyüktür. `DATETIME` Kullanım`DATETIME2`aralığı dışındaki tarihlerle ilgili özel durumların önlenmesine yardımcı olmak için, Microsoft SQL Server 2008 ' den başlayarak kullanılabilir. `DATETIME2`CLR <xref:System.DateTime?displayProperty=nameWithType>'nin aralığıyla ve duyarlığına göre eşleşir.  
  
 SQL Server tarihleri <xref:System.TimeZone>, clr 'de zengin olarak desteklenen bir özellik olan kavramı değildir. <xref:System.TimeZone>değerler, özgün <xref:System.DateTimeKind> bilgilerden bağımsız olarak, dönüştürme yapılmadan <xref:System.TimeZone> veritabanına olarak kaydedilir. Değerler veritabanından alındığında, ' <xref:System.DateTime> <xref:System.DateTimeKind> nin<xref:System.DateTimeKind.Unspecified>değeri ' a ' olan olarak yüklenir. <xref:System.DateTime> Desteklenen <xref:System.DateTime?displayProperty=nameWithType> yöntemler hakkında daha fazla bilgi için bkz. [System. DateTime yöntemleri](system-datetime-methods.md).  
  
### <a name="systemtimespan"></a>System.TimeSpan  
 Microsoft SQL Server 2008 ve .NET Framework 3,5 SP1, clr <xref:System.TimeSpan?displayProperty=nameWithType> türünü SQL Server `TIME` türüyle eşlemenizi sağlar. Ancak, clr <xref:System.TimeSpan?displayProperty=nameWithType> 'nin desteklediği Aralık ve SQL Server `TIME` türünün desteklediği büyük bir fark vardır. Değer 0 ' dan küçük veya 23:59 ' dan daha büyük bir değere eşleniyor: `TIME` 59.9999999 saat, taşma özel durumlarına neden olur. Daha fazla bilgi için bkz. [System. TimeSpan yöntemleri](system-timespan-methods.md).  
  
 Microsoft SQL Server 2000 ve SQL Server 2005 ' de, veritabanı alanlarını ile <xref:System.TimeSpan>eşleyemezsiniz. Ancak, değerler çıkarma <xref:System.TimeSpan> işleminden <xref:System.DateTime> döndürülebilecek <xref:System.TimeSpan> veya bir ifadenin bir sabit değer ya da bağlı değişken olarak tanıtıldığı için üzerinde işlemler desteklenir.  
  
<a name="BinaryMapping"></a>   
## <a name="binary-mapping"></a>İkili eşleme  
 CLR türüyle <xref:System.Data.Linq.Binary?displayProperty=nameWithType>eşleyebileceğiniz pek çok SQL Server türü vardır. Aşağıdaki tabloda, veritabanı temelinde bir nesne modeli veya dış eşleme dosyası oluştururken O/R Tasarımcısı ve SQLMetal <xref:System.Data.Linq.Binary?displayProperty=nameWithType> 'un bir clr türü tanımlamasına neden olan SQL Server türleri gösterilmektedir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)``FILESTREAM` özniteliği ile|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 Sonraki tabloda, nesne modelinizde veya dış eşleme dosyanızda tanımlanan <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> clr türleriyle eşlemek için hangi tür SQL sütunlarının oluşturulduğunu tanımlamak üzere yöntemi tarafından kullanılan varsayılan tür eşlemeleri gösterilmektedir.  
  
|CLR türü|Tarafından kullanılan varsayılan SQL Server türü<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 Seçebileceğiniz birçok başka ikili eşleme vardır ancak bazıları taşma ya da veri kaybı özel durumları veritabanına veya veritabanından çevrilirken ortaya çıkabilir. Daha fazla bilgi için, [tür eşleme çalışma zamanı davranış matrisine](#BehaviorMatrix)bakın.  
  
### <a name="sql-server-filestream"></a>SQL Server FıLESTREAM  
 Sütunları `FILESTREAM` için`VARBINARY(MAX)` özniteliği Microsoft SQL Server 2008 ' den başlayarak kullanılabilir; .NET Framework SP1 3,5 sürümünden başlayarak LINQ to SQL ile eşleyebilirsiniz.  
  
 Nesneleri<xref:System.Data.Linq.Binary> `VARBINARY(MAX)` özniteliğine`FILESTREAM`sahip sütunları nesneleriyle eşlemenize rağmen, `FILESTREAM` yöntemiözniteliğiyleotomatikolaraksütunoluşturamaz.<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Hakkında `FILESTREAM`daha fazla bilgi için bkz. Microsoft SQL Server çevrimiçi kitapları [FILESTREAM 'e genel bakış](https://go.microsoft.com/fwlink/?LinkId=115291) .  
  
<a name="BinarySerialization"></a>   
### <a name="binary-serialization"></a>İkili Serileştirme  
 Bir sınıf <xref:System.Runtime.Serialization.ISerializable> arabirimini uyguluyorsa, bir nesneyi herhangi bir SQL ikili alanına (`BINARY`, `VARBINARY`, `IMAGE`) seri hale getirebilirsiniz. Nesne serileştirilir ve <xref:System.Runtime.Serialization.ISerializable> arabirimin nasıl uygulandığınıza göre seri durumdan çıkarılırlar. Daha fazla bilgi için bkz. [Ikili serileştirme](https://go.microsoft.com/fwlink/?LinkId=115581).  
  
<a name="MiscMapping"></a>   
## <a name="miscellaneous-mapping"></a>Çeşitli eşleme  
 Aşağıdaki tabloda, henüz açıklanmayan bazı çeşitli türler için varsayılan tür eşlemeleri gösterilmektedir. Aşağıdaki tabloda, veritabanınıza göre bir nesne modeli veya dış eşleme dosyası oluştururken O/R Tasarımcısı ve SQLMetal Select CLR türleri gösterilmektedir.  
  
|SQL Server türü|O/R Tasarımcısı ve SQLMetal tarafından kullanılan varsayılan CLR türü eşleme|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 Sonraki tabloda, nesne modelinizde veya dış eşleme dosyanızda tanımlanan <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> clr türleriyle eşlemek için hangi tür SQL sütunlarının oluşturulduğunu tanımlamak üzere yöntemi tarafından kullanılan varsayılan tür eşlemeleri gösterilmektedir.  
  
|CLR türü|Tarafından kullanılan varsayılan SQL Server türü<xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 LINQ to SQL, bu çeşitli türler için başka tür eşlemelerini desteklemez.  Daha fazla bilgi için, [tür eşleme çalışma zamanı davranış matrisine](#BehaviorMatrix)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelik Tabanlı Eşleme](attribute-based-mapping.md)
- [Dış Eşleme](external-mapping.md)
- [Veri Türleri ve İşlevleri](data-types-and-functions.md)
- [SQL-CLR Tür Uyumsuzlukları](sql-clr-type-mismatches.md)
