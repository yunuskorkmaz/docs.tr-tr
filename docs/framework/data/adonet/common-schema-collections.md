---
title: Ortak şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: fc8b581a127fbef0f32cdee53eaa62d241e4ae31
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="common-schema-collections"></a>Ortak şema koleksiyonları
Ortak şema koleksiyonları her .NET çerçevesi ile yönetilen sağlayıcıları tarafından uygulanan şema koleksiyonlarıdır. Çağıran desteklenen şema koleksiyonları listesini belirlemek için bir .NET Framework yönetilen sağlayıcısı sorgulayabilirsiniz **GetSchema** yöntemi bağımsız değişken içermeyen veya şema koleksiyonu adı "MetaDataCollections". Bu döndürülecek bir <xref:System.Data.DataTable> desteklenen şeması koleksiyonları, her destekledikleri kısıtlama sayısı ve kullandıkları tanımlayıcı bölümlerinin sayısını listesini içeren. Bu koleksiyonları tüm gerekli sütunları açıklanmaktadır. Sağlayıcıları istediklerinde ek sütunlar eklemek boş. Örneğin, `SqlClient` ve `OracleClient` ParameterName kısıtlamaları koleksiyonuna ekleyin.  
  
 Bir sağlayıcı gerekli bir sütunun değeri belirlenemiyor ise null döndürür.  
  
 Kullanma hakkında daha fazla bilgi için **GetSchema** yöntemleri bkz [GetSchema ve şeması koleksiyonları](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Bu şema koleksiyonu tüm veritabanına bağlanmak için kullanılan .NET Framework yönetilen sağlayıcısı tarafından desteklenen şema koleksiyonları hakkında bilgiler sunar.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|CollectionName|dize|Geçirilecek koleksiyonunun adı **GetSchema** koleksiyon döndürmek için yöntem.|  
|NumberOfRestrictions|int|Koleksiyon için belirtilen kısıtlamaları sayısı.|  
|NumberOfIdentifierParts|int|Bileşik Tanımlayıcı/veritabanı nesne adı bölümlerinde sayısı. Örneğin, tabloları için 3 ve 4 sütunlar için'da bu bir SQL Server'da olacaktır. Oracle, tablolar için 2 ve 3 sütunlar için olacaktır.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Bu şema koleksiyonu yönetilen şu anda sağlayıcısıdır .NET Framework bağlanmak için veri kaynağı ile ilgili bilgileri gösterir.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|dize|Bileşik ayırıcı bileşik bir tanımlayıcı olarak eşleştirilecek normal ifade. Örneğin, "\\." (için SQL Server) veya "@&#124;\\." (Oracle için).<br /><br /> Bileşik bir tanımlayıcı genellikle ne için veritabanı nesne adı, örneğin kullanılır: pubs.dbo.authors veya pubs@dbo.authors.<br /><br /> SQL Server için normal ifade kullanın "\\.". OracleClient için kullanma "@&#124;\\.".<br /><br /> ODBC için Catalog_name_seperator kullanın.<br /><br /> OLE DB için DBLITERAL_CATALOG_SEPARATOR veya DBLITERAL_SCHEMA_SEPARATOR kullanın.|  
|DataSourceProductName|dize|"Oracle" veya "SQLServer" gibi sağlayıcısı tarafından erişilen ürünün adı.|  
|DataSourceProductVersion|dize|Veri kaynakları yerel biçiminde ve Microsoft biçiminde değil sağlayıcısı tarafından erişilen ürünün sürümünü gösterir.<br /><br /> Bazı durumlarda, DataSourceProductVersion ve DataSourceProductVersionNormalized aynı değer olacaktır. Temel alınan yerel API'sindeki aynı işlev çağrısı için eşlenmiş olarak OLE DB ve ODBC söz konusu olduğunda, bu her zaman aynı olacaktır.|  
|DataSourceProductVersionNormalized|dize|Verileri için normalleştirilmiş bir sürümü kaynak ile karşılaştırılabilir şekilde `String.Compare()`. Bu sürüm 1 ve sürüm 2 arasında sıralamasını sürüm 10 önlemek için Sağlayıcı'nin tüm sürümleri için tutarlı biçimidir.<br /><br /> Örneğin, Oracle sağlayıcısı Oracle 8i veri kaynağı "08.01.07.04.01" döndürülecek neden olan kendi normalleştirilmiş sürümü için "nn.nn.nn.nn.nn" biçimini kullanır. SQL Server normal Microsoft "nn.nn.nnnn" biçimini kullanır.<br /><br /> Bazı durumlarda, DataSourceProductVersion ve DataSourceProductVersionNormalized aynı değer olacaktır. Temel alınan yerel API'sindeki aynı işlev çağrısı için eşlenmiş olarak OLE DB ve ODBC söz konusu olduğunda bu her zaman aynı olacaktır.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Seçim listesindeki bir GROUP BY yan tümcesinde sütunlar ve toplanan olmayan sütunlar arasındaki ilişkiyi belirtir.|  
|IdentifierPattern|dize|Bir tanımlayıcı ile eşleşen ve tanımlayıcısı eşleşme değerine sahip bir normal ifade. Örneğin, "[A-Za-z0-9_ #$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Tırnak işaretli olmayan tanıtıcıları olarak büyük küçük harfe duyarlı olmadığı kabul edilip edilmeyeceğini belirtir.|  
|OrderByColumnsInSelect|bool|Seçim listesinde ORDER BY yan tümcesi sütunlarında olması gerekip gerekmediğini belirtir. Doğru değeri, seçim listesinde olması gerekir, false değeri, seçim listesinde olması gerekmez gösterir gösterir.|  
|ParameterMarkerFormat|dize|Bir parametre biçimlendirme temsil eden bir biçim dizesi.<br /><br /> Adlandırılmış parametreleri veri kaynağı tarafından destekleniyorsa, bu dizenin ilk yer tutucuyu parametre adı burada biçimlendirilmiş olması gerekir.<br /><br /> Örneğin, veri kaynağı adlı ve önekine sahip parametreleri görüyorsa bir ':' Bu olur ":{0}". Bu parametre adı "p1" ile elde edilen biçimlendirirken dizedir ": p1".<br /><br /> Veri kaynağı ile önek için parametre bekliyor varsa ' @', ancak adlarını bunları zaten içerir, bu olacaktır '{0}' ve adlı bir parametre biçimlendirme sonucu "@p1"yalnızca olacaktır"@p1".<br /><br /> Adlandırılmış parametreler beklediğiniz ve kullanımını beklediğiniz veri kaynakları için '?' karakter, biçim dizesi basit belirtilebilir '?', parametre adı yoksayacaktır. OLE DB için döndürürüz '?'.|  
|ParameterMarkerPattern|dize|Bir parametre işaretçisi eşleşen normal bir ifade. Varsa, parametre adı bir eşleşme değeri olur.<br /><br /> Örneğin, adlandırılmış parametreleri ile desteklenen bir '\@' eklenecek öncü karakter parametre adı bu olur: "(\@[A-Za-z0-9_$ #]*)".<br /><br /> Ancak, adlandırılmış parametreleri ile destekleniyorsa, bir ':' parametre adı parçası öncü karakter ve değil gibi bu olur: ": ([A-Za-z0-9_$ #]\*)".<br /><br /> Elbette, veri kaynağı adlandırılmış parametreleri desteklemiyorsa, bu yalnızca olur "?".|  
|ParameterNameMaxLength|int|Bir parametre adı karakter cinsinden en büyük uzunluğu. Visual Studio parametre adları destekleniyorsa, en fazla uzunluğu için en düşük değer 30 karakter olduğunu bekliyor.<br /><br /> Veri kaynağı adlandırılmış parametreleri desteklemiyorsa bu özellik sıfır döndürür.|  
|ParameterNamePattern|dize|Geçerli parametre adları eşleşen normal bir ifade. Farklı veri kaynakları için parametre adları kullanılabilir karakterleri ilgili farklı kuralları vardır.<br /><br /> Visual Studio parametre adları destekleniyorsa, "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" karakterlerin en düşük desteklenen parametre adları için geçerli bir karakter kümesini olduğunu bekliyor.|  
|QuotedIdentifierPattern|dize|Tırnak işaretli tanımlayıcısıyla eşleşip ve tırnak işaretleri olmadan tanımlayıcı kendisini eşleşme değerine sahip bir normal ifade. Örneğin, veri kaynağı çift tırnak tırnak işaretli tanımlayıcılar tanımlamak için kullanılan bu şöyle olur: "(([^\\"]&#124;\\"\\") *) ".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Tırnak işaretli tanımlayıcılar olarak büyük küçük harfe duyarlı olmadığı kabul edilip edilmeyeceğini belirtir.|  
|StatementSeparatorPattern|dize|Deyimi ayırıcı eşleşen normal bir ifade.|  
|StringLiteralPattern|dize|Bir değişmez dize değeri ile eşleşen ve sabit bir eşleşme değerine sahip bir normal ifade. Örneğin, veri kaynağı tek tırnak işareti dizeleri tanımlamak için kullanılan bu şöyle olur: "('([^']&#124;'') *')"'|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|SQL birleştirme deyimleri hangi türde veri kaynağı tarafından desteklenen belirtir.|  
  
## <a name="datatypes"></a>Veri türleri  
 Bu şema koleksiyonu çıkarır bilgileri .NET Framework sağlayıcısı yönetilen veritabanı tarafından desteklenen veri türleri hakkında şu anda bağlı.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|TypeName|dize|Sağlayıcıya özel veri türü adı.|  
|ProviderDbType|int|Bir parametrenin türünü belirtirken kullanılmalıdır sağlayıcıya özgü türü değeri. Örneğin, SqlDbType.Money veya OracleType.Blob.|  
|ColumnSize|long|Sayısal olmayan sütun veya parametre uzunluğu en fazla veya bu tür için sağlayıcı tarafından tanımlanan uzunluğunu ifade eder.<br /><br /> Karakter verileri için bu en yüksek değer veya birimler, veri kaynağı tarafından tanımlanan uzunluk tanımlı. Oracle bir uzunluk belirtme ve bazı karakter veri türleri için gerçek depolama boyutunu belirtme kavramı vardır. Bu yalnızca Oracle için birimlerindeki tanımlar.<br /><br /> Tarih-saat veri türleri için (Kesirli saniye bileşeni izin verilen en yüksek duyarlık varsayılarak) dize gösterimi uzunluğu budur.<br /><br /> Bu veri türü sayısal ise veri türünde en yüksek duyarlık üzerindeki üst sınırdır.|  
|CreateFormat|dize|CREATE TABLE gibi bir veri tanım deyimi bu sütun eklemek nasıl temsil eden biçim dizesi. CreateParameter dizideki her öğe bir "parametre işaretçisi" dize biçiminde temsil.<br /><br /> Örneğin, SQL veri türü ondalık bir duyarlık ve ölçek gerekir. Bu durumda, biçim dizesi olacaktır "ondalık ({0},{1})".|  
|CreateParameters|dize|Bu veri türünde bir sütun oluştururken belirtilmelidir oluşturma parametreleri. Her oluşturma parametre sağlanacak oldukları sırada virgülle ayrılmış bir string listelenir.<br /><br /> Örneğin, SQL veri türü ondalık bir duyarlık ve ölçek gerekir. Bu durumda, oluşturma parametreleri "duyarlık, Ölçek" dize içermesi gerekir.<br /><br /> 10 kesinliği ve ölçeği 2 ondalık bir sütun oluşturmak için bir metin komutunda, CreateFormat sütunun değeri ondalık olabilir ({0},{1}) "ve tam tür belirtimi DECIMAL(10,2) olacaktır.|  
|Veri türü|dize|.NET Framework türü veri türünün adı.|  
|IsAutoincrementable|bool|doğru — değerleri bu veri türünün otomatik artırma olabilir.<br /><br /> yanlış — değerleri bu veri türünün otomatik artırma olmayabilir.<br /><br /> Bu yalnızca otomatik artan bu veri türünde bir sütun olabilir olup olmadığını belirtir, Not Bu türdeki tüm sütunları otomatik artan değil.|  
|IsBestMatch|bool|doğru — tüm veri türlerinin veri deposunda ve veri türü sütunundaki değeri tarafından belirtilen .NET Framework veri türü arasında en iyi eşleşme veri türüdür.<br /><br /> yanlış — veri türü en iyi eşleşmeyi değil.<br /><br /> Her veri türü sütununun değeri olduğu aynı satır kümesi için IsBestMatch sütun ayarlamak tek bir satırda true.|  
|IsCaseSensitive|bool|doğru — veri türü bir karakter türü ve küçük harf duyarlıdır.<br /><br /> yanlış — veri türü bir karakter türü değil veya büyük küçük harfe duyarlı değildir.|  
|Isfixedlength|bool|doğru — veri tanımlama dili (DDL) tarafından oluşturulan bu veri türü sütunlar, sabit uzunluk olacaktır.<br /><br /> yanlış — DDL tarafından oluşturulan bu veri türü sütunlar, değişken uzunlukta olacaktır.<br /><br /> DBNull.Value—It sağlayıcı sabit uzunluklu veya değişken uzunlukta bir sütun bu alanla eşler bilinmiyor.|  
|IsFixedPrecisionScale|bool|doğru — Sabit duyarlık ve ölçek veri türüne sahip.<br /><br /> yanlış — veri türü, Sabit duyarlık ve ölçek yok.|  
|IsLong|bool|doğru — veri türü çok uzun veri içeriyorsa sağlayıcıya özgü çok uzun veri tanımıdır.<br /><br /> yanlış — veri türü çok uzun veri içermiyor.|  
|IsNullable|bool|doğru — veri türü null olabilir.<br /><br /> yanlış — veri türü null olabilir değil.<br /><br /> Veri türü null atanabilir olup olmadığını DBNull.Value—It bilinmiyor.|  
|IsSearchable|bool|doğru — veri türü, WHERE yan tümcesinde LIKE dışında herhangi bir işleç ile birlikte kullanılabilir.<br /><br /> yanlış — veri türü LIKE dışında herhangi bir işleç ile bir WHERE yan tümcesinde kullanılamaz.|  
|IsSearchableWithLike|bool|doğru — veri türü LIKE ile kullanılabilir<br /><br /> yanlış — veri türü LIKE ile kullanılamaz.|  
|IsUnsigned|bool|doğru — veri türü imzasız'dır.<br /><br /> yanlış — veri türü imzalanır.<br /><br /> DBNull.Value—Not veri türü için uygulanabilir.|  
|MaximumScale|short|Türü göstergenin sayısal bir tür ise, ondalık konumun sağında izin basamak sayısı üst sınırı budur. Aksi takdirde DBNull.Value budur.|  
|MinimumScale|short|Türü göstergenin sayısal bir tür ise, ondalık konumun sağında izin basamak sayısı alt sınırını budur. Aksi takdirde DBNull.Value budur.|  
|IsConcurrencyType|bool|doğru – veri türü veritabanı tarafından satır değiştirilir ve sütun değeri tüm önceki değerlerinden farklı her zaman güncelleştirilir<br /><br /> yanlış – veri satırı her değiştiğinde veritabanı tarafından güncelleştirilmiş not türüdür<br /><br /> DBNull.Value – veritabanı, bu tür veri türünü desteklemiyor|  
|IsLiteralSupported|bool|doğru – veri türü bir sabit değer olarak ifade edilebilir<br /><br /> yanlış – veri türü bir sabit değer olarak ifade edilebilir değil|  
|LiteralPrefix|dize|Belirli bir hazır değer için uygulanan önek.|  
|LiteralSuffix|dize|Belirli bir hazır değer için uygulanan soneki.|  
|NativeDataType|Dize|NativeDataType OLE DB veri türündeki gösterme için bir OLE DB belirli bir sütundur.|  
  
## <a name="restrictions"></a>Kısıtlamalar  
 Bu şema koleksiyonu şu anda veritabanına bağlanmak için kullanılan .NET Framework yönetilen sağlayıcısı tarafından desteklenen sınırlamaları hakkında bilgi açık.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|CollectionName|dize|Bu kısıtlamalar uygulamak koleksiyon adı.|  
|RestrictionName|dize|Koleksiyondaki kısıtlama adı.|  
|RestrictionDefault|dize|Yoksayıldı.|  
|RestrictionNumber|int|Bu belirli kısıtlama döner koleksiyonları kısıtlamaları gerçek konumu.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Bu şema koleksiyonu şu anda bağlı sağlayıcısı .NET Framework yönetilen veritabanı tarafından ayrılmış sözcükler hakkında bilgi gösterir.  
  
|columnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|ReservedWord|dize|Sağlayıcı belirli ayrılmış sözcük.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [GetSchema ve Şema Koleksiyonları](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
