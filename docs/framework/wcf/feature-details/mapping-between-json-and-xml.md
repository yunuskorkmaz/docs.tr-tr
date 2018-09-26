---
title: JSON ve XML Arasında Eşleme
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: 075f85887f99708dd1f3479bf0b036203886af71
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156682"
---
# <a name="mapping-between-json-and-xml"></a>JSON ve XML Arasında Eşleme
Okuyucular ve yazıcılar tarafından üretilen <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> üzerinde JavaScript nesne gösterimi (JSON) içerik bir XML API sağlar. JSON, JavaScript nesne değişmez değerler kümesini kullanarak veri kodlar. JSON içeriği yüklenirken okuyucular ve yazıcılar bu üretici tarafından üretilen de kullanılan gönderilen veya alınan kullanarak Windows Communication Foundation (WCF) uygulamaları tarafından <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> veya <xref:System.ServiceModel.WebHttpBinding>.

JSON içeriği ile hazırlarken, JSON okuyucu XML örneği üzerinde bir metinsel XML okuyucusu yaptığı aynı şekilde davranır. JSON içeriği üreten bir metinsel XML okuyucusu üzerinde bir belirli XML örneği, bir dizi çağrıları verildiğinde JSON yazıcı yazar. Bu örnek XML ve JSON içeriği arasındaki eşleme, Gelişmiş senaryolarında kullanım için bu konuda açıklanmıştır.

Dahili olarak, JSON, WCF tarafından işlendiğinde bir XML bilgi kümesi olarak temsil edilir. Normalde eşleme mantıksal bir tane olduğundan bu iç gösterimi ile konusunda endişe duymaları gerekmez: JSON normalde fiziksel bellekte XML'ye dönüştürülecek veya XML'den JSON'a dönüştürülür. Eşleme XML API'lerini JSON içeriğe erişmeye kullanılmasını anlamına gelir.

WCF JSON kullandığında, olan Normal senaryo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> otomatik olarak tarafından prize takılı olduğu <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> davranış veya <xref:System.ServiceModel.Description.WebHttpBehavior> uygun olduğunda davranışı. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> JSON ve XML bilgi kümesi arasındaki eşleme anlar ve JSON ile doğrudan ilgili yokmuş gibi davranır. (Kullanmak mümkün mü <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> XML okuyucusu veya yazar, XML aşağıdaki eşleme uygun olduğunu anlamak.)

Gelişmiş senaryolar aşağıdaki eşlemeyi doğrudan erişmek gerekli olabilir. Bağlı kalmadan özel yollarla JSON seri hale getrime ve istediğiniz zaman bu senaryolar ortaya <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, veya ile ilgilenirken <xref:System.ServiceModel.Channels.Message> doğrudan JSON içeren iletileri için türü. JSON-XML eşleme için ileti günlüğe kaydetmeyi de kullanılır. WCF'de ileti günlüğe kaydetme özelliğini kullanırken, JSON iletilerini günlüğe kaydedilir XML olarak göre sonraki bölümde açıklanan eşleme.

Bir eşleme kavramı açıklamak için aşağıdaki örnekte bir JSON belgesinin bulunur.

```json
{"product":"pencil","price":12}
```

Daha önce bahsedilen okuyucular birini kullanarak bu JSON belgesini okumaya aynı sırada kullanın <xref:System.Xml.XmlDictionaryReader> aşağıdaki XML belgesi okumak için yaptığınız gibi çağırır.

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

Ayrıca, örnek JSON iletisinde WCF tarafından alınan ve günlüğe, XML parçası önceki günlüğüne bakın.

## <a name="mapping-between-json-and-the-xml-infoset"></a>JSON ve XML bilgi kümesi arasında eşleme
İzlerse, eşleme açıklandığı JSON arasında bir [RFC 4627](https://go.microsoft.com/fwlink/?LinkId=98808) (belirli kısıtlamalar gevşek ve belirli eklenen diğer kısıtlamaları hariç) ve XML bilgi kümesi (ve metinsel olmayan XML) olarak açıklanan [XML bilgi Ayarlama](https://go.microsoft.com/fwlink/?LinkId=98809) . Tanımları için şu konuya bakın *bilgi öğeleri* ve alanlar [köşeli ayraç].

Boş bir XML belgesi için boş bir JSON belgesi eşler ve boş bir XML belgesi için boş bir JSON belgesi eşler. JSON eşleme XML boşluk harfinden önce ve sonra belgeyi sondaki boşlukları izin verilmez.

Ya da bir belge bilgi öğesi (DII) veya bir öğe bilgi öğesi (EII) ve JSON arasında eşleme tanımlanır. EII veya DII'ın [belge öğesi] özelliği, kök JSON öğesi olarak adlandırılır. Belge parçalarını (birden çok kök öğesi ile XML), bu eşlemeyi desteklenmediğini unutmayın.

Örnek: Aşağıdaki belge:

```xml
<?xml version="1.0"?>
<root type="number">42</root>`
```

Ve şu öğe:

```xml
<root type="number">42</root>
```

Hem de JSON bir eşlemeye sahip. <`root`> Kök JSON öğesinde her iki durumda bir öğedir.

Ayrıca, bir DII söz konusu olduğunda, aşağıdaki bulundurulmalıdır:

- Bazı öğeler [alt] listesinde mevcut olmalıdır. Bu olgu üzerinde XML JSON'dan eşlenen okurken güvenmeyin.

- [Alt] liste yorum bilgi öğeleri içerir.

- Hiçbir DTD'nin bilgi öğeleri [alt] listesini tutar.

- Hiçbir kişisel bilgileri (PI) bilgi öğeleri [alt] liste tutar ( `<?xml…>` bildirimi olarak kabul edilmez PI bilgi öğesi)

- [Gösterimler] boş kümesidir.

- [Ayrıştırılmamış varlıklar] boş kümesidir.

Örnek: Aşağıdaki belge yok JSON olduğundan eşleme sahip [alt] ayrı tutma PI ve bir açıklama.

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

EII kök JSON öğesi için aşağıdaki özelliklere sahiptir:

- [yerel adı] "Kök" değeri vardır.

- [ad], değer yok.

- [ön ek] değeri yok.

- (Bu iç öğelerini temsil eden daha da açıklandığı gibi) EIIs veya CIIs (karakter bilgi daha ayrıntılı olarak açıklandığı gibi öğeleri) ya da hiçbiri bu, ancak ikisi birden değil, [alt] ya da içerebilir.

- Aşağıdaki isteğe bağlı öznitelik bilgileri öğeler (AIIs) [öznitelikler] içerebilir

- JSON tür özniteliği ("daha fazla açıklandığı türü"). Bu öznitelik, eşlenen XML'de JSON türünü (dize, sayı, Boole, nesne, dizi veya null) korumak için kullanılır.

- Veri anlaşması Name özniteliği ("\_\_türü") daha ayrıntılı olarak açıklandığı gibi. Bu öznitelik yalnızca JSON tür özniteliği de varsa ve [normalleştirilmiş değeri] "nesne" dir bulunabilir. Bu öznitelik tarafından kullanılan `DataContractJsonSerializer` korumak için veri türü bilgisi - Örneğin, çok biçimli durumlarda türetilmiş bir türü seri olduğunda ve bir taban türü beklenen konumda anlaşması. İle çalışmıyorsanız `DataContractJsonSerializer`, çoğu durumda, bu öznitelik yoksayılır.

- [kapsamdaki ad alanları] içerir "xml" bağlantısını için `http://www.w3.org/XML/1998/namespace` sonrası bilgi kümesi belirtimi tarafından uygulanan gibi.

- [alt], [öznitelikler] ve [kapsamındaki namespaces] olarak belirtilen dışındaki tüm öğeler daha önce olmamalıdır ve [ad alanı öznitelikleri] üye olmalıdır, ancak bu, olgulara JSON'dan eşlenen XML okunurken güvenmeyin.

Örnek: Aşağıdaki belge yok JSON olduğundan eşleme sahip [ad alanı öznitelikleri] boş değil.

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

JSON türü özniteliği için tümü, aşağıdaki özelliklere sahiptir:

- [ad], değer yok.
- [ön ek] değeri yok.
- [Yerel] "type" dir.
- [normalleştirilmiş value] aşağıdaki bölümde açıklanan muhtemel tür değerlerinden biri.
- [] belirtilmiştir `true`.
- [öznitelik türü] değeri yok.
- [başvuruları] değeri yok.

Veri anlaşması Name özniteliği için tümü, aşağıdaki özelliklere sahiptir:

- [ad], değer yok.
- [ön ek] değeri yok.
- [yerel adı] "\_\_türü" (iki alt çizgi ve ardından "tür").
- [normalleştirilmiş değeri] geçerli herhangi bir Unicode dize – bu JSON dizesine eşlemesi aşağıdaki bölümde açıklanmıştır.
- [] belirtilmiştir `true`.
- [öznitelik türü] değeri yok.
- [başvuruları] değeri yok.

Kök JSON öğesi veya diğer iç öğeleri içinde bulunan iç öğeleri şu özelliklere sahiptir:

- [yerel adı] daha ayrıntılı olarak açıklandığı gibi herhangi bir değere sahip.
- [ad], [ön ek], [alt], [öznitelikler] [ad alanı öznitelikleri] ve [kapsamdaki ad], bir kök JSON öğesi olarak aynı kurallara tabidir.

Kök JSON öğesini ve iç öğeleri JSON tür özniteliği JSON ve olası [alt] ve bunların yorumu eşlemeyi tanımlar. Özniteliğin [normalleştirilmiş değeri] büyük/küçük harfe ve küçük harfli olması gerektiğini ve boşluk içeremez.

|[normalleştirilmiş değeri] JSON türü özniteliğin tümü,|İzin verilen [alt] karşılık gelen EII|JSON eşleme|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (veya tümü JSON türünde olmaması)<br /><br /> A `string` ve devamsızlık JSON türünde tümü aynı yapar `string` varsayılan.<br /><br /> Bu nedenle, `<root> string1</root>` JSON değerine eşleyen `string` "string1".|0 veya daha fazla CIIs|Bir JSON `string` (JSON RFC, 2.5 bölümü). Her `char` [karakter kodu] için CII karşılık gelen bir karakterdir. Hiçbir CIIs varsa, boş bir JSON ile eşler. `string`.<br /><br /> Örnek: Şu öğe için bir JSON parça eşlemeleri:<br /><br /> `<root type="string">42</root>`<br /><br /> JSON parçası, "42" olur.<br /><br /> XML ile JSON eşlemesi olmalıdır karakterleri harita atlatmalı karakterler için kaçış karakterleri, diğerlerini çıkarılmayan karakter eşleyin. "/" Karakteri özel – olması gerekmez ancak kaçan (out yazılı olarak "\\/").<br /><br /> Örnek: Şu öğe için bir JSON parçası eşler.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON parçası olan " \\" da\\/ta\\"".<br /><br /> XML eşleme için JSON üzerinde karşılık gelen [karakter kodu] için harita doğru herhangi atlatmalı karakterler ve karakterler kaçan.<br /><br /> Örnek: "\u0041BC" JSON parçası, aşağıdaki XML öğesi eşler.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Dize, XML eşlenmedi boşluk (JSON RFC bölümünde 2'ws ') tarafından içine alınır.<br /><br /> Örnek: JSON "ABC" parçası, (ilk çift tırnak işareti önceki boşluklar bulunur), aşağıdaki XML öğesi eşler.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Herhangi bir boşluğu XML boşluk json'da eşlenir.<br /><br /> Örnek: JSON parçaya şu XML öğesi eşler.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON parçası, "BC" olan.|
|`number`|1 veya daha fazla CIIs|Bir JSON `number` (JSON RFC, bölüm 2.4), büyük olasılıkla arasına boşluk tarafından. Sayı/boşluk birlikte her bir karakter CII [karakter kodu] için karşılık gelen bir karakterdir.<br /><br /> Örnek: Şu öğe için bir JSON parçası eşler.<br /><br /> `<root type="number">    42</root>`<br /><br /> 42 JSON parçası olan<br /><br /> (Boşluk korunur).|
|`boolean`|4 veya 5 CIIs (karşılık gelen `true` veya `false`), büyük olasılıkla arasında ek boşluk CIIs tarafından olacak.|Değişmez değer "true" dizesine karşılık gelen bir CII dizisi eşlendi `true`, ve "false" dizesine karşılık gelen bir CII dizi değişmez değer eşlendi `false`. Boşluk çevresindeki korunur.<br /><br /> Örnek: Şu öğe için bir JSON parçası eşler.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON parçası olan `false`.|
|`null`|Hiçbirine izin verilmiyor.|Değişmez değer `null`. XML eşleme için JSON üzerinde `null` XML eşlenmedi boşluk (2. bölümündeki ' ws') tarafından içine alınır.<br /><br /> Örnek: Şu öğe için bir JSON parçası eşler.<br /><br /> `<root type="null"/>`<br /><br /> veya<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Her iki durumda JSON parçası olan `Null`.|
|`object`|0 veya daha fazla EIIs.|A `begin-object` (sol küme ayracı) daha ayrıntılı olarak açıklandığı gibi bir üye kaydında bölümüne JSON RFC olduğu gibi 2.2, her EII için izlenen. Birden fazla EII ise, üye kayıtları arasında değeri-ayırıcılar (virgül) vardır. Tüm bunlar bir end-nesnesiyle (sağ küme ayracı) izler.<br /><br /> Örnek: Şu öğe için JSON parçası eşler.<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> JSON parçası olan `{"type1":"aaa","type2":"bbb"}`.<br /><br /> Veri anlaşması türü özniteliği için JSON eşleme XML varsa, ek bir üye kaydı başında'e eklenir. Veri anlaşması türü özniteliği [yerel adı] adıdır ("\_\_türü"), ve değeri [normalleştirilmiş değeri] özniteliği. Buna karşılık, ilk üye-kaydın adı [Yerel] veri anlaşması türü özniteliğinin adıysa XML eşleme için JSON üzerinde (diğer bir deyişle, "\_\_türü"), eşlenen XML'de karşılık gelen bir veri anlaşması türü özniteliği varsa ancak bir karşılık gelen EII mevcut değil. JSON nesnesinde uygulamak bu özel eşleme için bu üye kaydını önce gerçekleşmesi gerektiğini unutmayın. Bu, burada üye kayıtları sırası önemli değildir normal JSON işleme gelen bir ayrılma temsil eder.<br /><br /> Örnek:<br /><br /> Aşağıdaki JSON parçası, XML eşler.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Aşağıdaki kod XML'dir.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Dikkat \_ \_türü tümü mevcut, ancak hiçbir \_ \_EII yazın.<br /><br /> Ancak, siparişin JSON olarak tersine, aşağıdaki örnekte gösterilir.<br /><br /> {"name": "John","\_\_türü": "Kişi"}<br /><br /> Karşılık gelen XML gösterilir.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Diğer bir deyişle, \__türü zamanki gibi özel bir anlamı ve bir EII eşlenir olması değil tümü olmaktan çıkar.<br /><br /> [Normalleştirilmiş değeri] kaçış/unescaping kuralları tümü için bir JSON değerine eşleştirildiğinde JSON dizeler, bu tablonun "dize" satırında belirtilen aynıdır.<br /><br /> Örnek:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> Önceki örnekte, aşağıdaki JSON eşlenebilir.<br /><br /> `{"__type":"\\abc"}`<br /><br /> Bir XML JSON eşleştirme, ilk EII's [yerel adı] olmamalıdır "\_\_türü".<br /><br /> Boşluk (`ws`) XML JSON eşleştirme nesneleri için hiçbir zaman oluşturulur ve JSON üzerinde XML eşleme için göz ardı edilir.<br /><br /> Örnek: Aşağıdaki JSON parçası, bir XML öğesi eşler.<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> XML öğesi, aşağıdaki kodda gösterilmiştir.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|dizi|0 veya daha fazla EIIs|Bir başlangıç daha ayrıntılı olarak açıklandığı gibi her EII için bir dizi kayıt tarafından izlenen dizi (sol köşeli ayraç) JSON RFC 2.3 bölümünü olduğu gibi. Birden fazla EII varsa, dizi kayıtlar arasında değeri-ayırıcılar (virgül) vardır. Tüm bu son dizi tarafından izlenir.<br /><br /> Örnek: JSON parçaya şu XML öğesi eşler.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> ["Aaa", "bbb"] JSON parçası olan<br /><br /> Boşluk (`ws`) XML JSON eşleştirme diziler için hiçbir zaman oluşturulur ve JSON üzerinde XML eşleme için göz ardı edilir.<br /><br /> Örnek: Bir JSON parçası.<br /><br />`["aaa", "bbb"]`<br /><br /> Eşlendiği XML öğesi.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

Üye kayıtları şu şekilde çalışır:

- İç öğenin [yerel adı] eşler `string` parçası `member` JSON RFC 2.2 bölümünde tanımlandığı gibi.

Örnek: Şu öğe için bir JSON parçası eşler.

`<root type="object"/>`

`<myLocalName type="string">aaa</myLocalName>`

`</root >`

Aşağıdaki JSON parçası görüntülenir.

`{"myLocalName":"aaa"}`

- JSON eşleme XML, JSON biçiminde atlanması gereken karakterler atlanır ve diğerleri kaçış. "/" Karakterini kaçış karakterleri eklenmelidir, bir karakter olmamasına rağmen yine de kaçırılmışsa (Bu JSON üzerinde XML eşleme için kaçış gerekmez). ASP.NET AJAX biçimini desteklemek için bu gerekli `DateTime` JSON verileri.

- XML eşleme için JSON üzerinde (gerekirse değil atlatmalı karakterler dahil) tüm karakterleri formuna yönlendirilirsiniz bir `string` , [yerel adı] üretir.

- İç öğeleri [alt] eşleme bölümünde 2.2, değere göre `JSON Type Attribute` için olduğu gibi `Root JSON Element`. Birden çok iç içe geçen düzeye EIIs (iç içe dizi içinde dahil), izin verilir.

Örnek: Şu öğe için bir JSON parçası eşler.

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

Aşağıdaki JSON parçası, ne eşlendiği ' dir.

`{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`

> [!NOTE]
> Önceki eşlemede hiçbir XML kodlama adım yoktur. Bu nedenle, WCF, yalnızca anahtar adları tüm karakterleri geçerli karakter XML öğe adlarındaki nerede JSON belgelerini destekler. Örneğin, JSON belgesini {"<": "a"} desteklenmiyor < bir XML öğesi için geçerli bir ad değil.

Önceki eşleme JSON kaçış/unescaping adımlar içerdiğinden ters durumu (XML ancak içinde olmayan JSON içinde geçerli karakter) herhangi bir sorunu neden olmaz.

Dizi kayıtları şu şekilde çalışır:

- İç öğenin [yerel adı] "öğesi" dir.

- İç öğenin [alt] eşleme bölümünde 2.3, değere göre JSON tür yaptığı için kök JSON öğesi olarak özniteliği. Birden çok iç içe geçen düzeye EIIs (iç içe nesneler içinde dahil), izin verilir.

Örnek: Şu öğe için bir JSON parçası eşler.

```xml
<root type="array"/>
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root >
```

Aşağıdaki JSON parçası olan.

`["myValue1",2,[true,null]]`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [Bağımsız JSON Seri Hale Getirme](stand-alone-json-serialization.md)