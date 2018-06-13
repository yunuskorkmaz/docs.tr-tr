---
title: JSON ve XML Arasında Eşleme
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: db34161ad3e2f7d2c9737e6a456b27bd70c5ebfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496993"
---
# <a name="mapping-between-json-and-xml"></a>JSON ve XML Arasında Eşleme
Yazarları ve okuyucular üretilen <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> XML API'si JavaScript nesne gösterimi (JSON) içeriği sağlar. JSON, JavaScript nesne değişmez değerler kümesini kullanarak verileri kodlar. JSON içeriği yüklenirken okuyucular ve bu fabrikası tarafından üretilen yazarları aynı zamanda kullanılan gönderilen veya alınan kullanarak Windows Communication Foundation (WCF) uygulamaları tarafından <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> veya <xref:System.ServiceModel.WebHttpBinding>.  
  
 JSON içeriği ile hazırlarken, JSON okuyucu XML örneği üzerinde bir metinsel XML okuyucusu mu aynı şekilde davranır. Üreten bir metinsel XML okuyucusu üzerinde bir belirli XML örneği, bir dizi çağrıları verildiğinde JSON yazan JSON içeriği teslim yazar. Bu örnek XML ve JSON içeriği arasında eşleme Gelişmiş senaryolarda kullanım için bu konudaki açıklanmıştır.  
  
 Dahili olarak, JSON WCF tarafından işlendiğinde bir XML bilgi olarak temsil edilir. Normalde eşleme mantıksal bir tane olduğundan iç bu gösterim ile ilgili gerekmez: JSON normalde fiziksel bellekte XML biçimine dönüştürülen veya XML'den JSON biçiminde seri hale dönüştürülür. Eşleme XML API'leri JSON içeriğe erişmek için kullanıldığı anlamına gelir.  
  
 WCF JSON kullandığında olan Normal senaryo <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> otomatik olarak tarafından prize takılı <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> davranışı ya da <xref:System.ServiceModel.Description.WebHttpBehavior> davranışı uygun olduğunda. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> JSON ve XML bilgi arasında eşleme anlar ve JSON ile doğrudan ilgili sanki gibi davranır. (Kullanmak da mümkündür <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> XML okuyucusu ya da XML aşağıdaki eşleme uyan anlama ile yazan.)  
  
 Gelişmiş senaryolar aşağıdaki eşlemesini doğrudan erişmek gerekli olabilir. Seri hale getirmek ve öğesine bağlı kalmadan özel yollarla JSON serisini kaldırmak istediğinizde bu senaryolar ortaya <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, veya ile ilgilenirken <xref:System.ServiceModel.Channels.Message> doğrudan JSON içeren iletileri için türü. JSON XML eşleme ileti günlüğe kaydetme için de kullanılır. WCF'de ileti günlüğe kaydetme özelliğini kullanırken, JSON iletileri günlüğe kaydedilir XML olarak sonraki bölümde açıklanan eşlemeyi göre.  
  
 Bir eşleme kavramı açıklamak için aşağıdaki örnek bir JSON belgesinin ' dir.  
  
```json  
{"product":"pencil","price":12}  
```  
  
 Daha önce bahsedilen okuyucular birini kullanarak bu JSON belgesini okumak için aynı dizisini kullanın <xref:System.Xml.XmlDictionaryReader> aşağıdaki XML belgeyi okumak için olduğu gibi çağırır.  
  
```xml  
<root type="object">  
    <product type="string">pencil</product>  
    <price type="number">12</price>  
</root>  
```  
  
 Ayrıca, örnek JSON iletisinde ise ve WCF tarafından alınan oturum XML parçası önceki günlüğüne bakın.  
  
## <a name="mapping-between-json-and-the-xml-infoset"></a>JSON ve XML bilgi arasında eşleme  
 Resmi olarak, JSON arasında açıklandığı gibi eşlemedir [RFC 4627](http://go.microsoft.com/fwlink/?LinkId=98808) (gevşek ve belirli bazı kısıtlamalar ile eklenen diğer kısıtlamalar hariç) ve XML bilgi (ve metinsel olmayan XML) olarak açıklanan [XML bilgileri Ayarlama](http://go.microsoft.com/fwlink/?LinkId=98809) . Bu konuda tanımları için bkz: *bilgisi öğeleri* ve [köşeli] alanlarında.  
  
 Boş bir JSON belgesi boş XML belgesi eşler ve boş bir XML belgesi için boş bir JSON belgesi eşler. JSON eşleme XML boşluk harfinden önce ve sonra belgeyi boşluk sondaki izin verilmez.  
  
 Eşleme ya da bir belge bilgi öğesi (DII) veya bir öğe bilgi öğesi (EII) ve JSON arasında tanımlanır. EII veya DII'ın [belge öğesi] özelliği, kök JSON öğesi olarak adlandırılır. Belge parçalarını (XML birden çok kök öğe ile) bu eşlemede desteklenmez unutmayın.  
  
 Örnek: Aşağıdaki belge:  
  
 `<?xml version="1.0"?>`  
  
 `<root type="number">42</root>`  
  
 Ve aşağıdaki öğe:  
  
 `<root type="number">42</root>`  
  
 Hem JSON için bir eşleme sahiptir. <`root`> Öğesidir kök JSON her iki durumda.  
  
 Ayrıca, bir DII söz konusu olduğunda, aşağıdaki bulundurulmalıdır:  
  
-   Bazı öğeler [alt] listesinde mevcut olmaması gerekir. Bu olgu üzerinde JSON öğesinden XML eşlenmiş okunurken kullanmayın.  
  
-   [Alt] liste yorum yok bilgisi öğeleri tutar.  
  
-   [Alt] liste DTD bilgi öğe tutar.  
  
-   Kişisel bilgileri (PI) bilgi öğe [alt] listesini tutar ( \<? xml... > PI bilgi öğesi bildirimi dikkate alınmaz)  
  
-   [Gösterimler] boş kümesidir.  
  
-   [Ayrýþtýrýlmamýþ varlıklar] boş kümesidir.  
  
 Örnek: Hiçbir JSON biçiminde seri hale çünkü eşleme aşağıdaki belge sahip [alt] ayrı tutma PI bir ve bir açıklama.  
  
 `<?xml version="1.0"?>`  
  
 `<!--comment--><?pi?>`  
  
 `<root type="number">42</root>`  
  
 Kök JSON öğesi EII aşağıdaki özelliklere sahiptir:  
  
-   [yerel adı] "root" değerine sahip.  
  
-   [ad alanı adı] değeri yok.  
  
-   [önek] değeri yok.  
  
-   [alt] (hangi iç öğelerini temsil eden ayrıntılarıyla açıklandığı gibi) EIIs veya CIIs (karakter bilgi ayrıntılarıyla açıklandığı gibi öğeler) ya da bu, ancak her ikisi de hiçbiri ya da içerebilir.  
  
-   Aşağıdaki isteğe bağlı öznitelik bilgileri öğeleri (AIIs) [öznitelikler] içerebilir  
  
-   JSON türü özniteliği ("ayrıntılarıyla açıklandığı gibi türü"). Bu öznitelik, eşlenen XML JSON türü (dize, sayı, boolean, nesne, dizi veya null) korumak için kullanılır.  
  
-   Veri sözleşmesi Name özniteliği ("ayrıntılarıyla açıklandığı gibi __type"). Bu öznitelik yalnızca JSON türü özniteliği de varsa ve [normalleştirilmiş değeri] "nesne" olduğu mevcut olabilir. Bu öznitelik tarafından kullanılan `DataContractJsonSerializer` korumak için veri türü bilgileri - Örneğin, çok biçimli durumlarda türetilmiş bir tür serileştirilmiş ve bir taban türü beklenen konumda sözleşme. İle çalışmıyorsanız `DataContractJsonSerializer`, çoğu durumda, bu öznitelik dikkate alınmaz.  
  
-   [kapsam içinde ad alanları] için "xml" bağlama içeren "http://www.w3.org/XML/1998/namespace" bilgi belirtimine göre zorunlu olarak.  
  
-   [alt], [öznitelikler] ve [kapsam içinde ad alanları] değil olmalıdır dışındaki tüm öğeleri belirtildiği gibi daha önce ve [ad alanı öznitelikler] hiç üyesi olması gerekir, ancak bu olgulara XML JSON öğesinden eşlenmiş okunurken güvenmeyin.  
  
 Örnek: Hiçbir JSON biçiminde seri hale çünkü eşleme aşağıdaki belge sahip [ad alanı öznitelikler] boş değil.  
  
 `<?xml version="1.0"?>`  
  
 `<root  xmlns:a="myattributevalue">42</root>`  
  
 JSON Type özniteliği için AII aşağıdaki özelliklere sahiptir:  
  
-   [ad alanı adı] değeri yok.  
  
-   [önek] değeri yok.  
  
-   [Yerel] "tür" adıdır.  
  
-   [normalleştirilmiş değeri] aşağıdaki bölümde açıklanan olası tür değerlerinden biri.  
  
-   [belirtilen] `true`.  
  
-   [öznitelik türü] değeri yok.  
  
-   [başvuruları] değeri yok.  
  
 Veri sözleşmesi adı özniteliği AII aşağıdaki özelliklere sahiptir:  
  
-   [ad alanı adı] değeri yok.  
  
-   [önek] değeri yok.  
  
-   [Yerel] "__type" (iki alt çizgi ve ardından "tür") adıdır.  
  
-   [normalleştirilmiş değeri] geçerli bir Unicode dize – JSON Bu dizeye eşleme aşağıdaki bölümde açıklanmıştır.  
  
-   [belirtilen] `true`.  
  
-   [öznitelik türü] değeri yok.  
  
-   [başvuruları] değeri yok.  
  
 İç öğeleri kök JSON öğesi veya diğer iç öğe içinde yer alan aşağıdaki özelliklere sahiptir:  
  
-   [yerel adı] ayrıntılarıyla açıklandığı gibi herhangi bir değer olabilir  
  
-   [ad alanı adı] [önek] [alt] [öznitelikler], [ad alanı öznitelikler] ve [kapsam içinde ad alanları] kök JSON öğesi olarak aynı kuralları tabidir.  
  
 Kök JSON öğesi hem iç öğeleri JSON türü özniteliği JSON ve olası [alt] ve bunların yorumlama eşleme tanımlar. Özniteliğin [normalleştirilmiş değeri] küçük harfe duyarlıdır ve küçük harfli olması gerektiğini ve boşluk içeremez.  
  
|[normalleştirilmiş değeri], `JSON Type Attribute`'s AII|İzin verilen [alt] karşılık gelen EII|JSON eşleme|  
|---------------------------------------------------------|---------------------------------------------------|---------------------|  
|`string` (veya JSON türü AII yokluğu)<br /><br /> A `string` ve JSON türü AII olmayışı aynı yapar `string` varsayılan.<br /><br /> Bu nedenle, `<root> string1</root>` eşler için JSON `string` "Dize1".|0 veya daha fazla CIIs|JSON `string` (JSON RFC, bölüm 2.5). Her `char` [karakter koduna] CII karşılık gelen bir karakterdir. Hiçbir CIIs varsa, boş bir JSON değerine eşleyen `string`.<br /><br /> Örnek: Bir JSON parça öğesi eşler:<br /><br /> `<root type="string">42</root>`<br /><br /> JSON parça "42" dir.<br /><br /> XML JSON eşlemesi olmalıdır karakter eşlemesi Atlanan karakterle kaçışlı, diğerlerini değil kaçış karakterleri harita. "/" Karakterini özel – olmasını yok olsa bile kaçışlı (olarak kullanıma yazılı "\\/").<br /><br /> Örnek: Bir JSON parça öğesi eşler.<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON parçası olan " \\" da\\/ta\\"".<br /><br /> XML eşleme için JSON üzerinde karşılık gelen [karakter kodu] için harita doğru herhangi Atlanan ve olmayan karakterler kaçışlı.<br /><br /> Örnek: "\u0041BC" JSON parça aşağıdaki XML öğesi eşler.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Dize, XML eşlenmedi boşluk (JSON RFC 2 bölümünde ' ws') tarafından arasında olmalıdır.<br /><br /> Örnek: JSON "ABC" parçalara, (ilk tırnak önce alanları olan), aşağıdaki XML öğesi eşler.<br /><br /> `<root type="string">ABC</root>`<br /><br /> Hiçbir boşluk XML boşluk JSON içinde eşler.<br /><br /> Örnek: Bir JSON parça aşağıdaki XML öğesi eşler.<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON parça "BC" dir.|  
|`number`|1 veya daha fazla CIIs|JSON `number` (JSON RFC, bölüm 2.4), büyük olasılıkla çevrelenen tarafından boşluk. Her karakteri sayı/boşluk birlikte CII [karakter kodu] için karşılık gelen bir karakterdir.<br /><br /> Örnek: Bir JSON parça öğesi eşler.<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON parça 42 olduğu<br /><br /> (Boşluk korunur).|  
|`boolean`|4 veya 5 CIIs (için karşılık geldiği `true` veya `false`), büyük olasılıkla çevrelenen ek boşluk CIIs tarafından.|Sabit değer için "true" dizesine karşılık gelen bir CII sırası eşlenen `true`, ve "false" dizesine karşılık gelen bir CII dizisi için sabit eşlendi `false`. Boşluk çevresindeki korunur.<br /><br /> Örnek: Bir JSON parça öğesi eşler.<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON parçası olan `false`.|  
|`null`|Hiçbirine izin verilmiyor.|Sabit `null`. XML eşleme için JSON üzerinde `null` XML eşlenmedi boşluk (2 bölümde ' ws') tarafından çevrelenen.<br /><br /> Örnek: Bir JSON parça öğesi eşler.<br /><br /> `<root type="null"/>`<br /><br /> veya<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> Her iki durumda JSON parçasında olduğu `Null`.|  
|`object`|0 veya daha fazla EIIs.|A `begin-object` (kuşak sol) ayrıntılarıyla açıklandığı gibi bir üye kaydında bölümüne JSON RFC olduğu gibi 2.2, her EII için izlenen. Birden fazla EII ise arasında üye kayıt değeri ayırıcılar (virgül) vardır. Tüm bunlar bir end-nesnesiyle (sağ kaşlı ayraç) izler.<br /><br /> Örnek: JSON parça öğesi eşler.<br /><br /> \<kök türü "nesne" = ><br /><br /> \<type1 türü "dize" = > aaa\</type1 ><br /><br /> \<type2 türü "dize" = > bbb\</type2 ><br /><br /> \</ root ><br /><br /> JSON parçası olan {"type1": "aaa", "type2": "bbb"}.<br /><br /> Veri sözleşmesi türü özniteliği için JSON eşleme XML varsa, ek bir üye kaydı başında eklenir. Veri sözleşmesi türü özniteliğinin ("__type") [yerel adı] adıdır ve özniteliğin [normalleştirilmiş değeri] değeri olduğu. Buna karşılık, ilk üye-kaydın adını [yerel adı] veri sözleşmesi türü özniteliği ise XML eşleme için JSON üzerinde (diğer bir deyişle, "\__ad"), karşılık gelen bir veri sözleşmesi türü özniteliği eşlenen XML'de varsa ancak karşılık gelen EII değil mevcut. Bu üye kaydını uygulamak bu özel eşleme için JSON nesnesinde ilk gerçekleşmelidir unutmayın. Bu üye kayıtların sırası önemli olduğu her zamanki JSON işlenmesini, bir ayrılma temsil eder.<br /><br /> Örnek:<br /><br /> Aşağıdaki JSON parça XML eşler.<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> Aşağıdaki kod XML'dir.<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> Dikkat \__ad AII mevcut, ancak hiçbir \__ad EII.<br /><br /> Ancak, JSON sırayla olarak ters aşağıdaki örnekte gösterilir.<br /><br /> {"name": "John","\__ad": "Kişi"}<br /><br /> Karşılık gelen XML gösterilir.<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> Diğer bir deyişle, \_her zamanki gibi özel bir anlamı ve bir EII eşlenir sahip _ad denetlemeyi AII değil.<br /><br /> [Normalleştirilmiş değeri] kaçış/unescaping kuralları AII için JSON değerine eşlenen JSON dizeler, bu tablonun "dize" satırı belirtilen aynıdır.<br /><br /> Örnek:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> önceki örneği aşağıdaki JSON eşlenebilir.<br /><br /> `{"__type":"\\abc"}`<br /><br /> JSON eşleme XML üzerinde ilk EII's [yerel adı] olmamalıdır "\__ad".<br /><br /> Boşluk (`ws`) XML JSON eşleştirme nesneleri için hiçbir zaman oluşturulur ve JSON üzerinde XML eşleme için göz ardı edilir.<br /><br /> Örnek: Bir XML öğesi aşağıdaki JSON parça eşler.<br /><br /> {"bilgi": "aaa", "ggg": "bbb"}<br /><br /> XML öğesi aşağıdaki kodda gösterilir.<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|  
Ray'|0 veya daha fazla EIIs|Bir başlangıç ayrıntılarıyla açıklandığı gibi her EII için bir dizi kaydı tarafından izlenen dizi (sol köşeli ayraç) JSON RFC 2.3 bölümünü olduğu gibi. Birden fazla EII ise, dizi kayıtlar arasında değer ayırıcılar (virgül) vardır. Tüm bu bitiş dizisi tarafından izlenir.<br /><br /> Örnek: Bir JSON parça aşağıdaki XML öğesi eşler.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> ["Aaa", "bbb"] JSON parçası değil<br /><br /> Boşluk (`ws`) XML JSON eşleştirme diziler için hiçbir zaman oluşturulur ve JSON üzerinde XML eşleme için göz ardı edilir.<br /><br /> Örnek: AJSON parça.<br /><br /> ["aaa", "bbb"]<br /><br /> Eşlendiği XML öğesi.<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|  
  
 Üye kayıtları şu şekilde çalışır:  
  
-   İç öğenin [yerel adı] eşlendiğini `string` parçası `member` JSON RFC 2.2 bölümünde tanımlandığı gibi.  
  
 Örnek: Bir JSON parça öğesi eşler.  
  
 `<root type="object"/>`  
  
 `<myLocalName type="string">aaa</myLocalName>`  
  
 `</root >`  
  
 Aşağıdaki JSON parça görüntülenir.  
  
 `{"myLocalName":"aaa"}`  
  
-   XML JSON eşlemesi JSON'de kaçış uygulanmalıdır karakterler atlanır ve diğerleri değil atlanır. Kaçış uygulanmalıdır, bir karakter olmasa bile "/" karakterini yine de kaçışlı (bunu JSON üzerinde XML eşleme için kaçış gerekmez). Bu ASP.NET AJAX biçimini desteklemek için gerekli `DateTime` JSON verileri.  
  
-   XML eşleme için JSON üzerinde (gerekirse değil Atlanan karakterleri dahil) tüm karakterleri forma gerçekleştirilen bir `string` [yerel adı] üretir.  
  
-   İç öğeleri [alt] eşlemek bölümünde 2.2, değerine göre `JSON Type Attribute` için olduğu gibi `Root JSON Element`. Birden çok düzeyde (iç içe geçme diziler içinde dahil) EIIs iç içe geçmiş izin verilir.  
  
 Örnek: Bir JSON parça öğesi eşler.  
  
 `<root type="object">`  
  
 `<myLocalName1 type="string">myValue1</myLocalName1>`  
  
 `<myLocalName2 type="number">2</myLocalName2>`  
  
 `<myLocalName3 type="object">`  
  
 `<myNestedName1 type="boolean">true</myNestedName1>`  
  
 `<myNestedName2 type="null"/>`  
  
 `</myLocalName3>`  
  
 `</root >`  
  
 Aşağıdaki JSON parça ne eşlendiği ' dir.  
  
 `{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`  
  
> [!NOTE]
>  Önceki eşlemesinde yok XML kodlama adım yoktur. Bu nedenle, WCF, yalnızca anahtar adları içindeki tüm karakterleri XML öğe adları geçerli karakterler nerede JSON belgelerini destekler. Örneğin, JSON belgesi {"<": "a"} desteklenmiyor < bir XML öğesi için geçerli bir ad değil.  
  
 Önceki eşleme JSON kaçış/unescaping adımları içerdiğinden ters durum (XML ancak içinde değil JSON geçerli karakterler) herhangi bir sorun neden olmaz.  
  
 Dizi kayıtları şu şekilde çalışır:  
  
-   İç öğenin [yerel adı] "öğesi" dir.  
  
-   İç öğenin [alt] eşleme bölümünde 2.3, değerine göre JSON türü kök JSON öğe için yaptığı gibi özniteliği. Birden çok düzeyde (iç içe nesne içindeki dahil) EIIs iç içe geçmiş izin verilir.  
  
 Örnek: Bir JSON parça öğesi eşler.  
  
 `<root type="array"/>`  
  
 `<item type="string">myValue1</item>`  
  
 `<item type="number">2</item>`  
  
 `<item type="array">`  
  
 `<item type="boolean">true</item>`  
  
 `<item type="null"/>`  
  
 `</item>`  
  
 `</root >`  
  
 JSON parça verilmiştir.  
  
 `["myValue1",2,[true,null]]`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>  
 [Bağımsız JSON Seri Hale Getirme](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
