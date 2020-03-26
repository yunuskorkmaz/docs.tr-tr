---
title: Ortak Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: b6c2c89101f3304a0cab014de2def22195541471
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249480"
---
# <a name="common-schema-collections"></a>Ortak Şema Koleksiyonları
Ortak şema koleksiyonları ,NET Framework yönetilen sağlayıcılarının her biri tarafından uygulanan şema koleksiyonlarıdır. **GetSchema** yöntemini bağımsız değişken olmadan veya şema toplama adı "MetaDataCollections" ile çağırarak desteklenen şema koleksiyonlarının listesini belirlemek için bir .NET Framework yönetilen sağlayıcısını sorgulayabilirsiniz. Bu, desteklenen <xref:System.Data.DataTable> şema koleksiyonlarının bir listesini, her destekledikleri kısıtlamaların sayısını ve kullandıkları tanımlayıcı parçalarının sayısını döndürecektir. Bu koleksiyonlar gerekli sütunların tümlerini açıklar. Sağlayıcılar isterlerse ek sütunlar eklemekte serbesttirler. Örneğin, `SqlClient` `OracleClient` kısıtlamalar koleksiyonuna ParameterName ekleyin.  
  
 Bir sağlayıcı gerekli bir sütunun değerini belirleyemiyorsa, null döndürecektir.  
  
 **GetSchema** yöntemlerini kullanma hakkında daha fazla bilgi için [GetSchema ve Schema Koleksiyonları'na](getschema-and-schema-collections.md)bakın.  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Bu şema koleksiyonu, veritabanına bağlanmak için şu anda kullanılan .NET Framework yönetilen sağlayıcısı tarafından desteklenen tüm şema koleksiyonları hakkındaki bilgileri ortaya çıkarır.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|CollectionName|string|Koleksiyonu döndürmek için **GetSchema** yöntemine geçecek koleksiyonun adı.|  
|Numara kısıtlamaları|int|Koleksiyon için belirtilebilecek kısıtlama sayısı.|  
|NumberOfIdentifierParçalar|int|Bileşik tanımlayıcı/veritabanı nesne adındaki parça sayısı. Örneğin, SQL Server'da bu tabloiçin 3 ve sütunlar için 4 olacaktır. Oracle'da tablolar için 2 ve sütunlar için 3 olacaktır.|  
  
## <a name="datasourceinformation"></a>Datasourceınformation  
 Bu şema koleksiyonu, .NET Framework yönetilen sağlayıcısının şu anda bağlandığı veri kaynağı hakkındaki bilgileri ortaya çıkarır.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|KompozitIdentifierSeparatorPattern|string|Bileşik ayırıcılar bileşik ayırıcıları eşleştirmek için normal ifade. Örneğin, "\\" (SQL Server için)\@ \\veya "&#124;." (Oracle için).<br /><br /> Bileşik tanımlayıcı genellikle bir veritabanı nesne adı için kullanılan, örneğin: pubs.dbo.authors veya\@pubs dbo.authors.<br /><br /> SQL Server için " ".\\ OracleClient için "\@ \\&#124;" kullanın.<br /><br /> ODBC için Catalog_name_seperator kullanın.<br /><br /> OLE DB için DBLITERAL_CATALOG_SEPARATOR veya DBLITERAL_SCHEMA_SEPARATOR kullanın.|  
|DataSourceProductName|string|Sağlayıcı tarafından erişilen "Oracle" veya "SQLServer" gibi ürünün adı.|  
|DataSourceProductVersion|string|Sağlayıcı tarafından erişilen ürünün sürümünü, veri kaynaklarının yerel biçiminde ve Microsoft biçiminde değil, biçiminde gösterir.<br /><br /> Bazı durumlarda DataSourceProductVersion ve DataSourceProductVersionNormalized aynı değer olacaktır. OLE DB ve ODBC durumunda, bunlar her zaman altta yatan yerel API'deki aynı işlev çağrısına eşlenenle aynı olacaktır.|  
|DataSourceProductVersionNormalized|string|Veri kaynağı için normalleştirilmiş bir sürüm, bu `String.Compare()`şekilde karşılaştırılabilir. Bu biçimi, sürüm 10'un sürüm 1 ve sürüm 2 arasında sıralanmasını önlemek için sağlayıcının tüm sürümleri için tutarlıdır.<br /><br /> Örneğin, Oracle sağlayıcısı normalleştirilmiş sürümü için "nn.nn.nn.nnn" biçimini kullanır ve bu da Oracle 8i veri kaynağının "08.01.07.04.01" döndürmesine neden olur. SQL Server tipik Microsoft "nn.nn.nnnn" biçimini kullanır.<br /><br /> Bazı durumlarda, DataSourceProductVersion ve DataSourceProductVersionNormalized aynı değer olacaktır. OLE DB ve ODBC durumunda bunlar, temel yerel API'deki aynı işlev çağrısına eşlenenler her zaman aynı olacaktır.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|GROUP BY yan tümcesindeki sütunlar ile seçili listedeki toplu olmayan sütunlar arasındaki ilişkiyi belirtir.|  
|TanımlayıcıDesen|string|Tanımlayıcıyla eşleşen ve tanımlayıcının eşleme değerine sahip normal bir ifade. Örneğin "[A-Za-z0-9_#$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Alıntı yapılan tanımlayıcıların servis talebine duyarlı olarak davranılıp davranılmadığını gösterir.|  
|OrderbyColumnsInSelect|bool|ORDER BY yan tümcesindeki sütunların seçili listede olup olmadığını belirtir. True değeri, seçme listesinde olmaları gerektiğini gösterir, yanlış bir değer, seçme listesinde olmaları gerekmediğini gösterir.|  
|ParametreMarkerFormat|string|Parametrenin nasıl biçimlendirilebildiğini gösteren biçim dizesi.<br /><br /> Adlandırılmış parametreler veri kaynağı tarafından desteklenirse, bu dizedeki ilk yer tutucu parametre adının biçimlendirilmesi gereken yer olmalıdır.<br /><br /> Örneğin, veri kaynağı parametrelerin adlandırılmasını ve ':' ile önceden belirlenmiş{0}olmasını bekliyorsa, bu ": ". Bunu "p1" parametre adı ile biçimlendirirken elde edilen dize ":p1"dir.<br /><br /> Veri kaynağı parametrelerin ' '\@ile önceden belirlenmiş olmasını bekliyorsa, ancak{0}adlar bunları zaten içeriyorsa, bu\@' 've "\@p1" adlı bir parametrebiçimlendirmesonucu sadece " p1" olacaktır.<br /><br /> Adlandırılmış parametreleri beklemeyen ve '?' karakterinin kullanılmasını bekleyen veri kaynakları için biçim dizesi, parametre adını yok sayan basitçe '?' olarak belirtilebilir. OLE DB için biz '?'.|  
|ParametreMarkerPattern|string|Parametre işaretçisi ile eşleşen normal bir ifade. Varsa parametre adının eşleme değerine sahip olacaktır.<br /><br /> Örneğin, adlandırılmış parametreler parametre adına\@eklenecek bir ' '' ana-in karakteriyle desteklenirse,\@bu şu olur: "( [A-Za-z0-9_$#]*)".<br /><br /> Ancak, adlandırılmış parametreler baş karakter olarak ':' ile desteklenirse ve parametre adının bir parçası değilse, bu şu olur: ":([A-Za-z0-9_$#]\*)".<br /><br /> Tabii ki, veri kaynağı adlı parametreleri desteklemiyorsa, bu sadece "?".|  
|ParametreNameMaxLength|int|Karakterlerdeki bir parametre adının maksimum uzunluğu. Visual Studio, parametre adları desteklenirse, en yüksek uzunluk için minimum değerin 30 karakter olmasını bekler.<br /><br /> Veri kaynağı adlandırılmış parametreleri desteklemiyorsa, bu özellik sıfır döndürür.|  
|ParametreName Deseni|string|Geçerli parametre adlarıyla eşleşen normal bir ifade. Farklı veri kaynakları, parametre adları için kullanılabilecek karakterlerle ilgili farklı kurallara sahiptir.<br /><br /> Visual Studio, parametre adları desteklenirse, "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" karakterlerinin parametre adları için geçerli olan en az desteklenen karakter kümesi olmasını bekler.|  
|AlıntıIdentifierPattern|string|Teklif edilen bir tanımlayıcıyla eşleşen ve tırnak işaretleri olmadan tanımlayıcının kendisiyle eşleşen normal bir ifade. Örneğin, veri kaynağı teklif edilen tanımlayıcıları tanımlamak için çift tırnak kullanırsa, bu şu\\olurdu: \\"(([^ "]&#124;")*)".\\|  
|AlıntıIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Alıntı yapılan tanımlayıcıların servis talebine duyarlı olarak davranılıp davranılmadığını gösterir.|  
|İfadeSeparatorPattern|string|İfade ayırıcıyla eşleşen normal bir ifade.|  
|StringLiteralPattern|string|Bir dize harfiyle eşleşen ve edebi değere sahip normal bir ifade. Örneğin, veri kaynağı dizeleri tanımlamak için tek tırnak kullanılırsa, bu olurdu: "('([^']&#124;')*'"'|  
|Desteklenen JoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Veri kaynağı tarafından hangi SQL birleştirme deyimlerinin destekleniyi belirtir.|  
  
## <a name="datatypes"></a>Veri Türleri  
 Bu şema koleksiyonu, .NET Framework yönetilen sağlayıcısının şu anda bağlı olduğu veritabanı tarafından desteklenen veri türleri hakkındaki bilgileri ortaya çıkarır.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TypeName|string|Sağlayıcıya özgü veri türü adı.|  
|SağlayıcıDbType|int|Bir parametrenin türünü belirtirken kullanılması gereken sağlayıcıya özgü tür değeri. Örneğin, SqlDbType.Money veya OracleType.Blob.|  
|Columnsize|long|Sayısal olmayan bir sütunun veya parametrenin uzunluğu, sağlayıcı tarafından bu tür için tanımlanan maksimum veya uzunluk anlamına gelir.<br /><br /> Karakter verileri için bu, veri kaynağı tarafından tanımlanan birimlerdeki maksimum veya tanımlanmış uzunluktur. Oracle bir uzunluk belirtme ve sonra bazı karakter veri türleri için gerçek depolama boyutunu belirtme kavramı vardır. Bu, Yalnızca Oracle için birimlerdeki uzunluğu tanımlar.<br /><br /> Tarih-saat veri türleri için bu dize gösteriminin uzunluğudur (kesirli saniye bileşeninin izin verilen maksimum hassasiyetini varsayarsak).<br /><br /> Veri türü sayısalsa, bu veri türünün maksimum hassasiyetinde üst sınırdır.|  
|CreateFormat|string|CREATE TABLE gibi veri tanımı deyimine bu sütunun nasıl ekleyeceğini gösteren biçim dizesi. CreateParameter dizisindeki her öğe biçim dizesinde bir "parametre işaretçisi" ile temsil edilmelidir.<br /><br /> Örneğin, SQL veri türü DECIMAL bir kesinlik ve bir ölçek gerekir. Bu durumda, biçim dizesi "DECIMAL(,{0}{1})" olacaktır.|  
|Oluşturma Parametreleri|string|Bu veri türünden bir sütun oluştururken belirtilmesi gereken oluşturma parametreleri. Her oluşturma parametresi, sağlanacakları sırada virgülle ayrılmış dizede listelenir.<br /><br /> Örneğin, SQL veri türü DECIMAL bir kesinlik ve bir ölçek gerekir. Bu durumda, oluşturma parametreleri "hassas, ölçek" dizesini içermelidir.<br /><br /> 10 ve 2 ölçeğinde bir ONDALIK sütun oluşturmak için bir metin komutunda, CreateFormat sütununun{0}değeri{1}ONDALIK olabilir( , )" ve tam tür belirtimi ONDALIK (10,2) olacaktır.|  
|DataType|string|Veri türünün .NET Framework türünün adı.|  
|IsAutoincrementable|bool|true—Bu veri türünün değerleri otomatik olarak artabilir.<br /><br /> false—Bu veri türünün değerleri otomatik olarak artmayabilir.<br /><br /> Bunun yalnızca bu veri türündeki bir sütunun otomatik artış yapıp olmadığını gösterir, bu türdeki tüm sütunların otomatik artış olduğunu değil.|  
|IsBestMatch|bool|doğru—Veri türü, veri deposundaki tüm veri türleri ile DataType sütunundaki değerle gösterilen .NET Framework veri türü arasındaki en iyi eşleşmedir.<br /><br /> yanlış-veri türü en iyi eşleşme değildir.<br /><br /> DataType sütununun değerinin aynı olduğu her satır kümesi için, IsBestMatch sütunu yalnızca bir satırda gerçek olarak ayarlanır.|  
|IsCaseSensitive|bool|true—Veri türü bir karakter türüdür ve büyük/küçük harf duyarlıdır.<br /><br /> false—Veri türü bir karakter türü değildir veya büyük/küçük harf duyarlı değildir.|  
|IsFixedLength|bool|true—Veri tanım dili (DDL) tarafından oluşturulan bu veri türünün sütunları sabit uzunlukta olacaktır.<br /><br /> false—DDL tarafından oluşturulan bu veri türünün sütunları değişken uzunlukta olacaktır.<br /><br /> DBNull.Value—Sağlayıcının bu alanı sabit uzunlukta veya değişken uzunlukta bir sütunla eşleyip haritalandırmayacağı bilinmemektedir.|  
|IsfixedPrecisionScale|bool|doğru—Veri türünün sabit bir hassasiyeti ve ölçeği vardır.<br /><br /> yanlış-Veri türünün sabit bir hassasiyeti ve ölçeği yoktur.|  
|ıslong|bool|doğru—Veri türü çok uzun veriler içerir; çok uzun verilerin tanımı sağlayıcıya özgüdür.<br /><br /> yanlış-Veri türü çok uzun veri içermez.|  
|ısnullable|bool|doğru—Veri türü geçersizdir.<br /><br /> yanlış-Veri türü nullable değildir.<br /><br /> DBNull.Value—Veri türünün geçersiz olup olmadığı bilinmemektedir.|  
|IsSearchable|bool|true—Veri türü, LIKE yüklemi dışında herhangi bir işleçle WHERE yan tümcesinde kullanılabilir.<br /><br /> false—Veri türü, LIKE yüklemi dışında herhangi bir işleçle WHERE yan tümcesinde kullanılamaz.|  
|IsSearchableWithLike|bool|true—Veri türü LIKE yüklemi ile kullanılabilir<br /><br /> false—Veri türü LIKE yüklemi ile kullanılamaz.|  
|İmzalandı|bool|true—Veri türü imzasızdır.<br /><br /> false—Veri türü imzalanır.<br /><br /> DBNull.Value—Veri türü için geçerli değildir.|  
|Maximumscale|short|Tür göstergesi sayısal bir türse, bu ondalık noktanın sağında izin verilen en büyük basamak sayısıdır. Aksi takdirde, bu DBNull.Value olduğunu.|  
|Minimumscale|short|Tür göstergesi sayısal bir türse, bu ondalık noktanın sağında izin verilen en az basamak sayısıdır. Aksi takdirde, bu DBNull.Value olduğunu.|  
|IsConcurrencyType|bool|true – satır her değiştirilse ve sütunun değeri önceki tüm değerlerden farklı olduğunda veri türü veritabanı tarafından güncelleştirilir<br /><br /> false – satır her değiştiğinde veri türü veritabanı tarafından güncelleştirilen not<br /><br /> DBNull.Value – veritabanı bu tür veri türünü desteklemiyor|  
|IsLiteralDestekli|bool|doğru – veri türü gerçek bir<br /><br /> yanlış – veri türü gerçek bir ifade edilemez|  
|LiteralPrefix|string|Önek belirli bir literal uygulanır.|  
|LiteralSuffix|string|Belirli bir edebi uygulanan sonek.|  
|NativeDataType|Dize|NativeDataType veri türünün OLE DB türünü açığa çıkarmak için bir OLE DB özel sütundur.|  
  
## <a name="restrictions"></a>Kısıtlamalar  
 Bu şema koleksiyonu, veritabanına bağlanmak için şu anda kullanılan .NET Framework yönetilen sağlayıcısı tarafından desteklenen kısıtlamalar hakkında bilgi açığa çıkardı.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|CollectionName|string|Bu kısıtlamaların geçerli olduğu koleksiyonun adı.|  
|Kısıtlama Adı|string|Koleksiyondaki kısıtlamanın adı.|  
|KısıtlamaVarsayılan|string|Göz ardı.|  
|Kısıtlama Numarası|int|Bu kısıtlamanın düştüğü koleksiyon kısıtlamalarındaki gerçek konum.|  
  
## <a name="reservedwords"></a>Ayrılmış Kelimeler  
 Bu şema koleksiyonu, şu anda bağlı olan .NET Framework yönetilen sağlayıcısının veritabanı tarafından ayrılmış sözcükler hakkındaki bilgileri ortaya çıkarır.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|Ayrılmış Word|string|Sağlayıcı belirli ayrılmış sözcük.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [GetSchema ve Şema Koleksiyonları](getschema-and-schema-collections.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
