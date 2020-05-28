---
title: DataContractJsonSerializer kullanarak tek başına JSON serileştirmesi
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 259d5da544262b5cae08e1be9e8ea6e077d5b947
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144935"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>DataContractJsonSerializer kullanarak tek başına JSON serileştirmesi

> [!NOTE]
> Bu makalede hakkında bilgi sağlanır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> . JSON serileştirilmesinin ve serisini kaldırma ile ilgili çoğu senaryo için, [System. Text. JSON ad alanındaki](../../../standard/serialization/system-text-json-overview.md)API 'leri öneririz.

JSON (JavaScript Nesne Gösterimi), tarayıcı içindeki Web sayfalarında çalışan JavaScript kodu tarafından kullanılmak üzere özel olarak tasarlanan bir veri biçimidir. Bu, Windows Communication Foundation (WCF) içinde oluşturulan ASP.NET AJAX Hizmetleri tarafından kullanılan varsayılan veri biçimidir.

Bu biçim, ASP.NET ile tümleştirmeden AJAX Hizmetleri oluştururken de kullanılabilir-Bu örnekte, XML varsayılandır ancak JSON seçilebilir.

Son olarak, JSON desteğine ihtiyacınız vardır ancak bir AJAX Hizmeti oluşturmadıysanız, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .net nesnelerinin doğrudan JSON verilerine serileştirmesini ve bu gibi verilerin serisini .net türlerinin örneklerine geri oluşturmasını mümkün hale getirir. Bunun nasıl yapılacağı hakkında bir açıklama için bkz. [nasıl yapılır: serileştirme ve seri durumdan ÇıKARMA JSON verileri](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

JSON ile çalışırken, tarafından desteklendiği gibi birkaç özel durum ile aynı .NET türleri desteklenir <xref:System.Runtime.Serialization.DataContractSerializer> . Desteklenen türlerin listesi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Buna en basit türler, çoğu dizi ve koleksiyon türü ve ve kullanan karmaşık türler dahildir <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> .

## <a name="mapping-net-types-to-json-types"></a>.NET türlerini JSON türleriyle eşleme

Aşağıdaki tabloda, serileştirme ve serisini kaldırma yordamları ile eşlendiğinde .NET türleri ve JSON/JavaScript türleri arasındaki yazışmalar gösterilmektedir.

|.NET türleri|JSON/JavaScript|Notlar|
|----------------|----------------------|-----------|
|Tüm sayısal türler, örneğin <xref:System.Int32> <xref:System.Decimal> veya<xref:System.Double>|Sayı|Ve gibi özel değerler `Double.NaN` `Double.PositiveInfinity` `Double.NegativeInfinity` desteklenmez ve geçersiz JSON ile sonuçlanır.|
|<xref:System.Enum>|Sayı|Bu konunun devamındaki "numaralandırmalar ve JSON" başlığına bakın.|
|<xref:System.Boolean>|Boole|--|
|<xref:System.String>, <xref:System.Char>|Dize|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Dize|JSON 'daki bu türlerin biçimi, XML (temel olarak, ISO 8601 süre biçimindeki zaman aralığı, "12345678-ABCD-ABCD-ABCD-1234567890AB" biçiminde ve URI DEĞERI "" gibi doğal dize biçiminde http://www.example.com ). Kesin bilgiler için bkz. [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|Dize|Biçim "ad: Namespace" (ilk iki nokta üst üsteden önce herhangi bir şey ad). Ad veya ad alanı eksik olabilir. Ad alanı yoksa, iki nokta üst üste işareti de atlanabilir.|
|<xref:System.Array>türünde<xref:System.Byte>|Sayı dizisi|Her sayı bir baytlık değeri temsil eder.|
|<xref:System.DateTime>|DateTime veya String|Bu konunun ilerleyen kısımlarında tarihlere/saatlere ve JSON öğesine bakın.|
|<xref:System.DateTimeOffset>|Karmaşık tür|Bu konunun ilerleyen kısımlarında tarihlere/saatlere ve JSON öğesine bakın.|
|XML ve ADO.NET türleri ( <xref:System.Xml.XmlElement> ,<br /><br /> <xref:System.Xml.Linq.XElement>. Dizileri <xref:System.Xml.XmlNode> ,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Dize|Bu konunun XML türleri ve JSON bölümüne bakın.|
|<xref:System.DBNull>|Boş karmaşık tür|--|
|Koleksiyonlar, sözlükler ve diziler|Dizi|Bu konunun koleksiyonlar, sözlükler ve diziler bölümüne bakın.|
|Karmaşık türler ( <xref:System.Runtime.Serialization.DataContractAttribute> veya <xref:System.SerializableAttribute> uygulanmış)|Karmaşık tür|Veri üyeleri JavaScript karmaşık türünün üyesi olur.|
|Arabirimi uygulayan karmaşık türler <xref:System.Runtime.Serialization.ISerializable> )|Karmaşık tür|Diğer karmaşık türlerle aynı ancak bazı <xref:System.Runtime.Serialization.ISerializable> türler desteklenmez – bu konunun gelişmiş bilgiler bölümünün ISerializable destek bölümüne bakın.|
|`Null`herhangi bir türün değeri|Null|Null yapılabilir değer türleri de desteklenir ve JSON ile aynı şekilde null atanamaz değer türleriyle eşlenir.|

### <a name="enumerations-and-json"></a>Numaralandırmalar ve JSON

Sabit listesi üyesi değerleri, JSON 'da sayı olarak değerlendirilir ve bu, üye adları olarak dahil oldukları veri sözleşmeleri içinde nasıl ele alındıklarından farklıdır. Veri anlaşması işlemi hakkında daha fazla bilgi için bkz. [veri sözleşmeleri Içindeki numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Örneğin, varsa `public enum Color {red, green, blue, yellow, pink}` serileştirmek, `yellow` "sarı" dizesini değil 3 sayısını üretir.

- Tüm `enum` Üyeler seri hale getirilebilir. <xref:System.Runtime.Serialization.EnumMemberAttribute>Kullanılıyorsa, ve <xref:System.NonSerializedAttribute> öznitelikleri yok sayılır.

- Varolmayan bir değerin serisini kaldırmak mümkündür; `enum` Örneğin, tanımlanmış bir renk adı olmasa bile 87 değeri önceki renk numaralandırmasında seri durumdan çıkarılmış olabilir.

- Bayrak `enum` özel değildir ve birbirleriyle aynı şekilde davranır `enum` .

### <a name="datestimes-and-json"></a>Tarihler/saatler ve JSON

JSON biçimi, tarihleri ve saatleri doğrudan desteklemez. Ancak, bunlar çok yaygın olarak kullanılır ve ASP.NET AJAX bu türler için özel destek sağlar. ASP.NET AJAX proxy 'leri kullanılırken, <xref:System.DateTime> .net 'teki tür JavaScript 'teki türü ile tam olarak karşılık gelir `DateTime` .

- ASP.NET kullanmadığınız durumlarda, bir <xref:System.DateTime> tür JSON içinde bu konunun gelişmiş bilgiler bölümünde açıklanan özel bir biçimde bir dize olarak temsil edilir.

- <xref:System.DateTimeOffset>, JSON 'da karmaşık bir tür olarak temsil edilir: {"DateTime":d Meditime, "OffsetMinutes": offsetMinutes}. `offsetMinutes`Üye, Greenwich saati 'nin (GMT) yerel saat farkıdır, Ayrıca artık ilgili etkinliğin konumuyla ilişkili olarak Eşgüdümlü Evrensel Saat (UTC) olarak da anılır. `dateTime`Üye, ilgilendiğiniz olayın gerçekleştiği zaman örneğini temsil eder (yine de, `DateTime` ASP.NET AJAX kullanımda olduğunda ve olmadığında bir dize olduğunda JavaScript 'te bir olur). Serileştirme sırasında, `dateTime` üye her zaman GMT 'de serileştirilir. Bu nedenle, 3:00 New York saati açıklanmışsa, `dateTime` 8:00 ' nin saat bileşeni vardır ve `offsetMinutes` 300 (300 eksi saat veya 5 saat GMT).

  > [!NOTE]
  > <xref:System.DateTime>ve <xref:System.DateTimeOffset> nesneler JSON ile serileştirildiğinde yalnızca milisaniyelik duyarlığa karşı bilgileri korur. Serileştirme sırasında alt milisaniyelik değerleri (mikro/nanosaniye) kaybolur.

### <a name="xml-types-and-json"></a>XML türleri ve JSON

XML türleri JSON dizeleri olur.

- Örneğin, XElement türünde bir veri üyesi "q" içeriyorsa \<abc/> , JSON {"q": " \<abc/> "} olur.

- XML 'in sarmalanmış olduğunu belirten bazı özel kurallar vardır. daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alan gelişmiş bilgiler bölümüne bakın.

- ASP.NET AJAX kullanıyorsanız ve JavaScript 'te dizeler kullanmak istemiyorsanız, ancak bunun yerine XML DOM ' ı istiyorsanız <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> özelliği üzerinde XML olarak <xref:System.ServiceModel.Web.WebGetAttribute> veya ÖZELLIĞINI üzerinde XML olarak ayarlayın <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> <xref:System.ServiceModel.Web.WebInvokeAttribute> .

### <a name="collections-dictionaries-and-arrays"></a>Koleksiyonlar, sözlükler ve diziler

Tüm koleksiyonlar, sözlükler ve diziler JSON 'da diziler olarak temsil edilir.

- Kullanan tüm özelleştirmeler <xref:System.Runtime.Serialization.CollectionDataContractAttribute> JSON gösteriminde yok sayılır.

- Sözlüklerde doğrudan JSON ile çalışmanın bir yolu yoktur. Sözlük \<string,object> , DIĞER JSON teknolojileriyle çalışılmasına benzer şekılde WCF 'de aynı şekilde desteklenmiyor olabilir. Örneğin, "abc", "XYZ" ile eşlenir ve "def" bir sözlükte 42 ile eşleştirilir, JSON temsili {"abc" değil: "XYZ", "def": 42}, ancak [{"Key": "abc", "Value": "XYZ"}, {"Key": "def", "Value": 42}] Bunun yerine.

- JSON ile doğrudan çalışmak istiyorsanız (bir rigıd sözleşmesini önceden tanımlamaya gerek kalmadan anahtar ve değerlere dinamik olarak erişme), birkaç seçeneğiniz vardır:

  - [Zayıf YAZıLMıŞ JSON serileştirme (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) örneğini kullanmayı göz önünde bulundurun.

  - <xref:System.Runtime.Serialization.ISerializable>Arabirim ve seri kaldırma oluşturucularını kullanmayı düşünün-bu iki mekanizma sırasıyla serileştirme ve seri durumundan çıkarma SıRASıNDA JSON anahtar/değer çiftlerine erişmenize izin verir, ancak kısmi güven senaryolarında çalışmaz.

  - Serileştirici kullanmak yerine [JSON ve XML arasındaki eşleme](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) ile çalışmayı düşünün.

  - Serileştirme bağlamındaki çok *biçimlilik* , temel türünün beklendiği türetilmiş bir türü seri hale getirme özelliğine başvurur. Koleksiyonlar polymorphically kullanılırken JSON 'a özgü özel kurallar vardır, örneğin, bir koleksiyon ' a atama <xref:System.Object> . Bu sorun, bu konunun ilerleyen bölümlerinde gelişmiş bilgiler bölümünde daha ayrıntılı olarak ele alınmıştır.

## <a name="additional-details"></a>Ek Ayrıntılar

### <a name="order-of-data-members"></a>Veri üyelerinin sırası

JSON kullanılırken veri üyelerinin sırası önemli değildir. Özellikle de ayarlanmış olsa bile <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> JSON verileri herhangi bir sırada seri durumdan çıkarılamaz.

### <a name="json-types"></a>JSON türleri

JSON türünün, seri durumdan çıkarma sırasında önceki tabloyla eşleşmesi gerekmez. Örneğin, normalde bir `Int` JSON numarasıyla eşleşir, ancak bu dize geçerli bir sayı içerdiği sürece BIR JSON dizesinden de başarıyla seri durumdan çıkarılmış olabilir. Diğer bir deyişle, `Int` "q" adlı bir veri üyesi varsa {"q": 42} ve {"q": "42"} geçerlidir.

### <a name="polymorphism"></a>Çok biçimlilik

Çok biçimli seri hale getirme, temel türünün beklenildiği türetilmiş bir türü seri hale getirme özelliğinden oluşur. Bu, XML serileştirme desteklenme yöntemine benzer şekilde WCF tarafından JSON serileştirme için desteklenir. Örneğin, `MyDerivedType` nerede `MyBaseType` beklenildiği veya seri hale getirme beklenen yerde seri hale getirebilirsiniz `Int` `Object` .

Karmaşık bir türü seri durumdan çıkarmadığınız takdirde, temel tür bekleniyorsa, tür bilgileri kaybolmuş olabilir. Örneğin, <xref:System.Uri> seri hale getiriliyorsa, <xref:System.Object> bir JSON dizesine neden olur. Bu dize daha sonra yeniden seri hale getirilir <xref:System.Object> , .net <xref:System.String> döndürülür. Seri hale getirici, dizenin başlangıçta tür olduğunu bilmez <xref:System.Uri> . Genellikle, beklenirken <xref:System.Object> Tüm json dizeleri .net dizeleri olarak seri durumdan çıkarılacak ve .net koleksiyonları, sözlükleri ve dizilerini seri hale getirmek için kullanılan tüm JSON dizileri, <xref:System.Array> <xref:System.Object> gerçek özgün türün ne olursa olsun, türü .net olarak seri durumdan çıkarılacak. Bir JSON Boole değeri bir .NET ile eşlenir <xref:System.Boolean> . Ancak <xref:System.Object> , bir değeri beklerken, .net ya da <xref:System.Int32> <xref:System.Decimal> <xref:System.Double> en uygun türün otomatik olarak çekildiği JSON numaralarının serisi kaldırılır.

Arabirim türünde seri durumdan çıkarılırken, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> belirtilen tür nesne gibi seri hale getirir.

Kendi Tabanınızla ve türetilmiş türlerle çalışırken, <xref:System.Runtime.Serialization.KnownTypeAttribute> <xref:System.ServiceModel.ServiceKnownTypeAttribute> veya ile eşdeğer bir mekanizma gereklidir. Örneğin, bir `Animal` dönüş değeri olan ve aslında (öğesinden türetilmiş) bir örneğini döndüren bir işlemden sahipseniz, `Cat` `Animal` <xref:System.Runtime.Serialization.KnownTypeAttribute> öğesini `Animal` türüne ya da öğesine uygulamanız gerekir <xref:System.ServiceModel.ServiceKnownTypeAttribute> ve `Cat` türü bu özniteliklerde belirtmeniz gerekir. Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Çok biçimli serileştirme çalışmasının nasıl çalıştığı ve bunu kullanırken dikkate alınmalıdır bazı sınırlamalara ilişkin bir Tartışmayla ilgili ayrıntılar için, bu konunun ilerleyen kısımlarında yer alan gelişmiş bilgiler bölümüne bakın.

### <a name="versioning"></a>Sürüm Oluşturma

Arabirim dahil, veri anlaşması sürüm oluşturma özellikleri <xref:System.Runtime.Serialization.IExtensibleDataObject> JSON 'da tamamen desteklenir. Ayrıca, çoğu durumda bir türün bir biçimde serisini kaldırmak (örneğin, XML) ve daha sonra başka bir biçimde (örneğin, JSON) seri hale getirmek ve ' de verileri sürdürmek mümkündür <xref:System.Runtime.Serialization.IExtensibleDataObject> . Daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Herhangi bir sipariş bilgisinin kaybedilmesi için JSON 'un sıralanmamış olduğunu unutmayın. Ayrıca, JSON aynı anahtar adına sahip birden çok anahtar/değer çiftini desteklemez. Son olarak, üzerindeki tüm işlemler <xref:System.Runtime.Serialization.IExtensibleDataObject> doğal olarak çok biçimli olur; bunların türetilmiş türü <xref:System.Object> , tüm türlerin temel türüdür.

## <a name="json-in-urls"></a>URL 'Lerdeki JSON

HTTP GET fiili ile ASP.NET AJAX uç noktaları kullanılırken ( <xref:System.ServiceModel.Web.WebGetAttribute> özniteliği kullanılarak), gelen parametreler ileti gövdesi yerine Istek URL 'sinde görüntülenir. JSON, istek URL 'sinde bile desteklenir, yani `Int` "numara" adlı bir işlem ve `Person` "p" adlı karmaşık bir tür varsa URL aşağıdaki URL 'ye benzeyebilir.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Hizmeti çağırmak için bir ASP.NET AJAX betik Yöneticisi denetimi ve proxy kullanıyorsanız, bu URL proxy tarafından otomatik olarak oluşturulur ve görünmez. JSON, non-ASP.NET AJAX uç noktalarında URL 'lerde kullanılamaz.

## <a name="advanced-information"></a>Gelişmiş bilgiler

### <a name="iserializable-support"></a>ISerializable desteği

#### <a name="supported-and-unsupported-iserializable-types"></a>Desteklenen ve desteklenmeyen ISerializable türleri

Genel olarak, arayüzü uygulayan türler <xref:System.Runtime.Serialization.ISerializable> JSON serileştirilirken/seri durumdan çıkarılırken tamamen desteklenir. Ancak, bu türlerden bazıları (bazı .NET Framework türler dahil), JSON 'a özgü serileştirme yönlerini doğru şekilde seri durumdan çıkarmamasına neden olacak şekilde uygulanır:

- İle <xref:System.Runtime.Serialization.ISerializable> , bireysel veri üyelerinin türü hiçbir şekilde önceden bilinmez. Bu, türlerin serisini kaldırmada benzer bir polimorfik bir duruma yol açar. Daha önce bahsedildiği gibi, bu, JSON içinde bilgi türü kaybına neden olabilir. Örneğin, kendi uygulamasında seri hale getirilen bir tür `enum` <xref:System.Runtime.Serialization.ISerializable> ve `enum` `enum` JSON ve JSON numaralarının yerleşik .net sayısal türlerine (Int32, Decimal veya Double) seri durumdan çıkarılabilecek şekilde serileştirildiği için, bu bir tür başarısız olur. Bu nedenle, bir değer olarak kullanılan sayının kaybolması aslında `enum` kaybolur.

- <xref:System.Runtime.Serialization.ISerializable>Seri hale getiricilerin çoğu belirli bir sırayı garanti etmez, bu, seri durumdan çıkarma oluşturucusunda belirli bir seri durumdan çıkarma sırasına bağlı bir tür JSON verilerinin serisini de gerçekleştiremeyebilir.

#### <a name="factory-types"></a>Fabrika türleri

<xref:System.Runtime.Serialization.IObjectReference>ARABIRIM JSON 'da genel olarak desteklenirken, "fabrika türü" özelliği gerektiren herhangi bir tür (arabirimi uygulayan türden farklı bir türün örneğini döndüren <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> ) desteklenmez.

### <a name="datetime-wire-format"></a>DateTime Tel biçimi

<xref:System.DateTime>değerler, "/date (700000 + 0500)/" biçiminde JSON dizeleri olarak görünür; burada ilk sayı (örnekteki 700000), gece yarısı, 1 Ocak 1970 ' de gece yarısından bu yana normal (günışığından yararlanma dışı tasarruf) zaman sayısıdır. Bu sayı, önceki süreleri temsil etmek için negatif olabilir. Örnekteki "+ 0500" ' den oluşan bölüm isteğe bağlıdır ve zamanın tür olduğunu, yani <xref:System.DateTimeKind.Local> seri durumundan çıkarma sırasında yerel saat dilimine dönüştürülmesi gerektiğini gösterir. Bu değer yoksa, saat seri durumdan çıkarılmış olur <xref:System.DateTimeKind.Utc> . Gerçek sayı (Bu örnekte "0500") ve işareti (+ veya-) yok sayılır.

Serileştirilirken <xref:System.DateTime> <xref:System.DateTimeKind.Local> ve <xref:System.DateTimeKind.Unspecified> zaman bir uzaklığa göre yazıldığında ve <xref:System.DateTimeKind.Utc> olmadan yazıldığında.

ASP.NET AJAX istemci JavaScript kodu, bu tür dizeleri otomatik olarak JavaScript `DateTime` örneklerine dönüştürür. .NET ' te türünde olmayan benzer bir forma sahip başka dizeler varsa <xref:System.DateTime> , bunlar da dönüştürülür.

Dönüştürme yalnızca, "/" karakterlerinin kaçış durumunda (yani, JSON " \\ /date (700000 + 0500) \\ /") ve bu nedenle WCF 'nin JSON Kodlayıcısı (tarafından etkinleştirilir <xref:System.ServiceModel.WebHttpBinding> ) her zaman "/" karakteri çıkar.

### <a name="xml-in-json-strings"></a>JSON dizelerinde XML

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement>, sarmalama olmadan, olarak serileştirilir. Örneğin, içeren türün "x" veri üyesi <xref:System.Xml.XmlElement> \<abc/> Şu şekilde temsil edilir:

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>XmlNode dizileri

<xref:System.Array>türündeki nesneler <xref:System.Xml.XmlNode> , türü için standart veri sözleşmesi ad alanında ArrayOfXmlNode adlı bir öğede sarmalanır. "X", "değer" ve boş bir "d" öğe düğümünü içeren "NS" ad alanındaki "N" öznitelik düğümünü içeren bir diziyse, Gösterim aşağıdaki gibidir.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 XmlNode dizilerinin başındaki (diğer öğelerden önceki) boş ad alanındaki öznitelikler desteklenmez.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>XElement ve DataSet dahil IXmlSerializable türleri

<xref:System.Runtime.Serialization.ISerializable>türler, "içerik türleri", "veri kümesi türleri" ve "öğe türleri" içinde alt bölümlere ayırır. Bu türlerin tanımları için bkz. [veri sözleşmeleri Içindeki XML ve ADO.net türleri](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

"İçerik" ve "veri kümesi" türleri, <xref:System.Array> <xref:System.Xml.XmlNode> önceki bölümde ele alınan nesnelere benzer şekilde serileştirilir. Ad ve ad alanı, söz konusu türün veri sözleşmesi adına ve ad alanına karşılık gelen bir öğede sarmalanır.

Gibi "öğe" türleri <xref:System.Xml.Linq.XElement> , <xref:System.Xml.XmlElement> Bu konuda daha önce açıklananlara benzer olarak serileştirilir.

### <a name="polymorphism"></a>Çok biçimlilik

#### <a name="preserving-type-information"></a>Tür bilgilerini koruma

Daha önce belirtildiği gibi, çok biçimlilik JSON 'ta bazı sınırlamalar ile desteklenir. JavaScript, Zayıf yazılmış bir dildir ve tür kimliği normalde bir sorun değildir. Ancak, türü kesin belirlenmiş bir sistem (.NET) ve zayıf türsüz bir sistem (JavaScript) arasında iletişim kurmak için JSON kullanılırken, tür kimliğini korumak yararlı olur. Örneğin, veri sözleşme adları "kare" ve "daire" olan türler, "Shape" veri sözleşmesi adına sahip bir türden türetilir. .NET ' ten JavaScript 'e ve daha sonra "şekil" bekleyen bir .NET metoduna "daire" döndürülürse, söz konusu nesnenin ilk olarak bir "daire" olduğunu ve aksi durumda türetilmiş türe özgü herhangi bir bilgiyi (örneğin, "daire" üzerinde "yarıçap" veri üyesi) kaybettiğini bilmeleri için .NET tarafında yararlı olur.

Tür kimliğini korumak için, karmaşık türler JSON 'a serileştirilirken bir "tür ipucu" eklenebilir ve seri hale getirici ipucunu algılar ve uygun şekilde davranır. "Tür ipucu", "Type" anahtar adına sahip bir JSON anahtar/değer çiftidir \_ \_ ("Type" kelimesinin ardından iki alt çizgi). Değer, "DataContractName: DataContractNamespace" biçiminde bir JSON dizesidir (ad, ilk iki nokta üst üste kadar olan addır). Önceki örneği kullanarak, "daire" aşağıdaki gibi seri hale getirilebilir.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Tür ipucu, `xsi:type` XML şema örneği standardı tarafından tanımlanan özniteliğe çok benzer ve XML serileştirilirken/seri durumdan çıkarılırken kullanılır.

"Type" adlı veri üyeleri \_ \_ , tür ipucuyla ilgili olası çakışma nedeniyle yasaktır.

#### <a name="reducing-the-size-of-type-hints"></a>Tür Ipuçlarının boyutunu azaltma

JSON iletilerinin boyutunu azaltmak için varsayılan veri sözleşmesi ad alanı ön eki ( `http://schemas.datacontract.org/2004/07/` ) "#" karakteriyle değiştirilmiştir. (Bu değişikliği geri döndürülebilir hale getirmek için, bir kaçış kuralı kullanılır: ad alanı "#" veya " \\ " karakterlerle başlıyorsa, bunlar fazladan bir " \\ " karakteriyle eklenir). Bu nedenle, "Circle" .NET ad alanındaki "MyApp. Shapes" türünde bir tür ise, varsayılan veri sözleşmesi ad alanı olur `http://schemas.datacontract.org/2004/07/MyApp` . Şekiller ve JSON temsili aşağıdaki gibidir.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Hem kesilmiş (#MyApp. Shapes) hem de Full ( <http://schemas.datacontract.org/2004/07/MyApp.Shapes> ) adları seri durumundan çıkarma sırasında anlaşıldı.

#### <a name="type-hint-position-in-json-objects"></a>JSON nesnelerinde tür Ipucu konumu

Tür ipucunun JSON temsilinin ilk bölümünde görünmesi gerektiğini unutmayın. Bu, anahtar/değer çiftlerinin sırasının JSON işlemede önemli olduğu tek durumdur. Örneğin, tür ipucunu belirtmek için aşağıdaki geçerli bir yol değildir.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>WCF ve ASP.NET Ajax istemci sayfaları tarafından kullanılan her ikisi de öncelikle tür ipucunu yayar.

#### <a name="type-hints-apply-only-to-complex-types"></a>Tür Ipuçları yalnızca karmaşık türler için geçerlidir

Karmaşık olmayan türler için bir tür ipucu yayın bir yolu yoktur. Örneğin, bir işlemin <xref:System.Object> dönüş türü varsa ancak bir daire döndürürse, JSON temsili daha önce gösterildiği gibi, tür bilgileri de korunur. Ancak, URI döndürülürse JSON temsili bir dizedir ve bir URI 'yi temsil etmek için kullanılan dize kaybedilir. Bu yalnızca temel türler için değil koleksiyonlar ve diziler için de geçerlidir.

#### <a name="when-are-type-hints-emitted"></a>Tür Ipuçları ne zaman yayınlanır

Tür ipuçları ileti boyutunu önemli ölçüde artırabilir (bunun bir yolu, mümkünse daha kısa veri anlaşması ad alanları kullanmaktır). Bu nedenle, aşağıdaki kurallar tür ipuçlarının yayılıp yayınlanmadığını yönetir:

- ASP.NET AJAX kullanırken, bir daire içine bir daire atansa bile, bir taban/türetilmiş atama olmasa bile tür ipuçları her zaman mümkün olduğunda dağıtılır. (Bu, Zayıf yazılmış JSON ortamından çağırma işleminin, önemli olmayan bir bilgi kaybı olmadan kesin türü belirtilmiş .NET ortamına çağrılması işlemini tam olarak etkinleştirmek için gereklidir.)

- ASP.NET tümleştirmesi olmadan AJAX Hizmetleri kullanırken, tür ipuçları yalnızca bir taban/türetilmiş atama olduğunda dağıtılır; bu, daire şekle atandığında veya <xref:System.Object> daire içine atandığında yayılır. Bu, JavaScript istemcisini doğru şekilde uygulamak için gereken en düşük bilgileri sağlar, bu sayede performansı geliştirir, ancak yanlış tasarlanmış istemcilerde tür bilgi kaybına karşı koruma sağlamaz. İstemcide bu sorunla ilgilenmemek istiyorsanız taban/türetilmiş atamalardan tamamen sunucu üzerinde kaçının.

- <xref:System.Runtime.Serialization.DataContractSerializer>Türü kullanılırken, `alwaysEmitTypeInformation` Oluşturucu parametresi yukarıdaki iki mod arasında seçim yapmanıza olanak sağlar. varsayılan olarak " `false` " (gerektiğinde yalnızca tür ipuçlarını göster).

#### <a name="duplicate-data-member-names"></a>Yinelenen veri üyesi adları

Türetilmiş tür bilgileri, temel tür bilgileriyle birlikte aynı JSON nesnesinde bulunur ve herhangi bir sırada gerçekleşebilir. Örneğin, `Shape` aşağıdaki gibi gösterilebilir.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Daire, aşağıdaki gibi gösterilebilir.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Temel `Shape` tür Ayrıca "" adlı bir veri üyesi içeriyorsa `radius` , bu, her iki SERILEŞTIRME (JSON nesneleri yinelenen anahtar adlarına sahip olmadığı için) ve seri durumundan çıkarma ("Radius" ya da buna işaret edildiği net olmadığından) için bir çarpışmayı doğurur `Shape.radius` `Circle.radius` . Bu nedenle, "özellik gizleme" kavramı (temel ve türetilmiş sınıflarda aynı ada sahip veri üyeleri) genellikle veri sözleşme sınıflarında önerilmemekle karşı, JSON durumunda gerçekten yasak olur.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Çok biçimlilik ve IXmlSerializable türleri

<xref:System.Xml.Serialization.IXmlSerializable>türler, her zamanki veri sözleşme kurallarına göre, bilinen türler karşılandığı sürece her zamanki gibi polymorphically atanmış olabilir. Ancak, <xref:System.Xml.Serialization.IXmlSerializable> <xref:System.Object> sonuç bir JSON dizesi olduğu için tür bilgilerinin kaybına neden olan bir türün serileştirilmesi.

#### <a name="polymorphism-and-certain-interface-types"></a>Çok biçimlilik ve belirli arabirim türleri

Bir koleksiyon türü veya <xref:System.Xml.Serialization.IXmlSerializable> olmayan bir koleksiyon türü <xref:System.Xml.Serialization.IXmlSerializable> (için hariç) için beklenen bir türü seri hale getirmek yasaktır <xref:System.Object> . Örneğin, adlı özel bir arabirim `IMyInterface` ve `MyType` hem türü hem de uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> `int` `IMyInterface` . `MyType`Dönüş türü olan bir işlemden döndürülmesi yasaktır `IMyInterface` . Bunun nedeni, `MyType` BIR JSON dizisi olarak serileştirilmesi ve bir tür ipucu gerektirdiğinden ve diziler içeren bir tür ipucu ve yalnızca karmaşık türlerle dahil edilebilmeniz gerekir.

#### <a name="known-types-and-configuration"></a>Bilinen türler ve yapılandırma

Tarafından kullanılan tüm bilinen tür mekanizmaları <xref:System.Runtime.Serialization.DataContractSerializer> , ile aynı şekilde de desteklenir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> . Her iki serileştiriciler, [\<dataContractSerializer>](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) [\<system.runtime.serialization>](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md) bir yapılandırma dosyası aracılığıyla eklenen bilinen türleri öğrenmek için içindeki aynı yapılandırma öğesini okur.

#### <a name="collections-assigned-to-object"></a>Nesneye atanan Koleksiyonlar

Nesnesine atanan koleksiyonlar, uygulayan koleksiyonlardır olarak serileştirilir <xref:System.Collections.Generic.IEnumerable%601> : BIR JSON dizisi, bir tür ipucu olan her bir girdi, karmaşık bir türdür. Örneğin, atanmış bir <xref:System.Collections.Generic.List%601> türü `Shape` <xref:System.Object> aşağıdaki gibi görünür.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Seri durumdan yeniden <xref:System.Object> :

- `Shape`Bilinen türler listesinde olmalıdır. <xref:System.Collections.Generic.List%601> `Shape` Bilinen türlerde türün bir etkisi yoktur. `Shape`Bu durumda, serileştirme üzerinde bilinen türlere eklemeniz gerekmez; bu otomatik olarak yapılır.

- Koleksiyon, örnekleri içeren bir tür olarak seri durumdan çıkarılacak <xref:System.Array> <xref:System.Object> `Shape` .

#### <a name="derived-collections-assigned-to-base-collections"></a>Taban koleksiyonlara atanmış türetilmiş Koleksiyonlar

Türetilmiş bir koleksiyon bir temel koleksiyona atandığında, koleksiyon genellikle temel türün bir koleksiyonu gibi serileştirilir. Ancak, türetilmiş koleksiyonun öğe türü, temel koleksiyonun öğe türüne atanmamışsa, bir özel durum oluşturulur.

#### <a name="type-hints-and-dictionaries"></a>Ipuçları ve sözlükler yazın

Bir sözlüğe bir sözlük atandığında <xref:System.Object> , Sözlükteki her anahtar ve değer girişi atanmış gibi değerlendirilir <xref:System.Object> ve bir tür ipucu alır.

Sözlük türlerini serileştirirken, "Key" ve "Value" üyelerini içeren JSON nesnesi `alwaysEmitTypeInformation` ayarından etkilenmez ve yalnızca önceki koleksiyon kuralları gerektirdiğinde bir tür ipucu içerir.

### <a name="valid-json-key-names"></a>Geçerli JSON anahtar adları

Seri hale getirici XML-geçerli XML adı olmayan anahtar adlarını kodlar. Örneğin, "123" adlı bir veri üyesi "x0031 x0032 x0033" gibi kodlanmış bir ada sahip olur, \_ \_ \_ \_ \_ \_ çünkü "123" geçersiz bir XML öğesi adı (bir basamakla başlar). Bazı uluslararası karakter kümelerinde XML adlarında geçerli olmayan benzer bir durum ortaya çıkabilir. JSON işlemede XML 'nin bu efektinin açıklaması için bkz. [JSON ve XML arasında eşleme](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Ayrıca bkz.

- [JSON ve Diğer Veri Aktarma Biçimleri için Destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
