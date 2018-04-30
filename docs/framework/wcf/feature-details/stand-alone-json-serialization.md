---
title: Bağımsız JSON Seri Hale Getirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d3c7234c25b0a968ca67b58a560e8c8b55bb73d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="stand-alone-json-serialization"></a>Bağımsız JSON Seri Hale Getirme
JSON (JavaScript nesne gösterimi) özellikle Web sayfalarında tarayıcı içinde çalışan JavaScript kodu tarafından kullanılmak üzere tasarlanmış bir veri biçimidir. Oluşturulan ASP.NET AJAX Hizmetleri tarafından kullanılan varsayılan veri biçimi olan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 Bu biçim, ASP.NET ile - bu durumda, tümleştirme olmadan AJAX hizmetleri oluşturma XML varsayılandır ancak JSON seçilebilir olduğunda kullanılabilir.  
  
 Son olarak, JSON desteği gerektirir, ancak bir AJAX hizmeti oluşturmadığınızı <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> doğrudan JSON verilerinin .NET nesnelerini seri hale getirmek için ve bu tür veriler geri .NET türleri örneğine seri durumdan çıkarılacak mümkün kılar. Bunun nasıl yapılacağı açıklaması için bkz: [nasıl yapılır: seri hale getirmek ve seri durumdan JSON verilerini](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 JSON ile çalışırken aynı .NET türleri, birkaç istisna dışında tarafından desteklenen gibi desteklenen <xref:System.Runtime.Serialization.DataContractSerializer>. Desteklenen türlerinin bir listesi için bkz: [veri sözleşmesi seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). En basit türler, çoğu dizi bu içerir ve koleksiyonu da kadar karmaşık türleri, kullanan <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
## <a name="mapping-net-types-to-json-types"></a>JSON türler için eşleme .NET türleri  
 Aşağıdaki tabloda .NET türleri ve seri hale getirme ve seri durumdan çıkarma yordamları tarafından eşlenen JSON/JavaScript türleri arasındaki ilişkiyi gösterir.  
  
|.NET türleri|JSON/JavaScript|Notlar|  
|----------------|----------------------|-----------|  
|Örneğin tüm sayısal türler <xref:System.Int32>, <xref:System.Decimal> veya <xref:System.Double>|Sayı|Özel değerler gibi `Double.NaN`, `Double.PositiveInfinity` ve `Double.NegativeInfinity` desteklenmez ve neden geçersiz JSON'da.|  
|<xref:System.Enum>|Sayı|"Numaralandırmalar ve JSON" bölümüne bakın.|  
|<xref:System.Boolean>|Boole değeri|--|  
|<xref:System.String>, <xref:System.Char>|Dize|--|  
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Dize|JSON içinde bu tür XML ile aynı biçimidir (temelde, "12345678-ABCD-ABCD-ABCD-1234567890AB" biçiminde GUID ve doğal dize biçimde URI TimeSpan ISO 8601 süre biçiminde gibi "http://www.example.com"). Kesin bilgi için bkz: [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|  
|<xref:System.Xml.XmlQualifiedName>|Dize|"Ad: ad alanı" (her şey ilk iki nokta üst üste adı önce) biçimidir. Adı veya ad alanı eksik olabilir. Ad alanı yok ise iki nokta üst üste de atlanabilir.|  
|<xref:System.Array> türü <xref:System.Byte>|Sayı dizisi|Her numarası bir bayt değeri temsil eder.|  
|<xref:System.DateTime>|DateTime veya dize|Tarih görmek / zamanları ve bu konunun ilerleyen bölümlerinde JSON.|  
|<xref:System.DateTimeOffset>|karmaşık türü|Tarih görmek / zamanları ve bu konunun ilerleyen bölümlerinde JSON.|  
|XML ve ADO.NET türleri (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Dizileri <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Dize|Bu konuda XML türleri ve JSON bölümüne bakın.|  
|<xref:System.DBNull>|Boş karmaşık türü|--|  
|Koleksiyonlar, sözlükler ve diziler|Dizi|Bu konuda koleksiyonlar, sözlükler ve dizileri bölümüne bakın.|  
|Karmaşık türler (ile <xref:System.Runtime.Serialization.DataContractAttribute> veya <xref:System.SerializableAttribute> uygulanır)|karmaşık türü|Veri üyeleri JavaScript karmaşık türün üyeleri haline gelir.|  
|Uygulama karmaşık türler <xref:System.Runtime.Serialization.ISerializable> arabirimi)|karmaşık türü|Ancak bazı diğer karmaşık türleri aynı <xref:System.Runtime.Serialization.ISerializable> türler desteklenmez – gelişmiş bilgileri bölümüne ISerializable destek parçası bakın.|  
|`Null` herhangi bir tür için değer|Null|Boş değer atanabilir türler de desteklenir ve eşlemek için JSON null türleri aynı şekilde.|  
  
### <a name="enumerations-and-json"></a>Numaralandırmalar ve JSON  
 Numaralandırma üye değerlerinin sayılar nasıl bunlar veri sözleşmelerinde davranılır öğesinden farklı üye adları dahil olduğu JSON olarak kabul edilir. Veri sözleşmesi işleme hakkında daha fazla bilgi için bkz: [veri sözleşmelerinde Numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   Örneğin, `public enum Color {red, green, blue, yellow, pink}`, biçimlendiricisi `yellow` 3 sayısını ve "Sarı" dize değil üretir.  
  
-   Tüm `enum` üyeleridir seri hale getirilebilir. <xref:System.Runtime.Serialization.EnumMemberAttribute> Ve <xref:System.NonSerializedAttribute> öznitelikleri kullanılırsa yoksayılır.  
  
-   Varolmayan bir seri durumdan mümkündür `enum` değer - Örneğin, değeri 87 olabilir ve önceki renk enum seri durumdan çıkarılmış karşılık gelen renk ad tanımlanmadı olsa bile.  
  
-   Bir bayrakları `enum` özel değil ve aynı diğer kabul `enum`.  
  
### <a name="datestimes-and-json"></a>Tarih/zaman ve JSON  
 JSON biçimi, tarihler ve saatler doğrudan desteklemez. Ancak, bunlar yaygın olarak kullanılan ve ASP.NET AJAX bu türleri için özel destek sağlar. ASP.NET AJAX proxy'lerini kullanırken <xref:System.DateTime> .NET içinde tam olarak karşılık gelen türü için `DateTime` JavaScript türü.  
  
-   ASP.NET, kullanmadığınızda bir <xref:System.DateTime> türü, bu konuda gelişmiş bilgileri bölümünde açıklanan özel bir biçime sahip bir dize olarak JSON'de gösterilir.  
  
-   <xref:System.DateTimeOffset> JSON karmaşık tür olarak temsil edilir: {"DateTime": dateTime, "OffsetMinutes": offsetMinutes}. `offsetMinutes` Üyesidir gelen Greenwich saati (olarak Eşgüdümlü Evrensel Saat (olay ilgi konumuyla ilişkili UTC), artık başvurulan GMT), yerel saat konumu. `dateTime` Üye ilgi olayın gerçekleştiği süre örneğini temsil eder (yeniden, bu duruma bir `DateTime` ASP.NET AJAX'ı kullanın ve bir dize olduğunda olmadığında JavaScript'te). Seri hale getirme üzerinde `dateTime` üye her zaman GMT serileştirilir. Bunu, New York saat 03: 00'da, açıklayan varsa `dateTime` 8: 00'da bir saat bileşeni vardır ve `offsetMinutes` olan 300 (eksi, 300 dakika veya GMT'den 5 saat).  
  
    > [!NOTE]
    >  <xref:System.DateTime> ve <xref:System.DateTimeOffset> JSON olarak serileştirilmiş nesneleri, yalnızca milisaniyelik duyarlık bilgileri korumak. Alt milisaniye değerleri (mikro/nanosaniye) serileştirme sırasında kaybolur.  
  
### <a name="xml-types-and-json"></a>XML türleri ve JSON  
 XML türleri JSON dizeler haline gelir.  
  
-   Örneğin, veri üyesi "q" XElement yazarsanız içerir \<abc / >, JSON {"q": "\<abc / >"}.  
  
-   Nasıl XML - daha fazla bilgi için kaydırılan belirtin, bu konunun ilerleyen bölümlerinde Gelişmiş bilgi bölümüne bakın özel bazı kurallar vardır.  
  
-   ASP.NET AJAX kullanıyorsanız ve istemediğiniz JavaScript'te dizeleri kullanın ancak bunun yerine XML DOM istediğiniz ayarlamak <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> XML özelliğine <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> XML özelliğine <xref:System.ServiceModel.Web.WebInvokeAttribute>.  
  
### <a name="collections-dictionaries-and-arrays"></a>Koleksiyonlar, sözlükler ve diziler  
 Tüm koleksiyonlar, sözlükler ve diziler JSON'de dizi olarak temsil edilir.  
  
-   Kullanan herhangi bir özelleştirme <xref:System.Runtime.Serialization.CollectionDataContractAttribute> JSON gösterimi göz ardı edilir.  
  
-   Sözlük doğrudan JSON ile çözmenin bir yolu değildir. Sözlük\<dize, Nesne > aynı yolla da desteklenmeyebilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] diğer JSON teknolojileriyle çalışmasını beklendiği gibi. Örneğin, "abc", "xyz" eşleştirilir ve "def" 42 sözlükteki eşlendiği, JSON temsili olmadığından {"abc": "xyz", "def": 42} ancak [{"Anahtarı": "Abc", "Değeri": "xyz"}, {"Anahtarı": "def", "Değeri": 42}] yerine.  
  
-   JSON ile doğrudan çalışmak isterseniz (anahtarlar ve değerler dinamik olarak katı sözleşme önceden tanımlamadan erişme), birkaç seçeneğiniz vardır:  
  
    -   Kullanmayı [zayıf yazılmış JSON seri hale getirme (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) örnek.  
  
    -   Kullanmayı <xref:System.Runtime.Serialization.ISerializable> arabirimi ve seri durumdan çıkarma oluşturucular - bu iki mekanizma JSON anahtar/değer çiftleri serileştirme üzerinde erişim ve sırasıyla seri durumundan çıkarma olanak sağlar, ancak kısmi güven senaryolarında çalışmaz.  
  
    -   İle çalışma göz önünde bulundurun [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) seri hale getirici kullanmak yerine.  
  
    -   *Çok biçimlilik* serileştirme bağlamında temel türü beklenirken türetilmiş bir tür serileştirmek için yeteneği anlamına gelir. Özel JSON özel kurallar koleksiyonları polymorphically, örneğin, bir koleksiyona atarken kullanırken yoktur bir <xref:System.Object>. Bu sorunu daha kapsamlı gelişmiş bilgileri bölümünde bu konunun ilerleyen bölümlerinde ele alınmıştır.  
  
## <a name="additional-details"></a>Ek Ayrıntılar  
  
### <a name="order-of-data-members"></a>Veri üye sırası  
 JSON kullanırken veri üye sırası önemli değildir. Özellikle, olsa bile <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> ayarlandığında, JSON verileri hala serisi kaldırılacak herhangi bir sırada.  
  
### <a name="json-types"></a>JSON türleri  
 JSON türü seri durumdan çıkarma önceki tabloda eşleşmesi gerekmez. Örneğin, bir `Int` bu dizesi geçerli bir sayı içerdiği sürece normalde bir JSON sayı, ancak eşlenir de bir JSON dizeden başarıyla Serisi kaldırılan olabilir. Diğer bir deyişle, her ikisini de {"q": 42} ve {"q": "42"} varsa geçerli bir `Int` "q" adlı veri üyesi.  
  
### <a name="polymorphism"></a>Çok Biçimlilik  
 Çok biçimli serileştirme temel türü beklenirken türetilmiş bir tür serileştirme yeteneğini oluşur. Bu JSON serileştirmesi tarafından desteklenen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XML serileştirme karşılaştırılabilir şekilde desteklenir. Örneğin, serileştirebilen `MyDerivedType` nerede `MyBaseType` beklenen veya seri `Int` burada `Object` beklenir.  
  
 Tür bilgilerini temel türü bekleniyorsa, bir karmaşık türü seri durumdan çıkarılırken sürece türetilmiş bir tür çıkarılırken kaybolmuş olabilir. Örneğin, varsa <xref:System.Uri> burada serileştirilmiş <xref:System.Object> beklenmektedir bir JSON dizesinde sonuçlanır. Bu dize sonra uygulamasına geri serisi varsa <xref:System.Object>, bir .NET <xref:System.String> döndürülür. Seri durumdan çıkarıcının dize başlangıçta türü olduğunu bilmez <xref:System.Uri>. Genellikle, bekleniyor zaman <xref:System.Object>, tüm JSON dizeler .NET dize olarak serisi ve .NET koleksiyonları, sözcüklerine serileştirmek için kullanılan tüm JSON dizileri ve diziler .NET seri durumdan <xref:System.Array> türü <xref:System.Object>ne olursa olsun, ne Gerçek özgün türü eklenmiştir. Bir .NET JSON boolean eşlemeleri <xref:System.Boolean>. Ancak beklediği zaman bir <xref:System.Object>, JSON sayılar ya da .NET seri durumdan <xref:System.Int32>, <xref:System.Decimal> veya <xref:System.Double>, burada en uygun türü otomatik olarak çekilir.  
  
 Bir arabirim türü seri durumdan çıkarılırken <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bildirilen bir türe nesne değilmiş gibi seri durumdan çıkarır.  
  
 Kendi temel ve türetilen türlerin ile çalışırken, kullanarak <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> veya eşdeğer bir mekanizma normalde gereklidir. Sahip bir işlem varsa, örneğin, bir `Animal` değeri ve gerçekte bir örneğini döndürür dönmek `Cat` (türetilmiş `Animal`), ya da uygulamalıdır <xref:System.Runtime.Serialization.KnownTypeAttribute>, `Animal` türü veya <xref:System.ServiceModel.ServiceKnownTypeAttribute> için işlemi ve belirtin `Cat` bu özniteliklerin türü. Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Nasıl biçimli serileştirme works ayrıntılarını ve bu kullanırken dikkate alınması gereken sınırlamalar bazılarının bir tartışma için bu konunun ilerleyen bölümlerinde gelişmiş bilgileri bölümüne bakın.  
  
### <a name="versioning"></a>Sürüm oluşturma  
 Veri sözleşmesi sürümü oluşturma özellikleri dahil olmak üzere, <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi, JSON içinde tam olarak desteklenir. Ayrıca, çoğu durumda bir biçimde (örneğin, XML) türü seri durumdan ve başka bir biçime (örneğin, JSON) seri hale ve hala verileri korumak mümkündür <xref:System.Runtime.Serialization.IExtensibleDataObject>. Daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Herhangi bir sırada bilgi kaybolur JSON düzenlenmemiş olduğunu unutmayın. Ayrıca, JSON anahtar aynı ada sahip birden çok anahtar/değer çiftlerinin desteklemez. Son olarak, tüm işlemler <xref:System.Runtime.Serialization.IExtensibleDataObject> kendi türetilmiş bir tür için atanan kendiliğinden çok biçimli - are <xref:System.Object>, tüm türleri için temel tür.  
  
## <a name="json-in-urls"></a>JSON URL'lerde  
 ASP.NET AJAX uç noktaları ile HTTP GET fiili kullanırken (kullanarak <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği), ileti gövdesi yerine istek URL'sindeki gelen parametreler görüntülenir. JSON istek URL'si bile, desteklenen bunu alan bir işlem varsa bir `Int` "number" olarak adlandırılan ve `Person` URL "p" adlı karmaşık türü aşağıdaki URL'yi benzer.  
  
```  
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}  
```  
  
 Hizmetini çağırmak için bir ASP.NET AJAX komut dosyası Manager denetim ve proxy kullanıyorsanız, bu URL proxy sunucu tarafından otomatik olarak oluşturulur ve değil görülür. JSON, ASP.NET AJAX uç noktalarda URL'ler kullanılamaz.  
  
## <a name="advanced-information"></a>Gelişmiş bilgiler  
  
### <a name="iserializable-support"></a>ISerializable desteği  
  
#### <a name="supported-and-unsupported-iserializable-types"></a>Desteklenen ve desteklenmeyen ISerializable türleri  
 Genel olarak, bu uygulama türleri <xref:System.Runtime.Serialization.ISerializable> arabirimi tam olarak serileştirme/seri durumdan çıkarılırken desteklenen JSON. Ancak, bazı (bazı .NET Framework türleri dahil) bu tür özel JSON seri hale getirme yönlerini bunları neden biçimde uygulanan doğru seri durumdan değil:  
  
-   İle <xref:System.Runtime.Serialization.ISerializable>, tek tek veri üyeleri tür hiçbir zaman önceden denir. Bu, bir nesneye türleri seri durumdan çıkarmak için benzer bir polimorfik durum neden olmaktadır. Önceden belirtildiği gibi JSON içinde türü bilgi kaybına yol açabilir. Örneğin, serileştiren bir türü bir `enum` içinde kendi <xref:System.Runtime.Serialization.ISerializable> uygulama ve seri durumdan girişimleri geri doğrudan bir `enum` (olmadan uygun atamaları) başarısız olur, çünkü bir `enum` numaraları JSON ve JSON kullanılarak serileştirilmiş sayı yerleşik .NET sayısal türler (Int32, Decimal veya çift) seri durumdan çıkarır. Bu nedenle olgu sayı olması için kullanılan bir `enum` değeri kaybolur.  
  
-   Bir <xref:System.Runtime.Serialization.ISerializable> seri durumdan çıkarma oluşturucusu içinde belirli bir sıraya bağlıdır türü de başarısız olabilir bazı JSON verilerini seri durumdan çıkarılacak çoğu JSON serileştiricileri belirli bir sıraya garanti değil çünkü.  
  
#### <a name="factory-types"></a>Fabrika türü  
 Sırada <xref:System.Runtime.Serialization.IObjectReference> arabirimi genel, "Fabrika türü" özelliği gerektiren herhangi bir türünün JSON'desteklenir (farklı bir türden örneğini döndüren <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> arabirimini uygulayan türünden) desteklenmez.  
  
### <a name="datetime-wire-format"></a>DateTime kablo biçimi  
 <xref:System.DateTime> değerler "/ Date(700000+0500) /" biçiminde JSON dizeler görünür ilk numarasının (700000 sağlanan örnekte) olduğu (olmayan gün ışığından yararlanma) olan normal GMT saat dilimi milisaniye sayısını gece, 1 Ocak 1970'ten itibaren zaman. Bu sayı önceki saatleri temsil etmek için negatif olabilir. Örnekte "+0500" oluşan bölümü isteğe bağlıdır ve zaman, gösterir <xref:System.DateTimeKind.Local> türü - diğer bir deyişle, dönüştürülmesi gereken seri durumdan çıkarma işleminde yerel saat dilimi. Olmazsa, saat olarak seri durumdan olan <xref:System.DateTimeKind.Utc>. Gerçek sayı ("0500" Bu örnekte) ve onun işareti (+ veya -) göz ardı edilir.  
  
 Serileştirilirken <xref:System.DateTime>, <xref:System.DateTimeKind.Local> ve <xref:System.DateTimeKind.Unspecified> kez bir uzaklık ile yazılır ve <xref:System.DateTimeKind.Utc> olmadan yazılır.  
  
 ASP.NET AJAX istemci JavaScript kodu gibi dizeleri JavaScript ile otomatik olarak dönüştürür. `DateTime` örnekleri. Türünde olmayan bir benzer bir form olan diğer dizeleri varsa <xref:System.DateTime> .NET, bunlar da dönüştürülür.  
  
 Yalnızca gerçekleşir "/" karakterler atlanır varsa dönüştürme (JSON benzer diğer bir deyişle, "\\/Date(700000+0500)\\/") ve bu nedenle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s JSON Kodlayıcısı (tarafından etkinleştirilen <xref:System.ServiceModel.WebHttpBinding>) her zaman çıkışları "/" karakter.  
  
### <a name="xml-in-json-strings"></a>JSON dizeler XML'de  
  
#### <a name="xmlelement"></a>XmlElement  
 <xref:System.Xml.XmlElement> , hiçbir kaydırma ile olduğu gibi serileştirilir. Örneğin, veri üyesi "x" türü <xref:System.Xml.XmlElement> içeren \<abc / > şu şekilde temsil aynıdır.  
  
```json  
{"x":"<abc/>"}  
```  
  
#### <a name="arrays-of-xmlnode"></a>XmlNode dizileri  
 <xref:System.Array> Nesne türü <xref:System.Xml.XmlNode> ArrayOfXmlNode türü için standart veri sözleşmesi ad alanına denilen bir elemana sarılır. "X" özniteliği "N" "değeri" içeren "ns" ad alanında ve bir boş öğesini düğümlerini "M" içeren bir dizi ise, temsili aşağıdaki gibidir.  
  
```  
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}  
```  
  
 XmlNode diziler (önce diğer öğeleri) başındaki boş ad alanındaki öznitelikler desteklenmez.  
  
#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>IXmlSerializable XElement ve veri kümesi dahil türleri  
 <xref:System.Runtime.Serialization.ISerializable> "içerik türleri", "Veri kümesi türleri" ve "öğe türleri" türleri ayırabilir. Bu tür tanımları için bkz: [XML ve ADO.NET türleri veri sözleşmelerinde](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
 "İçerik" ve "Veri kümesi" türleri benzer serileştirilir <xref:System.Array> nesnelerin <xref:System.Xml.XmlNode> önceki bölümde tartışılan. Bir öğe adı sarılır ve ad alanı veri sözleşme adına ve türünün ad alanını söz konusu karşılık gelir.  
  
 "Öğesi" türleri gibi <xref:System.Xml.Linq.XElement> , benzer olarak serileştirilmiş <xref:System.Xml.XmlElement> daha önce bu konuda tartışılan.  
  
### <a name="polymorphism"></a>Çok Biçimlilik  
  
#### <a name="preserving-type-information"></a>Koruma türü bilgileri  
 Çok biçimlilik daha önce belirtildiği gibi bazı kısıtlamalarla JSON'desteklenir. JavaScript bir zayıf yazılmış bir dildir ve türü kimliği bir sorun değildir normalde. Ancak, JSON kesin türü belirtilmiş bir sistem (.NET) ve bir zayıf yazılmış sistem (JavaScript) arasında iletişim kurmak için kullanırken türü kimlik korumak yararlıdır. Örneğin, adları "Kare" ve "Yuvarlak" bir türden "Şeklin" bir veri sözleşmesi adıyla türetilmesi veri türleriyle sözleşme. "Daire".NET JavaScript gönderilir ve daha sonra "Şekil" bekliyor bir .NET yöntemi döndürülür, söz konusu nesne özgün olarak bir "daire" - Aksi durumda olduğunu bilmek için .NET tarafı yararlı olur (örneğin türetilmiş türüne özgü herhangi bir bilgi "Daire" üzerindeki "RADIUS" veri üyesi) kaybolmuş olabilir.  
  
 JSON "türü ipucu" için karmaşık türleri serileştirmek eklenebilir ve seri durumdan çıkarıcının ipucu tanır ve uygun şekilde davranan türü kimlik korumak için. "Türü ipucu", "__type" ("tür" sözcüğü ve ardından iki alt çizgi), JSON anahtar/değer çifti anahtar adlı olur. "(İlk iki nokta üst üste kadar herhangi bir şey adıdır) DataContractName:DataContractNamespace" biçiminde bir JSON dizesi değeridir. Önceki örneği kullanarak, "Daire" gibi seri hale getirilebilir.  
  
```json  
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}  
```  
  
 Tür ipucu çok benzer `xsi:type` özniteliği XML Şeması örneği standardına göre tanımlanır ve ne zaman kullanılır seri hale getirme/XML seri durumdan çıkarılıyor.  
  
 Veri üyeleri "__type" olarak adlandırılan türü İpucu ile olası çakışması nedeniyle yasaktır.  
  
#### <a name="reducing-the-size-of-type-hints"></a>Türü ipuçları boyutunu azaltma  
 JSON boyutunu azaltmak için iletileri, varsayılan veri sözleşmesi ad alanı öneki (http://schemas.datacontract.org/2004/07/) "#" karakteri ile değiştirilir. (Escaping bir kural bu değiştirme ters çevrilebilir yapmak için kullanılır: ad "#" ile başlıyorsa veya "\\" karakterleri, fazladan ile eklenir "\\" karakter). Bu nedenle, "Daire" "MyApp.Shapes".NET ad alanındaki bir türü, varsayılan veri sözleşmesi ad alanı ise, http://schemas.datacontract.org/2004/07/MyApp. Şekiller ve JSON gösterimi aşağıdaki gibidir.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}  
```  
  
 Kesilmiş (#MyApp.Shapes) ve tam (http://schemas.datacontract.org/2004/07/MyApp.Shapes) adları seri durumundan çıkarma işleminde anladım.  
  
#### <a name="type-hint-position-in-json-objects"></a>JSON nesnelerinin türü ipucu konumu  
 Tür ipucu JSON gösterimi ilk olması gerektiğini unutmayın. Bu anahtar/değer çiftlerinin sırasını JSON işlenirken önemli olduğu tek bir durumdur. Örneğin, şu tür ipucu belirtmek için geçerli bir yol değil.  
  
```json  
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}  
```  
  
 Her iki <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tarafından kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve ASP.NET AJAX istemci sayfaları her zaman yayma türü ipucu ilk.  
  
#### <a name="type-hints-apply-only-to-complex-types"></a>Türü ipuçları yalnızca karmaşık türleri için geçerlidir  
 Karmaşık olmayan türleri için tür ipucu yaymak üzere yolu yoktur. Örneğin, bir işlem varsa bir <xref:System.Object> bir daire dönüş türü döndürür ancak, daha önce gösterildiği gibi JSON gösterimi olabilir ve tür bilgileri korunur. Ancak, URI döndürülürse, JSON temsili bir dize ve bir URI temsil etmek için kullanılan dize kaybolur olgu gerekir. Bu, yalnızca ilkel türler için aynı zamanda koleksiyonlar ve diziler için geçerlidir.  
  
#### <a name="when-are-type-hints-emitted"></a>Türü ipuçları zaman gösterilen  
 Türü ipuçları artırabileceği ileti boyutu önemli ölçüde (azaltmak için tek yönlü kısa veri sözleşmesi ad alanları mümkünse kullanmak için budur). Bu nedenle, türü ipuçları yayılan olup olmadığını aşağıdaki kurallar kapsar:  
  
-   Olsa bile hiçbir temel ve türetilen atama - Örneğin, bir daire bir daire atanmış olsa bile ASP.NET AJAX'ı kullanırken, türü ipuçları her zaman mümkün olduğunda, gösterilen. (Bu kesin türü belirtilmiş .NET ortamına zayıf yazılmış JSON ortamından arama işlemi şaşırtıcı hiçbir bilgi kaybı ile tam olarak etkinleştirmek için gereklidir.)  
  
-   Daire şekle atandığında yayılan bir taban ve türetilmiş atamasını - olduğunda AJAX Hizmetleri ile tümleştirme yoktur ASP.NET kullanılırken türü ipuçları yalnızca gösterilen veya <xref:System.Object> ancak daireye atandığında değil. Bu doğru böylece performansı, iyileştirme bir JavaScript istemci uygulamak için gereken en az bilgiyi sağlar ancak yanlış tasarlanan istemciler türü bilgi kaybına karşı koruma sağlamaz. Bu sorunla istemcide önlemek istiyorsanız, temel ve türetilen atamaları sunucu üzerinde tamamen kaçının.  
  
-   Kullanırken <xref:System.Runtime.Serialization.DataContractSerializer> türü, `alwaysEmitTypeInformation` Oluşturucusu parametresi, varsayılan olan ile önceki iki mod arasında seçim yapmanızı sağlar "`false`" (yalnızca gerekli olduğunda türü ipuçları yayma).  
  
#### <a name="duplicate-data-member-names"></a>Yinelenen veri üyesi adları  
 Türetilmiş bir tür bilgiler temel türü bilgileriyle birlikte aynı JSON nesnesinde yok ve herhangi bir sırada ortaya çıkabilir. Örneğin, `Shape` gibi temsil edilebilir.  
  
```json  
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}  
```  
  
 Daire gibi temsil edilebilir ise.  
  
```json  
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}  
```  
  
 Varsa temel `Shape` türü olarak adlandırılan bir veri üyesi de yer alan "`radius`", (JSON nesnelerinin anahtar adları yinelenen olamayacağından) Bu bir çakışma üzerinde hem serileştirme müşteri adayları ve (, "RADIUS" için olupbaşvuruyorbelirsizolduğundanseridurumundançıkarma`Shape.radius` veya `Circle.radius`). Bu nedenle, "özelliği gizleme" kavramı while (veri üyeleri aynı adına, temel ve türetilmiş sınıfları) genellikle önerilmez veri sözleşmesi sınıflarda, aslında yasaklandı JSON söz konusu olduğunda.  
  
#### <a name="polymorphism-and-ixmlserializable-types"></a>Çok biçimlilik ve IXmlSerializable türleri  
 <xref:System.Xml.Serialization.IXmlSerializable> Bilinen türleri gereksinimleri karşılandığında, normal veri sözleşmesi kurallara göre sürece türleri polymorphically birbirlerine her zamanki gibi atanmış olabilir. Ancak, seri hale getirilirken bir <xref:System.Xml.Serialization.IXmlSerializable> yerine yazın <xref:System.Object> sonucu bir JSON dizesi olarak türü bilgi kaybına sonuçlanır.  
  
#### <a name="polymorphism-and-certain-interface-types"></a>Çok biçimlilik ve belirli arabirimi türleri  
 Koleksiyon türü veya uygulayan bir tür serileştirmek için Yasak <xref:System.Xml.Serialization.IXmlSerializable> değil bir koleksiyon olmayan tür burada <xref:System.Xml.Serialization.IXmlSerializable> (dışında <xref:System.Object>) bekleniyor. Örneğin, özel bir arabirim adlı `IMyInterface` ve bir tür `MyType` da uygulayan her ikisi de <xref:System.Collections.Generic.IEnumerable%601> türü `int` ve `IMyInterface`. Döndürülecek Yasak `MyType` dönüş türü olan bir işlem `IMyInterface`. Bunun nedeni, `MyType` , önce belirtilen olarak içeremez yalnızca karmaşık türlerle diziler türü ipucuyla bir JSON dizisi olarak seri hale ve türü ipucu gerektirir.  
  
#### <a name="known-types-and-configuration"></a>Bilinen türler ve yapılandırma  
 Tarafından kullanılan bilinen türü mekanizmaları tümünün <xref:System.Runtime.Serialization.DataContractSerializer> da aynı şekilde tarafından desteklenen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Aynı yapılandırma öğesinde hem serileştiricileri okuma [ \<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) içinde [ \<system.runtime.serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), eklenen bilinen türleri bulmak için bir yapılandırma dosyası.  
  
#### <a name="collections-assigned-to-object"></a>Nesne atanmış koleksiyonları  
 Nesnesine atanmış koleksiyonları uygulamak koleksiyonları varsa gibi serileştirilir <xref:System.Collections.Generic.IEnumerable%601>: karmaşık bir tür ise türü ipucu sahip her giriş ile JSON dizisi. Örneğin, bir <xref:System.Collections.Generic.List%601> türü `Shape` atanan <xref:System.Object> aşağıdaki gibi görünür.  
  
```json  
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},  
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},  
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]  
```  
  
 Uygulamasına geri seri zaman <xref:System.Object>:  
  
-   `Shape` Bilinen türleri listesinde olması gerekir. Sahip <xref:System.Collections.Generic.List%601> türü `Shape` bilinen türleri hiçbir etkisi olmaz. Eklemek zorunda değilsiniz Not `Shape` için bilinen seri hale getirme türlerinde bu durumda - bu otomatik olarak yapılır.  
  
-   Koleksiyon olarak seri durumdan bir <xref:System.Array> türü <xref:System.Object> içeren `Shape` örnekleri.  
  
#### <a name="derived-collections-assigned-to-base-collections"></a>Temel koleksiyonlara atanmış türetilmiş koleksiyonları  
 Türetilen bir koleksiyon temel bir koleksiyona atandığında, temel türünü birtakım boşmuş gibi koleksiyon genellikle seri değildir. Ancak, temel koleksiyonun öğe türü türetilen koleksiyonun öğe türü atanamıyorsa özel durum oluşur.  
  
#### <a name="type-hints-and-dictionaries"></a>Türü ipuçları ve sözlük  
 Ne zaman bir sözlük atanması bir <xref:System.Object>, atanmış gibi her anahtar ve değer giriş sözlükteki davranılır <xref:System.Object> ve türü ipucu alır.  
  
 Sözlük türleri serileştirilirken "Anahtar" ve "Değeri" üyeleri içeren JSON nesnesi tarafından etkilenmez `alwaysEmitTypeInformation` ayarlama ve önceki toplama kuralları gerektirdiğinde türü İpucu yalnızca içerir.  
  
### <a name="valid-json-key-names"></a>Geçerli bir JSON anahtar adları  
 Geçerli XML adları seri hale getirici XML kodlar anahtar adları. Örneğin, bir veri üyesi "123" adı ile kodlanmış bir adı gibi gerekir "_x0031\__x0032\__x0033\_" "123" geçersiz bir XML öğesi adı (bir rakam ile başlayan) olduğundan. XML adlarında geçerli olmayan bazı uluslararası karakter kümeleri ile benzer bir durum ortaya çıkabilir. Bu JSON işleme XML etkisini açıklaması için bkz: [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JSON ve Diğer Veri Aktarma Biçimleri için Destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
