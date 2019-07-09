---
title: Bağımsız JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 63f40333b53bce33e4c3aafb784e038f52bc8630
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663753"
---
# <a name="stand-alone-json-serialization"></a>Bağımsız JSON Seri Hale Getirme

JSON (JavaScript nesne gösterimi) özellikle Web sayfalarında tarayıcı içinde çalışan JavaScript kodu tarafından kullanılmak üzere tasarlanmış bir veri biçimidir. Bu, Windows Communication Foundation (WCF) oluşturan ASP.NET AJAX Hizmetleri tarafından kullanılan varsayılan veri biçimidir.

Bu biçim, bu durumda, ASP.NET ile - tümleştirme olmadan AJAX hizmetleri oluşturma XML varsayılan ancak JSON seçilebilir kullanılabilir.

Son olarak, JSON desteğine ihtiyaç duyar, ancak bir AJAX hizmeti oluşturmadığınızı <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> doğrudan JSON verilerinin .NET nesneleri serileştirmek için ve bu tür veriler geri .NET türleri örneğine seri durumdan çıkarılacak mümkün kılar. Bunun nasıl yapılacağı ile ilgili açıklama için bkz: [nasıl yapılır: JSON verileri seri hale getrime ve](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

JSON ile çalışırken aynı .NET türleri, bazı istisnalar tarafından desteklenen desteklenir <xref:System.Runtime.Serialization.DataContractSerializer>. Desteklenen türleri listesi için bkz. [veri sözleşme seri hale getirici tarafından desteklenen türleri](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). En basit türler, çoğu dizi bu içerir ve koleksiyon türleri de gibi karmaşık türler kullanan <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute>.

## <a name="mapping-net-types-to-json-types"></a>JSON türleri için .NET türlerini eşleme

Aşağıdaki tablo, .NET türleri ile serileştirme ve seri durumundan çıkarma yordamları tarafından eşleştirildiğinde JSON/JavaScript türleri arasındaki ilişkiyi gösterir.

|.NET türleri|JSON/JavaScript|Notlar|
|----------------|----------------------|-----------|
|Örneğin, tüm sayısal türlerin <xref:System.Int32>, <xref:System.Decimal> veya <xref:System.Double>|Sayı|Özel değerler gibi `Double.NaN`, `Double.PositiveInfinity` ve `Double.NegativeInfinity` desteklenmez ve neden geçersiz JSON.|
|<xref:System.Enum>|Sayı|"Sabit listeleri ve JSON" bölümüne bakın.|
|<xref:System.Boolean>|Boole değeri|--|
|<xref:System.String>, <xref:System.Char>|Dize|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Dize|Bu tür JSON biçimi XML olduğu gibi aynıdır (aslında gibi "12345678-ABCD-ABCD-ABCD-1234567890AB" biçiminde GUID ve URI, doğal dize biçiminde TimeSpan ISO 8601 süre biçiminde "http://www.example.com"). Tam bilgi için bkz: [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|Dize|"Ad: ad alanı" (her şey adı iki nokta üst üste ilk önce) biçimidir. Adı veya ad alanı eksik olabilir. Ad alanı yok ise iki nokta üst üste de atlanabilir.|
|<xref:System.Array> türü <xref:System.Byte>|Bir sayı dizisi|Her bir sayının bir bayt değerini temsil eder.|
|<xref:System.DateTime>|DateTime ya da dize|Tarihleri bkz / saatler ve bu konunun ilerleyen bölümlerinde JSON.|
|<xref:System.DateTimeOffset>|Karmaşık tür|Tarihleri bkz / saatler ve bu konunun ilerleyen bölümlerinde JSON.|
|XML ve ADO.NET türleri (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Dizileri <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Dize|Bu konunun XML türleri ve JSON bölümüne bakın.|
|<xref:System.DBNull>|Boş bir karmaşık tür|--|
|Koleksiyonlar, sözlük ve diziler|Array|Bu konunun koleksiyonlar, sözlük ve dizileri bölümüne bakın.|
|Karmaşık türler (ile <xref:System.Runtime.Serialization.DataContractAttribute> veya <xref:System.SerializableAttribute> uygulanmış)|Karmaşık tür|Veri üyeleri, JavaScript karmaşık türün üyeleri haline gelir.|
|Uygulama karmaşık türler <xref:System.Runtime.Serialization.ISerializable> arabirimi)|Karmaşık tür|Ancak bazı diğer karmaşık türleri aynı <xref:System.Runtime.Serialization.ISerializable> türler desteklenmiyor: Bu konunun Gelişmiş bilgi bölümüne ISerializable destek bölümünü görmek.|
|`Null` herhangi bir tür için değer|Null|Boş değer atanabilir türler de desteklenir ve eşlemek için alamayan türleri aynı şekilde JSON.|

### <a name="enumerations-and-json"></a>Numaralandırmalar ve JSON

Sabit listesi üye değerlerinin sayılar üye adları dahil oldukları nasıl bunlar veri anlaşmalarında ele alındığı öğesinden farklı olan JSON olarak kabul edilir. Veri sözleşmesi işleme hakkında daha fazla bilgi için bkz. [veri sözleşmelerinde Numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Örneğin, `public enum Color {red, green, blue, yellow, pink}`, serileştirmek `yellow` 3 numaralı ve "Sarı" dize değil üretir.

- Tüm `enum` üyeleridir seri hale getirilebilir. <xref:System.Runtime.Serialization.EnumMemberAttribute> Ve <xref:System.NonSerializedAttribute> kullandıysanız öznitelikleri yoksayılır.

- Varolmayan bir'seri durumdan çıkarılacak mümkündür `enum` değeri - örneğin, ' % s'değeri 87 olabilir önceki renk enum seri durumdan çıkarılmış tanımlanan karşılık gelen renk adı olsa bile.

- Bir bayrakları `enum` özel tutulmadığından ve aynı diğer kabul `enum`.

### <a name="datestimes-and-json"></a>Tarihleri/saatleri ve JSON

Tarihler ve saatler JSON biçimini doğrudan desteklemez. Ancak, bunlar yaygın olarak kullanılan ve ASP.NET AJAX için bu tür özel destek sağlar. ASP.NET AJAX proxy'leri kullanırken <xref:System.DateTime> .NET türünde tam olarak karşılık gelen `DateTime` JavaScript türü.

- ASP.NET, kullanılmadığında bir <xref:System.DateTime> türü JSON'da bu konunun gelişmiş bilgileri bölümünde açıklanan özel bir biçime sahip bir dize olarak gösterilir.

- <xref:System.DateTimeOffset> JSON karmaşık bir tür olarak temsil edilir: {"DateTime": "OffsetMinutes" tarih/saat: offsetMinutes}. `offsetMinutes` Üyesidir gelen Greenwich saati (Eşgüdümlü Evrensel Saat (ilgilendiğiniz bir olayı konumu ile ilişkili UTC olarak), artık referans GMT), yerel saat uzaklığı. `dateTime` Üye ilgi olayın gerçekleştiği zaman örneğini temsil eder (yeniden, bu duruma bir `DateTime` ASP.NET AJAX kullanın ve bir dize olduğunda olmadığında JavaScript dilinde). Seri hale getirme üzerinde `dateTime` üye GMT cinsinden her zaman serileştirilmiş. Bu nedenle, New York saat 03: 00'da, açıklayan `dateTime` 8: 00'da bir saat bileşeni vardır ve `offsetMinutes` 300'ü (eksi 300 dakika veya GMT 5 saat).

  > [!NOTE]
  > <xref:System.DateTime> ve <xref:System.DateTimeOffset> JSON olarak serileştirilmiş nesneler, yalnızca milisaniyelik duyarlılığa bilgilerini korumak. Milisaniyenin değerleri (mikro/nanosaniye), serileştirme sırasında kaybolur.

### <a name="xml-types-and-json"></a>XML türleri ve JSON

XML türleri JSON dizeleri haline gelir.

- Örneğin, bir veri üyesi "q", XElement yazarsanız içerir \<abc / >, bir JSON olduğundan {"q": "\<abc / >"}.

- Nasıl XML - daha fazla bilgi için sarmalandıktan belirtin, bu konunun ilerleyen bölümlerinde Gelişmiş bilgi bölümüne bakın özel bazı kurallar vardır.

- ASP.NET AJAX kullanıyorsanız ve istemediğiniz JavaScript'te dizeleri kullanın, ancak bunun yerine XML DOM istediğiniz ayarlayın <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> XML özelliğini <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> XML özelliğini <xref:System.ServiceModel.Web.WebInvokeAttribute>.

### <a name="collections-dictionaries-and-arrays"></a>Koleksiyonlar, sözlük ve diziler

Tüm koleksiyonlar, sözlük ve dizileri JSON dizileri olarak temsil edilir.

- Kullanan herhangi bir özelleştirme <xref:System.Runtime.Serialization.CollectionDataContractAttribute> JSON gösteriminde göz ardı edilir.

- Sözlük, doğrudan JSON ile çalışmak için bir yol değildir. Sözlük\<dize, Nesne > wcf'de tıpkı diğer JSON teknolojileri ile çalışmaktan beklendiği gibi desteklenmiyor olabilir. Örneğin, "abc", "xyz için" eşlenir ve "def" 42 bir sözlükte eşlenmiş durumda, JSON gösterimi değil {"abc": "xyz", "def": 42} değil [{"Key": "Abc", "Değer": "xyz"}, {"Anahtarını": "def", "Value": 42}] bunun yerine.

- JSON ile doğrudan çalışmak istiyorsanız (anahtarları ve değerleri dinamik olarak katı bir sözleşme önceden tanımlamadan erişme), birkaç seçeneğiniz vardır:

  - Kullanmayı [zayıf yazılmış JSON seri hale getirme (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) örnek.

  - Kullanmayı <xref:System.Runtime.Serialization.ISerializable> arabirimi ve seri durumundan çıkarma oluşturucular - bu iki mekanizma JSON anahtar/değer çiftleri seri hale getirme üzerinde erişim ve sırasıyla seri durumdan çıkarma olanak sağlar ancak kısmi güven senaryolarında çalışmaz.

  - Çalışmak göz önünde bulundurun [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) seri hale getirici kullanmak yerine.

  - *Çok biçimlilik* kendi temel türü beklenirken türetilmiş bir türü seri hale özelliği serileştirme bağlamında ifade eder. Koleksiyonları polymorphically, örneğin, bir koleksiyona atarken kullanırken, özel JSON özgü kurallar olan bir <xref:System.Object>. Bu sorunu daha gelişmiş bilgileri bölümünde bu konunun ilerleyen bölümlerinde ele alınmıştır.

## <a name="additional-details"></a>Ek Ayrıntılar

### <a name="order-of-data-members"></a>Veri üye sırası

JSON kullanırken veri üye sırası önemli değildir. Özellikle, bile <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> ayarlandığında, JSON verilerini hala seri herhangi bir sırada.

### <a name="json-types"></a>JSON türleri

JSON türü seri durumdan çıkarma önceki tabloda eşleşmesi gerekmez. Örneğin, bir `Int` Bu dize geçerli bir sayı içerdiği sürece normalde bir JSON sayı, ancak eşlenir ayrıca JSON dizeden başarılı bir şekilde seri durumdan olabilir. Diğer bir deyişle, her ikisi de {"q": 42} ve {"q": "42"} varsa, geçerli bir `Int` "q" adlı veri üyesi.

### <a name="polymorphism"></a>Çok Biçimlilik

Çok biçimli Serileştirme kendi temel türü beklenirken türetilmiş bir türü seri hale getirme yeteneği oluşur. JSON serileştirme için bu XML serileştirme desteklenen şekilde karşılaştırılabilir WCF tarafından desteklenir. Örneğin, serileştirebiliyorsa `MyDerivedType` burada `MyBaseType` bekleniyor veya seri hale getirmek `Int` burada `Object` beklenir.

Temel tür bekleniyorsa, karmaşık bir türü seri durumdan çıkarılırken sürece türetilmiş bir türü seri durumdan çıkarmak olduğunda tür bilgileri kaybolabilir. Örneğin, varsa <xref:System.Uri> nerede serileştirilmiş <xref:System.Object> beklenir, bir JSON dizesinde sonuç. Bu dize daha sonra tekrar seri durumdan, <xref:System.Object>, bir .NET <xref:System.String> döndürülür. Seri durumdan çıkarıcı dize başlangıçta türü olduğunu bilmez <xref:System.Uri>. Genellikle, beklenirken <xref:System.Object>, tüm JSON dizeleri .NET dize olarak seri durumdan çıkarılmakta ve tüm JSON dizileri sözlükleri, .NET koleksiyonlarında serileştirmek için kullanılır ve diziler .NET seri durumdan <xref:System.Array> türü <xref:System.Object>ne bakılmaksızın Gerçek özgün tür eklenmiştir. .NET ile JSON boolean eşler <xref:System.Boolean>. Ancak beklenirken bir <xref:System.Object>, JSON sayı ya da .NET seri durumdan <xref:System.Int32>, <xref:System.Decimal> veya <xref:System.Double>, burada en uygun türüne otomatik olarak seçilir.

Bir arabirim türü seri durumdan çıkarılırken zaman <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bildirilen türü nesneymiş gibi seri durumdan çıkarır.

Kendi temel ve türetilmiş türleri ile çalışmaktan kullandığınızda <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> veya eşdeğer bir mekanizma normalde gereklidir. Sahip bir işlem varsa, örneğin, bir `Animal` değeri ve gerçekten örneğini bir döndürür dönüş `Cat` (türetilen `Animal`), ya da uygulamalıdır <xref:System.Runtime.Serialization.KnownTypeAttribute>, `Animal` türü veya <xref:System.ServiceModel.ServiceKnownTypeAttribute> için işlem ve belirtin `Cat` bu öznitelikler türü. Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Nasıl polimorfik serileştirme works ayrıntılarını ve bazı kullanırken dikkate alınması kısıtlamalar nedeniyle tartışılması, bu konunun devamındaki Gelişmiş bilgi bölümüne bakın.

### <a name="versioning"></a>Sürüm Oluşturma

Veri sözleşmesi sürümü oluşturma özelliklerini <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirim, JSON'da tam olarak desteklenir. Ayrıca, çoğu durumda bir biçimde (örneğin, XML) bir türü seri durumdan ve başka bir biçimde (örneğin, JSON) olarak seri hale yine de verileri korumak mümkündür <xref:System.Runtime.Serialization.IExtensibleDataObject>. Daha fazla bilgi için [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Tüm sipariş bilgileri kaybolur JSON sırasız olduğunu unutmayın. Ayrıca, JSON anahtar aynı ada sahip birden çok anahtar/değer çiftleri desteklemez. Son olarak, tüm işlemleri <xref:System.Runtime.Serialization.IExtensibleDataObject> kendi türetilmiş bir tür atanmış olan doğası gereği çok biçimli - olan <xref:System.Object>, tüm türleri için temel tür.

## <a name="json-in-urls"></a>JSON URL'lerinde

ASP.NET AJAX uç noktaları ile HTTP GET fiili kullanırken (kullanarak <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği), gelen parametreleri istek URL'si yerine ileti görüntülenir. JSON istek URL'si bile, desteklenen alan bir işlem varsa, bunu bir `Int` "number" olarak adlandırılan ve `Person` karmaşık tür "p", URL olarak adlandırılan aşağıdaki URL'ye benzer.

```
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Hizmeti çağırmak için bir ASP.NET AJAX komut dosyası Manager denetim ve Ara sunucu kullanıyorsanız, bu URL'yi proxy sunucu tarafından otomatik olarak oluşturulur ve değil görülür. JSON URL'lerinde ASP.NET AJAX uç noktaları üzerinde kullanılamaz.

## <a name="advanced-information"></a>Gelişmiş bilgiler

### <a name="iserializable-support"></a>ISerializable desteği

#### <a name="supported-and-unsupported-iserializable-types"></a>Desteklenen ve desteklenmeyen ISerializable türler

Genel olarak, uygulayan türleri <xref:System.Runtime.Serialization.ISerializable> arabirimi serileştirme/seri durumdan çıkarılırken zaman tam olarak desteklenen JSON. (Bazı .NET Framework türleri gibi) bu tür bazı özel JSON seri hale getirme yönü bunları neden biçimde uygulanabilir ancak doğru bir şekilde seri durumdan değil:

- İle <xref:System.Runtime.Serialization.ISerializable>, tek tek veri üyeleri tür hiçbir zaman önceden denir. Bu türler bir nesnede seri durumdan çıkarmak için benzer bir çok biçimli durum neden olur. Daha önce belirtildiği gibi bu JSON türü bilgi kaybına neden olabilir. Örneğin, serileştiren bir türü bir `enum` içinde kendi <xref:System.Runtime.Serialization.ISerializable> uygulama ve seri durumdan çıkarılacak denemeleri geri doğrudan bir `enum` (olmadan uygun atamalar) başarısız olur, çünkü bir `enum` JSON ve JSON sayılar kullanılarak serileştirilmiş sayılar, yerleşik .NET sayısal tür olarak (Int32, Decimal veya çift) seri durumdan çıkarır. Bu nedenle gerçek sayı olarak kullanılan bir `enum` değeri kaybolur.

- Bir <xref:System.Runtime.Serialization.ISerializable> seri durumundan çıkarma, seri durumundan çıkarma oluşturucuda, belirli bir sıraya bağlıdır türü de başarısız olabilir bazı JSON verileri seri durumdan çıkarılacak JSON serileştiricileri çoğu belirli bir sıraya göre garanti edemediğinden.

#### <a name="factory-types"></a>Fabrika türü

Sırada <xref:System.Runtime.Serialization.IObjectReference> arabirimi JSON genel, "Fabrika türü" özelliği gerektiren herhangi bir türü desteklenir (farklı bir tür örneği döndüren <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> türünden arabirimi uygulayan) desteklenmez.

### <a name="datetime-wire-format"></a>DateTime kablo biçimini

<xref:System.DateTime> değerler "/ Date(700000+0500) /" biçiminde JSON dizeler olarak görünür (sağlanan örnekte 700000) ilk sayı olduğu (olmayan gün ışığından tasarruf) olan normal GMT saat diliminde milisaniye sayısını 1 Ocak 1970 gece yarısından zaman. Bu sayı, önceki saatleri temsil etmek için negatif olabilir. Örnekte "+0500" içeren bölümü isteğe bağlıdır ve zamanı, olduğunu gösterir <xref:System.DateTimeKind.Local> tür - diğer bir deyişle, dönüştürülmesi gereken seri durumundan çıkarma üzerinde yerel saat dilimi. Olmazsa, saat olarak seri durumda <xref:System.DateTimeKind.Utc>. Gerçek sayı ("0500" Bu örnekte) ve işareti (+ veya -) göz ardı edilir.

Serileştirilirken <xref:System.DateTime>, <xref:System.DateTimeKind.Local> ve <xref:System.DateTimeKind.Unspecified> kez bir uzaklık ile yazılır ve <xref:System.DateTimeKind.Utc> olmadan yazılır.

ASP.NET AJAX istemci JavaScript kodu gibi dizeleri JavaScript ile otomatik olarak dönüştürür. `DateTime` örnekleri. Türü olmayan benzer bir forma sahip diğer dizeleri varsa <xref:System.DateTime> . NET'te, bunlar da dönüştürülür.

Yalnızca gerçekleşir, "/" karakterleri kaçış dönüştürme (diğer bir deyişle, JSON şuna benzer "\\/Date(700000+0500)\\/") ve bu nedenle WCF'ın JSON Kodlayıcı (etkin <xref:System.ServiceModel.WebHttpBinding>) her zaman "/" karakter çıkışları.

### <a name="xml-in-json-strings"></a>JSON dizeler XML

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement> , hiçbir kaydırma ile olduğu gibi seri hale getirilir. Örneğin, türü veri üyesi "x" <xref:System.Xml.XmlElement> içeren \<abc / > aşağıdaki şekilde gösterilen aynıdır.

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>XmlNode dizilerini

<xref:System.Array> türündeki nesneler <xref:System.Xml.XmlNode> ArrayOfXmlNode türü için standart veri anlaşması ad alanında denilen bir elemana sarmalanır. "X", "value" içerir "ns" ad alanında öznitelik düğümü "N" ve "M" bir boş öğe düğümü içeren bir dizi ise, temsili aşağıdaki gibidir.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Boş ad alanı başına XmlNode dizilerini (önce diğer öğeleri) öznitelikleri desteklenmez.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>XElement ve veri kümesi dahil olmak üzere IXmlSerializable türü

<xref:System.Runtime.Serialization.ISerializable> türleri "içerik türleri", "Veri kümesi türleri" ve "öğe türleri" alt bölümlere ayırır. Bu tür tanımları için bkz. [XML ve ADO.NET türleri veri anlaşmalarında](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

"İçerik" ve "Veri kümeleri" türleri benzer serileştirilme <xref:System.Array> nesnelerin <xref:System.Xml.XmlNode> önceki bölümde açıklanan. Bir öğe adı sarmalanır ve ad alanı türünün ad alanını ve veri anlaşması adına söz konusu karşılık gelir.

"Öğesi" gibi türleri <xref:System.Xml.Linq.XElement> , benzer olarak serileştirilme şeklini <xref:System.Xml.XmlElement> bu konuda daha önce tartışılan.

### <a name="polymorphism"></a>Çok Biçimlilik

#### <a name="preserving-type-information"></a>Koruma türü bilgileri

Daha önce belirtildiği gibi çok biçimlilik JSON'da bazı sınırlamalarıyla birlikte desteklenir. JavaScript bir zayıf yazılmış bir dildir ve tür kimliği bir sorun değildir normalde. Ancak, kesin türü belirtilmiş bir sistem (.NET) ve zayıf yazılmış bir sistem (JavaScript) arasında iletişim kurmak için JSON'ı kullanırken, türü kimlik korumak yararlıdır. Örneğin, adları "Kare" ve "Daire" bir türden "Şeklin" bir veri anlaşması adına sahip türetilmiş veri türleriyle sözleşme. "Daire".NET, JavaScript için gönderilir ve daha sonra "Şekline" bekliyor bir .NET yöntemi döndürülen, söz konusu nesne ilk olarak bir "daire" - Aksi durumda olduğunu bilmek .NET tarafı için kullanışlıdır (örneğin türetilmiş türüne özgü herhangi bir bilgi "Daire" Şirket "RADIUS" veri üyesi) kaybolabilir.

Türü kimlik JSON "türü ipucu" karmaşık türleri serileştirmek eklenebilir ve seri durumdan çıkarıcı ipucu tanır ve uygun şekilde davranan korumak için. Anahtar adını içeren bir JSON anahtar/değer çifti "Türü ipucu" olan "\_\_türü" (iki alt çizgi ve ardından "type" sözcüğü). "(İlk iki nokta üst üste kadar her şeyi adıdır) DataContractName:DataContractNamespace" biçiminin bir JSON dizesi değeridir. Önceki örneği kullanarak "Daire" gibi seri hale getirilebilir.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Tür ipucu çok benzer `xsi:type` özniteliği XML şema örnek standardı tarafından tanımlanan ve kullanılabilir serileştirme/XML seri durumdan çıkarılırken.

Veri üyeleri adında "\_\_türü" türü ipucuyla birlikte çakışma olasılığı nedeniyle Yasak.

#### <a name="reducing-the-size-of-type-hints"></a>Tür ipuçlarını boyutunu küçültme

JSON boyutunu azaltmak için iletileri, varsayılan veri anlaşması ad alanı öneki (`http://schemas.datacontract.org/2004/07/`) "#" karakteriyle değiştirilir. (Bu değişikliği geri alınabilir hale getirmek için escaping bir kuralı kullanılır: ad alanı "#" ile başlıyorsa veya "\\" karakter ile fazladan eklenmiş "\\" karakter). Bu nedenle, .NET ad alanı "MyApp.Shapes" tür "Daire" ise, varsayılan veri anlaşması ad olduğu `http://schemas.datacontract.org/2004/07/MyApp`. Şekiller ve JSON gösterimi gibidir.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Kesilmiş (#MyApp.Shapes) hem de tam (http://schemas.datacontract.org/2004/07/MyApp.Shapes) adları seri durumundan çıkarma işleminde anladım.

#### <a name="type-hint-position-in-json-objects"></a>JSON nesnesi tür ipucu konumu

Tür İpucu'nda JSON gösterimi ilk olması gerektiğini unutmayın. Bu, anahtar/değer çiftleri sırasını JSON işleme önemli olduğu, yalnızca durumdur. Örneğin, aşağıdaki tür ipucunu belirlemek için geçerli bir yol değil.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Her iki <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> WCF ve ASP.NET AJAX tarafından kullanılan istemci sayfalarında her zaman türü ipucu ilk gösterin.

#### <a name="type-hints-apply-only-to-complex-types"></a>Yalnızca karmaşık türler için tür ipuçlarını uygulayın

Karmaşık olmayan türler için tür ipucu yaymak için hiçbir yolu yoktur. Örneğin, bir işlem varsa, bir <xref:System.Object> bir daire dönüş türü döndürür ancak, daha önce gösterildiği gibi JSON gösterimi olabilir ve tür bilgileri korunur. Ancak, URI döndürülürse, JSON temsili bir dize ve bir URI temsil etmek için kullanılan dize kaybolur olgu olur. Bu, yalnızca ilkel türler için aynı zamanda koleksiyonlar ve diziler için geçerlidir.

#### <a name="when-are-type-hints-emitted"></a>Ne tür ipuçlarını gönderilir

Tür ipuçlarını artırabileceği ileti boyutunu önemli ölçüde (azaltmak için tek yönlü kısa veri anlaşması ad alanları mümkünse kullanılacak budur). Tür ipuçlarını yayılan olup olmadığını, bu nedenle, aşağıdaki kurallar yöneten:

- Olsa bile hiçbir taban/türetilmiş atama - Örneğin, bir daire dairenin atanmış olsa bile ASP.NET AJAX kullanırken, türü ipuçları her zaman mümkün olduğunda gönderilir. (Bu bilgi kaybı olmadan şaşırtıcı kesin .NET ortamına zayıf yazılmış JSON ortamından çağırma işlemine tam olarak etkinleştirmek için gereklidir.)

- Daire şekle atanmış durumdayken yayılan olan bir taban/türetilmiş atama - olduğunda tür ipuçlarını AJAX Hizmetleri ile tümleştirme yoktur ASP.NET kullanırken, yalnızca gönderilir veya <xref:System.Object> ancak daireye atandığında değil. Bu nedenle performansını geliştirme bir JavaScript istemci doğru uygulamak için gerekli en düşük bilgi sağlar ancak istemcileri yanlış şekilde tasarlanmış türü bilgi kaybına karşı koruma sağlamaz. İstemci üzerinde bu sorunu uğraşmanızı kaçınmak istiyorsanız taban/türetilmiş atamaları sunucu üzerinde tamamen kaçının.

- Kullanırken <xref:System.Runtime.Serialization.DataContractSerializer> türü `alwaysEmitTypeInformation` Oluşturucu parametresi olan varsayılan ile önceki iki modları arasında seçim yapmanızı sağlayan "`false`" (yalnızca gerekli olduğunda tür ipuçlarını göster).

#### <a name="duplicate-data-member-names"></a>Yinelenen veri üye adları

Türetilmiş tür bilgiler, temel tür bilgileriyle birlikte aynı JSON nesnesinde var ve herhangi bir sırayla gerçekleşebilir. Örneğin, `Shape` şu şekilde temsil edilebilir.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Daire şu şekilde temsil edilebilir ise.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Temel `Shape` türü adlı bir veri üyesi de yer alan "`radius`", (JSON nesneleri anahtar adları yinelenen bulunamayacağından) için bir çakışma hem seri hale getirme üzerinde bu doğurur ve ("RADIUS" içinolupolmadığınıgösterirbelirsizolduğundanseridurumdançıkarma`Shape.radius` veya `Circle.radius`). Bu nedenle, "özelliği gizleme" kavramını while (üzerinde aynı ada sahip veri üyeleri temel ve türetilmiş sınıflar) genellikle önerilmez veri sözleşme sınıflarda, aslında yasaklandı JSON söz konusu olduğunda.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Çok biçimlilik ve IXmlSerializable türü

<xref:System.Xml.Serialization.IXmlSerializable> normal veri sözleşme kurallara göre bilinen türleri gereksinimlerin karşılanıp karşılanmadığından sürece türleri polymorphically birbirine zamanki atanabilir. Ancak, serileştirme bir <xref:System.Xml.Serialization.IXmlSerializable> yerine yazın <xref:System.Object> sonuç bir JSON dizesi olarak türü bilgi kaybına sonuçlanır.

#### <a name="polymorphism-and-certain-interface-types"></a>Çok biçimlilik ve belirli bir arabirim türleri

Bir koleksiyon türü veya uygulayan bir tür olarak serileştirmek için Yasak <xref:System.Xml.Serialization.IXmlSerializable> olmayan bir toplama olmayan tür burada <xref:System.Xml.Serialization.IXmlSerializable> (dışında <xref:System.Object>) bekleniyor. Örneğin, özel arabirim adlı `IMyInterface` ve türü `MyType` , uygulama her ikisi de <xref:System.Collections.Generic.IEnumerable%601> türü `int` ve `IMyInterface`. Döndürülecek Yasak `MyType` , dönüş türü olan bir işlemden `IMyInterface`. Bunun nedeni, `MyType` , önce belirtilen olarak içeremez dizilerle, yalnızca karmaşık türler türü ipucuyla bir JSON dizisi olarak seri hale getirilmesi gerekir ve türü ipucu gerektirir.

#### <a name="known-types-and-configuration"></a>Bilinen türler ve yapılandırma

Tüm tarafından kullanılan bilinen türü mekanizmaları <xref:System.Runtime.Serialization.DataContractSerializer> da aynı şekilde tarafından desteklenen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Aynı yapılandırma öğesinde hem seri hale getiricileri genişletme okuma [ \<dataContractSerializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) içinde [ \<system.runtime.serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), bilinen türleri eklenen bulmak için bir yapılandırma dosyası.

#### <a name="collections-assigned-to-object"></a>Nesnesine atanan koleksiyonlar

Nesnesine atanan koleksiyonlar uygulayan koleksiyonları olmaları durumunda olarak serileştirilir <xref:System.Collections.Generic.IEnumerable%601>: karmaşık bir tür ise bir tür ipucu sahip her giriş içeren bir JSON dizisi. Örneğin, bir <xref:System.Collections.Generic.List%601> türü `Shape` atanan <xref:System.Object> aşağıdaki gibi görünür.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Geri seri durumdan olduğunda <xref:System.Object>:

- `Shape` Bilinen türleri listesinde olmalıdır. Sahip <xref:System.Collections.Generic.List%601> türü `Shape` Bilinen türlerin etkisi yoktur. Not eklemek için olmayan `Shape` bilinen türlere serileştirme bu durumda - bu otomatik olarak gerçekleştirilir.

- Koleksiyon olarak seri durumdan bir <xref:System.Array> türü <xref:System.Object> içeren `Shape` örnekleri.

#### <a name="derived-collections-assigned-to-base-collections"></a>Temel koleksiyonlara atanmış türetilmiş koleksiyonları

Türetilen bir koleksiyon temel bir koleksiyona atandığında, temel türün bir koleksiyon olduysa gibi koleksiyon genellikle serileştirilir. Ancak, temel koleksiyon öğesi türü için türetilmiş koleksiyonun öğe türü atanamaz ise bir özel durum oluşturulur.

#### <a name="type-hints-and-dictionaries"></a>Tür ipuçlarını ve sözlük

Ne zaman bir sözlük atandığı bir <xref:System.Object>, sanki atanmış her anahtar ve değer giriş sözlükteki kabul edilir <xref:System.Object> ve ipucu türü alır.

Sözlük türleri serileştirilirken "Anahtarını" ve "Değer" üyeleri içeren bir JSON nesnesi tarafından etkilenmez `alwaysEmitTypeInformation` ayarlama ve önceki toplama kuralları gerektirdiğinde yalnızca bir tür ipucu içeriyor.

### <a name="valid-json-key-names"></a>Geçerli bir JSON anahtar adları

Geçerli XML adları seri hale getirici XML kodlar anahtar adları. Örneğin, bir veri üyesi "123" adı ile kodlanmış bir adı gibi gerekir "\_x0031\_\_x0032\_\_x0033\_" "123" geçersiz bir XML öğesi adı olduğundan (ile başlayan bir basamak). Geçersiz XML adlarında bazı uluslararası karakter kümeleriyle benzer bir durum ortaya çıkabilir. Bu JSON işleme XML etkisini açıklaması için bkz: [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Ayrıca bkz.

- [JSON ve Diğer Veri Aktarma Biçimleri için Destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
