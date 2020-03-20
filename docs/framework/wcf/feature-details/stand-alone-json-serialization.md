---
title: DataContractJsonSerializer kullanarak Tek Başına JSON Serileştirme
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 36945f2d42f22ef3aa4f27bcbe403466f124a279
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184416"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>DataContractJsonSerializer kullanarak Tek Başına JSON Serileştirme

> [!NOTE]
> Bu makale <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>hakkında . JSON'u serihale ve deserializing içeren çoğu senaryo için [System.Text.Json ad alanında](../../../standard/serialization/system-text-json-overview.md)API'leri öneririz.

JSON (JavaScript Object Notation), tarayıcının içindeki Web sayfalarında çalışan JavaScript kodu tarafından kullanılmak üzere özel olarak tasarlanmış bir veri biçimidir. Windows Communication Foundation (WCF) ASP.NET AJAX hizmetleri tarafından kullanılan varsayılan veri biçimidir.

Bu biçim, ASP.NET ile tümleştirme den AJAX hizmetleri oluştururken de kullanılabilir - bu durumda, XML varsayılandır ancak JSON seçilebilir.

Son olarak, JSON desteğine ihtiyaç duyuyorsanız ancak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir AJAX hizmeti oluşturmuyorsanız, .NET nesnelerini doğrudan JSON verilerine seri hale getirmek ve bu tür verileri .NET türleri örneklerine yeniden dizileştirebilmek mümkün olur. Bunun nasıl yapılacağının açıklaması için [bkz: Serialize ve Deserialize JSON Verileri.](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md)

JSON ile çalışırken, aynı .NET türleri, birkaç istisna dışında, <xref:System.Runtime.Serialization.DataContractSerializer>tarafından desteklenen . Desteklenen türlerin listesi için [bkz.](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md) Bu en ilkel türleri, en dizi ve koleksiyon türleri yanı <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute>sıra ve kullanan karmaşık türleri içerir.

## <a name="mapping-net-types-to-json-types"></a>JSON Türlerine .NET türlerini eşleme

Aşağıdaki tabloda serileştirme ve deserialization yordamları ile eşlendiğinde .NET türleri ile JSON/JavaScript türleri arasındaki yazışmalar gösterilmektedir.

|.NET Türleri|JSON/JavaScript|Notlar|
|----------------|----------------------|-----------|
|Tüm sayısal türleri, örneğin <xref:System.Int32> <xref:System.Decimal> , veya<xref:System.Double>|Sayı|' `Double.NaN` `Double.PositiveInfinity` ve desteklenmez ve `Double.NegativeInfinity` geçersiz JSON ile sonuçlanır gibi özel değerler.|
|<xref:System.Enum>|Sayı|Bu konunun ilerleyen saatlerinde "Sonlandırma ve JSON" konusuna bakın.|
|<xref:System.Boolean>|Boole|--|
|<xref:System.String>, <xref:System.Char>|Dize|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Dize|JSON bu tür biçimi XML (aslında, ISO 8601 Süre biçiminde TimeSpan, "12345678-ABCD-ABCD-ABCD-1234567890AB" biçiminde GUID ve " "http://www.example.comgibi doğal dize şeklinde URI) aynıdır. Kesin bilgi için Bkz. [Veri Sözleşmesi Şeması Referansı.](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)|
|<xref:System.Xml.XmlQualifiedName>|Dize|Biçim "name:namespace" (ilk üst üste önce bir şey addır). Ad veya ad alanı eksik olabilir. Ad alanı yoksa, iki nokta üst üste de atlanabilir.|
|<xref:System.Array>türü<xref:System.Byte>|Sayı dizisi|Her sayı bir bayt değerini temsil eder.|
|<xref:System.DateTime>|DateTime veya String|Bu konunun ilerleyen dönemlerinde Tarihler/Saatler ve JSON'a bakın.|
|<xref:System.DateTimeOffset>|Karmaşık tür|Bu konunun ilerleyen dönemlerinde Tarihler/Saatler ve JSON'a bakın.|
|XML ve ADO.NET<xref:System.Xml.XmlElement>tipleri ( ,<br /><br /> <xref:System.Xml.Linq.XElement>. Diziler <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Dize|Bu konunun XML Türleri ve JSON bölümüne bakın.|
|<xref:System.DBNull>|Boş karmaşık türü|--|
|Koleksiyonlar, sözlükler ve diziler|Dizi|Bu konunun Koleksiyonlar, Sözlükler ve Diziler bölümüne bakın.|
|Karmaşık türleri <xref:System.Runtime.Serialization.DataContractAttribute> (veya <xref:System.SerializableAttribute> uygulanan ile)|Karmaşık tür|Veri üyeleri JavaScript karmaşık türüne üye olur.|
|<xref:System.Runtime.Serialization.ISerializable> Arabirimi uygulayan karmaşık türler)|Karmaşık tür|Diğer karmaşık türleri ile <xref:System.Runtime.Serialization.ISerializable> aynı ancak bazı türleri desteklenmez – bu konunun Gelişmiş Bilgiler bölümünün ISerializable Destek bölümüne bakın.|
|`Null`herhangi bir tür için değer|Null|Nullable türleri de desteklenir ve boşolmayan türleri ile aynı şekilde JSON eşlenir.|

### <a name="enumerations-and-json"></a>Sayısallaştırmalar ve JSON

Numaralandırma üye değerleri JSON'da sayı olarak değerlendirilir, bu da veri sözleşmelerinde nasıl ele alındıklarından farklıdır ve üye adolarak dahil edilirler. Veri sözleşmesi tedavisi hakkında daha fazla bilgi için, [Veri Sözleşmelerinde Numaralandırma Türleri'ne](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)bakın.

- Örneğin, varsa, `public enum Color {red, green, blue, yellow, pink}`serileştirme `yellow` "sarı" dizedeğil, 3 sayısını üretir.

- Tüm `enum` üyeler serileştirilebilir. Ve <xref:System.Runtime.Serialization.EnumMemberAttribute> <xref:System.NonSerializedAttribute> öznitelikleri kullanılırsa yoksayılır.

- Var olmayan bir `enum` değeri deserialize etmek mümkündür - örneğin, değer 87 tanımlanan karşılık gelen renk adı olmamasına rağmen önceki Renk enum içine deserialized olabilir.

- Bayraklar `enum` özel değildir ve diğer `enum`bayraklar gibi aynı muamele yitirmektir.

### <a name="datestimes-and-json"></a>Tarihler/Saatler ve JSON

JSON biçimi doğrudan tarihleri ve saatleri desteklemez. Ancak, çok yaygın olarak kullanılan ve ASP.NET AJAX bu tür için özel destek sağlar. ASP.NET AJAX yakınlıklarını kullanırken, .NET'teki <xref:System.DateTime> tür `DateTime` JavaScript'teki türe tam olarak karşılık gelir.

- ASP.NET kullanmadığınızda, <xref:System.DateTime> json'da bir tür, bu konunun Gelişmiş Bilgiler bölümünde açıklanan özel bir biçime sahip bir dize olarak temsil edilir.

- <xref:System.DateTimeOffset>karmaşık bir tür olarak JSON temsil edilir: {"DateTime":dateTime,"OfsetMinutes":offsetMinutes}. Üye, `offsetMinutes` greenwich ortalama saatinden (GMT) gelen yerel saat mahsupedilir ve şimdi de eşgüdümlü Evrensel Zaman (UTC) olarak da adlandırılır ve olayın ilgi çekici yeri ile ilişkilidir. Üye, `dateTime` ilgi olayının meydana geldiği zamandaki örneği temsil eder `DateTime` (yine, ASP.NET AJAX kullanımda olduğunda JavaScript'te bir olur ve olmadığında bir dize olur). Serileştirme `dateTime` de, üye her zaman GMT serihale edilir. Yani, 03:00 New York `dateTime` saati açıklayan, 8:00 `offsetMinutes` AM bir zaman bileşeni vardır ve 300 (eksi 300 dakika veya GMT 5 saat).

  > [!NOTE]
  > <xref:System.DateTime>ve <xref:System.DateTimeOffset> nesneler, JSON'a serileştirildiğinde, bilgileri yalnızca milisaniye hassasiyete kadar korur. Alt milisaniye değerleri (mikro/nanosaniye) serileştirme sırasında kaybolur.

### <a name="xml-types-and-json"></a>XML Türleri ve JSON

XML türleri JSON dizeleri olur.

- Örneğin, XElement türünden bir veri üyesi \<"q" abc/> içeriyorsa,\<JSON {"q":" abc/>"}olur.

- XML'in nasıl paketlediğini belirten bazı özel kurallar vardır - daha fazla bilgi için bu konunun ilerleyen bölümlerinde Gelişmiş Bilgiler bölümüne bakın.

- ASP.NET AJAX kullanıyorsanız ve JavaScript dizeleri kullanmak istemiyorsanız, ancak XML DOM yerine <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> istiyorsanız, XML <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> veya XML için <xref:System.ServiceModel.Web.WebInvokeAttribute>özelliği ayarlayın .

### <a name="collections-dictionaries-and-arrays"></a>Koleksiyonlar, Sözlükler ve Diziler

Tüm koleksiyonlar, sözlükler ve diziler JSON'da dizi olarak temsil edilir.

- Kullanan <xref:System.Runtime.Serialization.CollectionDataContractAttribute> herhangi bir özelleştirme JSON gösteriminde yoksayılır.

- Sözlükler doğrudan JSON ile çalışmak için bir yol değildir. Sözlük\<dizesi, nesne> wcf diğer JSON teknolojileri ile çalışan beklendiği gibi aynı şekilde desteklenmeyebilir. Örneğin, "abc" "xyz" ve "def" sözlükte 42 olarak eşlenirse, JSON gösterimi {"abc":"xyz","def":42} değil, [{"Key":"abc","Value":"xyz"},{"Key":"def","Value":42}] yerine.

- JSON ile doğrudan çalışmak istiyorsanız (katı bir sözleşmeyi önceden tanımlamadan tuşlara ve değerlere dinamik olarak erişme), birkaç seçeneğiniz var:

  - [Zayıf yazılanmış JSON Serialization (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) örneğini kullanmayı düşünün.

  - <xref:System.Runtime.Serialization.ISerializable> Arabirimi ve deserialization oluşturucuları kullanmayı düşünün - bu iki mekanizma, sırasıyla serileştirme ve deserialization JSON anahtar/değer çiftleri erişmenize olanak sağlar, ancak kısmi güven senaryolarında çalışmaz.

  - Bir serializer kullanmak yerine [JSON ve XML arasındaki Haritalama](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) ile çalışmayı düşünün.

  - Serileştirme bağlamında *çok biçimlilik,* türemiş bir türü, taban türünün beklendiği yerde serileştirme yeteneğini ifade eder. Koleksiyonları çok biçimli olarak kullanırken, örneğin bir koleksiyona bir <xref:System.Object>koleksiyon atarken, JSON'a özgü özel kurallar vardır. Bu konu daha sonra bu konuda İleri Bilgiler bölümünde daha tam olarak ele alınmıştır.

## <a name="additional-details"></a>Ek Ayrıntılar

### <a name="order-of-data-members"></a>Veri Üyeleri Sırası

JSON kullanırken veri üyelerinin sırası önemli değildir. Özellikle, ayarlanmış olsa <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> bile, JSON verileri yine de herhangi bir sırada deserialized olabilir.

### <a name="json-types"></a>JSON Türleri

JSON türü deserialization önceki tablo eşleşmesi gerekmez. Örneğin, normalde `Int` bir JSON numarasıyla eşleşir, ancak bu dize geçerli bir sayı içerdiği sürece JSON dizesinden başarıyla deserialed edilebilir. Diğer bir nokta, "q" adlı bir `Int` veri üyesi varsa hem {"q":42} hem de {"q":"42"} geçerlidir.

### <a name="polymorphism"></a>Çok biçimlilik

Polimorfik serileştirme, türemiş bir türü, taban türünün beklendiği yerde serileştirme yeteneğinden oluşur. Bu, XML serileştirmenin desteklenme şekliyle karşılaştırılabilir WCF tarafından JSON serileştirmesi için desteklenir. `MyDerivedType` Örneğin, beklendiği yeri `MyBaseType` serihale getirebilir veya `Int` beklendiği `Object` yeri serihale edebilirsiniz.

Karmaşık bir türü deserializing sürece, taban türü bekleniyorsa türemiş bir tür deserializing kaybolabilir. Örneğin, beklenen <xref:System.Uri> yerde <xref:System.Object> seri hale getirilirse, json dizesi ile sonuçlanır. Bu dize daha sonra tekrar <xref:System.Object>deserialized <xref:System.String> ise , bir .NET döndürülür. Deserializer dize türü başlangıçta olduğunu <xref:System.Uri>bilmiyor. Genellikle, beklerken, <xref:System.Object>tüm JSON dizeleri .NET dizeleri olarak deserialized ve tüm JSON dizileri serialize .NET koleksiyonları, sözlükler ve <xref:System.Array> diziler , ne olursa olsun gerçek orijinal türü ne olursa olsun <xref:System.Object>.NET olarak deserialized. Bir JSON boolean haritaları <xref:System.Boolean>bir .NET . <xref:System.Object>Ancak, json numaraları <xref:System.Int32>,.NET olarak <xref:System.Decimal> <xref:System.Double>deserialized veya , en uygun türü otomatik olarak seçilir bekliyor.

Arabirim türüne deserializing, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bildirilen türü nesne gibi deserialize.

Kendi tabanınız ve türetilmiş türleriile <xref:System.ServiceModel.ServiceKnownTypeAttribute> çalışırken, normalde eşdeğer bir mekanizma yı kullanmak <xref:System.Runtime.Serialization.KnownTypeAttribute>gerekir. Örneğin, iade değeri olan bir `Animal` işleminz varsa ve bu `Cat` işlem gerçekten `Animal`bir örneğini <xref:System.Runtime.Serialization.KnownTypeAttribute>döndürürse (türetilmiş), ya , `Animal` türe veya <xref:System.ServiceModel.ServiceKnownTypeAttribute> operasyona uygulamalı ve bu özniteliklerdeki `Cat` türü belirtmelisiniz. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)

Polimorfik serileştirmenin nasıl çalıştığına ilişkin ayrıntılar ve kullanırken uyulması gereken bazı sınırlamaların tartışılması için, bu konunun ilerleyen bölümlerinde Gelişmiş Bilgiler bölümüne bakın.

### <a name="versioning"></a>Sürüm oluşturma

<xref:System.Runtime.Serialization.IExtensibleDataObject> Arayüz de dahil olmak üzere veri sözleşmesi sürüm özellikleri, JSON'da tam olarak desteklenir. Ayrıca, çoğu durumda bir tür bir biçimde (örneğin, XML) deserialize ve sonra başka bir biçimde serileştirmek mümkündür (örneğin, JSON) ve hala verileri korumak <xref:System.Runtime.Serialization.IExtensibleDataObject>. Daha fazla bilgi için, [İleri-Uyumlu Veri Sözleşmeleri'ne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)bakın. JSON'Un siparişsiz olduğunu unutmayın, böylece herhangi bir sipariş bilgisi kaybolur. Ayrıca, JSON aynı anahtar adı ile birden çok anahtar/değer çiftini desteklemez. Son olarak, <xref:System.Runtime.Serialization.IExtensibleDataObject> tüm işlemler doğal olarak polimorfik - bu <xref:System.Object>onların türetilmiş türü , tüm türleri için temel türüa atanır.

## <a name="json-in-urls"></a>URL'lerde JSON

HTTP GET fiili (öznitelik kullanarak) <xref:System.ServiceModel.Web.WebGetAttribute> ile ASP.NET AJAX uç noktalarını kullanırken, gelen parametreler ileti gövdesi yerine istek URL'sinde görünür. JSON istek URL'sinde bile desteklenir, bu nedenle "sayı" adı verilen `Person` ve "p" adı verilen karmaşık bir tür içeren bir `Int` işleminiz varsa, URL aşağıdaki URL'ye benzeyebilir.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Hizmeti aramak için ASP.NET bir AJAX Script Manager denetimi ve proxy kullanıyorsanız, bu URL proxy tarafından otomatik olarak oluşturulur ve görülmez. JSON, NON-ASP.NET AJAX uç noktalarında URL'lerde kullanılamaz.

## <a name="advanced-information"></a>Gelişmiş bilgiler

### <a name="iserializable-support"></a>ISerializable Destek

#### <a name="supported-and-unsupported-iserializable-types"></a>Desteklenen ve Desteklenmeyen ISerializable Türleri

Genel olarak, <xref:System.Runtime.Serialization.ISerializable> arabirimi uygulayan türler JSON'u seri hale/deserializing'de tam olarak desteklenir. Ancak, bu türlerden bazıları (bazı .NET Framework türleri de dahil olmak üzere) JSON'a özgü serileştirme yönlerinin doğru şekilde deserialize edilmemelerine neden olacak şekilde uygulanır:

- Bununla <xref:System.Runtime.Serialization.ISerializable>birlikte, tek tek veri üyelerinin türü önceden bilinmez. Bu, türleri bir nesneye deserializing benzer bir polimorfik duruma yol açar. Daha önce de belirtildiği gibi, bu JSON türü bilgilerinin kaybına yol açabilir. Örneğin, `enum` bir uygulamayı seri hale getiren <xref:System.Runtime.Serialization.ISerializable> ve json ve JSON `enum` numaralarındaki sayılar kullanılarak seri hale `enum` getirilmiş olduğundan, bir tür doğrudan bir (uygun dökümler olmadan) yeniden seriselleştirmeye çalışır, yerleşik .NET sayısal türlerine (Int32, Ondalık veya Çift) ayrılır. Yani eskiden bir `enum` değer olan sayının kaybolması.

- Deserialization oluşturucusundaki belirli bir deserialization sırasına bağlı olan bir <xref:System.Runtime.Serialization.ISerializable> tür, bazı JSON verilerini deserialize etmekte başarısız olabilir, çünkü çoğu JSON serileştiricisi belirli bir siparişi garanti etmez.

#### <a name="factory-types"></a>Fabrika Tipleri

<xref:System.Runtime.Serialization.IObjectReference> Arabirim genel olarak JSON'da desteklenirken, "fabrika türü" özelliğini gerektiren (arabirimi <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> uygulayan türden farklı bir türe örnek döndürme) herhangi bir tür desteklenmez.

### <a name="datetime-wire-format"></a>DateTime Tel Biçimi

<xref:System.DateTime>değerler JSON dizeleri olarak "/Date(700000+0500)/", burada ilk sayı (7000000 verilen örnekte) GMT saat diliminde milisaniye sayısı, gece yarısından bu yana düzenli (gün ışığı dışı) zaman, 1 Ocak 1970 şeklinde görünür. Sayı daha önceki kez temsil etmek için negatif olabilir. Örnekte "+0500"den oluşan bölüm isteğe bağlıdır ve zamanın <xref:System.DateTimeKind.Local> türünün aynı olduğunu gösterir - yani, deserialization yerel saat dilimine dönüştürülmelidir. Yoksa, zaman <xref:System.DateTimeKind.Utc>. Bu örnekteki gerçek sayı ("0500" ve işareti (+ veya -) yoksayılır.

Serileştirme <xref:System.DateTime>ve <xref:System.DateTimeKind.Local> <xref:System.DateTimeKind.Unspecified> saatler ofset ile yazıldığında ve <xref:System.DateTimeKind.Utc> olmadan yazılır.

ASP.NET AJAX istemcijavascript kodu otomatik olarak JavaScript `DateTime` örnekleri ne tür dizeleri dönüştürür. .NET'te türü <xref:System.DateTime> olmayan benzer bir forma sahip başka dizeleri varsa, bunlar da dönüştürülür.

Dönüştürme yalnızca "/" karakterleri kaçarsa (diğer bir şekilde JSON\\" /Date(700000+0500)\\/") gibi görünürse) gerçekleşir ve bu <xref:System.ServiceModel.WebHttpBinding>nedenle WCF'nin JSON kodlayıcısı (etkin) her zaman "/" karakterinden kaçar.

### <a name="xml-in-json-strings"></a>XML Içinde JSON Dizeleri

#### <a name="xmlelement"></a>Xmlelement

<xref:System.Xml.XmlElement>olduğu gibi seri hale getirilir, sarma yoktur. Örneğin, abc/> içeren <xref:System.Xml.XmlElement> \<türdeki veri üyesi "x" aşağıdaki gibi temsil edilir:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>XmlNode dizileri

<xref:System.Array>tür <xref:System.Xml.XmlNode> nesneleri türü için standart veri sözleşme ad alanında ArrayOfXmlNode adlı bir öğeye sarılır. "x" ad alanı "ns" öznitelik düğümü "değer" ve boş bir eleman düğümü "M" içeren bir dizi ise, gösterimi aşağıdaki gibidir.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 XmlNode dizilerinin başındaki boş ad alanındaki öznitelikler (diğer öğelerden önce) desteklenmez.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>XElement ve DataSet dahil IXmlSerializable Türleri

<xref:System.Runtime.Serialization.ISerializable>türleri "içerik türleri", "DataSet türleri" ve "öğe türleri" olarak ikiye ayrılır. Bu tür tanımlar [için, Veri Sözleşmelerinde XML ve ADO.NET Türleri'ne](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)bakın.

"İçerik" ve "DataSet" türleri, <xref:System.Array> önceki bölümde <xref:System.Xml.XmlNode> tartışılan nesnelere benzer seri hale getirilmiştir. Bunlar, adı ve ad alanı söz konusu türdeki veri sözleşme adı ve ad alanına karşılık gelen bir öğeye sarılır.

"Öğe" türleri <xref:System.Xml.Linq.XElement> gibi serileştirilmiş, daha <xref:System.Xml.XmlElement> önce bu konuda tartışılan benzer.

### <a name="polymorphism"></a>Çok biçimlilik

#### <a name="preserving-type-information"></a>Tür Bilgilerinin Korunması

Daha önce de belirtildiği gibi, polimorfizm JSON bazı sınırlamalar ile desteklenir. JavaScript zayıf yazılmış bir dildir ve tür kimliği normalde bir sorun değildir. Ancak, güçlü bir şekilde yazılmış bir sistem (.NET) ve zayıf yazılmış bir sistem (JavaScript) arasında iletişim kurmak için JSON kullanırken, tür kimliğini korumak yararlıdır. Örneğin, veri sözleşmesi adları "Kare" ve "Daire" olan türler, "Şekil" veri sözleşme adı olan bir türden türetilmiştir. "Circle" .NET'ten JavaScript'e gönderilir ve daha sonra "Şekil" bekleyen bir .NET yöntemine döndürülürse, .NET tarafının söz konusu nesnenin başlangıçta bir "Daire" olduğunu bilmesi yararlıdır - aksi takdirde türemiş türe özgü herhangi bir bilgi (örneğin , "Circle" veri üyesi kaybolabilir.

Tür kimliğini korumak için, karmaşık türleri JSON'a seri hale getirmek için bir "tür ipucu" eklenebilir ve deserializer ipucunu tanır ve uygun şekilde davranır. "Tür ipucu" "\_\_türü" anahtar adı ile bir JSON anahtar / değer çifti (iki underscores kelime "türü") takip eder. Değer formu "DataContractName:DataContractNamespace" (ilk üst üste kadar bir şey adıdır) bir JSON dizesidir. Önceki örnek kullanılarak, "Circle" aşağıdaki gibi seri hale getirilebilir.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Tür ipucu, XML `xsi:type` Şema Örneği standardı tarafından tanımlanan ve XML'i serihale/deserialize ederken kullanılan özniteliğe çok benzer.

İpucu ile\_\_olası çakışma nedeniyle "tür" adı verilen veri üyeleri yasaktır.

#### <a name="reducing-the-size-of-type-hints"></a>Tür İpuçlarının Boyutunu Küçültme

JSON iletilerinin boyutunu küçültmek için varsayılan veri sözleşme`http://schemas.datacontract.org/2004/07/`ad alanı öneki ( ) "#" karakteriyle değiştirilir. (Bu değişikliği geri döndürülebilir hale getirmek için bir kaçış kuralı kullanılır: ad alanı\\"#" veya " " karakterlerle\\başlarsa, bunlar aki " " " karakteriyle eklenir). Bu nedenle, "Circle" .NET ad alanında "MyApp.Shapes" bir tür ise, `http://schemas.datacontract.org/2004/07/MyApp`varsayılan veri sözleşmesi namespace . Şekiller ve JSON gösterimi aşağıdaki gibidir.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Hem kesilen (#MyApp.Şekiller) hem dehttp://schemas.datacontract.org/2004/07/MyApp.Shapes) tam (adlar deserialization üzerinde anlaşılmaktadır.

#### <a name="type-hint-position-in-json-objects"></a>JSON Nesnelerinde İpucu Konumu Yazın

Tür ipucunun önce JSON gösteriminde görünmesi gerektiğini unutmayın. Bu, JSON işleminde anahtar/değer çiftleri sırasının önemli olduğu tek durumdur. Örneğin, aşağıdaki tür ipucu belirtmek için geçerli bir yol değildir.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Hem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> WCF ve ASP.NET AJAX istemci sayfaları tarafından kullanılan her zaman ilk tür ipucu yontun.

#### <a name="type-hints-apply-only-to-complex-types"></a>Tür İpuçları Yalnızca Karmaşık Türlere Uygulanır

Karmaşık olmayan türler için bir tür ipucu yontmak için bir yol yoktur. Örneğin, bir işlemin <xref:System.Object> bir iade türü varsa ancak bir Daire döndürürse, JSON gösterimi daha önce gösterildiği gibi olabilir ve tür bilgileri korunur. Ancak, Uri döndürülürse, JSON gösterimi bir dizedir ve Uri'yi temsil etmek için kullanılan dize kaybolur. Bu yalnızca ilkel türler için değil, koleksiyonlar ve diziler için de geçerlidir.

#### <a name="when-are-type-hints-emitted"></a>Tür İpuçları Ne Zaman Yayılır

Tür ipuçları ileti boyutunu önemli ölçüde artırabilir (bunu azaltmanın bir yolu, mümkünse daha kısa veri sözleşmesi ad alanları kullanmaktır). Bu nedenle, tür ipuçlarının yayılıp yayılmayacağı aşağıdaki kuralları yönetir:

- ASP.NET AJAX kullanırken, tür ipuçları her zaman mümkün olduğunda, hiçbir temel / türetilmiş atama olsa bile - örneğin, bir Daire bir Daire atanmış olsa bile yayılan. (Bu, zayıf yazılan JSON ortamından şaşırtıcı bir bilgi kaybı olmadan güçlü bir şekilde yazılan .NET ortamına arama işlemini tam olarak etkinleştirmek için gereklidir.)

- ASP.NET tümleştirmesi olmayan AJAX hizmetlerini kullanırken, tür ipuçları yalnızca bir temel/türetilmiş atama olduğunda yayılır - <xref:System.Object> yani Circle Şekil'e atandığında veya Circle'a atandığında değil, yayımlandığında. Bu, bir JavaScript istemcisini doğru bir şekilde uygulamak için gereken minimum bilgileri sağlar, böylece performansı artırır, ancak yanlış tasarlanmış istemcilerde tür bilgi kaybına karşı koruma sağlamaz. İstemci de bu sorunla uğraşmaktan kaçınmak istiyorsanız, sunucuda temel/türetilmiş atamaları tamamen kaçının.

- <xref:System.Runtime.Serialization.DataContractSerializer> Türü kullanırken, `alwaysEmitTypeInformation` oluşturucu parametresi varsayılan " (yalnızca`false`gerektiğinde tür ipuçları yontarak) ile, önceki iki mod arasında seçim yapmanızı sağlar.

#### <a name="duplicate-data-member-names"></a>Yinelenen Veri Üye Adları

Türetilen tür bilgileri, temel tür bilgileriyle birlikte aynı JSON nesnesinde bulunur ve herhangi bir sırada oluşabilir. Örneğin, `Shape` aşağıdaki gibi temsil edilebilir.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Oysa Circle aşağıdaki gibi temsil edilebilir.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Temel `Shape` türde " "`radius`" adlı bir veri üyesi de içeriyorsa, bu hem serileştirmede (JSON nesnelerinin anahtar adlarını yineleyemediği `Shape.radius` için) hem de deserialization 'da çakışmaya yol açar (çünkü "yarıçap"ın başvurup başvurulmadığı veya ifade edilip edilmediği `Circle.radius`belirsizdir). Bu nedenle, "özellik gizleme" kavramı (temelve türetilmiş sınıflara göre aynı adı taşıyan veri üyeleri) genellikle veri sözleşmesi sınıflarında önerilmez, aslında JSON durumunda yasaktır.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polimorfizm ve IXmlSerializable Türleri

<xref:System.Xml.Serialization.IXmlSerializable>türleri, bilinen tür gereksinimleri, olağan veri sözleşmesi kurallarına göre karşılandığı sürece, her zamanki gibi birbirlerine polimorfik olarak atanabilir. Ancak, sonuç <xref:System.Xml.Serialization.IXmlSerializable> olarak tür <xref:System.Object> bilgilerinin kaybı sonuçları yerine bir tür serileştirme bir JSON dizesi.

#### <a name="polymorphism-and-certain-interface-types"></a>Polimorfizm ve Belirli Arayüz Türleri

Bir koleksiyon türünü veya (hariç) <xref:System.Xml.Serialization.IXmlSerializable> <xref:System.Xml.Serialization.IXmlSerializable> <xref:System.Object>olmayan bir koleksiyon türü beklenen bir tür uygulayan bir türü seri hale getirmek yasaktır. Örneğin, özel bir `IMyInterface` arabirim `MyType` adlı ve <xref:System.Collections.Generic.IEnumerable%601> hem `int` `IMyInterface`tür ve . İade türü olan `MyType` bir işlemden dönmek `IMyInterface`yasaktır. Bunun nedeni, `MyType` JSON dizisi olarak serihale edilmesi ve bir tür ipucu gerektirmesi ve daha önce belirtildiği gibi dizili bir tür ipucunu yalnızca karmaşık türleri ile içeremeyeceğinizdir.

#### <a name="known-types-and-configuration"></a>Bilinen Türleri ve Yapılandırma

Kullanılan bilinen tip mekanizmaların <xref:System.Runtime.Serialization.DataContractSerializer> tümü de aynı şekilde <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>desteklenir. Her iki serializers aynı yapılandırma öğesi okumak, [ \<dataContractSerializer](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) [ \<system.runtime.serialization>](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)>, bilinen türleri keşfetmek için bir yapılandırma dosyası üzerinden eklendi.

#### <a name="collections-assigned-to-object"></a>Nesneye Atanan Koleksiyonlar

Object'e atanan koleksiyonlar, sanki uygulayan <xref:System.Collections.Generic.IEnumerable%601>koleksiyonlarmış gibi seri hale getirilmiştir: karmaşık bir türse, her girişi olan bir JSON dizisi. Örneğin, atanan <xref:System.Collections.Generic.List%601> bir `Shape` tür <xref:System.Object> aşağıdaki gibi görünür.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Tekrar deserialized <xref:System.Object>zaman:

- `Shape`Bilinen Türler listesinde olmalıdır. Bilinen <xref:System.Collections.Generic.List%601> türlerde tür `Shape` olmasının hiçbir etkisi yoktur. Bu durumda serileştirme de `Shape` bilinen türleri eklemek zorunda olmadığını unutmayın - bu otomatik olarak yapılır.

- Koleksiyon örnekleri içeren <xref:System.Array> <xref:System.Object> `Shape` bir tür olarak deserialized.

#### <a name="derived-collections-assigned-to-base-collections"></a>Temel Koleksiyonlara Atanan Türemiş Koleksiyonlar

Türetilmiş bir koleksiyon bir temel koleksiyona atandığında, koleksiyon genellikle temel türün bir koleksiyonuymuş gibi seri hale getirilir. Ancak, türemiş koleksiyonun madde türü temel koleksiyonun madde türüne atanamıyorsa, bir özel durum atılır.

#### <a name="type-hints-and-dictionaries"></a>Tip İpuçları ve Sözlükler

Bir sözlük, <xref:System.Object>sözlükteki her Anahtar ve Değer girişine atandığında, atanmış <xref:System.Object> gibi değerlendirilir ve bir tür ipucu alır.

Sözlük türlerini seri hale alırken, "Anahtar" ve "Değer" üyelerini içeren `alwaysEmitTypeInformation` JSON nesnesi ayardan etkilenmez ve yalnızca önceki koleksiyon kuralları gerektirdiğinde bir tür ipucu içerir.

### <a name="valid-json-key-names"></a>Geçerli JSON Anahtar Adları

Serileştirici XML, geçerli XML adları olmayan anahtar adlarını kodlar. Örneğin, "123" adında bir veri üyesinin kodlanmış adı "\_x0031\_\_x0032\_\_x0033\_" gibi kodlanmış bir adı vardır, çünkü "123" geçersiz bir XML öğesi adıdır (basamakla başlar). Benzer bir durum, XML adlarında geçerli olmayan bazı uluslararası karakter kümeleri ile ortaya çıkabilir. XML'in JSON işleme üzerindeki bu etkisinin açıklaması için [JSON ve XML arasındaki haritalama](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [JSON ve Diğer Veri Aktarma Biçimleri için Destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
