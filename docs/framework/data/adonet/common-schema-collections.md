---
title: Ortak şema koleksiyonları
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: 29ccd2af4268a86ae4c2047ad2523f68b0f6489e
ms.sourcegitcommit: a474397fd4de822f0d878d86d907e49763872b0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2018
ms.locfileid: "37072130"
---
# <a name="common-schema-collections"></a>Ortak şema koleksiyonları
Ortak şema koleksiyonları her .NET Framework yönetilen sağlayıcıları tarafından uygulanan şema koleksiyonlarıdır. Desteklenen şema koleksiyonları listesi çağırarak belirlemek için bir .NET Framework yönetilen sağlayıcı sorgulayabilirsiniz **GetSchema** yöntemi bağımsız değişken olmadan veya şema koleksiyonu adı "MetaDataCollections". Bu döndürür bir <xref:System.Data.DataTable> listesiyle desteklenen şema koleksiyonları, desteklediği her kısıtlama sayısı ve kullandıkları tanımlayıcısı parçaların sayısı. Bu koleksiyonlar tüm gerekli sütunlar açıklanmaktadır. Sağlayıcıları istedikleri ek sütunlar eklemek ücretsizdir. Örneğin, `SqlClient` ve `OracleClient` ParameterName kısıtlamaları koleksiyona ekleyin.  
  
 Bir sağlayıcı gerekli bir sütunun değeri belirlenemiyor ise null döndürür.  
  
 Kullanma hakkında daha fazla bilgi için **GetSchema** yöntemleri bkz [GetSchema ve şema koleksiyonları](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  
 Bu şema koleksiyonu, tüm veritabanına bağlanmak için kullanılan .NET Framework yönetilen sağlayıcı tarafından desteklenen şema koleksiyonları hakkında bilgiler sunar.  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|CollectionName|dize|Geçirilecek koleksiyonun adı **GetSchema** koleksiyon döndürmek için yöntemi.|  
|NumberOfRestrictions|int|Koleksiyon için belirtilebilir kısıtlama sayısı.|  
|NumberOfIdentifierParts|int|Bileşik tanımlayıcısı/veritabanı nesne adı bölümlerinde sayısı. Örneğin, sütun için tablolar için 3 ve 4'da bu bir SQL Server'da olacaktır. Oracle, tablolar için 2 ve 3 sütunlar için olacaktır.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  
 Bu şema koleksiyonu, şu anda yönetilen sağlayıcı olan .NET Framework bağlanmak için veri kaynağı hakkında bilgi gösterir.  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|CompositeIdentifierSeparatorPattern|dize|Bileşik bir tanımlayıcıda bileşik ayırıcılar eşleştirilecek normal ifade. Örneğin, "\\." (için SQL Server) veya "\@&#124;\\." (Oracle için).<br /><br /> Bir bileşik genellikle ne örnek bir veritabanı nesne adı için kullanılan tanımlayıcıdır: pubs.dbo.authors ya da pubs\@dbo.authors.<br /><br /> SQL Server için normal ifade kullanın "\\.". OracleClient için kullanma "\@&#124;\\.".<br /><br /> ODBC için Catalog_name_seperator kullanın.<br /><br /> OLE DB için DBLITERAL_CATALOG_SEPARATOR veya DBLITERAL_SCHEMA_SEPARATOR kullanın.|  
|DataSourceProductName|dize|"Oracle" veya "SQLServer" gibi bir sağlayıcı tarafından erişilen ürünün adı.|  
|DataSourceProductVersion|dize|Veri kaynakları yerel biçiminde ve Microsoft biçiminde sağlayıcısı tarafından erişilen ürün sürümünü gösterir.<br /><br /> Bazı durumlarda, aynı değeri DataSourceProductVersion ve DataSourceProductVersionNormalized olacaktır. Aynı temel alınan yerel API işlev çağrısı için eşleştirilen OLE DB ve ODBC söz konusu olduğunda, bunlar her zaman aynı olacaktır.|  
|DataSourceProductVersionNormalized|dize|Normalleştirilmiş bir sürüm için veri kaynağı ile karşılaştırılabilir şekilde `String.Compare()`. Bu biçim sağlayıcısı sürüm 10, sürüm 1 ve sürüm 2 sıralamasını önlemek için tüm sürümleri için tutarlıdır.<br /><br /> Örneğin, Oracle sağlayıcısı "nn.nn.nn.nn.nn" biçiminin Oracle 8i veri kaynağı "08.01.07.04.01" döndürmesine neden olur, normalleştirilmiş sürümü için kullanır. SQL Server, Microsoft "nn.nn.nnnn" biçim kullanır.<br /><br /> Bazı durumlarda, aynı değeri DataSourceProductVersion ve DataSourceProductVersionNormalized olacaktır. Aynı temel alınan yerel API işlev çağrısı için eşleştirilen OLE DB ve ODBC söz konusu olduğunda bunlar her zaman aynı olacaktır.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|Seçim listesindeki bir GROUP BY yan tümcesindeki sütun ve toplu olmayan sütunları arasındaki ilişkiyi belirtir.|  
|IdentifierPattern|dize|Eşleşen bir tanımlayıcı ve tanımlayıcı bir eşleşme değerine sahip bir normal ifade. Örneğin "[A-Za-z0-9_ #$]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Tırnak içinde olmayan tanımlayıcıları olarak büyük küçük harfe duyarlı veya kabul edilip edilmeyeceğini belirtir.|  
|OrderByColumnsInSelect|bool|Seçim listesinde ORDER BY yan tümcesindeki sütun olması gerekip gerekmediğini belirtir. True değerini gösterir: seçim listesinde olması gerektiği, bunlar seçim listesinde olması gerekmez, false değeri gösterir.|  
|ParameterMarkerFormat|dize|Bir parametre biçimine temsil eden bir biçim dizesi.<br /><br /> Adlandırılmış parametreler veri kaynağı tarafından destekleniyorsa, bu dizenin ilk yer tutucuyu parametre adı burada biçimlendirilmiş olmalıdır.<br /><br /> Örneğin, veri kaynağı adlı ve ön ekine sahip parametre bekliyor bir ':' Bu ":{0}". Bu sonuç "p1" parametre adı ile biçimlendirilirken bir dizedir ": p1".<br /><br /> Veri kaynağı ile önek için parametreler bekliyor durumunda '\@', ancak bunları adları zaten dahil, bu '{0}', adlı bir parametre biçimlendirme sonucu "\@p1" yalnızca olacaktır "\@p1".<br /><br /> Adlandırılmış parametreler beklediğiniz ve kullanımını beklediğiniz veri kaynakları için '?' karakter, biçim dizesi olarak belirtilebilir '?', parametre adı yoksayacaktır. OLE DB için size dönüş '?'.|  
|ParameterMarkerPattern|dize|Bir parametre işaretçisi eşleşen normal bir ifade. Varsa, parametre adının bir eşleşme değerine sahip olacaktır.<br /><br /> Adlandırılmış parametreler ile destekleniyorsa, örneğin, bir '\@' dahil edilecek öncü karakter parametre adı, bu olacaktır: "(\@[A-Za-z0-9_$ #] *)".<br /><br /> Ancak, adlandırılmış parametreler ile destekleniyorsa, bir ':' parametre adı bir parçası ve öncü karakteri değil gibi olacaktır: ": ([A-Za-z0-9_$ #]\*)".<br /><br /> Elbette, veri kaynağı adlandırılmış parametreler desteklemiyorsa, bu yalnızca olabilir "?".|  
|ParameterNameMaxLength|int|Bir parametre adı karakter cinsinden en büyük uzunluğu. Visual Studio, parametre adları destekleniyorsa, en düşük değer uzunluğu üst sınırı 30 karakter olduğunu bekliyor.<br /><br /> Veri kaynağı adlandırılmış parametreleri desteklemez, bu özelliği sıfır döndürür.|  
|ParameterNamePattern|dize|Geçerli parametre adları eşleşen normal bir ifade. Farklı veri kaynakları, parametre adları için kullanılan karakter ile ilgili farklı kuralları vardır.<br /><br /> Visual Studio, parametre adları destekleniyorsa, "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" karakterlerin en düşük desteklenen parametre adları için geçersiz bir karakter kümesini olduğunu bekliyor.|  
|QuotedIdentifierPattern|dize|Tırnak işaretli tanımlayıcı eşleşir ve bir eşleşme değeri tırnak işaretleri olmadan tanımlayıcısının kendisini normal bir ifade. Veri kaynağı tırnak işaretli tanımlayıcılar tanımlamak için çift tırnak kullandıysanız, bu gibi olacaktır: "(([^\\"]&#124;\\"\\") *) ".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Tırnak işaretli tanımlayıcılar olarak büyük küçük harfe duyarlı veya kabul edilip edilmeyeceğini belirtir.|  
|StatementSeparatorPattern|dize|Deyim ayırıcısı eşleşen normal bir ifade.|  
|StringLiteralPattern|dize|Bir dize sabit değeri ile eşleşen ve sabit değerinin eşleşen değeri normal bir ifade. Veri kaynağı, dizeleri bulmak için tek tırnak işaretleri kullandıysanız, bu gibi olacaktır: "('([^']&#124;'') *')"'|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|SQL birleştirme deyimleri hangi türde veri kaynağı tarafından desteklenen belirtir.|  
  
## <a name="datatypes"></a>Veri türleri  
 .NET Framework sağlayıcısı yönetilen veritabanı tarafından desteklenen veri türleri hakkındaki bu şema koleksiyonu kullanıma sunan bilgileri şu anda bağlı.  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|TypeName|dize|Sağlayıcıya özel veri türü adı.|  
|ProviderDbType|int|Bir parametrenin türünü belirtmek için kullanılması gereken sağlayıcıya özgü türü değeri. Örneğin, SqlDbType.Money veya OracleType.Blob.|  
|ColumnSize|long|Sayısal olmayan sütun veya parametre uzunluğu üst sınırı veya bu tür için sağlayıcı tarafından tanımlanan uzunluk ifade eder.<br /><br /> Karakter verileri için en büyük veya bu birimleri, veri kaynağı tarafından tanımlanan uzunluk tanımlanan. Oracle belirten bir uzunluk ve bazı karakter veri türleri için gerçek depolama boyutunu belirterek kavramı vardır. Bu yalnızca uzunluğu, Oracle için birimi tanımlar.<br /><br /> Tarih-saat veri türleri için (Kesirli saniye bileşeni izin verilen duyarlık üst sınırını varsayılarak) dize gösteriminin uzunluğu budur.<br /><br /> Veri türü sayısal, bu veri türünün verilen duyarlık üst sınırı ise.|  
|CreateFormat|dize|Bu sütun bir veri tanımı ifadesi CREATE TABLE gibi ekleme temsil eden bir biçim dizesi. CreateParameter dizideki her öğe Biçim dizesinde "parametre işaretleyici" tarafından temsil edilebilir.<br /><br /> Örneğin, SQL veri türünü ondalık bir kesinlik ve ölçek gerekir. Bu durumda, biçim dizesi olabilir "ondalık ({0},{1})".|  
|CreateParameters|dize|Bu veri türünde bir sütun oluştururken belirtilmelidir oluşturma parametreleri. Her oluşturma parametresi sağlanacak oldukları sırada bir virgülle ayrılmış bir dize içinde listelenir.<br /><br /> Örneğin, SQL veri türünü ondalık bir kesinlik ve ölçek gerekir. Bu durumda, oluşturma parametreleri "duyarlığı, Ölçek" dize içermesi gerekir.<br /><br /> Bir metin komut 10 kesinliği 2'in bir ölçek ile ondalık bir sütun oluşturmak için CreateFormat sütununun değerini ondalık olabilir ({0},{1}) "ve tam bir tür belirtimi DECIMAL(10,2) olacaktır.|  
|Veri türü|dize|.NET Framework türü veri türünün adı.|  
|IsAutoincrementable|bool|TRUE: otomatik artan değerleri bu veri türünde olabilir.<br /><br /> False-Bu veri türünün değerlerini otomatik olarak artırma olmayabilir.<br /><br /> Bu yalnızca otomatik artan bir sütun bu veri türü olabilir olup olmadığını belirtir, Not Bu türdeki tüm sütunları otomatik artan değil.|  
|IsBestMatch|bool|TRUE: veri deposunda tüm veri türleri ve veri türü sütunundaki değeri tarafından belirtilen .NET Framework veri türü arasında en iyi eşleşme veri türüdür.<br /><br /> false-veri türü en iyi eşleşmeyi değil.<br /><br /> Her veri türü sütununun değeri olduğu aynı satır kümesi için IsBestMatch sütun kümesi tek bir satırda true.|  
|IsCaseSensitive|bool|TRUE: veri türü bir karakter türüdür ve büyük küçük harfe duyarlıdır.<br /><br /> false-veri türü bir karakter türü değil ya da büyük küçük harfe duyarlı değildir.|  
|Isfixedlength|bool|TRUE: veri tanımlama dili (DDL) tarafından oluşturulan bu veri türünde sütunlar sabit uzunluk olur.<br /><br /> false-DDL tarafından oluşturulan bu veri türünde sütunlar, değişken uzunluğu olacaktır.<br /><br /> Sağlayıcı bu alanı, sabit uzunluklu veya değişken uzunluklu bir sütun eşleme olmadığını DBNull.Value—It bilinmiyor.|  
|IsFixedPrecisionScale|bool|TRUE; bir sabit kesinlik ve ölçek veri türüne sahip.<br /><br /> false-veri türü, bir sabit kesinlik ve ölçek yok.|  
|IsLong|bool|TRUE — uzun veri; veri türü içeriyor sağlayıcıya özgü çok uzun veri tanımıdır.<br /><br /> false-veri türü çok uzun veri içermiyor.|  
|IsNullable|bool|TRUE: veri türü null olabilir.<br /><br /> false-veri türü null olabilir değil.<br /><br /> Veri türü boş değer atanabilir olup olmadığını DBNull.Value—It bilinmiyor.|  
|Issearchable ayarı|bool|TRUE: veri türü, WHERE yan tümcesinde LIKE dışında herhangi bir işleci ile kullanılabilir.<br /><br /> false-veri türü ile LIKE dışında herhangi bir işleç bir WHERE yan tümcesinde kullanılamaz.|  
|IsSearchableWithLike|bool|TRUE: veri türü LIKE ile kullanılabilir<br /><br /> false-veri türü LIKE ile kullanılamaz.|  
|IsUnsigned|bool|TRUE: veri türü imzalanmamış.<br /><br /> false-veri türü imzalanır.<br /><br /> DBNull.Value—Not veri türü için uygulanabilir.|  
|MaximumScale|short|Türü göstergesi bir sayısal türü ise, izin verilen ondalık noktasının sağındaki basamak sayısı budur. Aksi takdirde, DBNull.Value budur.|  
|MinimumScale|short|Türü göstergesi bir sayısal türü ise, Ondalık ayırıcının sağında izin basamak sayısı alt sınırını budur. Aksi takdirde, DBNull.Value budur.|  
|IsConcurrencyType|bool|doğru – veri türü veritabanı tarafından her zaman satır değiştirilir ve sütununun değerini, önceki tüm değerlerinden farklıdır güncelleştirilir<br /><br /> yanlış – veri türü Not satırın her değiştiğinde veritabanı tarafından güncelleştirilmiş olur<br /><br /> DBNull.Value – veritabanı bu tür veri türünü desteklemiyor|  
|IsLiteralSupported|bool|doğru – veri türünün değişmez değer olarak ifade edilebilir<br /><br /> yanlış – veri türünün değişmez değer olarak ifade edilebilir değil|  
|LiteralPrefix|dize|Belirli bir sabit değer için uygulanan önek.|  
|LiteralSuffix|dize|Belirli bir sabit değer için uygulanan soneki.|  
|NativeDataType|Dize|NativeDataType OLE DB veri türü türünü kullanıma sunmak için bir OLE DB belirli bir sütundur.|  
  
## <a name="restrictions"></a>Kısıtlamalar  
 Veritabanına bağlanmak için kullanılan .NET Framework yönetilen sağlayıcı tarafından desteklenen kısıtlamaları hakkında bilgi için bu şema koleksiyonu ortaya çıkar.  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|CollectionName|dize|Bu kısıtlamalar geçerli koleksiyonun adı.|  
|RestrictionName|dize|Koleksiyondaki kısıtlama adı.|  
|RestrictionDefault|dize|Yoksayıldı.|  
|RestrictionNumber|int|Bu belirli kısıtlama döner, koleksiyonları kısıtlamaları gerçek konumu.|  
  
## <a name="reservedwords"></a>ReservedWords  
 Bu şema koleksiyonu, şu anda bağlı sağlayıcı .NET Framework yönetilen veritabanı tarafından ayrılmış sözcükler hakkında bilgi gösterir.  
  
|ColumnName|Veri türü|Açıklama|  
|----------------|--------------|-----------------|  
|ReservedWord|dize|Sağlayıcı özel amaçlı sözcük.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [GetSchema ve Şema Koleksiyonları](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
