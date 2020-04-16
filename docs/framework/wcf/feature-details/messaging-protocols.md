---
title: Mesajlaşma Protokolleri
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 814347c77b54c4450aabf0a4f3966df223360663
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463825"
---
# <a name="messaging-protocols"></a>Mesajlaşma Protokolleri

Windows Communication Foundation (WCF) kanal yığını, dahili ileti gösterimini tel biçimine dönüştürmek ve belirli bir aktarım kullanarak göndermek için kodlama ve aktarım kanalları kullanır. Web hizmetleri birlikte çalışabilirlik için kullanılan en yaygın aktarım HTTP'dir ve Web hizmetleri tarafından kullanılan en yaygın kodlamalar XML tabanlı SOAP 1.1, SOAP 1.2 ve İleti İletim OptimizasyonU Mekanizması 'dır (MTOM).

Bu konu, aşağıdaki protokoller için WCF <xref:System.ServiceModel.Channels.HttpTransportBindingElement>uygulama ayrıntılarını kapsamaktadır.

Belirtim/belge:

- [HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [SOAP 1.1 HTTP Ciltleme](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Bölüm 7
- [SOAP 1.2 HTTP Ciltleme](https://www.w3.org/TR/soap12-part2) Bölüm 7

Bu konu, aşağıdaki protokoller için WCF uygulama ayrıntılarını kapsar <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanır.

Şartname/Belge:

- [Xml](https://www.w3.org/TR/REC-xml)
- [SABUN 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [SOAP 1.2 Çekirdek](https://www.w3.org/TR/soap12-part1/)
- [WS-Adresleme 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [W3C Web Hizmetleri Adresleme 1.0 - Çekirdek](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [W3C Web Hizmetleri Adresleme 1.0 - SOAP Bağlama](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [W3C Web Hizmetleri Adresleme 1.0 - WSDL Bağlama](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [W3C Web Hizmetleri Adresleme 1.0 - Metadata](https://www.w3.org/TR/ws-addr-metadata/)
- [WSDL SOAP1.1 Ciltleme](https://www.w3.org/TR/wsdl/)
- [WSDL SOAP1.2 Bağlama](https://www.w3.org/Submission/wsdl11soap12/)

Bu konu, <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> aşağıdaki protokoller için WCF uygulama ayrıntılarını kapsar.

Belirtim/belge:

- [XOP](https://www.w3.org/TR/xop10/)
- [MTOM + SABUN 1.2 Bağlama](https://www.w3.org/TR/soap12-mtom/)
- [MTOM SABUN 1.1 Ciltleme](https://www.w3.org/Submission/soap11mtom10/)
- [MTOM WS-Politika İddiası](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

Bu konu boyunca aşağıdaki XML ad alanları ve ilişkili önekler kullanılır:

| Ön ek | Namespace Uniform Resource Tanımlayıcı (URI) |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| s12 |`http://www.w3.org/2003/05/soap-envelope` |
| Wsa |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| xop |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| Dp |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>SABUN 1.1 ve SABUN 1.2

### <a name="envelope-and-processing-model"></a>Zarf ve İşleme Modeli
WCF, Temel Profil 1.1 (BP11) ve Temel Profil 1.0 'dan (SSBP10) sonra SOAP 1.1 zarf işleme uygular. SOAP 1.2 Zarf işleme, SOAP12-Part1'den sonra uygulanır.

Bu bölümde, WCF tarafından BP11 ve SOAP12-Part1 ile ilgili olarak alınan bazı uygulama seçenekleri açıklanmaktadır.

#### <a name="mandatory-header-processing"></a>Zorunlu Üstbilgi İşleme
WCF, SOAP 1.1 `mustUnderstand` ve SOAP 1.2 belirtimlerinde açıklanan başlıkların işlenmesi için aşağıdaki varyasyonlarla birlikte kurallara uyar.

WCF kanal yığınına giren bir ileti, Metin İleti Kodlaması, Güvenlik, Güvenilir İleti ve Hareketler gibi ilişkili bağlama öğeleri tarafından yapılandırılan tek tek kanallar tarafından işlenir. Her kanal ilişkili ad alanından üstbilgi tanır ve anlaşıldığı şekilde işaretler. İleti sevk irsaliyesi girdikten sonra, ilgili ileti/işlem sözleşmesitarafından beklenen üstleri okur ve anlaşıldı işaretler. Daha sonra, kalan üstbilginin anlaşılmadığını ancak özel `mustUnderstand` durum olarak işaretlenip işaretlenmediğini doğrular. Alıcıyı hedefleyen `mustUnderstand` üstbilgileri içeren iletiler alıcı uygulama kodu tarafından işlenmez.

Bu tür katmanlı işleme altyapı katmanları ve SOAP düğümü uygulama katmanları arasında ayrım sağlar:

- B1111: İleti WCF altyapı kanalı yığını tarafından işlendikten sonra ancak uygulama tarafından işlenmeden önce anlaşılamayan üstbilgi algılanır

     `mustUnderstand` Başlık değeri SOAP 1.1 ile SOAP 1.2 arasında farklılık gösterir. Temel Profil 1.1, `mustUnderstand` SOAP 1.1 iletileri için değerin 0 veya 1 olmasını gerektirir. SOAP 1.2, 0, `false`1 `true` ve değerler olarak izin verir, ancak değerlerin `xs:boolean` kanonik bir temsilini yayan önerir (`false`, `true`).

- B1112: WCF, `mustUnderstand` SOAP zarfının SOAP 1.1 ve SOAP 1.2 versiyonları için 0 ve 1 değerlerini yayır. `xs:boolean` WCF `mustUnderstand` üstbilgi için tüm değer alanını kabul eder `false`(0, 1, , `true`)

#### <a name="soap-faults"></a>SABUN Arızaları
Aşağıda WCF'ye özgü SOAP hata uygulamalarının bir listesi verem.

- B2121: WCF aşağıdaki SOAP 1.1 `s11:mustUnderstand`Arıza `s11:Client`Kodları `s11:Server`döndürür: , , ve .

- B2122: WCF aşağıdaki SOAP 1.2 `s12:MustUnderstand`Arıza `s12:Sender`Kodları `s12:Receiver`döndürür: , , ve .

### <a name="http-binding"></a>HTTP Ciltleme

#### <a name="soap-11-http-binding"></a>SOAP 1.1 HTTP Ciltleme
WCF aşağıdaki açıklamalar ile Temel Profil 1.1 belirtimi bölüm 3.4 aşağıdaki SOAP1.1 HTTP bağlama uygular:

- B2211: WCF hizmeti HTTP POST isteklerinin yeniden yönlendirilmesi uygulamaz.

- B2212: WCF müşterileri HTTP Çerezleri'ni 3.4.8 uyarınca destekler.

#### <a name="soap-12-http-binding"></a>SOAP 1.2 HTTP Ciltleme
WCF aşağıdaki açıklamalar ile SOAP 1.2-part 2 (SOAP12Part2) belirtiminde açıklandığı gibi SOAP 1.2 HTTP bağlama uygular.

SOAP `application/soap+xml` 1.2, ortam türü için isteğe bağlı bir eylem parametresi tanıttı. Bu parametre, WS-Adresleme kullanılmadığında SOAP iletisinin gövdesinin ayrıştırılmasına gerek kalmadan ileti gönderimi optimize etmek için yararlıdır.

- R2221: `application/soap+xml` Bir SOAP 1.2 isteğinde mevcut olduğunda eylem `soapAction` parametresi, `wsoap12:operation` ilgili WSDL bağlama içindeki öğedeki öznitelikle eşleşmelidir.

- R2222: `application/soap+xml` Bir SOAP 1.2 iletisi üzerinde mevcut `wsa:Action` olduğunda, ws-Adresleme 2004/08 veya WS-Adresleme 1.0 kullanıldığında eylem parametresi eşleşmelidir.

WS Adresi devre dışı bırakıldığında ve gelen istek bir eylem `Action` parametresi içermiyorsa, ileti belirtilmemiş olarak kabul edilir.

## <a name="ws-addressing"></a>WS-Adresleme
WCF WS-Adresleme 3 sürümleri uygular:

- WS-Adresleme 2004/08

- W3C Web Hizmetleri Adresleme 1.0 Çekirdekli (ADDR10-CORE) ve SABUN Bağlama (ADDR10-SOAP)

- WS-Adresleme 1.0 - Meta veriler

### <a name="endpoint-references"></a>Bitiş Noktası Referansları
WCF'nin uyguladığı WS Adresi'nin tüm sürümleri uç noktaları açıklamak için uç nokta başvurularını kullanır.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Uç Nokta Referansları ve WS Adresleme Sürümleri
WCF, WS-Addressing'i ve özellikle `EndpointReference` öğeve `W3C.WsAddressing.EndpointReferenceType` sınıfı (örneğin, WS-ReliableMessaging, WS-SecureConversation ve WS-Trust) kullanan bir dizi altyapı protokolünü uygular. WCF, WS-Addressing'in her iki sürümünün de diğer altyapı protokolleriyle kullanımını destekler. WCF uç noktaları, bitiş noktası başına WS adreslemenin bir sürümünü destekler.

R3111 için, WCF `EndpointReference` bitiş noktasıyla değiştirilen iletilerde kullanılan öğe veya tür için ad alanı, bu bitiş noktası tarafından uygulanan WS-Adresleme sürümüyle eşleşmelidir.

Örneğin, bir WCF bitiş noktası WS-ReliableMessaging `AcksTo` uygularsa, üstbilgi içinde `CreateSequenceResponse` böyle bir bitiş noktası `EncodingBinding` tarafından döndürülen öğe, bu bitiş noktası için belirttiği WS Adresleme sürümünü kullanır.

#### <a name="endpoint-references-and-metadata"></a>Uç Nokta Referansları ve Meta veriler
Bir dizi senaryo, belirli bir bitiş noktası için meta verilerin iletişimini veya meta verilere başvuruyu gerektirir.

B3121: WCF, WS-MetadataExchange (MEX) belirtiminde Bölüm 6'da açıklanan mekanizmaları, değer veya referans olarak uç nokta referansları için meta verileri içerecek şekilde kullanır.

Bir WCF hizmetinin, belirteç veren kuruluş tarafından verilen Güvenlik İddiaları İşaretleyici Dili (SAML) belirteci kullanarak kimlik doğrulaması gerektirdiği bir senaryo `http://sts.fabrikam123.com`düşünün. WCF bitiş noktası belirteç veren `sp:IssuedToken` işaret eden `sp:Issuer` iç içe bir setir ile iddia kullanarak bu kimlik doğrulama gereksinimi açıklar. `sp:Issuer` Sermesi erişen istemci uygulamaları, belirteç veren bitiş noktasıyla nasıl iletişim kuracağını bermesi gerekir. İstemcinin belirteç veren hakkında meta verileri bilmesi gerekir. WCF, MEX'te tanımlanan uç nokta referans meta veri uzantılarını kullanarak belirteç veren meta verilerine bir başvuru sağlar.

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

### <a name="message-addressing-headers"></a>İleti Adresleme Üstbilgileri

#### <a name="message-headers"></a>İleti Üstbilgi
WCF, her iki WS Adresleme sürümü için, `wsa:To`belirtimler , `wsa:ReplyTo` `wsa:Action`, `wsa:MessageID`, `wsa:RelatesTo`ve .

B3211: Tüm WS Adresleme sürümleri için, WCF onur, ancak kutunun dışında üretmek değil, `wsa:FaultTo` `wsa:From`WS-Adresleme ileti üstbilgileri ve .

WCF uygulamalarıyla etkileşimedebilen uygulamalar bu ileti üstbilgilerini ekleyebilir ve WCF bunları buna göre işleyebilir.

#### <a name="reference-parameters-and-properties"></a>Referans Parametreleri ve Özellikleri

WCF, uç nokta referans parametrelerinin ve referans özelliklerinin ilgili spesifikasyonlara uygun olarak işlenmesini uygular.

B3221: WS-Addressing 2004/08'i kullanacak şekilde yapılandırıldığında, WCF uç noktaları başvuru özelliklerini işleme ve Referans Parametreleri arasında ayrım yapmaz.

### <a name="message-exchange-patterns"></a>İleti Değişim Desenleri
Web hizmeti işlemi çağırmasında yer alan iletilerin sırası *ileti alışverişi deseni*olarak adlandırılır. WCF tek yönlü, istek-yanıt ve çift yönlü ileti alışverişi modellerini destekler. Bu bölümde, kullanılan ileti alışverişi desenine bağlı olarak ileti işlemede WS-Adresleme gereksinimleri açıklamaktadır.

Bu bölüm boyunca, istekte bulundurucu ilk iletiyi gönderir ve yanıtlayan ilk iletiyi alır.

#### <a name="one-way-message"></a>Tek Yönlü İleti
Bir WCF bitiş noktası, tek yönlü bir `Action` desen izlemek için verilen iletileri destekleyecek şekilde yapılandırıldığında, WCF bitiş noktası aşağıdaki davranışları ve gereksinimleri izler. Aksi belirtilmedikçe, WCF'de desteklenen WS-Addressing'in her iki sürümü için de davranışlar ve kurallar geçerlidir:

- R3311: İstekli, `wsa:To`bitiş `wsa:Action`noktası referansı tarafından belirtilen tüm başvuru parametreleri için , ve üstbilgi içermelidir. WS Adresi 2004/08 kullanıldığında ve [başvuru özellikleri] bitiş noktası referansı yla belirtildiğinde, ilgili üstbilginin de iletiye eklenmesi gerekir.

- B3312: İstekli , `MessageID` `ReplyTo`ve `FaultTo` üstbilgi içerebilir. Alıcı altyapısı bunları yok sayacak ve uygulamaya geçirilecek.

- R3313: HTTP kullanıldığında ve HTTP yanıt bacağına mesaj gönderilmediğinde, yanıtlayan boş bir gövde ve HTTP 202 durum kodu içeren bir HTTP yanıtı göndermelidir.

     HTTP aktarım ı kullanımda olduğunda ve işlem sözleşmesi tek yönlü bir ileti beyan ettiğinde, HTTP yanıtı yine de altyapı `SequenceAcknowledgement` iletileri göndermek için kullanılabilir(örneğin, güvenilir ileti bir HTTP yanıtı na ileti gönderebilir).

- B3314: WCF yanıtlayıcısı tek yönlü bir iletiye yanıt olarak hata iletisi göndermez.

#### <a name="request-reply"></a>İstek-Yanıt
Bir WCF bitiş noktası, istek yanıtı `Action` deseni izlemek için verilen bir ileti için yapılandırıldığında, WCF bitiş noktası aşağıdaki davranışları ve gereksinimleri izler. Aksi belirtilmedikçe, WCF'de desteklenen WS-Addressing'in her iki sürümü için de davranışlar ve kurallar geçerlidir:

- R3321: İstekli, bitiş noktası `wsa:To` `wsa:Action`referansı tarafından belirtilen tüm başvuru parametreleri veya başvuru özellikleri (veya her ikisi) için istek, `wsa:MessageID`ve üstbilgi içermelidir.

- R3322: WS-Adresleme 2004/08 kullanıldığında, `ReplyTo` isteğe de dahil edilmelidir.

- R3323: WS-Adresleme 1.0 kullanıldığında `ReplyTo` ve istekte bulunmadığında, [adres] özelliğine `http://www.w3.org/2005/08/addressing/anonymous` eşit olan varsayılan uç nokta başvurusu kullanılır.

- R3324: İstekli, `wsa:To`yanıt `wsa:Action`iletisinde üstbilgi ve `wsa:RelatesTo` üstbilginin yanı sıra istekteki `ReplyTo` bitiş noktası referansı tarafından belirtilen tüm başvuru parametreleri veya başvuru özellikleri (veya her ikisi) için üstbilgi içermelidir.

### <a name="web-services-addressing-faults"></a>Hataları Gideren Web Hizmetleri
R3411: WCF, WS-Addressing 2004/08 tarafından tanımlanan aşağıdaki hataları üretir.

| Kod | Nedeni |
|----------|-----------|
| `wsa:DestinationUnreachable` | İleti, bu `ReplyTo` kanal için kurulan yanıt adresinden farklı bir iletiyle geldi; To üstbilgisinde belirtilen adreste son nokta dinleme yoktur. |
| `wsa:ActionNotSupported` | bitiş noktasıyla ilişkili altyapı kanalları veya sevk `Action` irsaliyesi üstbilgide belirtilen eylemi tanımaz. |

R3412: WCF, WS-Adresleme 1.0 tarafından tanımlanan aşağıdaki hataları üretir.

| Kod | Nedeni |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | Yinelenen `wsa:To` `wsa:ReplyTo`, `wsa:From` `wsa:MessageID`veya . Aynı `wsa:RelatesTo` `RelationshipType`ile yinelenen . |
| `wsa10:MessageAddressingHeaderRequired` | Gerekli Adresleme üstbilgisi eksik. |
| `wsa10:DestinationUnreachable` | İleti, bu `ReplyTo` kanal için kurulan yanıt adresinden farklı bir iletiyle geldi. To başlığında belirtilen adreste bitiş noktası dinleme yoktur. |
| `wsa10:ActionNotSupported` | `Action` Üstbilgide belirtilen bir eylem, bitiş noktasıyla ilişkili altyapı kanalları veya gönderen tarafından tanınmaz. |
| `wsa10:EndpointUnavailable` | RM kanalı, bitiş noktasının `CreateSequence` iletinin adreslenen üstbilgileri incelenerek diziyi işlemeyeceğini belirten bu hatayı geri gönderir. |

Önceki tablolardaki kod, `FaultCode` SOAP 1.1'e ve `SubCode` (Code=Sender ile) SOAP 1.2'ye eşler.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 Bağlayıcı ve WS-İlke İddiaları

#### <a name="indicating-use-of-ws-addressing"></a>WS-Adresleme kullanımını gösteren
WCF, belirli bir WS Adresleme sürümü için uç nokta desteğini belirtmek için ilke iddialarını kullanır.

Aşağıdaki ilke iddiasında Endpoint İlkesi Konusu [WS-PA] vardır ve uç noktadan gönderilen ve alınan iletilerin WS-Addressing 2004/08'i kullanması gerektiğini gösterir.

```xml
<wsap:UsingAddressing />
```

Bu ilke iddiası WS-Adresleme 2004/08 belirtimini genişletiyor.

Aşağıdaki ilke iddiası, gönderilen/alınan iletilerin WS Adresi 1.0'ı kullanması gerektiğini gösterir.

```xml
<wsam:Addressing/>
```

Aşağıdaki ilke iddiasının bir Bitiş Noktası İlkesi Konusu [WS-PA] vardır ve son noktadan gönderilen ve alınan iletilerin WS Adresi 2004/08'i kullanması gerektiğini gösterir.

```xml
<wsaw10:UsingAddressing />
```

Öğe `wsaw10:UsingAddressing` [WS-Addressing-WSDL] ödünç ve bu belirtim, bölüm 3.1.2 uygun olarak WS-Politikası bağlamında kullanılır.

Adresleme nin kullanımı WSDL 1.1, SOAP 1.1 ve SOAP 1.2 HTTP Ciltlemelerinin anlambilimini değiştirmez. Örneğin, Adresleme ve WSDL SOAP 1.x HTTP bağlama kullanan bir bitiş noktasına gönderilen bir isteğe yanıt bekleniyorsa, yanıt HTTP yanıtı kullanılarak gönderilmelidir.

http yanıtı üzerinden gönderilen yanıtlar için WS-AM iddiası:

```xml
<wsam:AnonymousResponses/>
```

Tam ilke iddiası aşağıdaki gibi görünebilir:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Ancak, istekte veren ve yanıtlayan arasında iki bağımsız converse HTTP bağlantısı nın kurulmasından yararlanan ileti alışverişi desenleri vardır, örneğin, yanıtlayan tarafından gönderilen istenmeyen tek yönlü iletiler.

WCF, bir kanalın giriş iletileri için, diğerinin çıkış iletileri için kullanıldığı bir Bileşik Çift Yönlü kanal oluşturabileceği bir özellik sunar. HTTP Transport durumunda, Bileşik Çift yönlü iki converse HTTP bağlantısı sağlar. İstekçi, yanıtlayana ileti göndermek için bir bağlantı kullanır ve yanıtlayan diğerini iletileri istekte bulunduracak şekilde kullanır.

Ayrı http istekleri üzerinden gönderilen yanıtlar için ws-am iddiası

```xml
<wsam:NonAnonymousResponses/>
```

Tam ilke iddiası aşağıdaki gibi görünebilir:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

WSDL 1.1 SOAP 1.x HTTP ciltlerini kullanan uç noktalarda Uç Nokta Politikası Konusu [WS-PA] bulunan aşağıdaki iddianın kullanımı, istektebulunaniletiden yanıtlayana ve yanıtlayana giden iletilere akan iletiler için sırasıyla iki ayrı converse HTTP bağlantısı nın kullanılmasını gerektirir.

```xml
<cdp:CompositeDuplex/>
```

Önceki deyim, istek iletileri `wsa:ReplyTo` için üstbilgide aşağıdaki gereksinimlere yol açar:

- R3514: Bitiş noktası WSDL 1.1 SOAP `[address]` 1.x `http://www.w3.org/2005/08/addressing/anonymous` HTTP bağlama kullanıyorsa ve `wsap10:UsingAddressing` `wsap:UsingAddressing` `cdp:CompositeDuplex` ekli bir veya bir leştirilmiş bir ilke alternatifi varsa, bitiş noktasına gönderilen istek iletilerinin özelliğine eşit olmayan bir `ReplyTo` üstbilgi olmalıdır.

- R3515: `ReplyTo` Bitiş noktasına `[address]` gönderilen istek iletilerinin, bitiş noktası WSDL 1.1 SOAP 1.x HTTP bağlayıcısı kullanıyorsa ve `http://www.w3.org/2005/08/addressing/anonymous` `ReplyTo` `wsap10:UsingAddressing` iddia ve hiçbir `cdp:CompositeDuplex` iddiaekli bir ilke alternatifi varsa, özelliği ne eşit sayılsa da hiç üstbilgi içermemelidir.

- R3516: Bitiş noktası WSDL 1.1 SOAP `[address]` 1.x `http://www.w3.org/2005/08/addressing/anonymous` HTTP bağlama kullanıyorsa ve iddia içeren `wsap:UsingAddressing` ve hiçbir `cdp:CompositeDuplex` iddiaekli bir ilke alternatifi varsa, bitiş noktasına eşit bir özelliğe sahip bir `ReplyTo` üstbilgi olmalıdır.

WS adresi WSDL belirtimi, `<wsaw:Anonymous/>` `wsa:ReplyTo` üstbilgideki gereksinimleri (bölüm 3.2) belirtmek için üç metin değeri (gerekli, isteğe bağlı ve yasak) olan bir öğe tanıtarak benzer iletişim kuralı bağlamalarını açıklamaya çalışır. Ne yazık ki, bu tür öğe tanımı, ws-policy bağlamında bir iddia olarak özellikle kullanılabilir değildir, çünkü bir iddia olarak böyle bir öğeyi kullanarak alternatiflerin kesişim desteklemek için etki alanına özgü uzantıları gerektirir. Bu tür öğe tanımı, `ReplyTo` telüzerindeki bitiş noktası davranışının aksine üstbilginin değerini de gösterir ve bu da onu HTTP aktarımına özgü kılar.

#### <a name="action-definition"></a>Eylem Tanımı
WS-Adresleme 2004/08 `wsa:Action` `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` öğeleri için bir öznitelik tanımlar. WS Adresi 1.0 WSDL Bağlama (WS-ADDR10-WSDL) benzer bir `wsaw10:Action`öznitelik tanımlar.

İkisi arasındaki tek fark, WS-ADDR'ın 3.3.2 bölümünde ve sırasıyla WS-ADDR10-WSDL'nin 4.4.4 bölümünde açıklanan varsayılan Eylem deseni semantikleridir.

Ws-Addressing'in farklı sürümlerini kullanarak `portType` aynı (veya sözleşme, WCF terminolojisinde) aynı payı paylaşan iki uç noktaolması makul bir durumdur. Ancak, Eylem tarafından tanımlandığı `portType` ve uygulayan uç noktalar arasında `portType`değişmemesi gerektiği göz önüne alındığında, her iki varsayılan eylem desenlerini de desteklemek imkansız hale gelir.

Bu sorunu çözmek için WCF özniteliğin `Action` tek bir sürümünü destekler.

B3521: WCF, `wsaw10:Action` bitiş `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` noktası tarafından kullanılan WS Adresleme sürümünden bağımsız olarak `Action` ilgili iletiler için URI'yi belirlemek için WS-ADDR10-WSDL'de tanımlanan öğeler üzerindeki özniteliği kullanır.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>WSDL Bağlantı Noktası İçinde Uç Nokta Referansı Kullanma
WS-ADDR10-WSDL bölüm 4.1, `wsdl:port` bitiş noktasını `<wsa10:EndpointReference…/>` WS-Adresleme terimleriyle açıklamak için alt öğeyi içerecek şekilde öğeyi genişletir. WCF WS-Adresleme 2004/08 bu yardımcı programı `<wsa:EndpointReference…/>` genişletir, bir `wsdl:port`alt öğe olarak görünmesini sağlar.

- R3531: Bir uç nokta, bir ilke `<wsaw10:UsingAddressing/>` iddiası ile `wsdl:port` ekli bir ilke `<wsa10:EndpointReference …/>`alternatifi varsa, karşılık gelen öğe bir alt öğe içerebilir.

- R3532: Bir `wsdl:port` alt öğe `<wsa10:EndpointReference …/>` `wsa10:EndpointReference/wsa10:Address` içeriyorsa, alt öğe değeri `@address` kardeş `wsdl:port` / `wsdl:location` öğenin özniteliğinin değeriyle eşleşmelidir.

- R3533: Bir uç nokta ilke iddiası `<wsap:UsingAddressing/>` ile ekli `wsdl:port` bir ilke alternatifi varsa, karşılık gelen öğe bir alt öğe `<wsa:EndpointReference …/>`içerebilir.

- R3534: Bir `wsdl:port` alt öğe `<wsa:EndpointReference …/>` `wsa:EndpointReference/wsa:Address` içeriyorsa, alt öğe değeri `@address` kardeş `wsdl:port` / `wsdl:location` öğenin özniteliğinin değeriyle eşleşmelidir.

### <a name="composition-with-ws-security"></a>WS-Security ile kompozisyon
WS-ADDR ve WS-ADDR10'daki güvenlik konuları bölümlerine göre, tüm adresleme ileti üstbilgileri, ileti gövdesi ile birlikte imzalanmalı ve bunları birbirine bağlar.

İleti bütünlüğü koruması için WS-Security kullanıldığında, başvuru parametreleri veya özelliklerinden (veya her ikisinden) kaynaklanan WS Adresleme ileti üstbilgileri ve üstbilgileri iletişin gövdesi ile birlikte imzalanmalıdır.

### <a name="examples"></a>Örnekler

#### <a name="one-way-message"></a>Tek Yönlü İleti
Bu senaryoda, gönderen alıcıya tek yönlü bir ileti gönderir. SOAP 1.2, HTTP 1.1 ve W3C WS-Adresleme 1.0 kullanılır.

İstek İletisi Yapısı: İleti `wsa10:To` `wsa10:Action` üstbilgisi ve öğeleri içerir. İleti gövdesi, uygulama `<app:Ping>` ad alanından belirli bir öğe içerir.

HTTP Başlıklar: POST'taki `wsa10:To` hedef, öğedeki URI ile eşleşir.

İçerik Türü üstbilgi, SOAP `application/soap+xml` 1.2'nin gerektirdiği değere sahiptir. Parametreler `charset` `action` ve dahildir. İçerik `action` Türü üstbilginin parametresi ileti üstbilgisinin değeriyle `wsa10:Action` eşleşir.

```
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

Alıcı boş bir HTTP yanıtı ve durum 202 ile yanıt verir. HTTP yanıtı bir örnek:

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a>SOAP İleti İleti optimizasyonu Mekanizması
Bu bölümde HTTP SOAP MTOM için WCF uygulama ayrıntıları açıklanmaktadır. MTOM teknolojisi, geleneksel metin/XML kodlama veya WCF İkili kodlama ile aynı sınıfın SOAP ileti kodlama mekanizmasıdır. MTOM aşağıdakileri içerir:

- Base64 kodlanmış ikili verileri içeren XML bilgi öğelerini ayrı ikili parçalarhalinde optimize eden [XOP] tarafından açıklanan bir XML kodlama ve paketleme mekanizması.

- XML Bilgi Seti'ni ve XOP paketinin her ikili parçasını ayrı bir MIME parçasına serileştiren XOP paketinin MIME kapsüllemi.

- SOAP 1.x Zarf'a uygulanan bir MIME XOP kodlaması.

- Bir HTTP aktarım bağlama.

MTOM'u WCF ile HTTP dışı taşımalarla kullanmak mümkündür. Ancak, bu konuda biz HTTP üzerinde durulacak.

MTOM biçimi, MTOM'un kendisini, XOP'u ve MIME'yi kapsayan geniş bir belirtim kümesinden yararlanır. Bu belirtim kümesinin modülerliği, biçim ve işleme semantikleri üzerinde tam gereksinimleri yeniden yapılandırmayı biraz zorlaştırır. Bu bölümde MTOM HTTP bağlama için biçim ve işleme gereksinimleri açıklanmaktadır.

### <a name="mtom-message-encoding"></a>MTOM İleti Kodlama

#### <a name="generating-mtom-messages"></a>MTOM iletileri oluşturma
[XOP] bölüm 3.1 soyut tanımlanmış bir XOP paketine base64 değerleri içeren eleman bilgi öğeleri ile XML kodlama işlemini açıklar.

Aşağıdaki adım sırası MTOM'a özgü kodlama işlemini açıklar:

1. Kodlanacak SOAP Zarfının `[namespace name]` a `http://www.w3.org/2004/08/xop/include` ve a `[local name]` ile hiçbir öğe bilgi `Include`öğesi içermediğinden emin olun.

2. Boş bir MIME paketi oluşturun.

3. Orijinal XML Bilgi Seti içinde en iyi duruma getirilecek öğe bilgi öğelerini tanımlayın. Öğelerin optimize edilememesi için, öğe bilgi `[children]` öğesinin oluşturan karakterlerin kanonik biçiminde `xs:base64Binary` olması gerekir (bkz. XSD-2, 3.2.16 base64Binary) ve beyaz alan içeriğinden önce, satır da veya aşağıdaki herhangi bir beyaz boşluk karakteri içermemelidir.

4. Orijinal SOAP Zarfının bir kopyası olan, ancak önceki adımda tanımlanan her öğebilgi öğesinin çocuklarıyla `xop:Include` birlikte aşağıdaki gibi oluşturulmuş bir öğe bilgi öğesi ile değiştirilen bir XOP SOAP Zarfı oluşturun:

    1. Değiştirilen karakterleri temel 64 kodlanmış veri olarak işleyerek ikili veriye dönüştürün.

    2. Gereksinimleri Karşılayan benzersiz bir İçerik-Kimlik üstbilgi değeri Oluşturun R3133 ve R3134.

    3. Değer ikili ile Bir İçerik-Transfer-Kodlama MIME üstbilgi oluşturun.

    4. Öğe bilgi öğesi en iyi duruma getiriliyorsa (yeni `xop:Include` eklenen öğe bilgi `xmime:contentType` öğesinin [üst öğesi] bir öznitelik bilgi öğesi `xmime:contentType` varsa, öznitelik değeri ile bir İçerik Türü MIME üstbilgisi oluşturun.

    5. Base64 olarak işlenen değiştirilen karakterlerden deşifre edilen ikili verilerden oluşturulan içerikle oluşan yeni bir ikili MIME parçası oluşturun, 4b'den İçerik-Kimlik üstbilgisi, 4c'den İçerik-Aktarım-Kodlama üstbilgisi, adım 4d'de oluşturulursa İçerik Türü üstbilgisi.

    6. Değeri `href` cid ile `xop:Include` öğeye bir öznitelik ekleyin: uri Adım 4b oluşturulan İçerik-Kimlik üstbilgi değeri türetilmiştir. " " ve\<">" karakterleri kaldırın, kalan dizeyi URL'den `cid:`kaldırıp önek ekleyin. Aşağıdaki minimum karakter kümesinin RFC1738 ve RFC2396 tarafından kaçılması gerekir. Diğer karakterler kaçabilir.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Adım 4 XOP SOAP Zarf ile bir kök MIME parçası oluşturun.

6. HTTP İçerik Türü üstbilgi de dahil olmak üzere HTTP üstbilgisini yazın.

7. MIME paketini yazın.

#### <a name="processing-mtom-messages"></a>MTOM iletilerini işleme
Bir MTOM iletisinin işlenmesi, önceki "MTOM iletileri oluşturma" bölümünde açıklanan işlemin tam tersidir:

1. Kök MIME parçasının İçerik Türüne `application/xop+xml`sahip olduğundan emin olun.

2. Paketin kök MIME kısmını XML belgesi olarak ayrıştarak bir SOAP Zarfı oluşturun. Karakter kodlaması, kök `charset` MIME bölümünün İçerik Türü parametresi ile belirlenir.

3. [Çocuk] özelliğinin tek üyesi olarak bir `xop:Include` öğe bilgi öğesi olan inşa SOAP Zarfı'ndaki her öğe bilgi öğesi için:

    1. Öğenin `cid:` özniteliğideğerindeki tüm URI kaçış dizilerini (RFC 2396) `@href` önekini kaldırın ve kaçışı kaldırın. `xop:Include` Sonuç dizesini "\<", ">" olarak ekle.

    2. Adım 3a'da türetilen dizeyle eşleşen İçerik-Kimlik üstbilgi değeriyle MIME parçasını bulun.

    3. Adım `xop:Include` 3b'de tanımlanan MIME parçasının varlık gövdesinin kanonik base64 kodlamasını (bkz. XSD-2, 3.2.16 base64Binary) temsil eden karakter bilgileri öğeleriyle her öğenin `children` özelliğinde görünen öğe bilgi öğesini değiştirin (öğe bilgi öğesini `xop:Include` paket parçasından yeniden yapılandırılan verilerle etkili bir şekilde değiştirin).

#### <a name="http-content-type-header"></a>HTTP İçerik Türü Üstbilgi
Aşağıda, MTOM belirtiminde belirtilen gereksinimlerden türetilen ve MTOM ve RFC 2387'den türetilen BIR SOAP 1.x MTOM kodlu iletinin HTTP İçerik Türü üstbilgisinin biçimine ait WCF açıklamalarının bir listesi vettir.

- R4131: BIR HTTP İçerik Türü üstbilginin çok parçalı/ilişkili (büyük/küçük harf duyarsız) değeri ve parametreleri olmalıdır. Parametre adları büyük/küçük harf duyarsızdır. Parametre sırası önemli değildir.

- MIME iletileri için İçerik Türü üstbilginin tam Backus-Naur Formu (BNF), RFC 2045, bölüm 5.1'de listelenmiştir.

- R4132: HTTP İçerik Türü üstbilginin değeri `application/xop+xml` çift tırnak işaretleriyle kapatılan bir tür parametresi olmalıdır.

RFC 2387'de çift tırnak işaretleri kullanma gereksinimi açık olmasa da, metinde tüm çok parçalı/ilişkili ortam türü\@parametrelerinin büyük olasılıkla " veya "/" gibi ayrılmış karakterler içerdiği ve bu nedenle çift tırnak işaretlerine ihtiyaç duyulduğu gözlemlenir.

- R4133: BIR HTTP İçerik Türü üstbilgi, çift tırnak işaretleriyle kapatılan SOAP 1.x Zarfını içeren MIME bölümünün İçerik-KIMLIK üstbilgisinin değerini içeren bir başlangıç parametresi olmalıdır. Başlangıç parametresi atlanırsa, ilk MIME parçası SOAP 1.x Zarfı içermelidir.

- R4134: SOAP 1.1 MTOM kodlanmış ileti için http İçerik Türü üstbilgi, çift tırnak işaretleriyle kaplanmış metin/xml değerini içeren başlangıç bilgi parametresini içermelidir.

- R4135: SOAP 1.2 MTOM kodlu ileti için http İçerik Türü üstbilgi, çift tırnak işaretleriyle birlikte başlangıç bilgisi parametresini `application/soap+xml`içermelidir.

- R4136: BIR SOAP 1.x MTOM kodlanmış ileti için HTTP İçerik Türü üstbilgi, RFC 2046'da tanımlanan MIME sınırı BNF ile eşleşen değere (çift tırnak işaretleriyle kapalı) sınır parametresi, bölüm 5.1.1 olmalıdır

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Örnekler:

     Doğru

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     Doğru

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     Yanlış

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a>Infoset MIME Parçası
SOAP 1.x Zarf XOP MIME paketinin bir kök parçası olarak kapsüllenir ve genellikle `infoset` parçası olarak adlandırılır.

- R4141: SOAP 1.x Zarf, XOP MIME paketinin bir `infoset` parçası olarak kapsüllenmelidir, adı verilen ve HTTP İçerik Türünden başvurulan.

- R4142: SOAP `Infoset` parçası aşağıdaki MIME başlıklarını `Content-ID` `Content-Transfer-Encoding`içermelidir: , , ve `Content-Type`.

İçerik-ID üstbilgisinin biçimi RFC 2045 tarafından

```
"Content-ID" ":" msg-id
```

RFC 2822'de tanımlandığı yer `msg-id` (RFC 822'nin yerini alan, RFC 2045'te başvurulan) şu şekildedir:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

ve " "\<ve ">" içinde yer alan bir e-posta adresidir. Önek `[CFWS]` ve sonek, yorumları taşımak için RFC 2822'ye eklendi ve birlikte çalışabilirliği korumak için kullanılmamalıdır.

R4143: Infoset MIME parçasının İçerik-ID üstbilgisinin `msg-id` değeri, önek ve sonek `[CFWS]` parçaları atlanmış olan RFC 2822'den gelen üretimi takip etmelidir.

Bir dizi MIME uygulaması, " "\<ve ">" içindeki değerin e-posta `absoluteURI` adresi olması\<için gerekli gereksinimleri gidermiş ve e-posta adresine ek olarak " , ">" olarak kullanılır. WCF'nin bu sürümü, formun İçerik-ID MIME üstbilgisinin değerlerini kullanır:

```
Content-ID: <http://tempuri.org/0>
```

R4144: MTOM işlemciler aşağıdaki rahatlıkla `msg-id`eşleşen İçerik-KIMLIK üstbilgi değerlerini kabul etmelidir.

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045), MIME bölümünün içeriğinin kodlanması ile iletişim kurmak için İçerik Aktar-Kodlama üstbilgisini sağlar. İçerik-Aktarım-Kodlama için tanımlanan varsayılan değer, çoğu SOAP iletisi için uygun olmayan 7 bit'tir, bu nedenle daha fazla birlikte çalışabilirlik için İçerik Aktar-Kodlama üstbilgisi gereklidir:

- R4145: SOAP Bilgi Seti bölümü İçerik Aktar-Kodlama üstbilgisini içermelidir.

- R4146: SOAP Envelope karakter kodlaması UTF-8 ise, İçerik Aktarımı-Kodlama üstbilgisinin değeri 8 bit olmalıdır.

- R4147: SOAP Envelope karakter kodlaması UTF-16 ise, İçerik Aktar-Kodlama üstbilgisinin değeri ikili olmalıdır.

- [XOP] bölüm 5'e göre,

- R4148: SOAP1.1 Bilgi seti parçası, ortam türü uygulaması/xop+xml ve parametreleri type="text/xml" ve charset ile İçerik Tipi başlık içermelidir

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: SOAP 1.2 Bilgi Seti parçası, ortam türü ve `application/xop+xml` parametreleri`application/soap+xml`type=" `charset`" ve .

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     XOP isteğe `charset` bağlı olması `application/xop+xml` için parametre tanımlar iken, `charset` `text/xml` medya türü için parametre bp 1.1 gereksinimi benzer birlikte çalışabilirlik için gereklidir.

- R41410: `type` `charset` SOAP 1.x Infoset bölümünün İçerik Tipi başlığında parametreler bulunmalıdır.

#### <a name="wcf-endpoint-support-for-mtom"></a>MTOM için WCF Uç Nokta Desteği
MTOM'un amacı, base64 kodlanmış verileri optimize etmek için bir SOAP iletisi kodlamaktır. Aşağıdaki kısıtlamaların bir listesi:

- R4151: Base64 kodlanmış verileri içeren tüm öğe bilgileri öğesi en iyi duruma getirilebilir.

- B4152: WCF, base64 kodlanmış veri içeren ve uzunluğu 1024 baytı aşan eleman bilgi öğelerini optimize eder.

MTOM'u kullanmak üzere yapılandırılan bir WCF bitiş noktası her zaman MTOM kodlu iletiler gönderir. Hiçbir parça gerekli ölçütleri karşılamasa bile, ileti hala MTOM kodludur (SOAP zarfını içeren tek bir MIME parçası olan bir MIME paketi olarak seri hale getirilmiştir).

### <a name="ws-policy-assertion-for-mtom"></a>MTOM için WS-Politika İddiası
WCF, MTOM kullanımını bitiş noktasına göre belirtmek için aşağıdaki ilke iddiasını kullanır:

```xml
<wsoma:OptimizedMimeSerialization />
```

- R4211: Önceki ilke iddiasında Bir Uç Nokta İlkesi Konusu vardır ve bitiş noktasından gönderilen ve alınan tüm iletilerin MTOM kullanılarak optimize edilmesi gerektiğini belirtir.

- B4212: MTOM optimizasyonu kullanmak üzere yapılandırıldığında, WCF bitiş noktası ilgili `wsdl:binding`ilkeekli bir MTOM İlkesi iddiası ekler.

### <a name="composition-with-ws-security"></a>WS-Security ile kompozisyon
MTOM ve WCF İkili XML benzer `text/xml` bir kodlama mekanizmasıdır. MTOM, WS-Security ve diğer WS-* protokolleri ile doğal kompozisyon sunar: WS-Security kullanılarak güvenli bir ileti MTOM kullanılarak optimize edilebilir.

### <a name="examples"></a>Örnekler

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 Mesaj MTOM Kullanılarak Kodlanmış

```
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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>WCF Secure SOAP 1.2 MTOM Kullanılarak Kodlanmış İleti
Bu örnekte, WS-Security kullanılarak korunan MTOM ve SOAP 1.2 kullanılarak bir ileti kodlanır. Kodlama için tanımlanan ikili `BinarySecurityToken`parçalar, şifreli `CipherValue` imza `EncryptedData` ve şifreli gövdeye karşılık gelen , içeriğidir. `CipherValue` Uzunluğu 1024 bayt daha az olduğundan, WCF tarafından optimizasyon için `EncryptedKey` tanımlanmadığını unutmayın.

```
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
