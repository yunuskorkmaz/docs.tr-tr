---
title: Mesajlaşma Protokolleri
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 69a92bfb406e2e1af3bdcbb0316711dbf531204b
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812061"
---
# <a name="messaging-protocols"></a>Mesajlaşma Protokolleri

Windows Communication Foundation (WCF) kanal yığını, iç ileti gösterimini kendi tel biçimine dönüştürmek ve belirli bir aktarımı kullanarak göndermek için kodlama ve taşıma kanalları kullanır. Web Hizmetleri birlikte çalışabilirliği için kullanılan en yaygın aktarım HTTP ve Web Hizmetleri tarafından kullanılan en yaygın Kodlamalar XML tabanlı SOAP 1,1, SOAP 1,2 ve Ileti Iletimi Iyileştirme mekanizması (MTOM).

Bu konu, tarafından kullanılan aşağıdaki protokollerin WCF uygulama ayrıntılarını içerir <xref:System.ServiceModel.Channels.HttpTransportBindingElement> .

Belirtim/belge:

- [HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)
- [SOAP 1,1 http bağlama](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Bölüm 7
- [SOAP 1,2 http bağlama](https://www.w3.org/TR/soap12-part2) Bölüm 7

Bu konuda, ve kullanan aşağıdaki protokollerin WCF uygulama ayrıntıları ele <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> alınmaktadır <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> .

Belirtim/belge:

- [XML](https://www.w3.org/TR/REC-xml)
- [SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [SOAP 1,2 Core](https://www.w3.org/TR/soap12-part1/)
- [WS-Addressing 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [W3C Web Hizmetleri adresleme 1,0-çekirdek](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [W3C Web Hizmetleri adresleme 1,0-SOAP bağlama](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [W3C Web Hizmetleri adresleme 1,0-WSDL bağlama](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [W3C Web Hizmetleri adresleme 1,0-meta veriler](https://www.w3.org/TR/ws-addr-metadata/)
- [WSDL SOAP 1.1 bağlama](https://www.w3.org/TR/wsdl/)
- [WSDL SOAP 1.2 bağlama](https://www.w3.org/Submission/wsdl11soap12/)

Bu konuda, kullanan aşağıdaki protokollerin WCF uygulama ayrıntıları ele alınmaktadır <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> .

Belirtim/belge:

- [XOP ıNCLUDE](https://www.w3.org/TR/xop10/)
- [MTOM + SOAP 1,2 bağlama](https://www.w3.org/TR/soap12-mtom/)
- [MTOM SOAP 1,1 bağlaması](https://www.w3.org/Submission/soap11mtom10/)
- [MTOM WS-Ilke onaylama](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

Aşağıdaki XML ad alanları ve ilgili ön ekler Bu konu başlığı altında kullanılır:

| Ön ek | Ad alanı Tekdüzen Kaynak tanımlayıcısı (URI) |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| S12 |`http://www.w3.org/2003/05/soap-envelope` |
| WSA |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| XOP Include |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| UDP |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>SOAP 1,1 ve SOAP 1,2

### <a name="envelope-and-processing-model"></a>Zarf ve Işleme modeli
WCF, temel profil 1,1 (BP11) ve temel profil 1,0 (SSBP10) için SOAP 1,1 zarfı işleme uygular. SOAP 1,2 zarf işleme, SOAP12-part1 sonrasında uygulanır.

Bu bölümde, BP11 ve SOAP12-part1 ile ilgili olarak WCF tarafından alınan bazı uygulama seçimleri açıklanmaktadır.

#### <a name="mandatory-header-processing"></a>Zorunlu üstbilgi Işleme
WCF, `mustUnderstand` soap 1,1 ve soap 1,2 belirtimleri bölümünde açıklanan üstbilgileri işlemek için aşağıdaki çeşitlerle kuralları izler.

WCF kanal yığınına giren bir ileti, ilişkili bağlama öğeleri tarafından yapılandırılan tek tek kanallar tarafından işlenir; Örneğin, SMS mesajı Encoding, Security, güvenilir mesajlaşma ve Işlemler. Her kanal, ilişkili ad alanındaki üst bilgileri tanır ve bunları anlamış olarak işaretler. İleti dağıtıcıya girdiğinde, işlem biçimlendirici ilgili ileti/işlem sözleşmesi tarafından beklenen üstbilgileri okur ve anladım. Ardından dağıtıcı, kalan tüm üstbilgilerin anlaşılmadığını ancak olarak işaretlendiğini doğrular `mustUnderstand` ve bir özel durum oluşturur. `mustUnderstand`Alıcıya hedeflenen üst bilgiler içeren iletiler, alıcı uygulama kodu tarafından işlenmez.

Bu tür katmanlı işleme, altyapı katmanları ile SOAP düğümünün uygulama katmanları arasında ayrım yapılmasına izin verir:

- B1111: anlaşılmayan üstbilgiler, ileti WCF altyapı kanal yığını tarafından işlendikten sonra, ancak uygulama tarafından işlenmeden önce algılanır

     `mustUnderstand`Üstbilgi DEĞERI soap 1,1 Ile soap 1,2 arasında farklılık gösterir. Temel profil 1,1, `mustUnderstand` SOAP 1,1 iletileri için değerin 0 veya 1 olmasını gerektirir. SOAP 1,2, 0, 1, `false` ve değerlerine izin verir `true` , ancak değerlerin kurallı bir gösterimini `xs:boolean` (,) yaymanızı önerir `false` `true` .

- B1112: WCF SOAP `mustUnderstand` zarfının hem soap 1,1 hem de soap 1,2 sürümleri için 0 ve 1 değerlerini yayar. WCF, üst bilgi için tüm değer alanını kabul eder `xs:boolean` `mustUnderstand` (0, 1, `false` , `true` )

#### <a name="soap-faults"></a>SOAP hataları
WCF 'e özgü SOAP hata uygulamalarının listesi aşağıda verilmiştir.

- B2121: WCF şu SOAP 1,1 hata kodlarını döndürür: `s11:mustUnderstand` , `s11:Client` , ve `s11:Server` .

- B2122: WCF şu SOAP 1,2 hata kodlarını döndürür: `s12:MustUnderstand` , `s12:Sender` , ve `s12:Receiver` .

### <a name="http-binding"></a>HTTP bağlama

#### <a name="soap-11-http-binding"></a>SOAP 1,1 HTTP bağlama
WCF, aşağıdaki açıklığa kavuşturun temel profil 1,1 belirtim bölümünde 3,4 SOAP 1.1 HTTP bağlamasını uygular:

- B2211: WCF hizmeti HTTP POST isteklerinin yeniden yönlendirilmesini uygulamıyor.

- B2212: WCF istemcileri, 3.4.8 'e göre HTTP tanımlama bilgilerini destekler.

#### <a name="soap-12-http-binding"></a>SOAP 1,2 HTTP bağlama
WCF, SOAP 1,2-Part 2 (SOAP12Part2) belirtiminde aşağıda açıklandığı şekilde SOAP 1,2 HTTP bağlamasını uygular.

SOAP 1,2, medya türü için isteğe bağlı bir eylem parametresi sunmuştur `application/soap+xml` . Bu parametre, WS-Addressing kullanılmazsa SOAP iletisi gövdesinin ayrıştırılmasını gerektirmeden ileti gönderimi iyileştirmek için yararlıdır.

- R2221: `application/soap+xml` BIR SOAP 1,2 isteğinde mevcut olduğunda Action parametresi, `soapAction` `wsoap12:operation` karşılık gelen wsdl bağlamasının içindeki öğe özniteliğiyle eşleşmelidir.

- R2222: `application/soap+xml` BIR SOAP 1,2 iletisinde mevcut olduğunda Action parametresi, `wsa:Action` ws-Addressing 2004/08 veya ws-Addressing 1,0 kullanıldığında eşleşmelidir.

WS-Addressing devre dışı olduğunda ve gelen istek bir eylem parametresi içermiyorsa, ileti `Action` belirtilmemiş olarak kabul edilir.

## <a name="ws-addressing"></a>WS-Addressing
WCF, WS-Addressing 3 sürümünü uygular:

- WS-Addressing 2004/08

- W3C Web Hizmetleri adresleme 1,0 Core (ADDR10-CORE) ve SOAP Binding (ADDR10-SOAP)

- WS-Addressing 1,0-meta veriler

### <a name="endpoint-references"></a>Uç nokta başvuruları
WCF 'nin uyguladığı tüm WS-Addressing sürümleri uç noktaları tanımlayan uç nokta başvurularını kullanır.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Uç nokta başvuruları ve WS-Addressing sürümleri
WCF, WS-Addressing ve belirli bir `EndpointReference` öğe ve `W3C.WsAddressing.EndpointReferenceType` Sınıf (ÖRNEĞIN, WS-RELIABLEMESSAGING, ws-SecureConversation ve WS-Trust) kullanan bir dizi altyapı protokolünü uygular. WCF, diğer altyapı protokolleriyle her iki WS-Addressing sürümünün kullanımını destekler. WCF uç noktaları, uç nokta başına bir WS-Addressing sürümünü destekler.

R3111 için, `EndpointReference` BIR WCF uç noktası ile değiş tokuş edilen iletilerde kullanılan öğe veya tür için ad alanı, bu uç nokta tarafından uygulanan ws-Addressing sürümüyle aynı olmalıdır.

Örneğin, bir WCF uç noktası WS-ReliableMessaging ' i uygularsa, `AcksTo` içinde böyle bir uç nokta tarafından döndürülen üst bilgi, `CreateSequenceResponse` `EncodingBinding` Bu uç nokta IÇIN öğenin belirttiği ws-Addressing sürümünü kullanır.

#### <a name="endpoint-references-and-metadata"></a>Uç nokta başvuruları ve meta verileri
Bir dizi senaryo, belirli bir uç nokta için meta verilerin veya bir meta verilerin bir başvurusunun iletişim kurmasını gerektirir.

B3121: WCF, WS-MetadataExchange (MEX) belirtimi Bölüm 6 ' da açıklanan mekanizmaları kullanır. Bu, bir değere veya başvuruya göre uç nokta başvuruları için meta verileri içerir.

WCF hizmetinin, ' de belirteç veren tarafından verilen güvenlik onayları biçimlendirme dili (SAML) belirtecini kullanarak kimlik doğrulaması gerektirdiğini bir senaryoya göz önünde bulundurun `http://sts.fabrikam123.com` . WCF uç noktası `sp:IssuedToken` `sp:Issuer` , belirteç verene işaret eden iç içe onaylama ile onaylama kullanarak bu kimlik doğrulama gereksinimini açıklar. Onay işaretine erişen istemci uygulamaların `sp:Issuer` , belirteç verenin uç noktasıyla nasıl iletişim kuracağını bilmeleri gerekir. İstemcinin belirteç veren ile ilgili meta verileri bilmeleri gerekir. WCF 'de tanımlanan uç nokta başvurusu meta veri uzantılarını kullanarak WCF, belirteç verenin meta verilerine bir başvuru sağlar.

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a>İleti adresleme üstbilgileri

#### <a name="message-headers"></a>İleti üstbilgileri
Her iki ws-Addressing sürümünde, WCF,,, ve belirtimleri tarafından belirtilen aşağıdaki ileti üstbilgilerini `wsa:To` kullanır `wsa:ReplyTo` `wsa:Action` `wsa:MessageID` `wsa:RelatesTo` .

B3211: tüm WS-Addressing sürümleri Için WCF, ancak WS-Addressing ileti üst bilgilerini `wsa:FaultTo` ve `wsa:From` .

WCF uygulamalarıyla etkileşime geçen uygulamalar, bu ileti üstbilgilerini ekleyebilir ve WCF bunları uygun şekilde işleyebilir.

#### <a name="reference-parameters-and-properties"></a>Başvuru parametreleri ve özellikleri

WCF, ilgili belirtimlere uygun olarak uç nokta başvuru parametrelerinin ve başvuru özelliklerinin işlenmesini uygular.

B3221: WS-Addressing 2004/08 kullanacak şekilde yapılandırıldığında, WCF uç noktaları işleme başvuru özelliklerini ve başvuru parametrelerini ayırt etmez.

### <a name="message-exchange-patterns"></a>İleti değişimi desenleri
Web hizmeti işlem çağrısına dahil olan iletilerin sırası *ileti değişim düzeniyle*adlandırılır. WCF tek yönlü, istek-yanıt ve çift yönlü ileti değişimi düzenlerini destekler. Bu bölüm, kullanılan ileti değişimi düzenine bağlı olarak ileti işleme üzerindeki WS-Addressing gereksinimlerini açıklar.

Bu bölümün tamamında, istek sahibi ilk iletiyi gönderir ve yanıtlayanın ilk iletiyi alır.

#### <a name="one-way-message"></a>Tek yönlü Ileti
Bir WCF uç noktası, tek yönlü bir model izlemek için verilen iletileri destekleyecek şekilde yapılandırıldığında `Action` , WCF uç noktası aşağıdaki davranışları ve gereksinimleri izler. Aksi belirtilmediği takdirde, WCF 'de desteklenen her iki WS-Addressing sürümü için davranışlar ve kurallar geçerlidir:

- R3311: istek sahibi, `wsa:To` `wsa:Action` uç nokta başvurusu tarafından belirtilen tüm başvuru parametreleri için, ve üst bilgilerini içermelidir. WS-Addressing 2004/08 kullanıldığında ve [başvuru özellikleri] bitiş noktası başvurusuyla belirtildiğinde, ilgili üst bilgilerin iletiye de eklenmesi gerekir.

- B3312: talep eden `MessageID` , `ReplyTo` ve `FaultTo` üst bilgileri içerebilir. Alıcı altyapısı onları yoksayacak ve uygulamaya geçirilecektir.

- R3313: HTTP kullanıldığında ve HTTP yanıt baındaki bir ileti gönderilmediği zaman, yanıtlayanın boş bir gövdeye ve HTTP 202 durum koduna sahip bir HTTP yanıtı gönderebilmesi gerekir.

     HTTP taşıması kullanımda olduğunda ve işlem anlaşması bir ileti tek yönlü olarak bildirilse de, HTTP yanıtı altyapı iletilerini göndermek için kullanılabilir. Örneğin, güvenilir mesajlaşma, `SequenceAcknowledgement` HTTP yanıtına bir ileti gönderebilir.

- B3314: WCF Yanıtlayıcı, tek yönlü bir iletiye yanıt olarak hata iletisi göndermez.

#### <a name="request-reply"></a>İstek-Yanıt
Bir WCF uç noktası, `Action` istek-yanıt modelini izlemek için verilen bir ileti için yapılandırıldığında, WCF uç noktası aşağıdaki davranışları ve gereksinimleri izler. Aksi belirtilmediği takdirde, WCF 'de desteklenen her iki WS-Addressing sürümü için davranışlar ve kurallar geçerlidir:

- R3321: talep `wsa:To` `wsa:Action` eden, `wsa:MessageID` tüm başvuru parametreleri için istek,, ve üst bilgileri ve uç nokta başvurusu tarafından belirtilen başvuru özelliklerini (veya her ikisi) içermelidir.

- R3322: WS-Addressing 2004/08 kullanıldığında, `ReplyTo` isteğe da eklenmesi gerekir.

- R3323: WS-Addressing 1,0 kullanıldığında ve istekte yoksa `ReplyTo` , ' e eşit olan [address] özelliğine sahip bir varsayılan uç nokta başvurusu `http://www.w3.org/2005/08/addressing/anonymous` kullanılır.

- R3324: talep `wsa:To` `wsa:Action` eden, yanıt iletisindeki,, ve `wsa:RelatesTo` üst bilgilerin yanı sıra, `ReplyTo` istekteki uç nokta başvurusuyla belirtilen tüm başvuru parametreleri veya başvuru özellikleri (ya da her ikisi) için üst bilgiler içermelidir.

### <a name="web-services-addressing-faults"></a>Web Hizmetleri adresleme hataları
R3411: WCF, WS-Addressing 2004/08 tarafından tanımlanan aşağıdaki hataları üretir.

| Kod | Nedeni |
|----------|-----------|
| `wsa:DestinationUnreachable` | İleti, `ReplyTo` Bu kanal için belirlenen yanıt adresinden farklı bir ile ulaştı; bitiş üstbilgisinde belirtilen adreste dinleme yapan bir uç nokta yok. |
| `wsa:ActionNotSupported` | uç noktayla ilişkili altyapı kanalları veya dağıtıcı üst bilgide belirtilen eylemi tanımıyor `Action` . |

R3412: WCF, WS-Addressing 1,0 tarafından tanımlanan aşağıdaki hataları üretir.

| Kod | Nedeni |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | Yinelenen `wsa:To` , `wsa:ReplyTo` , `wsa:From` veya `wsa:MessageID` . `wsa:RelatesTo`Aynı ile yineleniyor `RelationshipType` . |
| `wsa10:MessageAddressingHeaderRequired` | Gerekli adresleme üst bilgisi eksik. |
| `wsa10:DestinationUnreachable` | İleti, `ReplyTo` Bu kanal için belirlenen yanıt adresinden farklı bir ile ulaştı. ' In üst bilgisinde belirtilen adreste dinleme yapan bir uç nokta yok. |
| `wsa10:ActionNotSupported` | Üst bilgide belirtilen bir eylem, `Action` uç noktayla ilişkili altyapı kanalları veya dağıtıcı tarafından tanınmıyor. |
| `wsa10:EndpointUnavailable` | RM kanalı bu hatayı geri gönderir ve uç noktanın, `CreateSequence` iletinin adres üst bilgilerinin incelenmesi için sırayı işlemeyeceğini belirtir. |

Yukarıdaki tablolardaki kod SOAP 1,2 ' de `FaultCode` soap 1,1 ve `SubCode` (Code = sender ile) ile eşlenir.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1,1 bağlama ve WS-Policy onayları

#### <a name="indicating-use-of-ws-addressing"></a>WS-Addressing kullanımını belirtir
WCF, belirli bir WS-Addressing sürümü için uç nokta desteğini göstermek üzere ilke onayları kullanır.

Aşağıdaki ilke onaylamanın uç nokta Ilkesi konusu [WS-PA] vardır ve uç noktadan gönderilen ve alınan iletilerin WS-Addressing 2004/08 kullanması gerektiğini gösterir.

```xml
<wsap:UsingAddressing />
```

Bu ilke onaylama işlemi WS-Addressing 2004/08 belirtimini genişletmelidir.

Aşağıdaki ilke onaylama işlemi, gönderilen/alınan iletilerin WS-Addressing 1,0 kullanması gerektiğini gösterir.

```xml
<wsam:Addressing/>
```

Aşağıdaki ilke onaylamanın bir uç nokta Ilkesi konusu [WS-PA] vardır ve uç noktadan gönderilen ve alınan iletilerin WS-Addressing 2004/08 kullanması gerektiğini gösterir.

```xml
<wsaw10:UsingAddressing />
```

`wsaw10:UsingAddressing`Öğesi [ws-Addressing-WSDL] öğesinden ödünç verilir ve bu belirtim, Bölüm 3.1.2 ile uyumlu WS-Policy bağlamında kullanılır.

Adresleme kullanımı, WSDL 1,1, SOAP 1,1 ve SOAP 1,2 HTTP bağlamalarının semantiğini değiştirmez. Örneğin, bir yanıtın, adresleme ve WSDL SOAP 1. x HTTP bağlama kullanan bir uç noktaya gönderilen bir istek olması bekleniyorsa, yanıt HTTP yanıtı kullanılarak gönderilmelidir.

Http yanıtı üzerinden gönderilen yanıtlar için, WS-har onaylama:

```xml
<wsam:AnonymousResponses/>
```

Tüm ilke onaylama işlemi şöyle görünebilir:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Bununla birlikte, istek sahibi ve Yanıtlayıcı arasında iki bağımsız listesiyse http bağlantısının (örneğin, Yanıtlayıcı tarafından gönderilen istenmeyen tek yönlü iletiler) olmasına yönelik ileti alışverişi desenleri bulunur.

WCF, iki temel taşıma kanalının bir kanalın giriş iletileri için kullanıldığı ve çıkış iletileri için kullanıldığı bir bileşik çift yönlü kanal oluşturmasının sağladığı bir özellik sunar. HTTP taşıması durumunda, bileşik çift yönlü iki listesiyse http bağlantısı sağlar. İstek sahibi, yanıtlaya ileti göndermek için bir bağlantı kullanır ve Yanıtlayıcı, iletileri istek sahibine geri göndermek için diğerini kullanır.

Ayrı http istekleri üzerinden gönderilen yanıtlar için, WS-har onaylama işlemi

```xml
<wsam:NonAnonymousResponses/>
```

Tüm ilke onaylama işlemi şöyle görünebilir:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

WSDL 1,1 SOAP 1. x http bağlamaları kullanan uç noktalarda uç nokta ilkesi konusunun [ws-PA] sahip olduğu aşağıdaki onaylama işleminin kullanılması, istek sahibinin, sırasıyla yanıtlayanın ve yanıtlayanın istek temelli olarak yanıtlamanın kullanıldığı iletiler için iki ayrı listesiyse http bağlantısı gerektirir.

```xml
<cdp:CompositeDuplex/>
```

Önceki ifade, istek iletileri üstbilgisinde aşağıdaki gereksinimlere yol gösterir `wsa:ReplyTo` :

- R3514: uç nokta `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` BIR WSDL 1,1 SOAP 1. x http bağlamasını kullanıyorsa ve ekli ile bağlanmış bir ilke alternatifi olan bir uç noktaya gönderilen istek iletilerinin, özelliği eşit olmayan bir üst bilgisine sahip olması gerekir `wsap10:UsingAddressing` `wsap:UsingAddressing` `cdp:CompositeDuplex` .

- R3515: bir uç nokta bir `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` `ReplyTo` WSDL 1,1 SOAP 1. x http bağlamasını kullanıyorsa ve bir ilke alternatifi `wsap10:UsingAddressing` ve onaylama ve onaylama olmadan bir ilke alternatifi `cdp:CompositeDuplex` varsa, bir uç noktaya gönderilen istek iletilerinin bir üst bilgisine sahip olması gerekir.

- R3516: uç nokta `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` BIR WSDL 1,1 SOAP 1. x HTTP bağlaması kullanıyorsa ve onaylama ve onaylama olmadan bir ilke alternatifi varsa, bir uç noktaya gönderilen istek iletilerinin bir özelliği olan bir üst bilgisine sahip olması gerekir `wsap:UsingAddressing` `cdp:CompositeDuplex` .

WS-Addressing WSDL belirtimi, `<wsaw:Anonymous/>` `wsa:ReplyTo` üst bilgide (Bölüm 3,2) üç metinsel değer içeren bir öğe (gerekli, isteğe bağlı ve yasaklanmış) girerek benzer protokol bağlamalarını açıklamaya çalışır. Ne yazık ki, bu tür öğe tanımı özellikle WS-Policy bağlamında bir onaylama işlemi olarak kullanılamaz, çünkü bu tür bir öğeyi onaylama olarak kullanma alternatiflerini desteklemek için etki alanına özgü uzantılar gerektirir. Bu tür öğe tanımı Ayrıca `ReplyTo` , ana hat üzerindeki uç nokta davranışına karşılık olarak, http taşımasına özel hale getiren üst bilgi değerini gösterir.

#### <a name="action-definition"></a>Eylem tanımı
WS-Addressing 2004/08 `wsa:Action` , öğeler için bir özniteliği tanımlar `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` . WS-Addressing 1,0 WSDL bağlama (WS-ADDR10-WSDL), benzer bir özniteliği tanımlar `wsaw10:Action` .

İkisi arasındaki tek fark, sırasıyla WS-ADDR 3.3.2 of WS-ADDR ve Section 4.4.4 bölümünde açıklanan varsayılan eylem deseninin semantiklerinden oluşur.

Aynı `portType` (veya aynı zamanda, WCF terminolojisinde olan), ancak farklı ws-Addressing sürümlerini kullanan iki uç nokta olması mantıklıdır. Ancak, bu eylem tarafından tanımlanır `portType` ve öğesini uygulayan uç noktalar genelinde değişmemelidir `portType` , her iki varsayılan eylem desenini desteklemek imkansız olur.

Bu Controversy 'yi çözmek için, WCF özniteliğin tek bir sürümünü destekler `Action` .

B3521: WCF, `wsaw10:Action` `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` `Action` uç nokta tarafından kullanılan ws-Addressing sürümünden bağımsız olarak, karşılık gelen iletiler için URI 'yi BELIRLEMEDE WS-ADDR10-WSDL ' d e tanımlanan öğeler üzerinde özniteliğini kullanır.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>WSDL bağlantı noktası Içinde uç nokta başvurusu kullan
WS-ADDR10-WSDL Bölüm 4,1, `wsdl:port` ÖĞEYI `<wsa10:EndpointReference…/>` ws-Addressing koşullarında bitiş noktasını tanımlayacak alt öğe içerecek şekilde genişletir. WCF, bu yardımcı programı WS-Addressing 2004/08 ' de genişleterek `<wsa:EndpointReference…/>` alt öğesi olarak görünmesine izin verir `wsdl:port` .

- R3531: bir uç nokta, ilke onaylama işlemi ile bağlı bir ilke alternatifi içeriyorsa `<wsaw10:UsingAddressing/>` , karşılık gelen `wsdl:port` öğe bir alt öğe içerebilir `<wsa10:EndpointReference …/>` .

- R3532: bir `wsdl:port` alt öğe içeriyorsa `<wsa10:EndpointReference …/>` , `wsa10:EndpointReference/wsa10:Address` alt öğe değeri `@address` eşdüzey öğenin özniteliğinin değeriyle eşleşmelidir `wsdl:port` / `wsdl:location` .

- R3533: bir uç nokta, ilke onaylama ile ilişkili bir ilke alternatifi içeriyorsa `<wsap:UsingAddressing/>` , karşılık gelen `wsdl:port` öğe bir alt öğe içerebilir `<wsa:EndpointReference …/>` .

- R3534: bir `wsdl:port` alt öğe içeriyorsa `<wsa:EndpointReference …/>` , `wsa:EndpointReference/wsa:Address` alt öğe değeri `@address` eşdüzey öğenin özniteliğinin değeriyle eşleşmelidir `wsdl:port` / `wsdl:location` .

### <a name="composition-with-ws-security"></a>WS-Security ile oluşturma
WS-ADDR ve WS-ADDR10 ' deki güvenlik değerlendirmesi bölümlerine göre, tüm adresleme ileti başlıklarının birlikte bağlamak için ileti gövdesinde birlikte imzalanması önerilir.

İleti bütünlüğü koruması için WS-Security kullanıldığında, WS-Addressing ileti üstbilgileri ve başvuru parametrelerinden veya özelliklerden (ya da her ikisi) kaynaklanan üstbilgilerin ileti gövdesinde birlikte imzalanması gerekir.

### <a name="examples"></a>Örnekler

#### <a name="one-way-message"></a>Tek yönlü Ileti
Bu senaryoda, gönderici alıcıya tek yönlü bir ileti gönderir. SOAP 1,2, HTTP 1,1 ve W3C WS-Addressing 1,0 kullanılır.

Istek Iletisi yapısı: ileti üstbilgileri `wsa10:To` ve `wsa10:Action` öğeleri. İleti gövdesi `<app:Ping>` , uygulama ad alanından belirli bir öğeyi içerir.

HTTP üstbilgileri: POSTADAKI hedef, öğesindeki URI ile eşleşir `wsa10:To` .

Content-Type üst bilgisinin `application/soap+xml` SOAP 1,2 için gereken şekilde değeri vardır. Parametreler `charset` ve `action` dahildir. `action`Content-Type üstbilgisinin parametresi, `wsa10:Action` ileti üstbilgisinin değeriyle eşleşir.

```http
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

Alıcı, boş bir HTTP yanıtı ve 202 durumu ile yanıt verir. HTTP yanıtına bir örnek:

```http
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a>SOAP Ileti Iletimi Iyileştirme mekanizması
Bu bölümde, HTTP SOAP MTOM için WCF uygulama ayrıntıları açıklanmaktadır. MTOM teknolojisi, geleneksel metin/XML kodlaması veya WCF Ikili kodlaması ile aynı sınıfın SOAP ileti kodlama mekanizmasıdır. MTOM şunları içerir:

- Base64 kodlamalı ikili verileri içeren XML bilgi öğelerini ayrı ikili parçalara ayıran XML kodlama ve paketleme mekanizması.

- XML bilgi kümesini ve XOP Package her bir ikili parçasını seri hale getirilen XOP paketini ayrı bir MIME bölümüne diztiren bir MIME kapsülleme.

- SOAP 1. x zarfı için uygulanan bir MIME XOP kodlaması.

- HTTP taşıma bağlaması.

WCF ile HTTP olmayan aktarımlarla MTOM kullanılması mümkündür. Bununla birlikte, bu konu başlığında HTTP 'ye odaklanacağız.

MTOM biçimi, MTOM kendisini, XOP ve MIME 'yi kapsayan büyük bir belirtim kümesi kullanır. Bu belirtim kümesinin modülerliği, tam gereksinimlerin biçim ve işleme semantiğinin yeniden ayarlanabilmesini oldukça zorlaştırır. Bu bölümde, MTOM HTTP bağlamasının biçim ve işleme gereksinimleri açıklanmaktadır.

### <a name="mtom-message-encoding"></a>MTOM Ileti kodlaması

#### <a name="generating-mtom-messages"></a>MTOM iletileri oluşturma
[XOP] Bölüm 3,1, bir soyut olarak tanımlanmış bir XOP Package içinde Base64 değerleri içeren öğe bilgi öğeleriyle XML kodlama işlemini açıklar.

Aşağıdaki adımlar dizisi, MTOM 'e özgü kodlama işlemini açıklar:

1. Kodlanacak SOAP zarfının, ve içeren bir öğe bilgisi öğesi olmadığından emin olun `[namespace name]` `http://www.w3.org/2004/08/xop/include` `[local name]` `Include` .

2. Boş bir MIME paketi oluşturun.

3. Özgün XML Infoset içinde, en iyi duruma getirilecek öğe bilgisi öğelerini belirleyin. Öğelerin en iyi duruma getirilmesi için, `[children]` öğe bilgileri öğesini oluşturan karakterlerin kurallı biçiminde olması gerekir `xs:base64Binary` (bkz. xsd-2, 3.2.16 base64Binary) ve boşluk olmayan veya sonrasında boşluk olmayan hiçbir boşluk karakteri içermemelidir.

4. Özgün SOAP zarfının bir kopyası olan bir XOP SOAP Zarfı oluşturun, ancak önceki adımda tanımlanan her öğe bilgi öğesinin alt öğeleri `xop:Include` aşağıdaki şekilde oluşturulmuş bir öğe bilgisi öğesiyle değiştirilmiştir:

    1. Değiştirilmiş karakterleri Base64 ile kodlanmış veriler olarak işleyerek ikili verilere dönüştürün.

    2. R3133 ve R3134 gereksinimlerini karşılayan benzersiz bir Içerik KIMLIĞI üst bilgisi değeri oluşturun.

    3. Binary değeri olan Content-Transfer-Encoding MIME üst bilgisi oluşturun.

    4. En iyi duruma getirilen öğe bilgisi öğesi (yeni eklenen öğe bilgileri öğesinin [üst] `xop:Include` ) bir `xmime:contentType` öznitelik bilgisi öğesi içeriyorsa, özniteliği değeri olan bir Content-Type MIME üst bilgisi oluşturun `xmime:contentType` .

    5. Base64 olarak işlenen ve adım 4d ' de oluşturulduysa, 4c 'den Content-Transfer-Encoding üst bilgisi, Content-Transfer-Encoding üst bilgisinden (örneğin,)

    6. `href` `xop:Include` Öğeye CID değeri olan bir öznitelik ekleyin: Adım 4B Içinde oluşturulan Content-ID üstbilgi değerinden türetilmiş URI. Kapsayan " \<" and "> " karakterlerini kaldırın, URL 'yi kalan dizeyi kaçış ve ön eki ekleme `cid:` . Aşağıdaki en küçük karakter kümesinin RFC1738 ve RFC2396 tarafından kaçılması gerekir. Diğer karakterlerin kaçışlı olması olabilir.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. 4. adımda XOP SOAP Zarfı ile bir kök MIME bölümü oluşturun.

6. HTTP Content-Type üst bilgisi dahil HTTP üst bilgilerini yazın.

7. MIME paketini yazın.

#### <a name="processing-mtom-messages"></a>MTOM iletilerini işleme
Bir MTOM iletisinin işlenmesi, önceki "MTOM iletileri oluşturma" bölümünde açıklanan işlemin tam tersidir:

1. Kök MIME bölümünün Içerik türüyle aynı olduğundan emin olun `application/xop+xml` .

2. Paketin kök MIME bölümünü bir XML belgesi olarak ayrıştırarak bir SOAP Zarfı oluşturun. Karakter kodlaması, `charset` kök MIME bölümünün Içerik türünün parametresine göre belirlenir.

3. Oluşturulan SOAP zarfının içindeki her öğe bilgi öğesi için, [children] özelliğinin tek üyesi olarak bir `xop:Include` öğe bilgisi öğesi olarak:

    1. Öneki kaldırın `cid:` ve öğenin özniteliği değerindeki tüm URI kaçış dizilerini (RFC 2396) kaldırın `@href` `xop:Include` . Sonuç dizesini "" içine alın \<", "> .

    2. Content-ID üst bilgisi değeri ile birlikte, adım 3A ' da türetilmiş dizeyle eşleşen MIME bölümünü bulun.

    3. `xop:Include`Her bir öğenin özelliğinde görünen öğe bilgisi öğesini, `children` adım 3b'de tanımlanan MIME bölümünün varlık gövdesinin (bkz. xsd-2, 3.2.16 base64Binary), adım 3B ' de tanımlanan MIME bölümünün varlık gövdesinin (bkz `xop:Include` ., öğe bilgileri öğesini paket bölümünden yeniden yapılandırılmış verilerle değiştirin

#### <a name="http-content-type-header"></a>HTTP Content-Type üst bilgisi
Aşağıda, MTOM belirtiminde belirtilen gereksinimlerden türetilmiş ve MTOM ve RFC 2387 ' den türetilen bir SOAP 1. x MTOM kodlu iletinin HTTP Content-Type üstbilgisinin biçimi için WCF açıklığa kavuşturininin bir listesi verilmiştir.

- R4131: bir HTTP Content-Type üst bilgisi, çok parçalı/ilgili (büyük/küçük harf duyarsız) ve parametrelerinin parametrelerine sahip olmalıdır. Parametre adları büyük/küçük harfe duyarlıdır. Parametre sırası önemli değil.

- MIME iletileri için Content-Type üstbilgisinin tam Backus-Naur form (BNF), RFC 2045, Bölüm 5,1 ' de listelenir.

- R4132: bir HTTP Content-Type üst bilgisinde `application/xop+xml` çift tırnak işareti içine alınmış değere sahip bir tür parametresi olmalıdır.

Çift tırnak işaretlerini kullanma gereksinimi RFC 2387 ' de açık olmadığından, büyük olasılıkla çok parçalı/ilgili medya türü parametrelerinin tümünün " \@ " veya "/" gibi ayrılmış karakterler içermesi ve bu nedenle çift tırnak işaretleri olması gerekir.

- R4133: bir HTTP Content-Type üst bilgisinde, çift tırnak işareti içine alınmış SOAP 1. x zarfı içeren MIME bölümünün Content-ID üstbilgisinin değeri ile bir start parametresi olmalıdır. Başlangıç parametresi atlanırsa, ilk MIME bölümünün SOAP 1. x zarfı içermesi gerekir.

- R4134: SOAP 1,1 MTOM kodlamalı bir ileti için bir HTTP Content-Type üst bilgisi, metin/xml değeri olan Start-Info parametresini çift tırnak işareti içine almalıdır.

- R4135: SOAP 1,2 MTOM kodlu bir ileti için bir HTTP Content-Type üst bilgisi, değeri çift tırnak içine alınmış olan Start-Info parametresini içermelidir `application/soap+xml` .

- R4136: bir SOAP 1. x MTOM kodlu ileti için HTTP Content-Type üst bilgisi, RFC 2046, Bölüm 5.1.1 ' de tanımlanan (çift tırnak işaretleri içine alınmış) bir sınır parametresine sahip olmalıdır.

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Örnekler:

     DÜZELTMEYE

    ```http
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     DÜZELTMEYE

    ```http
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     OLMAYAN

    ```http
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a>Bilgi kümesi MIME bölümü
SOAP 1. x zarfı, XOP MIME paketinin kök parçası olarak kapsüllenir ve genellikle bölüm olarak adlandırılır `infoset` .

- R4141: SOAP 1. x zarfı, ' ın parçası olarak adlandırılan `infoset` ve http Content-Type ' dan başvurulan, XOP MIME paketinin kök parçası olarak kapsüllenmelidir.

- R4142: SOAP `Infoset` bölümü AŞAĞıDAKI MIME üstbilgilerini içermelidir: `Content-ID` , `Content-Transfer-Encoding` , ve `Content-Type` .

Content-ID üstbilgisinin biçimi RFC 2045 tarafından şu şekilde tanımlanır

```
"Content-ID" ":" msg-id
```

`msg-id`, rfc 2822 ' de (rfc 2045 ' de başvurulur olan rfc 822 ' de bulunur) şu şekilde tanımlanır:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

ve "" içine alınmış etkin bir e-posta adresidir \<" and  "> . `[CFWS]`Ön ek ve sonek, açıklama taşımak IÇIN RFC 2822 ' ye eklenmiştir ve birlikte çalışabilirliği korumak için kullanılmamalıdır.

R4143: Infoset MIME bölümü için Content-ID üstbilgisinin değeri, `msg-id` RFC 2822 `[CFWS]` ' den ön ek ve sonek bölümleri atlanmalıdır.

"" İçinde bir e-posta adresi \<" and "> olması ve `absoluteURI` \<" , "> e-posta adresine ek olarak "" içinde kullanılması için "" içinde yer alan değer için gevşek gereksinimlere sahıp bir dizi MIME uygulaması. WCF 'nin bu sürümü, formun Content-ID MIME üstbilgisinin değerlerini kullanır:

```
Content-ID: <http://tempuri.org/0>
```

R4144: MTOM işlemcileri, aşağıdaki gevşek ile eşleşen Içerik KIMLIĞI üst bilgi değerlerini kabul etmelidir `msg-id` .

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045), MIME bölümünün içeriğinin kodlanmasını iletmek için Content-Transfer-Encoding üst bilgisini sağlar. Content-Transfer-Encoding için tanımlanan varsayılan değer 7 bittir, bu da çoğu SOAP iletisi için uygun değildir, bu nedenle daha fazla birlikte çalışabilirlik için Content-Transfer-Encoding üst bilgisi gereklidir:

- R4145: SOAP bilgi kümesi bölümü Content-Transfer-Encoding üst bilgisini içermelidir.

- R4146: SOAP Zarf karakter kodlaması UTF-8 ise Content-Transfer-Encoding üstbilgisinin değeri 8 bit olmalıdır.

- R4147: SOAP Zarf karakter kodlaması UTF-16 ise, Content-Transfer-Encoding üst bilgisinin değeri binary olmalıdır.

- [XOP] Bölüm 5 ' e göre,

- R4148: SOAP 1.1 Infoset bölümü, medya türü application/xop + xml ve Parameters Type = "text/xml" ve charset olan Content-Type üst bilgisi içermelidir

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: SOAP 1,2 Infoset bölümü, medya türü `application/xop+xml` ve parametre türü = "" olan Content-Type üst bilgisini içermelidir `application/soap+xml` `charset` .

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     XOP, için `charset` parametresini `application/xop+xml` isteğe bağlı olarak tanımladığında, `charset` medya türü için parametresindeki BP 1,1 gereksinimine benzer şekilde birlikte çalışabilirlik için bu gereklidir `text/xml` .

- R41410: `type` ve `charset` parametreleri soap 1. x Infoset bölümünün Content-Type üstbilgisinde bulunmalıdır.

#### <a name="wcf-endpoint-support-for-mtom"></a>MTOM için WCF uç noktası desteği
MTOM 'in amacı, Base64 kodlamalı verileri iyileştirmek için bir SOAP iletisi kodlayasağlamaktır. Kısıtlamaların listesi aşağıda verilmiştir:

- R4151: Base64 kodlamalı verileri içeren herhangi bir öğe bilgisi öğesi iyileştirilebilir.

- B4152: WCF, Base64 kodlamalı verileri içeren ve 1024 baytlık uzunluğu aşan öğe bilgisi öğelerini iyileştirir.

MTOM 'i kullanacak şekilde yapılandırılmış bir WCF uç noktası, her zaman MTOM kodlu iletiler gönderir. Gerekli ölçütlere uyan hiçbir bölüm olmasa bile, ileti hala MTOM kodlamalı (SOAP Zarfı içeren tek bir MIME parçası ile bir MIME paketi olarak serileştirilir).

### <a name="ws-policy-assertion-for-mtom"></a>MTOM için WS-Policy assertion
WCF, uç noktaya göre MTOM kullanımını göstermek için aşağıdaki ilke onayını kullanır:

```xml
<wsoma:OptimizedMimeSerialization />
```

- R4211: Yukarıdaki ilke onaylaması bir uç nokta Ilkesi konusuna sahiptir ve uç noktadan gönderilen ve alınan tüm iletilerin MTOM kullanılarak iyileştirildiğini belirtir.

- B4212: MTOM iyileştirmesi kullanacak şekilde yapılandırıldığında, bir WCF uç noktası karşılık gelen ilkeye bir MTOM Ilke onayı ekler `wsdl:binding` .

### <a name="composition-with-ws-security"></a>WS-Security ile oluşturma
MTOM, `text/xml` ve WCF IKILI XML 'e benzer bir kodlama mekanizmasıdır. MTOM, WS-Security ve diğer WS-* protokolleriyle doğal bileşim sunar: WS-Security kullanılarak güvenliği sağlanmış bir ileti, MTOM kullanılarak iyileştirilebilir.

### <a name="examples"></a>Örnekler

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>MTOM kullanılarak kodlanan WCF SOAP 1,1 Iletisi

```http
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>MTOM kullanılarak WCF güvenli SOAP 1,2 Iletisi kodlandı
Bu örnekte, bir ileti, MTOM ve WS-Security kullanılarak korunan SOAP 1,2 kullanılarak kodlanır. Kodlama için tanımlanan ikili parçalar, `BinarySecurityToken` `CipherValue` `EncryptedData` şifreli imzaya ve şifrelenmiş gövdeye karşılık gelen öğesinin içeriğidir. `CipherValue`Öğesinin `EncryptedKey` uzunluğu daha az 1024 bayt olduğu için WCF tarafından iyileştirmede tanımlanmadığını unutmayın.

```http
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml";
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```
