---
description: 'Hakkında daha fazla bilgi edinin: JSON ve XML arasında eşleme'
title: JSON ve XML Arasında Eşleme
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 1d9652d1683446da9946987a31a92906d5e38e55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793681"
---
# <a name="mapping-between-json-and-xml"></a>JSON ve XML Arasında Eşleme

Tarafından üretilen okuyucular ve yazıcılar, <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> JavaScript nesne gösterimi (JSON) içeriğine yönelik BIR XML API 'si sağlar. JSON, JavaScript 'in nesne sabit değerlerinin bir alt kümesini kullanarak verileri kodlar. Bu fabrika tarafından üretilen okuyucular ve yazıcılar, veya kullanılarak JSON içeriği gönderilirken veya Windows Communication Foundation (WCF) uygulamalar tarafından alındığında da kullanılır <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> <xref:System.ServiceModel.WebHttpBinding> .

JSON içeriğiyle birlikte başlatıldığında JSON okuyucusu, metinsel XML okuyucusu bir XML örneğinin üzerinde çalıştığı şekilde davranır. JSON yazarı, bir metinsel XML okuyucusuna yönelik bir dizi çağrının belirli bir XML örneğini oluşturduğu durumlarda JSON içeriğini yazar. Bu XML örneği ile JSON içeriği arasındaki eşleme, bu konuda Gelişmiş senaryolarda kullanılmak üzere açıklanmaktadır.

Dahili olarak, JSON, WCF tarafından işlendiğinde bir XML bilgi kümesi olarak temsil edilir. Normalde, eşleme yalnızca mantıksal bir değer olduğu için bu iç gösterimle ilgilenmemeniz gerekmez: JSON normalde bellekteki XML 'e fiziksel olarak dönüştürülmez veya XML 'den JSON 'a dönüştürülmez. Eşleme, XML API 'Lerinin JSON içeriğine erişmek için kullanıldığı anlamına gelir.

WCF JSON kullandığında, her zamanki senaryo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> otomatik olarak <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> davranışa göre veya <xref:System.ServiceModel.Description.WebHttpBehavior> uygun olduğunda davranışa göre prize takılır. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>JSON Ile xml bilgi kümesi arasındaki eşlemeyi anlamıştır ve doğrudan JSON ile ilgilendiği gibi davranır. ( <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> XML 'nin aşağıdaki eşlemeye uygun olduğunu anlamak için herhangi BIR XML okuyucusu veya yazıcı ile kullanabilirsiniz.)

Gelişmiş senaryolarda, aşağıdaki eşlemeye doğrudan erişmek için gerekli hale gelebilir. Bu senaryolar, JSON 'u özel yöntemlerle seri hale getirmek ve seri durumdan çıkarmak istediğinizde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> veya <xref:System.ServiceModel.Channels.Message> doğrudan JSON içeren iletiler için tür ile ilgilenirken oluşur. JSON-XML eşlemesi de ileti günlüğe kaydetme için kullanılır. WCF 'de ileti günlüğü özelliğini kullanırken JSON iletileri, sonraki bölümde açıklanan eşlemeye göre XML olarak günlüğe kaydedilir.

Bir eşlemenin kavramını netleştirmek için aşağıdaki örnek bir JSON belgesidir.

```json
{"product":"pencil","price":12}
```

Daha önce bahsedilen okuyuculardan birini kullanarak bu JSON belgesini okumak için, <xref:System.Xml.XmlDictionaryReader> AŞAĞıDAKI XML belgesini okumak için kullandığınız her bir çağrı dizisini kullanın.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Ayrıca, örnekteki JSON iletisi WCF tarafından alınıp günlüğe kaydedildiğinde, XML parçasını önceki günlükte görürsünüz.

## <a name="mapping-between-json-and-the-xml-infoset"></a>JSON ile XML bilgi kümesi arasında eşleme

Yani, eşleme, [RFC 4627](https://www.ietf.org/rfc/rfc4627.txt) ' de AÇıKLANDıĞı gibi JSON arasındadır (bazı kısıtlamalar gevşek ve diğer diğer kısıtlamalar hariç) ve XML [bilgi kümesi](https://www.w3.org/TR/2004/REC-xml-infoset-20040204/)Içinde açıklandığı gibi xml bilgi KÜMESI (ve metinsel XML değildir). [Köşeli ayraç] içindeki *bilgi öğelerinin* ve alanlarının tanımları için bu konuya bakın.

Boş bir JSON belgesi boş bir XML belgesiyle eşlenir ve boş bir XML belgesi boş bir JSON belgesiyle eşlenir. XML-JSON eşlemesinde, önceki boşluk ve belgenin sonundaki beyaz boşluk kullanılamaz.

Eşleme, bir belge bilgisi öğesi (DII) veya bir öğe bilgisi öğesi (EII) ve JSON arasında tanımlanır. EII veya DII 'ın [Document element] özelliği kök JSON öğesi olarak adlandırılır. Belge parçalarının (birden çok kök öğe içeren XML) bu eşlemede desteklenmediğini unutmayın.

Örnek: aşağıdaki belge:

```xml
<?xml version="1.0"?>
<root type="number">42</root>
```

Ve aşağıdaki öğesi:

```xml
<root type="number">42</root>
```

Her ikisinde de JSON eşleştirmesi vardır. <`root`> öğesi her iki durumda da kök JSON öğesidir.

Ayrıca, bir DII söz konusu olduğunda aşağıdakiler göz önünde bulundurulmalıdır:

- [Children] listesindeki bazı öğeler mevcut olmamalıdır. JSON 'dan eşlenen XML 'yi okurken bu olguyu kullanmayın.

- [Children] listesinde yorum bilgisi öğesi yoktur.

- [Children] listesinde DTD bilgisi öğesi yoktur.

- [Children] listesi hiçbir kişisel bilgi (PI) bilgi öğesi bulundurmaz ( `<?xml…>` bildirim BIR PI bilgi öğesi olarak değerlendirilmez)

- [Gösterimler] kümesi boş.

- [Ayrıştırılmamış varlıklar] kümesi boş.

Örnek: Şu belgede JSON ile eşleme yok çünkü [children] bir PI ve bir açıklama barındırır.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

Kök JSON öğesi için EII aşağıdaki özelliklere sahiptir:

- [yerel ad] "root" değerine sahip.

- [Namespace Name] değeri yok.

- [önek] değeri yok.

- [children], Eine (daha fazla açıklandığı gibi Iç öğeleri temsil eder) veya CIAS (daha fazla açıklanacak olan karakter bilgileri öğeleri) ya da bunlardan hiçbirini (daha fazlasını değil) içerebilir.

- [öznitelikler] aşağıdaki isteğe bağlı öznitelik bilgileri öğelerini içerebilir (AIIS)

- Daha ayrıntılı olarak açıklandığı gibi JSON türü özniteliği ("tür"). Bu öznitelik, eşlenmiş XML 'de JSON türünü (dize, sayı, Boolean, nesne, dizi veya null) korumak için kullanılır.

- Daha ayrıntılı olarak açıklandığı gibi, veri anlaşması adı özniteliği (" \_ \_ tür"). Bu öznitelik yalnızca JSON türü özniteliği de varsa ve [normalleştirilmiş değer] değeri "Object" ise mevcut olabilir. Bu öznitelik, `DataContractJsonSerializer` veri anlaşması türü bilgilerini korumak için tarafından kullanılır; Örneğin, türetilmiş bir türün serileştirildiği ve temel bir türün beklendiği çok biçimli durumlarda. İle çalışmıyorsanız, `DataContractJsonSerializer` çoğu durumda bu öznitelik yok sayılır.

- [kapsam içi ad alanları], "xml" öğesinin `http://www.w3.org/XML/1998/namespace` bilgi kümesi belirtimine göre uygulanan olarak bağlamasını içerir.

- [children], [öznitelikler] ve [kapsam içi ad alanları], daha önce belirtildiği gibi herhangi bir öğeye sahip olmamalıdır ve [ad alanı öznitelikleri] hiçbir üye içermemelidir, ancak JSON 'dan eşlenen XML 'yi okurken bu olgulara güvenmeyin.

Örnek: Şu belgenin JSON ile eşlemesi yok, çünkü [ad alanı öznitelikleri] boş değil.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

JSON türü özniteliği için AII aşağıdaki özelliklere sahiptir:

- [Namespace Name] değeri yok.
- [önek] değeri yok.
- [yerel ad] "tür".
- [normalleştirilmiş değer] aşağıdaki bölümde açıklanan olası tür değerlerinden biridir.
- [belirtilen] `true` .
- [öznitelik türü] bir değere sahip değil.
- [References] değeri yok.

Veri anlaşması adı özniteliği için AII aşağıdaki özelliklere sahiptir:

- [Namespace Name] değeri yok.
- [önek] değeri yok.
- [yerel ad] " \_ \_ tür" (iki alt çizgi ve sonra "tür").
- [normalleştirilmiş değer] geçerli herhangi bir Unicode dizesidir: Bu dizenin JSON ile eşlenmesi aşağıdaki bölümde açıklanmıştır.
- [belirtilen] `true` .
- [öznitelik türü] bir değere sahip değil.
- [References] değeri yok.

Kök JSON öğesi veya diğer iç öğeler içinde yer alan iç öğeler aşağıdaki özelliklere sahiptir:

- [yerel ad] daha fazla açıklanacak şekilde herhangi bir değere sahip olabilir.
- [ad alanı adı], [önek], [alt öğeler], [öznitelikler], [ad alanı öznitelikleri] ve [kapsam içi ad alanları], kök JSON öğesiyle aynı kurallara tabidir.

Hem kök JSON öğesinde hem de iç öğelerde, JSON türü özniteliği JSON ve olası [alt öğeler] ve yorumlarına yönelik eşlemeyi tanımlar. Özniteliğin [normalleştirilmiş değer] büyük küçük harfe duyarlıdır ve küçük harfle yazılmalıdır ve boşluk içeremez.

|[normalleştirilmiş değer] JSON türü özniteliğinin AII|Karşılık gelen EII izin verilen [alt öğe]|JSON ile eşleme|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (veya JSON türü AII yokluğu)<br /><br /> A `string` ve JSON türü AII yokluğu, varsayılan olarak aynı olur `string` .<br /><br /> Bu nedenle, `<root> string1</root>` JSON `string` "Dize1" ile eşlenir.|0 veya daha fazla CIO|JSON `string` (JSON RFC, bölüm 2,5). Her biri, `char` CII öğesinden [karakter koduna] karşılık gelen bir karakterdir. Hiçbir CIO yoksa, boş bir JSON ile eşlenir `string` .<br /><br /> Örnek: aşağıdaki öğe bir JSON parçasına eşlenir:<br /><br /> `<root type="string">42</root>`<br /><br /> JSON parçası "42".<br /><br /> XML 'den JSON eşlemesinde, kaçışlı olması gereken karakterler kaçış karakterleri ile eşlenir, diğer tüm diğerleri de kaçışsız karakterlerle eşlenir. "/" Karakteri özeldir; ("/" olarak yazılmış) olmasa bile kaçış olur \\ .<br /><br /> Örnek: aşağıdaki öğe bir JSON parçasına eşlenir.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON parçası "" de \\ \\ /ta \\ "" dir.<br /><br /> JSON 'dan XML eşlemesi için, kaçış karakteri ve kaçış karakterleri karşılık gelen [karakter kodu] ile doğru eşlemedir.<br /><br /> Örnek: "\u0041BC" JSON parçası aşağıdaki XML öğesiyle eşlenir.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Dize, XML 'e eşlenmiş olmayan, JSON RFC 'nin 2. bölümünde yer alan boşluk (' ws ') ile çevrelenebilir.<br /><br /> Örnek: "ABC" JSON parçası (ilk çift tırnadan önce boşluklar bulunur), aşağıdaki XML öğesiyle eşlenir.<br /><br /> `<root type="string">ABC</root>`<br /><br /> XML 'deki tüm boşluklar JSON 'daki boşluk ile eşlenir.<br /><br /> Örnek: aşağıdaki XML öğesi bir JSON parçasına eşlenir.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON parçası "bir BC" dır.|
|`number`|1 veya daha fazla CIO|Muhtemelen boşluk `number` ile çevrelenen BIR JSON (JSON RFC, bölüm 2,4). Sayı/boşluk kombinasyondaki her bir karakter, CII öğesinden [karakter koduna] karşılık gelen bir karakterdir.<br /><br /> Örnek: aşağıdaki öğe bir JSON parçasına eşlenir.<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON parçası 42 ' dir<br /><br /> (Boşluk korunur).|
|`boolean`|4 veya 5 CII (veya buna karşılık `true` gelen `false` ), büyük olasılıkla ek beyaz boşluk CIO tarafından çevrelenmiş.|"True" dizesine karşılık gelen bir CII sırası değişmez değere eşlenir `true` ve "false" dizesine karşılık gelen BIR CII sırası değişmez değere eşlenir `false` . Çevreleyen boşluk korunur.<br /><br /> Örnek: aşağıdaki öğe bir JSON parçasına eşlenir.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON parçası `false` .|
|`null`|Hiçbiri izin verilmiyor.|Değişmez değer `null` . JSON ile XML eşleme üzerinde, `null` XML 'e eşlenmemiş boşluk (Bölüm 2 ' de ' ws ') ile çevrelenebilir.<br /><br /> Örnek: aşağıdaki öğe bir JSON parçasına eşlenir.<br /><br /> `<root type="null"/>`<br /><br /> veya<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Her iki durumda da JSON parçası olur `Null` .|
|`object`|0 veya daha fazla Eior.|`begin-object`JSON RFC 'nin 2,2 bölümünde olduğu gibi bir (sol küme ayracı) ve ardından her EII için bir üye kaydının daha sonra açıklandığı gibi. Birden fazla EII varsa, üye kayıtları arasında değer ayırıcıları (virgüller) vardır. Bunun ardından bir son nesne (sağ kaşlı ayraç) gelir.<br /><br /> Örnek: aşağıdaki öğe JSON parçasına eşlenir.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> JSON parçası `{"type1":"aaa","type2":"bbb"}` .<br /><br /> Veri sözleşmesi türü özniteliği XML üzerinde JSON eşlemesinde varsa, başlangıca ek bir üye kaydı eklenir. Adı, veri anlaşması türü özniteliği ("tür") için [yerel ad] \_ \_ ve değeri özniteliğin [normalleştirilmiş değer]. Buna karşılık, JSON ile XML eşleme arasında, ilk üyenin kayıt adı veri sözleşmesi türü özniteliğinin [yerel adı] ise (yani, " \_ \_ tür"), eşlenen XML 'de karşılık gelen bir veri sözleşmesi türü özniteliği bulunur, ancak buna karşılık gelen bir EII yoktur. Bu özel eşlemenin uygulanabilmesi için önce Bu üye kaydının JSON nesnesinde gerçekleşmesi gerektiğini unutmayın. Bu, üye kayıtlarının sırasının önemli olmadığı olağan JSON işlemeden bir ayrıltı temsil eder.<br /><br /> Örnek:<br /><br /> Aşağıdaki JSON parçası XML ile eşlenir.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> XML aşağıdaki koddur.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> \_ \_ Aİİ türünün var olduğunu ancak \_ \_ EII türünde olmadığını unutmayın.<br /><br /> Ancak, JSON 'daki sıra, aşağıdaki örnekte gösterildiği gibi tersine çevrilir.<br /><br /> `{"name":"John","\_\_type":"Person"}`<br /><br /> Karşılık gelen XML gösterilir.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Diğer bir deyişle, \_ _Type özel anlamlara sahip olacak şekilde sona erer ve AII değil, her zamanki gibi BIR EII eşlenir.<br /><br /> Bir JSON değeriyle eşlendiğinde AII 'nin [normalleştirilmiş değer] için kaçış/kaçış kuralları, bu tablonun "String" satırında belirtilen JSON dizeleriyle aynı.<br /><br /> Örnek:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> önceki örnek için aşağıdaki JSON ile eşlenebilir.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Bir XML-JSON eşlemesinde, ilk EII 'nin [yerel adı] " \_ \_ tür" olmaması gerekir.<br /><br /> Boşluk ( `ws` ), nesneler IÇIN XML Ile JSON eşlemesinde hiçbir şekilde oluşturulmaz ve JSON Ile XML eşlemesi arasında yok sayılır.<br /><br /> Örnek: aşağıdaki JSON parçası bir XML öğesiyle eşlenir.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> XML öğesi aşağıdaki kodda gösterilmiştir.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|array|0 veya daha fazla EİA|JSON RFC 'nin 2,3 bölümünde olduğu gibi bir BEGIN-Array (sol köşeli ayraç) ve ardından her EII için bir dizi kaydının daha sonra açıklandığı gibi. Birden fazla EII varsa, dizi kayıtları arasında değer ayırıcıları (virgüller) vardır. Bunun ardından bir bitiş dizisi gelir.<br /><br /> Örnek: aşağıdaki XML öğesi bir JSON parçasına eşlenir.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> JSON parçası `["aaa","bbb"]`<br /><br /> Boşluk ( `ws` ), diziler IÇIN XML Ile JSON eşlemesinde hiçbir şekilde oluşturulmaz ve JSON 'DAN XML eşlemesinde yok sayılır.<br /><br /> Örnek: bir JSON parçası.<br /><br />`["aaa", "bbb"]`<br /><br /> Eşlendiği XML öğesi.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Üye kayıtları aşağıdaki gibi çalışır:

- İç öğenin [yerel ad] `string` , `member` JSON RFC 'nin 2,2 bölümünde tanımlanan bir bölümüyle eşlenir.

Örnek: aşağıdaki öğe bir JSON parçasına eşlenir.

```xml
<root type="object">
    <myLocalName type="string">aaa</myLocalName>
</root>
```

Aşağıdaki JSON parçası görüntülenir.

```json
{"myLocalName":"aaa"}
```

- XML-JSON eşlemesinde, JSON 'da kaçışın olması gereken karakterlerin üzerine kaçışın ve diğerlerinin kaçışsız olması gerekir. "/" Karakteri, kaçılması gereken bir karakter olmasa da, bununla birlikte kaçışın, ancak JSON 'dan XML eşlemesi için kaçılması gerekmez. Bu, JSON 'daki veriler için ASP.NET AJAX biçimini desteklemek için gereklidir `DateTime` .

- JSON for XML eşlemesinde, bir `string` [yerel ad] üreten bir oluşturmak için tüm karakterler (varsa kaçan karakterler dahil) alınır.

- İç öğeler [alt öğe], ' ın ' de olduğu gibi, Bölüm 2,2 ' deki değere eşlenir `JSON Type Attribute` `Root JSON Element` . Birden çok sayıda iç içe geçme düzeyine (diziler içinde iç içe geçme dahil) izin verilir.

Örnek: aşağıdaki öğe bir JSON parçasına eşlenir.

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

Aşağıdaki JSON parçası, eşlendiği şeydir.

```json
{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}
```

> [!NOTE]
> Önceki eşlemede XML kodlama adımı yok. Bu nedenle, WCF yalnızca anahtar adlarındaki tüm karakterlerin XML öğe adlarında geçerli karakterler olduğu JSON belgelerini destekler. Örneğin, "a"} JSON belgesi, bir XML öğesi için geçerli bir ad olmadığından, {"<": "a"} < desteklenmez.

Önceki eşleme JSON kaçış/unkaçış adımlarını içerdiğinden, ters durum (XML 'de geçerli olan ancak JSON içinde olmayan karakterler) herhangi bir soruna neden olmaz.

Dizi kayıtları aşağıdaki gibi çalışır:

- İç öğenin [yerel ad] öğesi "öğe".

- İç öğenin [alt öğeleri], Node JSON öğesi için olduğu gibi JSON türü özniteliğine göre Bölüm 2,3 ' deki değere eşlenir. Birden çok sayıda iç içe geçme düzeyine (nesneler içinde iç içe geçme dahil) izin verilir.

Örnek: aşağıdaki öğe bir JSON parçasına eşlenir.

```xml
<root type="array">
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root>
```

JSON parçası aşağıda verilmiştir.

```json
["myValue1",2,[true,null]]
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Bağımsız JSON Seri Hale Getirme](stand-alone-json-serialization.md)
