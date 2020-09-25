---
title: Ortak Şema Koleksiyonları
ms.date: 03/30/2017
ms.assetid: 50127ced-2ac8-4d7a-9cd1-5c98c655ff03
ms.openlocfilehash: f822de27e53554aba4011a701f59a8feda847c67
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203819"
---
# <a name="common-schema-collections"></a>Ortak Şema Koleksiyonları

Ortak şema koleksiyonları, .NET Framework yönetilen sağlayıcıların her biri tarafından uygulanan şema koleksiyonlarıdır. .NET Framework yönetilen bir sağlayıcıyı, **GetSchema** yöntemini bağımsız değişken olmadan veya "MetaDataCollections" şema koleksiyonu adıyla çağırarak, desteklenen şema koleksiyonlarının listesini belirleyecek şekilde sorgulayabilirsiniz. Bu, <xref:System.Data.DataTable> Desteklenen şema koleksiyonlarının listesi, her birinin desteklediği kısıtlamaların sayısı ve kullandıkları tanımlayıcı bölümlerinin sayısı ile birlikte döndürülür. Bu koleksiyonlar tüm gerekli sütunları anlatmaktadır. Sağlayıcılar, isterseniz ek sütunlar eklemek için ücretsizdir. Örneğin, `SqlClient` ve öğesini `OracleClient` kısıtlamalar koleksiyonuna ekleyin.  
  
 Bir sağlayıcı gerekli bir sütunun değerini tespit leyemiyorsa, null döndürür.  
  
 **GetSchema** yöntemlerini kullanma hakkında daha fazla bilgi için bkz. [GetSchema ve Schema Collections](getschema-and-schema-collections.md).  
  
## <a name="metadatacollections"></a>MetaDataCollections  

 Bu şema koleksiyonu, veritabanına bağlanmak için şu anda kullanılan .NET Framework yönetilen sağlayıcı tarafından desteklenen tüm şema koleksiyonları hakkında bilgi sunar.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|CollectionName|string|Koleksiyonu döndürmek için **GetSchema** yöntemine geçirilecek koleksiyonun adı.|  
|NumberOfRestrictions|int|Koleksiyon için belirtime kısıtlamaların sayısı.|  
|NumberOfIdentifierParts|int|Bileşik tanımlayıcı/veritabanı nesne adındaki parçaların sayısı. Örneğin, SQL Server, bu tablo için 3 ve sütunlar için 4. Oracle 'da tablolar için 2, sütunlar için 3 olacaktır.|  
  
## <a name="datasourceinformation"></a>DataSourceInformation  

 Bu şema koleksiyonu, .NET Framework yönetilen sağlayıcının Şu anda bağlantı aldığı veri kaynağı hakkında bilgi sunar.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|Compositeıdentifierseparatormodel|string|Bileşik Tanımlayıcıdaki bileşik ayırıcıların eşleşmesi için normal ifade. Örneğin, " \\ ." (SQL Server için) veya " \@&#124;\\ ". (Oracle için).<br /><br /> Bir bileşik tanımlayıcı genellikle veritabanı nesnesi adı için kullanılır, örneğin: pubs. dbo. yazarlar veya pubs \@ dbo. yazarlar.<br /><br /> SQL Server için "." normal ifadesini kullanın \\ . OracleClient için " \@&#124;\\ ." kullanın.<br /><br /> ODBC için Catalog_name_seperator kullanın.<br /><br /> OLE DB için DBLITERAL_CATALOG_SEPARATOR veya DBLITERAL_SCHEMA_SEPARATOR kullanın.|  
|DataSourceProductName|string|Sağlayıcı tarafından erişilen ürünün adı (örneğin, "Oracle" veya "SQLServer").|  
|DataSourceProductVersion|string|Microsoft biçiminde değil, sağlayıcı tarafından erişilen ürünün sürümünü, veri kaynakları yerel biçiminde gösterir.<br /><br /> Bazı durumlarda DataSourceProductVersion ve Datasourceproductversionnormalleştirilmiş aynı değer olacaktır. OLE DB ve ODBC söz konusu olduğunda, bunlar her zaman temel alınan yerel API 'deki aynı işlev çağrısıyla eşleştirildiği gibi olacaktır.|  
|Datasourceproductversionnormalleştirilmiş|string|Veri kaynağı için, ile karşılaştırılabilmesi için normalleştirilmiş bir sürüm `String.Compare()` . Sürüm 10 ' un sürüm 1 ile sürüm 2 arasında sıralanmasını engellemek için, bu biçim, sağlayıcının tüm sürümleri için tutarlıdır.<br /><br /> Örneğin, Oracle sağlayıcısı normalleştirilmiş sürümü için "NN. nn. nn. nn. nn" biçimini kullanarak Oracle 8ı veri kaynağının "08.01.07.04.01" döndürmesini sağlar. SQL Server tipik Microsoft "NN. nn. nnnn" biçimini kullanır.<br /><br /> Bazı durumlarda, DataSourceProductVersion ve Datasourceproductversionnormalleştirilmiş aynı değer olacaktır. OLE DB ve ODBC söz konusu olduğunda, bunlar her zaman temel alınan yerel API 'de aynı işlev çağrısıyla eşleştirildiği gibi olacaktır.|  
|GroupByBehavior|<xref:System.Data.Common.GroupByBehavior>|GROUP BY yan tümcesinde sütunlar ve seçim listesindeki toplanmış olmayan sütunlar arasındaki ilişkiyi belirtir.|  
|Identifiermodel|string|Tanımlayıcıyla eşleşen ve tanımlayıcı değeri olan bir normal ifade. Örneğin, "[A-Za-z0-9_ # $]".|  
|IdentifierCase|<xref:System.Data.Common.IdentifierCase>|Tırnak işareti olmayan Tanımlayıcıların büyük/küçük harfe duyarlı olup olmadığını gösterir.|  
|OrderByColumnsInSelect|bool|ORDER BY yan tümcesindeki sütunların seçim listesinde olması gerekip gerekmediğini belirtir. Doğru değeri, seçim listesinde olması gerektiğini gösterir, yanlış değeri seçim listesinde olması gerekmediği anlamına gelir.|  
|ParameterMarkerFormat|string|Bir parametrenin nasıl biçimlendirileceğini temsil eden bir biçim dizesi.<br /><br /> Adlandırılmış parametreler veri kaynağı tarafından destekleniyorsa, bu dizedeki ilk yer tutucu parametre adının biçimlendirilmesi gereken yerde olmalıdır.<br /><br /> Örneğin, veri kaynağı parametrelerin adlandırıldığını ve ': ' önekini içeriyorsa, bu ": {0} " olur. Bunu "P1" parametre adıyla biçimlendirirken, sonuçta elde edilen dize ":p 1" dir.<br /><br /> Veri kaynağı parametrelerin ' ' önekini ön eki olmasını bekliyorsa \@ , ancak adlar zaten içeriyorsa, bu ' {0} ' olur ve "P1" adlı bir parametreyi biçimlendirmenin sonucu \@ yalnızca " \@ P1" olur.<br /><br /> Adlandırılmış parametreleri beklemediği ve '? ' karakterinin kullanımını bekleyen veri kaynakları için, biçim dizesi yalnızca '? ' olarak belirtilebilir, bu da parametre adını yoksayar. OLE DB için '? ' döndürüyoruz.|  
|Parametermarkermodel|string|Bir parametre işaretleyicisi ile eşleşen bir normal ifade. Varsa parametre adının eşleşme değerine sahip olacaktır.<br /><br /> Örneğin, adlandırılmış parametreler \@ parametre adına dahil edilecek bir ' ' bekleme karakteriyle destekleniyorsa, bu şöyle olacaktır: "( \@ [A-Za-z0-9_ $ #] *)".<br /><br /> Ancak, adlandırılmış parametreler bir ': ' ile birlikte gelen ve parametre adının bir parçası değilse, bu şöyle olacaktır: ":([A-Za-z0-9_ $ #] \* )".<br /><br /> Kuşkusuz, veri kaynağı adlandırılmış parametreleri desteklemiyorsa, bu yalnızca "?" olacaktır.|  
|ParameterNameMaxLength|int|Karakter cinsinden parametre adının uzunluk üst sınırı. Visual Studio, parametre adları desteklendiğinde, en fazla uzunluk için en düşük değer olan 30 karakterdir.<br /><br /> Veri kaynağı adlandırılmış parametreleri desteklemiyorsa, bu özellik sıfır değerini döndürür.|  
|Parameternamemodel|string|Geçerli parametre adlarıyla eşleşen bir normal ifade. Farklı veri kaynakları, parametre adları için kullanılabilecek karakterlerle ilgili farklı kurallara sahiptir.<br /><br /> Visual Studio, parametre adları desteklendiğinde, "\p{Lu}\p{Ll}\p{Lt}\p{Lm}\p{Lo}\p{Nl}\p{Nd}" karakterlerinin parametre adları için geçerli olan en düşük desteklenen karakter kümesidir.|  
|Quotedidentifiermodel|string|Tırnak içine alınmış bir tanımlayıcıyla eşleşen ve tanımlayıcı değeri tırnak işareti olmadan bir normal ifade. Örneğin, veri kaynağı tırnak işaretleri belirlemek için çift tırnak kullanıyorsa, bu şöyle olacaktır: "(([^ \\ "] &#124;\\ " \\ ") *) ".|  
|QuotedIdentifierCase|<xref:System.Data.Common.IdentifierCase>|Alıntılanmış Tanımlayıcıların büyük/küçük harfe duyarlı olup olmadığını gösterir.|  
|Statementseparatormodel|string|Deyim ayırıcısıyla eşleşen bir normal ifade.|  
|Stringedemodel|string|Bir dize sabit değeri ile eşleşen ve değişmez değeri ile eşleşen bir normal ifade. Örneğin, veri kaynağı dizeleri belirlemek için tek tırnak kullanıyorsa, bu şöyle olacaktır: "(' ([^ '] &#124; ' ') * ')" '|  
|SupportedJoinOperators|<xref:System.Data.Common.SupportedJoinOperators>|Veri kaynağı tarafından desteklenen SQL JOIN deyimlerinin türlerini belirtir.|  
  
## <a name="datatypes"></a>Türleriyle  

 Bu şema koleksiyonu, .NET Framework yönetilen sağlayıcının o anda bağlı olduğu veritabanı tarafından desteklenen veri türleri hakkında bilgi sunar.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|TypeName|string|Sağlayıcıya özgü veri türü adı.|  
|ProviderDbType|int|Bir parametrenin türünü belirtirken kullanılması gereken sağlayıcıya özgü tür değeri. Örneğin, SqlDbType. Money veya OracleType. blob.|  
|ColumnSize|long|Sayısal olmayan bir sütunun veya parametrenin uzunluğu, sağlayıcı tarafından bu tür için tanımlanan en büyük veya daha fazla uzunluğa başvurur.<br /><br /> Karakter verilerinde bu, veri kaynağı tarafından tanımlanan, birim cinsinden en yüksek veya tanımlanmış uzunluktadır. Oracle, bir uzunluk belirtme ve daha sonra bazı karakter veri türleri için gerçek depolama boyutunu belirtme kavramıdır. Bu, yalnızca Oracle için birim cinsinden uzunluğu tanımlar.<br /><br /> Tarih-saat veri türleri için, bu dize gösteriminin uzunluğudur (kesirli saniye bileşeninin izin verilen en büyük duyarlık değerini varsayarak).<br /><br /> Veri türü sayısal ise, bu, veri türünün en büyük hassasiyetinin üst sınırıdır.|  
|CreateFormat|string|Bu sütunun CREATE TABLE gibi bir veri tanımı bildirimine nasıl ekleneceğini temsil eden biçim dizesi. CreateParameter dizisindeki her öğe, biçim dizesinde bir "parametre işaretleyicisi" ile temsil edilmelidir.<br /><br /> Örneğin, SQL veri türü DECIMAL bir duyarlık ve bir ölçeğe ihtiyaç duyuyor. Bu durumda, biçim dizesi "DECIMAL ( {0} , {1} )" olacaktır.|  
|CreateParameters|string|Bu veri türünde bir sütun oluşturulurken belirtilmesi gereken oluşturma parametreleri. Her oluşturma parametresi, bir virgülle ayırarak, bu parametre, sağlanması gereken sırada yazılır.<br /><br /> Örneğin, SQL veri türü DECIMAL bir duyarlık ve bir ölçeğe ihtiyaç duyuyor. Bu durumda, oluşturma parametreleri "Precision, Scale" dizesini içermelidir.<br /><br /> Bir metin komutunda, duyarlılığı 10 ve ölçeği 2 olan ondalık bir sütun oluşturmak için CreateFormat sütununun değeri DECIMAL ( {0} , {1} ) "ve tüm tür belirtimi ondalık (10, 2) olabilir.|  
|DataType|string|Veri türünün .NET Framework türünün adı.|  
|IsAutoincrementable|bool|doğru — bu veri türünün değerleri otomatik olarak arttırılarak olabilir.<br /><br /> false — bu veri türünün değerleri otomatik olarak arttırılmayabilir.<br /><br /> Bunun yalnızca bu veri türü sütununun otomatik olarak artırılamayacağını, bu türdeki tüm sütunların otomatik olarak artırılmadığını gösterir.|  
|I, eşleşme|bool|doğru — veri türü, veri deposundaki tüm veri türleri ve DataType sütunundaki değer tarafından gösterilen .NET Framework veri türü arasındaki en iyi eşleşmedir.<br /><br /> false — veri türü en iyi eşleşme değildir.<br /><br /> DataType sütununun değerinin aynı olduğu her satır kümesi için, ı, Match sütunu yalnızca bir satırda true olarak ayarlanır.|  
|Icasesensitive|bool|doğru — veri türü bir karakter türüdür ve büyük/küçük harfe duyarlıdır.<br /><br /> false — veri türü bir karakter türü değildir veya büyük/küçük harfe duyarlı değildir.|  
|IsFixedLength true olarak|bool|doğru — veri tanımlama dili (DDL) tarafından oluşturulan bu veri türünün sütunları sabit uzunlukta olacaktır.<br /><br /> false — DDL tarafından oluşturulan bu veri türünün sütunları değişken uzunlukta olacaktır.<br /><br /> DBNull. Value — sağlayıcının bu alanı sabit uzunluklu veya değişken uzunluklu bir sütunla eşleştirip eşlemediği bilinmiyor.|  
|Ifixedınisionscale|bool|doğru — veri türü sabit bir duyarlığa ve ölçeğe sahiptir.<br /><br /> false — veri türü sabit bir duyarlığa ve ölçeğe sahip değildir.|  
|IsLong|bool|doğru — veri türü çok uzun veriler içerir; çok uzun verilerin tanımı sağlayıcıya özeldir.<br /><br /> false — veri türü çok uzun veri içermez.|  
|IsNullable|bool|doğru — veri türü null olabilir.<br /><br /> false — veri türü null yapılabilir değildir.<br /><br /> DBNull. Value — veri türünün null yapılabilir olup olmadığı bilinmiyor.|  
|IsSearchable|bool|doğru — veri türü WHERE yan tümcesinde LIKE koşulu hariç herhangi bir işleçle kullanılabilir.<br /><br /> false — veri türü, LIKE koşulu hariç herhangi bir işleçle bir WHERE yan tümcesinde kullanılamaz.|  
|Isearchablewithlike|bool|doğru — veri türü LIKE koşulunda kullanılabilir<br /><br /> false — veri türü LIKE koşulunda kullanılamaz.|  
|Iunsigned|bool|doğru — veri türü imzasız.<br /><br /> false — veri türü imzalanır.<br /><br /> DBNull. Value — veri türü için geçerli değildir.|  
|MaximumScale|short|Tür göstergesi sayısal bir tür ise, bu, ondalık noktanın sağında izin verilen en fazla basamak sayısıdır. Aksi takdirde, bu DBNull. Value ' dır.|  
|MinimumScale|short|Tür göstergesi sayısal bir tür ise, bu, ondalık noktanın sağında izin verilen en az basamak sayısıdır. Aksi takdirde, bu DBNull. Value ' dır.|  
|IsConcurrencyType|bool|true: veri türü, satır her değiştirildiğinde veritabanı tarafından güncelleştirilir ve sütunun değeri önceki değerlerden farklıdır<br /><br /> yanlış – veri türü, satır her değiştirildiğinde veritabanı tarafından güncelleştirilir<br /><br /> DBNull. Value: veritabanı bu tür veri türünü desteklemiyor|  
|Isedesupported|bool|true: veri türü bir sabit değer olarak ifade edilebilir<br /><br /> false – veri türü sabit değer olarak ifade edilemez|  
|Edeprefıx|string|Verilen bir sabit değere uygulanan önek.|  
|Edesuffix|string|Belirli bir sabit değere uygulanan sonek.|  
|NativeDataType|Dize|NativeDataType, veri türünün OLE DB türünü açığa çıkarmak için OLE DB özel bir sütundur.|  
  
## <a name="restrictions"></a>Kısıtlamalar  

 Bu şema koleksiyonu, veritabanına bağlanmak için şu anda kullanılan .NET Framework yönetilen sağlayıcı tarafından desteklenen kısıtlamalar hakkında bilgi açığa çıkardık.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|CollectionName|string|Bu kısıtlamaların uygulandığı koleksiyonun adı.|  
|RestrictionName|string|Koleksiyondaki kısıtlamanın adı.|  
|RestrictionDefault|string|LIP.|  
|RestrictionNumber|int|Koleksiyonlar kısıtlamalarında bu özel kısıtlamanın bulunduğu gerçek konum.|  
  
## <a name="reservedwords"></a>ReservedWords  

 Bu şema koleksiyonu, şu anda bağlı olan .NET Framework yönetilen sağlayıcının veritabanı tarafından ayrılmış sözcükler hakkında bilgi sunar.  
  
|ColumnName|DataType|Açıklama|  
|----------------|--------------|-----------------|  
|ReservedWord|string|Sağlayıcıya özel ayrılmış sözcük.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [GetSchema ve Şema Koleksiyonları](getschema-and-schema-collections.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
