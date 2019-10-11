---
title: DataContractJsonSerializer kullanarak tek başına JSON serileştirmesi
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 65cae13d0185ea1f18bdd54cd26f703fde984f69
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180244"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>DataContractJsonSerializer kullanarak tek başına JSON serileştirmesi

> [!NOTE]
> Bu makale <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ' dır. JSON serileştirilmesinin ve serisini kaldırma ile ilgili çoğu senaryo için, [System. Text. JSON ad alanındaki](../../../standard/serialization/system-text-json-overview.md)araçları öneririz. 

JSON (JavaScript Nesne Gösterimi), tarayıcı içindeki Web sayfalarında çalışan JavaScript kodu tarafından kullanılmak üzere özel olarak tasarlanan bir veri biçimidir. Bu, Windows Communication Foundation (WCF) içinde oluşturulan ASP.NET AJAX Hizmetleri tarafından kullanılan varsayılan veri biçimidir.

Bu biçim, ASP.NET ile tümleştirmeden AJAX Hizmetleri oluştururken de kullanılabilir-Bu örnekte, XML varsayılandır ancak JSON seçilebilir.

Son olarak, JSON desteğine ihtiyacınız varsa ancak bir AJAX Hizmeti oluşturmadıysanız, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, .NET nesnelerinin doğrudan JSON verilerine serileştirmesini ve bu gibi verilerin serisini .NET türlerinin örneklerine geri oluşturmasını mümkün kılar. Bunun nasıl yapılacağı hakkında bir açıklama için bkz. [nasıl yapılır: serileştirme ve seri durumdan ÇıKARMA JSON verileri](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

JSON ile çalışırken, <xref:System.Runtime.Serialization.DataContractSerializer> tarafından desteklenen birkaç özel durum ile aynı .NET türleri desteklenir. Desteklenen türlerin listesi için bkz. [veri sözleşmesi serileştiricisi tarafından desteklenen türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Buna en basit türler, çoğu dizi ve koleksiyon türü ve <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> kullanan karmaşık türler dahildir.

## <a name="mapping-net-types-to-json-types"></a>.NET türlerini JSON türleriyle eşleme

Aşağıdaki tabloda, serileştirme ve serisini kaldırma yordamları ile eşlendiğinde .NET türleri ve JSON/JavaScript türleri arasındaki yazışmalar gösterilmektedir.

|.NET türleri|JSON/JavaScript|Notlar|
|----------------|----------------------|-----------|
|Tüm sayısal türler, örneğin <xref:System.Int32>, <xref:System.Decimal> veya <xref:System.Double>|Sayı|@No__t-0, `Double.PositiveInfinity` ve `Double.NegativeInfinity` gibi özel değerler desteklenmez ve geçersiz JSON ile sonuçlanır.|
|<xref:System.Enum>|Sayı|Bu konunun devamındaki "numaralandırmalar ve JSON" başlığına bakın.|
|<xref:System.Boolean>|Boole|--|
|<xref:System.String>, <xref:System.Char>|Dize|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|Dize|Bu türlerin JSON içindeki biçimi, XML 'dekiyle aynıdır (temelde, ISO 8601 Duration biçimindeki zaman aralığı, "12345678-ABCD-ABCD-ABCD-1234567890AB" biçimindeki ve URI 'nin "http://www.example.com" gibi doğal dize biçiminde GUID 'si). Kesin bilgiler için bkz. [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|Dize|Biçim "ad: Namespace" (ilk iki nokta üst üsteden önce herhangi bir şey ad). Ad veya ad alanı eksik olabilir. Ad alanı yoksa, iki nokta üst üste işareti de atlanabilir.|
|<xref:System.Array> tür <xref:System.Byte>|Sayı dizisi|Her sayı bir baytlık değeri temsil eder.|
|<xref:System.DateTime>|DateTime veya String|Bu konunun ilerleyen kısımlarında tarihlere/saatlere ve JSON öğesine bakın.|
|<xref:System.DateTimeOffset>|Karmaşık tür|Bu konunun ilerleyen kısımlarında tarihlere/saatlere ve JSON öğesine bakın.|
|XML ve ADO.NET türleri (<xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. @No__t dizileri-0,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|Dize|Bu konunun XML türleri ve JSON bölümüne bakın.|
|<xref:System.DBNull>|Boş karmaşık tür|--|
|Koleksiyonlar, sözlükler ve diziler|Dizi|Bu konunun koleksiyonlar, sözlükler ve diziler bölümüne bakın.|
|Karmaşık türler (<xref:System.Runtime.Serialization.DataContractAttribute> veya <xref:System.SerializableAttribute> uygulanmış)|Karmaşık tür|Veri üyeleri JavaScript karmaşık türünün üyesi olur.|
|@No__t-0 arabirimini uygulayan karmaşık türler)|Karmaşık tür|Diğer karmaşık türlerle aynı ancak bazı <xref:System.Runtime.Serialization.ISerializable> türleri desteklenmez – bu konunun gelişmiş bilgiler bölümünün ISerializable destek bölümüne bakın.|
|her tür için `Null` değeri|Null|Null yapılabilir türler de desteklenir ve JSON ile aynı şekilde null atanamaz türler ile eşlenir.|

### <a name="enumerations-and-json"></a>Numaralandırmalar ve JSON

Sabit listesi üyesi değerleri, JSON 'da sayı olarak değerlendirilir ve bu, üye adları olarak dahil oldukları veri sözleşmeleri içinde nasıl ele alındıklarından farklıdır. Veri anlaşması işlemi hakkında daha fazla bilgi için bkz. [veri sözleşmeleri Içindeki numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Örneğin, `public enum Color {red, green, blue, yellow, pink}` varsa, seri hale getirme `yellow`, "sarı" dizesini değil 3 sayısını üretir.

- Tüm `enum` üyeleri seri hale getirilebilir. @No__t-0 ve <xref:System.NonSerializedAttribute> öznitelikleri kullanılırsa yok sayılır.

- Varolmayan `enum` değerinin serisini kaldırmak mümkündür-Örneğin, tanımlı bir renk adı olmasa bile 87 değeri önceki renk numaralandırmasında seri durumdan çıkarılmış olabilir.

- @No__t-0 bayrakları özel değildir ve diğer `enum` ile aynı şekilde değerlendirilir.

### <a name="datestimes-and-json"></a>Tarihler/saatler ve JSON

JSON biçimi, tarihleri ve saatleri doğrudan desteklemez. Ancak, bunlar çok yaygın olarak kullanılır ve ASP.NET AJAX bu türler için özel destek sağlar. ASP.NET AJAX proxy 'leri kullanılırken, .NET 'teki <xref:System.DateTime> türü JavaScript 'teki `DateTime` türüne karşılık gelir.

- ASP.NET kullanmayan bir <xref:System.DateTime> türü, JSON içinde bu konunun gelişmiş bilgiler bölümünde açıklanan özel bir biçimde bir dize olarak temsil edilir.

- <xref:System.DateTimeOffset>, JSON içinde karmaşık bir tür olarak temsil edilir: {"DateTime":d ateTime, "OffsetMinutes": offsetMinutes}. @No__t-0 üyesi Greenwich saati 'nin (GMT) yerel zaman farkıdır, Ayrıca artık ilgili etkinliğin konumuyla ilişkili olan Eşgüdümlü Evrensel Saat (UTC) olarak da anılır. @No__t-0 üyesi, ilgilendiğiniz olayın gerçekleştiği zaman örneğini temsil eder (ASP.NET AJAX kullanımda olduğunda ve olmadığında bir dize olduğunda, JavaScript 'te bir `DateTime` olur). Serileştirme sırasında `dateTime` üyesi her zaman GMT 'de serileştirilir. Bu nedenle, 3:00 New York saati açıklanmışsa, `dateTime` ' ın saat bileşeni 8:00 ' dir ve `offsetMinutes` ' in 300 300 (GMT 'den 5 saat).

  > [!NOTE]
  > <xref:System.DateTime> ve <xref:System.DateTimeOffset> nesneleri JSON ile serileştirildiğinde yalnızca milisaniyelik duyarlığa karşı bilgileri korur. Serileştirme sırasında alt milisaniyelik değerleri (mikro/nanosaniye) kaybolur.

### <a name="xml-types-and-json"></a>XML türleri ve JSON

XML türleri JSON dizeleri olur.

- Örneğin, XElement türündeki bir "q" veri üyesi \<abc/> içeriyorsa JSON {"q": "\<ABC/>"} olur.

- XML 'in sarmalanmış olduğunu belirten bazı özel kurallar vardır. daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alan gelişmiş bilgiler bölümüne bakın.

- ASP.NET AJAX kullanıyorsanız ve JavaScript 'te dizeler kullanmak istemiyorsanız, ancak bunun yerine XML DOM ' ı istiyorsanız, <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> özelliğini <xref:System.ServiceModel.Web.WebGetAttribute> veya <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> özelliği <xref:System.ServiceModel.Web.WebInvokeAttribute> üzerinde XML olarak ayarlayın.

### <a name="collections-dictionaries-and-arrays"></a>Koleksiyonlar, sözlükler ve diziler

Tüm koleksiyonlar, sözlükler ve diziler JSON 'da diziler olarak temsil edilir.

- @No__t-0 kullanan tüm özelleştirmeler JSON gösteriminde yok sayılır.

- Sözlüklerde doğrudan JSON ile çalışmanın bir yolu yoktur. Sözlük @ no__t-0string, nesne >, diğer JSON teknolojileriyle çalışılmasına benzer şekilde WCF 'de aynı şekilde desteklenmiyor olabilir. Örneğin, "abc", "XYZ" ile eşlenir ve "def" bir sözlükte 42 ile eşleştirilir, JSON temsili {"abc" değil: "XYZ", "def": 42}, ancak [{"Key": "abc", "Value": "XYZ"}, {"Key": "def", "Value": 42}] Bunun yerine.

- JSON ile doğrudan çalışmak istiyorsanız (bir rigıd sözleşmesini önceden tanımlamaya gerek kalmadan anahtar ve değerlere dinamik olarak erişme), birkaç seçeneğiniz vardır:

  - [Zayıf YAZıLMıŞ JSON serileştirme (AJAX)](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md) örneğini kullanmayı göz önünde bulundurun.

  - @No__t-0 arabirimini ve seri kaldırma oluşturucularını kullanmayı düşünün-bu iki mekanizma sırasıyla serileştirme ve seri durumundan çıkarma sırasında JSON anahtar/değer çiftlerine erişmenize izin verir, ancak kısmi güven senaryolarında çalışmaz.

  - Serileştirici kullanmak yerine [JSON ve XML arasındaki eşleme](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) ile çalışmayı düşünün.

  - Serileştirme bağlamındaki çok *biçimlilik* , temel türünün beklendiği türetilmiş bir türü seri hale getirme özelliğine başvurur. Koleksiyonlar polymorphically kullanılırken JSON 'a özgü özel kurallar vardır, örneğin, <xref:System.Object> ' a koleksiyon atama. Bu sorun, bu konunun ilerleyen bölümlerinde gelişmiş bilgiler bölümünde daha ayrıntılı olarak ele alınmıştır.

## <a name="additional-details"></a>Ek Ayrıntılar

### <a name="order-of-data-members"></a>Veri üyelerinin sırası

JSON kullanılırken veri üyelerinin sırası önemli değildir. Özellikle de <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> ayarlansa bile JSON verileri herhangi bir sırada seri durumdan çıkarılamaz.

### <a name="json-types"></a>JSON türleri

JSON türünün, seri durumdan çıkarma sırasında önceki tabloyla eşleşmesi gerekmez. Örneğin, bir @no__t 0 normal olarak bir JSON numarasıyla eşlenir, ancak bu dize geçerli bir sayı içerdiği sürece bir JSON dizesinden de başarıyla seri durumdan çıkarılmış olabilir. Diğer bir deyişle, "q" adlı bir `Int` veri üyesi varsa, {"q": 42} ve {"q": "42"} geçerlidir.

### <a name="polymorphism"></a>Çok biçimlilik

Çok biçimli seri hale getirme, temel türünün beklenildiği türetilmiş bir türü seri hale getirme özelliğinden oluşur. Bu, XML serileştirme desteklenme yöntemine benzer şekilde WCF tarafından JSON serileştirme için desteklenir. Örneğin, `MyBaseType` ' in beklenildiği `MyDerivedType` ' ı veya @no__t 3 ' ün beklenen `Int` ' yi seri hale getirebilirsiniz.

Karmaşık bir türü seri durumdan çıkarmadığınız takdirde, temel tür bekleniyorsa, tür bilgileri kaybolmuş olabilir. Örneğin, <xref:System.Object> ' in beklenildiği <xref:System.Uri> seri hale getirilemiyorsa, JSON dizesine neden olur. Daha sonra bu dizenin serisi <xref:System.Object> ' a geri döndürülürse, bir .NET <xref:System.String> döndürülür. Seri hale getirici, dizenin başlangıçta <xref:System.Uri> türünde olduğunu bilmez. Genellikle <xref:System.Object> beklenirken, tüm JSON dizeleri .NET dizeleri olarak seri durumdan çıkarılacak ve .NET koleksiyonları, sözlükleri ve dizileri seri hale getirmek için kullanılan tüm JSON dizileri, gerçek özgün tür ne olursa olsun, <xref:System.Object> türünde .NET <xref:System.Array> olarak seri durumdan çıkarılacak Olmuştu. Bir JSON Boole değeri bir .NET @no__t eşlenir-0. Ancak, bir @no__t 0 beklerken, en uygun türün otomatik olarak çekildiği .NET <xref:System.Int32>, <xref:System.Decimal> veya <xref:System.Double> olarak JSON numaraları seri hale getirilmesi gerekir.

Arabirim türünde seri durumdan çıkarılırken, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, belirtilen tür nesne gibi seri hale getirir.

Kendi Tabanınızla ve türetilmiş türlerle çalışırken, <xref:System.Runtime.Serialization.KnownTypeAttribute> ' ı kullanarak, <xref:System.ServiceModel.ServiceKnownTypeAttribute> ' i veya eşdeğer bir mekanizma normalde gereklidir. Örneğin, `Animal` dönüş değerine sahip bir işleme sahipseniz ve aslında bir `Cat` (`Animal` ' den türetilmiş) örneği döndürürse, <xref:System.Runtime.Serialization.KnownTypeAttribute> ' i `Animal` türüne veya <xref:System.ServiceModel.ServiceKnownTypeAttribute> ' i, işleme ve `Cat` türünü belirtmeniz gerekir. Bu öznitelikler. Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Çok biçimli serileştirme çalışmasının nasıl çalıştığı ve bunu kullanırken dikkate alınmalıdır bazı sınırlamalara ilişkin bir Tartışmayla ilgili ayrıntılar için, bu konunun ilerleyen kısımlarında yer alan gelişmiş bilgiler bölümüne bakın.

### <a name="versioning"></a>Sürüm oluşturma

@No__t-0 arabirimi de dahil olmak üzere veri sözleşmesi sürüm oluşturma özellikleri JSON 'da tam olarak desteklenmektedir. Ayrıca, çoğu durumda bir türün bir biçimde serisini kaldırmak (örneğin, XML) ve sonra başka bir biçimde (örneğin JSON) seri hale getirmek ve <xref:System.Runtime.Serialization.IExtensibleDataObject> ' daki verileri sürdürmek mümkündür. Daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Herhangi bir sipariş bilgisinin kaybedilmesi için JSON 'un sıralanmamış olduğunu unutmayın. Ayrıca, JSON aynı anahtar adına sahip birden çok anahtar/değer çiftini desteklemez. Son olarak, <xref:System.Runtime.Serialization.IExtensibleDataObject> ' da tüm işlemler doğal olarak çok biçimli olduğundan, türetilmiş türleri tüm türler için temel tür olan <xref:System.Object> ' e atanır.

## <a name="json-in-urls"></a>URL 'Lerdeki JSON

HTTP GET fiili ile ASP.NET AJAX uç noktaları kullanılırken (<xref:System.ServiceModel.Web.WebGetAttribute> özniteliği kullanılarak), gelen parametreler ileti gövdesi yerine istek URL 'sinde görüntülenir. JSON, istek URL 'sinde bile desteklenir. bu nedenle, "Number" adlı bir @no__t ve "p" adlı `Person` karmaşık türü alan bir işlem varsa URL aşağıdaki URL 'ye benzemeyebilir.

```
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Hizmeti çağırmak için bir ASP.NET AJAX betik Yöneticisi denetimi ve proxy kullanıyorsanız, bu URL proxy tarafından otomatik olarak oluşturulur ve görünmez. JSON, non-ASP.NET AJAX uç noktalarında URL 'lerde kullanılamaz.

## <a name="advanced-information"></a>Gelişmiş bilgiler

### <a name="iserializable-support"></a>ISerializable desteği

#### <a name="supported-and-unsupported-iserializable-types"></a>Desteklenen ve desteklenmeyen ISerializable türleri

Genel olarak, <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayan türler JSON serileştirilirken/seri durumdan çıkarılırken tamamen desteklenir. Ancak, bu türlerden bazıları (bazı .NET Framework türler dahil), JSON 'a özgü serileştirme yönlerini doğru şekilde seri durumdan çıkarmamasına neden olacak şekilde uygulanır:

- @No__t-0 ile, bireysel veri üyelerinin türü hiçbir şekilde önceden bilinmez. Bu, türlerin serisini kaldırmada benzer bir polimorfik bir duruma yol açar. Daha önce bahsedildiği gibi, bu, JSON içinde bilgi türü kaybına neden olabilir. Örneğin, bir `enum` ' ı <xref:System.Runtime.Serialization.ISerializable> uygulamasında seri hale getirmeye çalışır ve doğrudan bir `enum` ' ye (uygun yayınlar olmadan) seri durumdan çıkarma girişiminde bulunur, çünkü bir `enum` JSON 'daki sayılar kullanılarak serileştirilir ve yerleşik .NET sayısal türleri (Int32, Decimal veya Double). Yani `enum` değeri olması için kullanılan sayının kaybolması.

- Seri hale getiricilerin belirli bir sırayı garanti etmez, ancak seri hale getiriciler oluşturucusunda belirli bir sıra serisini belirten bir <xref:System.Runtime.Serialization.ISerializable> türü bazı JSON verilerinin serisini de bozabilir.

#### <a name="factory-types"></a>Fabrika türleri

@No__t-0 arabirimi genel olarak JSON 'da desteklenirken, "fabrika türü" özelliği gerektiren herhangi bir tür (<xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> ' den arabirimi uygulayan türden farklı bir türün örneğini döndüren) desteklenmez.

### <a name="datetime-wire-format"></a>DateTime Tel biçimi

<xref:System.DateTime> değerleri, "/date (700000 + 0500)/" biçiminde JSON dizeleri olarak görünür; burada ilk sayı (örnekteki 700000), gece yarısı, 1 Ocak 1970 ' de gece yarısından bu yana normal (günışığından yararlanma dışı tasarruf) zaman sayısıdır. Bu sayı, önceki süreleri temsil etmek için negatif olabilir. Örnekteki "+ 0500" ' den oluşan bölüm isteğe bağlıdır ve zamanın <xref:System.DateTimeKind.Local> türünde olduğunu belirtir; yani, seri durumdan çıkarma sırasında yerel saat dilimine dönüştürülmelidir. Bu değer yoksa, <xref:System.DateTimeKind.Utc> olarak seri durumdan çıkarılmış olur. Gerçek sayı (Bu örnekte "0500") ve işareti (+ veya-) yok sayılır.

@No__t-0 ' ı serileştirilirken, <xref:System.DateTimeKind.Local> ve <xref:System.DateTimeKind.Unspecified> kez bir uzaklığa yazılır ve <xref:System.DateTimeKind.Utc>, olmadan yazılır.

ASP.NET AJAX istemci JavaScript kodu, bu tür dizeleri otomatik olarak JavaScript `DateTime` örneklerine dönüştürür. .NET içinde <xref:System.DateTime> türünde olmayan benzer bir forma sahip başka dizeler varsa, bunlar da dönüştürülür.

Dönüştürme yalnızca "/" karakterlerinin kaçış durumunda (yani, JSON "\\/Date (700000 + 0500) \\/") ve bu nedenle WCF 'nin JSON Kodlayıcısı (<xref:System.ServiceModel.WebHttpBinding> tarafından etkinleştirilir) her zaman "/" karakteri çıkar.

### <a name="xml-in-json-strings"></a>JSON dizelerinde XML

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement>, sarmalama olmadan olduğu gibi serileştirilir. Örneğin, \<ABC/> içeren <xref:System.Xml.XmlElement> türündeki veri üyesi "x" aşağıdaki gibi gösterilir.

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>XmlNode dizileri

<xref:System.Xml.XmlNode> türündeki <xref:System.Array> nesneleri, türü için standart veri sözleşmesi ad alanında ArrayOfXmlNode adlı bir öğede sarmalanmış. "X", "değer" ve boş bir "d" öğe düğümünü içeren "NS" ad alanındaki "N" öznitelik düğümünü içeren bir diziyse, Gösterim aşağıdaki gibidir.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 XmlNode dizilerinin başındaki (diğer öğelerden önceki) boş ad alanındaki öznitelikler desteklenmez.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>XElement ve DataSet dahil IXmlSerializable türleri

<xref:System.Runtime.Serialization.ISerializable> türleri, "içerik türleri", "veri kümesi türleri" ve "öğe türleri" içinde alt bölümlere ayırır. Bu türlerin tanımları için bkz. [veri sözleşmeleri Içindeki XML ve ADO.net türleri](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

"İçerik" ve "veri kümesi" türleri, önceki bölümde açıklanan <xref:System.Xml.XmlNode> <xref:System.Array> nesnelerine benzer şekilde serileştirilir. Ad ve ad alanı, söz konusu türün veri sözleşmesi adına ve ad alanına karşılık gelen bir öğede sarmalanır.

@No__t-0 gibi "öğe" türleri, bu konuda daha önce açıklanan <xref:System.Xml.XmlElement> ' e benzer şekilde olarak serileştirilir.

### <a name="polymorphism"></a>Çok biçimlilik

#### <a name="preserving-type-information"></a>Tür bilgilerini koruma

Daha önce belirtildiği gibi, çok biçimlilik JSON 'ta bazı sınırlamalar ile desteklenir. JavaScript, Zayıf yazılmış bir dildir ve tür kimliği normalde bir sorun değildir. Ancak, türü kesin belirlenmiş bir sistem (.NET) ve zayıf türsüz bir sistem (JavaScript) arasında iletişim kurmak için JSON kullanılırken, tür kimliğini korumak yararlı olur. Örneğin, veri sözleşme adları "kare" ve "daire" olan türler, "Shape" veri sözleşmesi adına sahip bir türden türetilir. .NET ' ten JavaScript 'e ve daha sonra "şekil" bekleyen bir .NET yöntemine "daire" döndürülürse, söz konusu nesnenin ilk olarak "daire" olduğunu ve diğer yandan türetilmiş türe özgü bilgileri (örneğin, "" daire "üzerinde" Radius "veri üyesi kaybolmuş olabilir.

Tür kimliğini korumak için, karmaşık türler JSON 'a serileştirilirken bir "tür ipucu" eklenebilir ve seri hale getirici ipucunu algılar ve uygun şekilde davranır. "Tür ipucu", "\_ @ no__t-1Type" anahtar adına sahip bir JSON anahtar/değer çiftidir ("Type" sözcüğünün ardından gelen iki alt çizgi). Değer, "DataContractName: DataContractNamespace" biçiminde bir JSON dizesidir (ad, ilk iki nokta üst üste kadar olan addır). Önceki örneği kullanarak, "daire" aşağıdaki gibi seri hale getirilebilir.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

Tür ipucu, XML şema örneği standardı tarafından tanımlanan ve XML serileştirilirken/seri durumdan çıkarılırken kullanılan `xsi:type` özniteliğine çok benzer.

"@No__t-0 @ no__t-1Type" adlı veri üyeleri, tür ipucuyla ilgili olası çakışma nedeniyle yasaktır.

#### <a name="reducing-the-size-of-type-hints"></a>Tür Ipuçlarının boyutunu azaltma

JSON iletilerinin boyutunu azaltmak için, varsayılan veri anlaşması ad alanı ön eki (`http://schemas.datacontract.org/2004/07/`) "#" karakteriyle değiştirilmiştir. (Bu değişikliği geri döndürülebilir hale getirmek için, bir kaçış kuralı kullanılır: ad alanı "#" veya "\\" karakterleriyle başlıyorsa, bunlar fazladan bir "\\" karakteriyle eklenir. Bu nedenle, "Circle" .NET ad alanındaki "MyApp. Shapes" türünde bir tür ise, varsayılan veri sözleşmesi ad alanı `http://schemas.datacontract.org/2004/07/MyApp` ' dır. Şekiller ve JSON temsili aşağıdaki gibidir.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Hem kesilmiş (#MyApp. Shapes) hem de Full (http://schemas.datacontract.org/2004/07/MyApp.Shapes) adları seri durumundan çıkarma sırasında anlaşıldı.

#### <a name="type-hint-position-in-json-objects"></a>JSON nesnelerinde tür Ipucu konumu

Tür ipucunun JSON temsilinin ilk bölümünde görünmesi gerektiğini unutmayın. Bu, anahtar/değer çiftlerinin sırasının JSON işlemede önemli olduğu tek durumdur. Örneğin, tür ipucunu belirtmek için aşağıdaki geçerli bir yol değildir.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

WCF ve ASP.NET AJAX istemci sayfaları tarafından kullanılan <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> her zaman önce tür ipucunu yayar.

#### <a name="type-hints-apply-only-to-complex-types"></a>Tür Ipuçları yalnızca karmaşık türler için geçerlidir

Karmaşık olmayan türler için bir tür ipucu yayın bir yolu yoktur. Örneğin, bir işlemin <xref:System.Object> dönüş türü varsa ancak bir daire döndürürse, JSON temsili daha önce gösterildiği gibi, tür bilgileri de korunur. Ancak, URI döndürülürse JSON temsili bir dizedir ve bir URI 'yi temsil etmek için kullanılan dize kaybedilir. Bu yalnızca temel türler için değil koleksiyonlar ve diziler için de geçerlidir.

#### <a name="when-are-type-hints-emitted"></a>Tür Ipuçları ne zaman yayınlanır

Tür ipuçları ileti boyutunu önemli ölçüde artırabilir (bunun bir yolu, mümkünse daha kısa veri anlaşması ad alanları kullanmaktır). Bu nedenle, aşağıdaki kurallar tür ipuçlarının yayılıp yayınlanmadığını yönetir:

- ASP.NET AJAX kullanırken, bir daire içine bir daire atansa bile, bir taban/türetilmiş atama olmasa bile tür ipuçları her zaman mümkün olduğunda dağıtılır. (Bu, Zayıf yazılmış JSON ortamından çağırma işleminin, önemli olmayan bir bilgi kaybı olmadan kesin türü belirtilmiş .NET ortamına çağrılması işlemini tam olarak etkinleştirmek için gereklidir.)

- ASP.NET tümleştirmesi olmadan AJAX Hizmetleri kullanırken, tür ipuçları yalnızca bir taban/türetilmiş atama olduğunda dağıtılır. bu @no__t, bir taban/türetilmiş atama olduğunda dağıtılır. Bu, JavaScript istemcisini doğru şekilde uygulamak için gereken en düşük bilgileri sağlar, bu sayede performansı geliştirir, ancak yanlış tasarlanmış istemcilerde tür bilgi kaybına karşı koruma sağlamaz. İstemcide bu sorunla ilgilenmemek istiyorsanız taban/türetilmiş atamalardan tamamen sunucu üzerinde kaçının.

- @No__t-0 türü kullanılırken, `alwaysEmitTypeInformation` Oluşturucu parametresi, varsayılan olarak "`false`" olacak şekilde, önceki iki mod arasında seçim yapmanıza izin verir (yalnızca gerekli olduğunda tür ipuçlarını göster).

#### <a name="duplicate-data-member-names"></a>Yinelenen veri üyesi adları

Türetilmiş tür bilgileri, temel tür bilgileriyle birlikte aynı JSON nesnesinde bulunur ve herhangi bir sırada gerçekleşebilir. Örneğin, `Shape` aşağıdaki gibi gösterilebilir.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Daire, aşağıdaki gibi gösterilebilir.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Taban `Shape` türü ayrıca "`radius`" adlı bir veri üyesi içeriyorsa, bu, her iki serileştirme (JSON nesneleri yinelenen anahtar adlarına sahip olmadığı için) ve serisini kaldırma ("Radius" ın @no__t-@no__ 2 ' e başvurduğundan net olmadığından) t-3). Bu nedenle, "özellik gizleme" kavramı (temel ve türetilmiş sınıflarda aynı ada sahip veri üyeleri) genellikle veri sözleşme sınıflarında önerilmemekle karşı, JSON durumunda gerçekten yasak olur.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Çok biçimlilik ve IXmlSerializable türleri

<xref:System.Xml.Serialization.IXmlSerializable> türleri, olağan veri sözleşmesi kurallarına göre tanınan türler karşılandığı sürece her zamanki gibi polymorphically atanmış olabilir. Ancak, <xref:System.Object> yerine <xref:System.Xml.Serialization.IXmlSerializable> türünün serileştirilmesi, sonuç bir JSON dizesi olduğu için tür bilgilerinin kaybına neden olur.

#### <a name="polymorphism-and-certain-interface-types"></a>Çok biçimlilik ve belirli arabirim türleri

@No__t-1 (<xref:System.Object> hariç) olmayan koleksiyon olmayan bir türün beklendiği <xref:System.Xml.Serialization.IXmlSerializable> uygulayan bir koleksiyon türü veya bir tür serileştirilmek yasaktır. Örneğin, `IMyInterface` adlı özel bir arabirim ve `int` ve `IMyInterface` türünde <xref:System.Collections.Generic.IEnumerable%601> ' i uygulayan `MyType` türü. Dönüş türü `IMyInterface` olan bir işlemden `MyType` döndürmesi yasaktır. Bunun nedeni, `MyType` ' ın bir JSON dizisi olarak serileştirilmesi ve bir tür ipucu gerektirmesi ve yalnızca karmaşık türlerle, dizilere sahip bir tür ipucu bulundurmadan önce belirtilmiş olması.

#### <a name="known-types-and-configuration"></a>Bilinen türler ve yapılandırma

@No__t-0 tarafından kullanılan tüm bilinen tür mekanizmaları, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ile aynı şekilde de desteklenir. Her iki serileştiriciler de bir yapılandırma dosyası aracılığıyla eklenen bilinen türleri saptamak için [\<system. Runtime. serialization >](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md) [\<datacontractserializer >](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) aynı yapılandırma öğesini okur.

#### <a name="collections-assigned-to-object"></a>Nesneye atanan Koleksiyonlar

Nesnesine atanan koleksiyonlar, <xref:System.Collections.Generic.IEnumerable%601> uygulayan koleksiyonlardır. bir JSON dizisi, karmaşık bir tür ise tür ipucu olan her bir girdiyle birlikte seri hale gelir. Örneğin, <xref:System.Object> ' ye atanmış `Shape` türündeki <xref:System.Collections.Generic.List%601> aşağıdaki gibi görünür.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Seri durumdan geri <xref:System.Object>:

- `Shape` bilinen türler listesinde olmalıdır. Bilinen türlerde `Shape` türünde <xref:System.Collections.Generic.List%601> olması hiçbir etkiye sahip değildir. Bu durumda, serileştirme üzerinde `Shape` bilinen türlere eklemeniz gerekmez; bu otomatik olarak yapılır.

- Koleksiyonun, `Shape` örnekleri içeren <xref:System.Object> türünde bir @no__t 0 olarak seri hale getirilmesi.

#### <a name="derived-collections-assigned-to-base-collections"></a>Taban koleksiyonlara atanmış türetilmiş Koleksiyonlar

Türetilmiş bir koleksiyon bir temel koleksiyona atandığında, koleksiyon genellikle temel türün bir koleksiyonu gibi serileştirilir. Ancak, türetilmiş koleksiyonun öğe türü, temel koleksiyonun öğe türüne atanmamışsa, bir özel durum oluşturulur.

#### <a name="type-hints-and-dictionaries"></a>Ipuçları ve sözlükler yazın

@No__t-0 ' a bir sözlük atandığında, Sözlükteki her anahtar ve değer girişi, <xref:System.Object> ' e atanmış gibi değerlendirilir ve bir tür ipucu alır.

Sözlük türlerini serileştirirken, "Key" ve "Value" üyelerini içeren JSON nesnesi `alwaysEmitTypeInformation` ayarından etkilenmez ve yalnızca önceki koleksiyon kuralları gerektirdiğinde bir tür ipucu içerir.

### <a name="valid-json-key-names"></a>Geçerli JSON anahtar adları

Seri hale getirici XML-geçerli XML adı olmayan anahtar adlarını kodlar. Örneğin, "123" adlı bir veri üyesinin "\_x0031 @ no__t-1 @ no__t-2x0032 @ no__t-3 @ no__t-4x0033 @ no__t-5" gibi kodlanmış bir adı olabilir, çünkü "123" geçersiz bir XML öğesi adı (bir basamakla başlar). Bazı uluslararası karakter kümelerinde XML adlarında geçerli olmayan benzer bir durum ortaya çıkabilir. JSON işlemede XML 'nin bu efektinin açıklaması için bkz. [JSON ve XML arasında eşleme](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Ayrıca bkz.

- [JSON ve diğer Veri Aktarımı biçimleri için destek](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
