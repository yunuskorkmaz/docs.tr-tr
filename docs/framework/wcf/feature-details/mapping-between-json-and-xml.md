---
title: JSON ve XML Arasında Eşleme
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 55812ad15d1f38bb0c295e6895dfff329035206d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464061"
---
# <a name="mapping-between-json-and-xml"></a>JSON ve XML Arasında Eşleme
Okuyucular ve yazarlar tarafından <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> üretilen JavaScript Nesne Gösterimi (JSON) içeriği üzerinde bir XML API sağlar. JSON, JavaScript nesnesi literallerinin bir alt kümesini kullanarak verileri kodlar. Bu fabrika tarafından üretilen okuyucular ve yazarlar da JSON içeriği gönderildiğinde veya Windows Communication Foundation <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> (WCF) uygulamaları tarafından alınan veya . <xref:System.ServiceModel.WebHttpBinding>

JSON içeriği yle baş harfe battığında, JSON okuyucusu metinsel bir XML okuyucusunun XML örneği üzerinden yaptığı gibi çalışır. JSON yazar, bir metin XML okuyucu belirli bir XML örneği üretir aramaları bir dizi verildiğinde, JSON içerik yazar. XML ve JSON içeriğinin bu örneği arasındaki eşleme, gelişmiş senaryolarda kullanılmak üzere bu konuda açıklanmıştır.

Dahili olarak, JSON WCF tarafından işlendiğinde bir XML bilgi seti olarak temsil edilir. Normalde eşleme sadece mantıklı bir olduğu gibi bu iç gösterimi ile ilgili olmak zorunda değildir: JSON normalde fiziksel bellekxml dönüştürülür veya XML JSON dönüştürülür değildir. Eşleme, XML API'lerinin JSON içeriğine erişmek için kullanıldığı anlamına gelir.

WCF JSON kullandığında, olağan senaryo, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> davranış tarafından veya uygun olduğunda <xref:System.ServiceModel.Description.WebHttpBehavior> davranış tarafından otomatik olarak takılı olmasıdır. JSON <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve XML bilgi seti arasındaki haritalama anlar ve doğrudan JSON ile ilgileniyor gibi davranır. (Herhangi bir XML <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> okuyucu veya yazar ile, XML aşağıdaki haritalama uygun olduğu anlayışı ile kullanmak mümkündür.)

Gelişmiş senaryolarda, aşağıdaki eşleme doğrudan erişmek için gerekli olabilir. Bu senaryolar, JSON'u özel yollarla seri hale getirmek ve deserialize etmek istediğinizde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>json içeren iletiler için <xref:System.ServiceModel.Channels.Message> doğrudan türle uğraşırken oluşur. JSON-XML eşleme, ileti günlüğe kaydetme için de kullanılır. WCF'de ileti günlüğe kaydetme özelliğini kullanırken, JSON iletileri bir sonraki bölümde açıklanan eşleme yle XML olarak günlüğe kaydedilir.

Eşleme kavramını açıklığa kavuşturmak için aşağıdaki örnek bir JSON belgesidir.

```json
{"product":"pencil","price":12}
```

Daha önce bahsedilen okuyuculardan birini kullanarak bu JSON belgesini <xref:System.Xml.XmlDictionaryReader> okumak için, aşağıdaki XML belgesini okumak için yaptığınız gibi aynı arama sırasını kullanın.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Ayrıca, örnekteki JSON iletisi WCF tarafından alınır ve günlüğe kaydedilirse, önceki günlükte XML parçasını görürsünüz.

## <a name="mapping-between-json-and-the-xml-infoset"></a>JSON ve XML Bilgi Seti Arasında Haritalama

Resmi olarak, haritalama JSON arasında [rfc 4627](https://www.ietf.org/rfc/rfc4627.txt) açıklandığı gibi (bazı kısıtlamalar rahat ve bazı diğer kısıtlamalar hariç) ve [XML Bilgi Seti](https://www.w3.org/TR/2004/REC-xml-infoset-20040204/)açıklandığı gibi XML bilgi kümesi (ve metinsel XML) . [Kare ayraçlarda] *bilgi öğeleri* ve alanları tanımları için bu konuya bakın.

Boş bir JSON belgesi boş bir XML belgesine eşler ve boş bir JSON belgesine boş bir XML belge eşlemleri. XML'den JSON eşlemesine, beyaz boşluktan önce ve belgeden sonra beyaz boşluk tan sonra izbırakana izin verilmez.

Eşleme, Belge Bilgi Öğesi (DII) veya Bir Öğe Bilgi Öğesi (EII) ve JSON arasında tanımlanır. EII veya DII'nin [belge öğesi] özelliği Root JSON Öğesi olarak adlandırılır. Bu eşlemede belge parçalarının (birden çok kök öğeye sahip XML) desteklenmediğini unutmayın.

Örnek: Aşağıdaki belge:

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

Ve aşağıdaki unsur:

```xml
<root type="number">42</root>
```

İkisinin de JSON'a ait bir haritası var. <`root`> öğesi her iki durumda da Root JSON Öğesidir.

Ayrıca, bir DII durumunda, aşağıdaki ler göz önünde bulundurulmalıdır:

- [Çocuklar] listesindeki bazı öğeler bulunmamalıdır. JSON'dan haritalanmış XML okurken bu gerçeğe güvenmeyin.

- [çocuklar] listesinde yorum bilgisi öğesi bulunmamaktadır.

- [Çocuklar] listesinde DTD bilgi öğesi bulunmamaktadır.

- [çocuklar] listesinde hiçbir kişisel Bilgi (PI) `<?xml…>` bilgi öğesi bulunmamaktadır (bildirim PI bilgi öğesi olarak kabul edilmez)

- [notasyonlar] kümesi boş.

- [Ayrıştırılmamış varlıklar] kümesi boştur.

Örnek: [çocuklar] bir PI ve yorum tuttuğundan, aşağıdaki belgenin JSON ile eşleme leri yoktur.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

Kök JSON Öğesi için EII aşağıdaki özelliklere sahiptir:

- [yerel ad] değeri "kök" vardır.

- [namespace adı] hiçbir değeri vardır.

- [önek] hiçbir değeri vardır.

- [çocuklar] EII (daha fazla açıklandığı şekilde Iç Öğeleri temsil eden) veya CIIs (daha fazla açıklandığı gibi Karakter Bilgi Öğeleri) veya bunların hiçbiri, ancak her ikisi de içerebilir.

- [öznitelikler] aşağıdaki isteğe bağlı öznitelik bilgi öğelerini (AIIs) içerebilir

- JSON Türü Özniteliği ("türü") daha ayrıntılı olarak açıklanmıştır. Bu öznitelik, eşlenen XML'deki JSON türünü (dize, sayı, boolean, nesne, dizi veya null) korumak için kullanılır.

- Daha sonra açıklandığı gibi\_\_Veri Sözleşmesi Adı Atfı (" türü"). Bu öznitelik yalnızca JSON türü özniteliği de varsa ve [normalleştirilmiş değeri] "nesne" ise kullanılabilir. Bu öznitelik, veri `DataContractJsonSerializer` sözleşmesi türü bilgilerini korumak için kullanılır - örneğin, türemiş bir türün serihale edildiği ve taban türünün beklendiği çok biçimli durumlarda. Çoğu durumda `DataContractJsonSerializer`, bu öznitelik ile çalışmıyorsanız, bu öznitelik yoksayılır.

- [kapsam içi ad alanları] infoset belirtimi `http://www.w3.org/XML/1998/namespace` tarafından zorunlu olarak "xml" bağlama içerir.

- [alt], [öznitelikler] ve [kapsam içi ad alanları] daha önce belirtildiği gibi dışında herhangi bir öğe ye sahip olmamalıdır ve [ad alanı öznitelikleri] üye olmamalıdır, ancak JSON'dan eşlenen XML'i okurken bu gerçeklere güvenmeyin.

Örnek: [namespace öznitelikleri] boş olmadığından aşağıdaki belgejson eşleme vardır.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

JSON Türü Özniteliği için AII aşağıdaki özelliklere sahiptir:

- [namespace adı] hiçbir değeri vardır.
- [önek] hiçbir değeri vardır.
- [yerel ad] "türü".
- [normalleştirilmiş değer] aşağıdaki bölümde açıklanan olası tür değerlerinden biridir.
- [belirtilen] `true`olduğunu.
- [öznitelik türü] hiçbir değeri vardır.
- [referanslar] hiçbir değeri vardır.

Veri Sözleşmesi Adı Özniteliği için AII aşağıdaki özelliklere sahiptir:

- [namespace adı] hiçbir değeri vardır.
- [önek] hiçbir değeri vardır.
- [yerel ad]\_\_" type" (iki alt ve sonra "yazın") olduğunu.
- [normalleştirilmiş değer] geçerli bir Unicode dizesidir – bu dizenin JSON ile eşlenemesi aşağıdaki bölümde açıklanmıştır.
- [belirtilen] `true`olduğunu.
- [öznitelik türü] hiçbir değeri vardır.
- [referanslar] hiçbir değeri vardır.

Kök JSON Öğesi veya diğer iç öğeler içinde bulunan iç öğeler aşağıdaki özelliklere sahiptir:

- [yerel ad] daha sonra açıklandığı gibi herhangi bir değere sahip olabilir.
- [namespace name], [önek], [altlar], [öznitelikler], [ad alanı öznitelikleri]ve [kapsam içi ad alanları] Root JSON Öğesi ile aynı kurallara tabidir.

Hem Root JSON Öğesi hem de iç öğelerde, JSON Türü Özniteliği JSON ve olası [çocuklar] ve bunların yorumlanması için eşleme tanımlar. Özniteliğin [normalleştirilmiş değeri] büyük/küçük türdedir ve küçük olmalıdır ve beyaz boşluk içeremez.

|JSON Tipi Öznitelik'in AII[normalleştirilmiş değeri]|İlgili EII'nin [çocuklarına] izin verilmesi|JSON için Haritalama|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string`(veya JSON tipi AII'nin yokluğu)<br /><br /> A `string` ve JSON türü AII yokluğu varsayılan `string` yapar aynıdır.<br /><br /> Yani, `<root> string1</root>` JSON `string` "string1" için haritalar.|0 veya daha fazla CIIs|Bir JSON `string` (JSON RFC, bölüm 2.5). Her `char` biri CII'deki [karakter koduna] karşılık gelen bir karakterdir. Hiçbir CIIs varsa, boş bir JSON `string`için eşler.<br /><br /> Örnek: Aşağıdaki öğe bir JSON parçasıyla eşler:<br /><br /> `<root type="string">42</root>`<br /><br /> JSON parçası "42".<br /><br /> XML'den JSON eşlemesine, kaçan karakterlere haritadan kaçan karakterler, diğerleri kaçamayan karakterlerle eşlenir. "/" karakteri özeldir – olması gerekmese bile kaçar ("\\/" olarak yazılır).<br /><br /> Örnek: Aşağıdaki öğe bir JSON parçasıyla eşler.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON parçası \\"da\\/ta"dır.\\<br /><br /> JSON'dan XML eşlemesine kadar, kaçan karakterler ve karakterler ilgili [karakter kodu] ile doğru bir şekilde eşlenir.<br /><br /> Örnek: JSON parçası "\u0041BC", aşağıdaki XML öğesine eşler.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Dize, XML'e eşlenen eteklere girmiyor beyaz boşluk (JSON RFC'nin bölüm 2'sinde'ws' ile çevrelenebilir.<br /><br /> Örnek: JSON parçası "ABC", (ilk çift teklifönce boşluklar vardır), aşağıdaki XML öğesine eşler.<br /><br /> `<root type="string">ABC</root>`<br /><br /> XML haritalarında json beyaz uzay için herhangi bir beyaz boşluk.<br /><br /> Örnek: Aşağıdaki XML öğesi bir JSON parçasıyla eşler.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON parçası " A BC ".|
|`number`|1 veya daha fazla CIIs|Bir JSON `number` (JSON RFC, bölüm 2.4), muhtemelen beyaz alan ile çevrili. Sayı/beyaz boşluk birleşimindeki her karakter, CII'deki [karakter koduna] karşılık gelen bir karakterdir.<br /><br /> Örnek: Aşağıdaki öğe bir JSON parçasıyla eşler.<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON parçası 42<br /><br /> (Beyaz alan korunur).|
|`boolean`|4 veya 5 CiIs (karşılık gelir `true` veya `false`), muhtemelen ek beyaz alan CIIs ile çevrili.|Dize "true" karşılık gelen bir CII dizisi literal `true`eşlenir ve dize karşılık gelen bir CII dizisi "yanlış" `false`literal eşlenir. Çevreleyen beyaz alan korunur.<br /><br /> Örnek: Aşağıdaki öğe bir JSON parçasıyla eşler.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON `false`parçası.|
|`null`|Hiçbiri izin vermedi.|`null`Gerçek. JSON'dan XML haritalamaya kadar, xml'e eşlenen alamadım beyaz boşluk ('ws' bölüm 2) ile çevrili `null` olabilir.<br /><br /> Örnek: Aşağıdaki öğe bir JSON parçasıyla eşler.<br /><br /> `<root type="null"/>`<br /><br /> or<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Her iki durumda da `Null`JSON parçası .|
|`object`|0 veya daha fazla ÇED.|JSON RFC'nin bölüm 2.2'sinde olduğu gibi bir `begin-object` (sol kıvırcık ayraç) ve ardından her EII için bir üye kaydı daha da açıklandığı şekilde anlatılmaktadır. Birden fazla EII varsa, üye kayıtlar arasında değer ayırıcılar (virgüller) vardır. Tüm bu bir son nesne (sağ kıvırcık ayraç) tarafından takip edilir.<br /><br /> Örnek: Aşağıdaki öğe JSON parçasıyla eşler.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> JSON `{"type1":"aaa","type2":"bbb"}`parçası.<br /><br /> XML'de JSON eşlemesinde Veri Sözleşmesi Türü Özniteliği varsa, başlangıçta ek bir Üye Kaydı eklenir. Adı, Veri Sözleşmesi Türü Özniteliğinin (" türü")\_\_[yerel adı] ve değeri özniteliğin [normalleştirilmiş değeri] dir. Tam tersine, JSON'dan XML eşlemesine, ilk üye kaydın adı Veri Sözleşmesi Türü Özniteliğinin [yerel adı] ise (yani" türü"),\_\_eşlenen XML'de karşılık gelen bir Veri Sözleşmesi Türü Özniteliği bulunur, ancak ilgili EII mevcut değildir. Bu özel eşlemenin uygulanabilmesi için bu üye kaydının önce JSON nesnesinde oluşması gerektiğini unutmayın. Bu, üye kayıtlarının sırasının önemli olmadığı olağan JSON işleminden ayrılmayı temsil eder.<br /><br /> Örnek:<br /><br /> Aşağıdaki JSON parçası XML eşler.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> XML aşağıdaki koddur.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> \_ \_AII türünün mevcut olduğuna, ancak \_ \_EII türü olmadığına dikkat edin.<br /><br /> Ancak, JSON'daki sıra aşağıdaki örnekte gösterildiği gibi tersine çevrilir.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> Karşılık gelen XML gösterilir.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Yani, \__type özel bir anlamı ve haritaları her zamanki gibi bir EII değil, AII için durur.<br /><br /> Bir JSON değerieşlendiğinde AII'nin [normalleştirilmiş değeri] için kaçan/kaçan kurallar, bu tablonun "dize" satırında belirtilen JSON dizeleri ile aynıdır.<br /><br /> Örnek:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> önceki örnekte aşağıdaki JSON eşlenebilir.<br /><br /> `{"__type":"\\abc"}`<br /><br /> XML ile JSON eşleme de ilk EII'nin [yerel\_\_adı] "türü" olmamalıdır.<br /><br /> Beyaz boşluk`ws`( ) nesneler için JSON eşleme XML üzerinde oluşturulan asla ve XML eşleme JSON üzerinde yoksayılır.<br /><br /> Örnek: Aşağıdaki JSON parçası bir XML öğesine eşler.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> XML öğesi aşağıdaki kodda gösterilir.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|array|0 veya daha fazla ÇED|JSON RFC'nin bölüm 2.3'ünde olduğu gibi bir başlangıç dizisi (sol kare ayraç), ardından her EII için daha fazla açıklandığı şekilde bir dizi kaydı. Birden fazla EII varsa, dizi kayıtları arasında değer ayırıcılar (virgüller) vardır. Tüm bunları bir son dizi takip ediyor.<br /><br /> Örnek: Aşağıdaki XML öğesi bir JSON parçasıyla eşler.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> JSON parçası.`["aaa","bbb"]`<br /><br /> Beyaz boşluk`ws`( ) diziler için JSON eşleme XML üzerinde oluşturulan asla ve XML eşleme JSON üzerinde yoksayılır.<br /><br /> Örnek: Bir JSON parçası.<br /><br />`["aaa", "bbb"]`<br /><br /> Eşlenebilen XML öğesi.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Üye Kayıtları aşağıdaki gibidir:

- İç öğenin [yerel adı] `string` JSON `member` RFC bölüm 2.2'de tanımlandığı şekilde bir bölümü eşler.

Örnek: Aşağıdaki öğe bir JSON parçasıyla eşler.

```xml
<root type="object">
    <myLocalName type="string">aaa</myLocalName>
</root>
```

Aşağıdaki JSON parçası görüntülenir.

```json
{"myLocalName":"aaa"}
```

- XML'den JSON haritalamada, JSON'da kaçması gereken karakterler kaçılır ve diğerleri kaçamaz. "/" karakteri, kaçması gereken bir karakter olmasa da, yine de kaçmıştır (JSON'dan XML haritalama için kaçmak zorunda değildir). Bu JSON veri için ASP.NET `DateTime` AJAX biçimini desteklemek için gereklidir.

- JSON-XML eşlemesi üzerinde, tüm karakterler (gerekirse kaçamayan karakterler de dahil `string` olmak üzere) [yerel ad] üreten bir karakter oluşturmak için alınır.

- İç öğeler [çocuklar] bölüm 2.2 değerine harita, `JSON Type Attribute` sadece `Root JSON Element`gibi göre . ÇED'lerin birden fazla iç içe geçme düzeyine (diziler içinde iç içe geçme dahil) izin verilir.

Örnek: Aşağıdaki öğe bir JSON parçasıyla eşler.

```xml
<root type="object">
    <myLocalName1 type="string">myValue1</myLocalName1>
    <myLocalName2 type="number">2</myLocalName2>
    <myLocalName3 type="object">
        <myNestedName1 type="boolean">true</myNestedName1>
        <myNestedName2 type="null"/>
    </myLocalName3>
</root >
```

Aşağıdaki JSON parçası ne eşler.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> Önceki eşlemede XML kodlama adımı yoktur. Bu nedenle, WCF yalnızca anahtar adlarda tüm karakterlerin XML öğesi adlarında geçerli karakterler olduğu JSON belgelerini destekler. Örneğin, < bir XML öğesi için geçerli bir ad olmadığından JSON belgesi {"<":"a"} desteklenmez.

Önceki eşleme JSON kaçış / unescaping adımları içerdiğinden ters durum (XML geçerli ancak JSON değil) herhangi bir soruna neden olmaz.

Array Records aşağıdaki gibi çalışır:

- İç öğenin [yerel adı] "öğe"dir.

- İç öğenin [alt] bölüm 2.3 değerine harita, Kök JSON Öğesi için yaptığı gibi JSON Türü Özniteliği göre. ÇED'lerin birden çok iç içe geçme düzeyine (nesnelerin içinde iç içe geçme dahil) izin verilir.

Örnek: Aşağıdaki öğe bir JSON parçasıyla eşler.

```xml
<root type="array">
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root>
```

Aşağıdaki JSON parçası.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Bağımsız JSON Seri Hale Getirme](stand-alone-json-serialization.md)
