---
title: Mesajlaşma Protokolleri
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 7d94b917f3d8d2fd7faed28b9320edc240724e0b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703017"
---
# <a name="messaging-protocols"></a>Mesajlaşma Protokolleri

Windows Communication Foundation (WCF) kanal yığın kodlama ve taşıma kanalları, kablo biçimini iç ileti gösterimine dönüştürmek ve belirli bir kullanarak göndermek için kullanır. HTTP Web Hizmetleri birlikte çalışabilirlik için kullanılan en yaygın taşıma olduğunda ve XML tabanlı SOAP 1.1 ve SOAP 1.2 ileti aktarım en iyi duruma getirme mekanizması (MTOM) Web Hizmetleri tarafından kullanılan en yaygın kodlamaları desteklenmektedir.

Bu konuda WCF tarafından kullanılan şu protokoller için uygulama ayrıntılarını kapsayan <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.

Belirtimi/belgesi:

- [HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [SOAP 1.1 HTTP bağlaması](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Bölüm 7
- [SOAP 1.2 HTTP bağlaması](https://www.w3.org/TR/soap12-part2) Bölüm 7

Şu protokoller için bu konuda WCF uygulama ayrıntılarını kapsayan <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> uyguluyor.

Belirtimi/belgesi:

- [XML](https://www.w3.org/TR/REC-xml)
- [SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [SOAP 1.2 Çekirdek](https://www.w3.org/TR/soap12-part1/)
- [WS-Addressing 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [Adresleme 1.0 - çekirdek W3C Web Hizmetleri](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [Adresleme 1.0 - SOAP bağlama W3C Web Hizmetleri](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [Adresleme 1.0 - WSDL bağlama W3C Web Hizmetleri](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [Adresleme 1.0 - meta verileri W3C Web Hizmetleri](https://www.w3.org/TR/ws-addr-metadata/)
- [WSDL SOAP1.1 bağlama](https://www.w3.org/TR/wsdl/)
- [WSDL SOAP1.2 bağlama](https://www.w3.org/Submission/wsdl11soap12/)

Şu protokoller için bu konuda WCF uygulama ayrıntılarını kapsayan <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> kullanır.

Belirtimi/belgesi:

- [XOP](https://www.w3.org/TR/xop10/)
- [MTOM + SOAP 1.2 bağlama](https://www.w3.org/TR/soap12-mtom/)
- [MTOM SOAP 1.1 bağlama](https://www.w3.org/Submission/soap11mtom10/)
- [MTOM WS-Policy onaylama](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

Bu konu başlığı altında yaptığımız, aşağıdaki XML ad alanları ve ilişkili ön ekleri kullanılır:

| Önek | Namespace Tekdüzen Kaynak Tanımlayıcısı (URI) | [---|---| | s11 | `http://schemas.xmlsoap.org/soap/envelope`| | s12 | `http://www.w3.org/2003/05/soap-envelope`| | wsa | `http://www.w3.org/2004/08/addressing`| | wsam | `http://www.w3.org/2007/05/addressing/metadata`| | wsap | `http://schemas.xmlsoap.org/ws/2004/09/policy/addressing`| | wsa10 | `http://www.w3.org/2005/08/addressing`| | wsaw10 | `http://www.w3.org/2006/05/addressing/wsdl`| | xop | `http://www.w3.org/2004/08/xop/include`| | xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime`| | dp |`http://schemas.microsoft.com/net/2006/06/duplex`|

## <a name="soap-11-and-soap-12"></a>SOAP 1.1 ve SOAP 1.2

### <a name="envelope-and-processing-model"></a>Zarf ve Model işleme
WCF SOAP 1.1 Zarf işleme temel Profil 1.1 (BP11) ve temel Profil 1.0 (SSBP10) uygular. 1.2 Zarf SOAP12 bölüm 1 aşağıdaki işlem uygulanır SOAP.

Bu bölümde BP11 ve SOAP12 bölüm 1 ile ilgili WCF tarafından yapılan belirli uygulama seçimler açıklanmaktadır.

#### <a name="mandatory-header-processing"></a>Zorunlu üstbilgiyi işleme
WCF üst işleme işaretlenmiş için kuralları aşağıdaki `mustUnderstand` aşağıdaki farklılıklar nedeniyle SOAP 1.1 ve SOAP 1.2 özellikleri açıklanmaktadır.

WCF kanalı yığın girdiği bir ileti ile ilişkili bağlama öğeleri, örneğin yapılandırılmış tek tek kanalları, ileti metin kodlama, güvenlik, güvenilir Mesajlaşma ve işlemler tarafından işlenir. Her kanal, ilişkili ad alanından üstbilgileri tanır ve bunları anladım olarak işaretler. Bir ileti dağıtıcısı girdikten sonra işlem biçimlendirici ve karşılık gelen ileti/işlem anlaşması ve bunları anladım işaretleri tarafından beklenen üst bilgilerini okur. Dağıtıcı kalan üst bilgileri olmayan anladı ancak olarak işaretlenmiş olup olmadığını doğrular `mustUnderstand` ve bir özel durum oluşturur. İçeren iletileri `mustUnderstand` alıcı hedeflenen üstbilgileri alıcı uygulama kodu tarafından işlenmedi.

Gibi katmanlı işleme altyapısı katmanları ve SOAP düğümünün uygulama katmanları arasında ayrım sağlar:

- B1111: değil anlaşılan üst bilgileri WCF altyapısı kanal yığını tarafından ileti işlendikten sonra ancak uygulama tarafından işlenmeden önce algılanan

     `mustUnderstand` Üstbilgi değeri SOAP 1.1 ve SOAP 1.2 arasında farklılık gösterir. Temel Profil 1.1 gerektirir `mustUnderstand` değeri SOAP 1.1 iletileri için 0 veya 1 olmalıdır. SOAP 1.2 izin verir, 0, 1, `false`, ve `true` gibi değerler, ancak kurallı bir temsilini yayma önerir `xs:boolean` değerleri (`false`, `true`).

- B1112: WCF yayan `mustUnderstand` SOAP zarfının değerleri 0 ile 1 hem SOAP 1.1 ve SOAP 1.2 sürümleri. WCF kabul ettiği tüm değerini alan `xs:boolean` için `mustUnderstand` üst bilgisi (0, 1, `false`, `true`)

#### <a name="soap-faults"></a>SOAP hataları
WCF özel SOAP hatası uygulamalarının listesi verilmiştir.

- B2121: WCF aşağıdaki SOAP 1.1 hata kodlarını döndürür: `s11:mustUnderstand`, `s11:Client`, ve `s11:Server`.

- B2122: WCF aşağıdaki SOAP 1.2 hata kodlarını döndürür: `s12:MustUnderstand`, `s12:Sender`, ve `s12:Receiver`.

### <a name="http-binding"></a>HTTP bağlama

#### <a name="soap-11-http-binding"></a>SOAP 1.1 HTTP bağlama
WCF ile aşağıdaki Açıklamalar bölümüne 3.4 temel Profil 1.1 belirtiminden SOAP1.1 HTTP bağlaması uygular:

- B2211: WCF hizmeti, HTTP POST istekleri yeniden yönlendirme uygulamıyor.

- B2212: WCF istemcileri 3.4.8 uygun olarak HTTP tanımlama bilgileri destekler.

#### <a name="soap-12-http-binding"></a>SOAP 1.2 HTTP bağlama
WCF SOAP 1.2 HTTP bağlaması SOAP 1.2-Bölüm 2 (SOAP12Part2) belirtimiyle aşağıdaki açıklamalar bölümünde anlatıldığı gibi uygular.

SOAP 1.2 bir isteğe bağlı eylem parametresi için sunulan `application/soap+xml` medya türü. Bu parametre, WS-Addressing kullanılmadığında SOAP iletisinin gövdesini ayrıştırılması gerek kalmadan ileti gönderme en iyi duruma getirmek kullanışlıdır.

- R2221: `application/soap+xml` eylem parametresi SOAP 1.2 istek üzerine varsa eşleşmelidir `soapAction` özniteliği `wsoap12:operation` içinde karşılık gelen WSDL bağlama öğesi.

- R2222: `application/soap+xml` eylem parametresi varsa bir SOAP 1.2 iletinin eşleşmelidir `wsa:Action` WS-Addressing 2004/08 veya WS-Addressing 1.0 ne zaman kullanılır.

WS-Addressing devre dışı ve gelen bir istek, bir eylem parametresinin içermiyor, ileti `Action` belirtilen olarak kabul edilmez.

## <a name="ws-addressing"></a>WS-Addressing
WCF WS-Addressing 3 versiyonunu uygular:

- WS-Addressing 2004/08

- W3C Web Hizmetleri 1.0 çekirdek (çekirdek ADDR10) ve SOAP (ADDR10 SOAP) bağlama

- WS-Addressing 1.0 - meta verileri

### <a name="endpoint-references"></a>Uç nokta başvuruları
WCF uygulayan WS-Addressing tüm sürümlerinde uç nokta başvuruları uç noktaları tanımlamak için kullanılır.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Uç nokta başvurular ve WS-Addressing sürümleri
WCF altyapısı kurallarının WS-Addressing kullanın ve belirli bir sayı uygulayan `EndpointReference` öğesi ve `W3C.WsAddressing.EndpointReferenceType` sınıfı (örneğin, WS-ReliableMessaging, WS-SecureConversation ve WS-Trust). WCF WS-Addressing diğer altyapı protokollerle iki sürümünü destekler. WCF bitiş noktalarını, uç noktası başına bir sürümü, WS-Addressing destekler.

R3111, ad alanı için `EndpointReference` öğesi veya bir WCF uç noktasıyla alınıp verilen iletileri kullanılan türü-bu bitiş noktası tarafından uygulanan WS Addressing sürümü aynı olmalıdır.

Örneğin, bir WCF uç noktası WS-ReliableMessaging uyguluyorsa `AcksTo` üst bilgisi içinde bir tür bir uç nokta tarafından döndürülen `CreateSequenceResponse` WS-Addressing sürümü kullanır, `EncodingBinding` öğesi için bu endpoint belirtir.

#### <a name="endpoint-references-and-metadata"></a>Uç nokta başvurular ve meta verileri
Birçok senaryoda meta verileri veya belirli bir uç nokta için meta veri başvurusu iletişim kurmasını gerektirir.

B3121: WCF 6. Bölüm değere veya başvuruya göre meta veri uç noktası başvurular eklemek için WS-MetadataExchange (MEX) belirtiminde açıklanan mekanizmalarını kullanır.

Burada bir WCF Hizmeti belirteci veren tarafından verilen bir güvenlik onaylama işaretleme dili (SAML) belirteci kullanarak kimlik doğrulaması gerektirir bir senaryo düşünün `http://sts.fabrikam123.com`. WCF uç noktayı kullanarak bu kimlik doğrulama gereksinimini açıklar `sp:IssuedToken` onaylama işlemi bir iç içe `sp:Issuer` onaylama için belirteç verenin işaret eden. Erişen istemci uygulamalar `sp:Issuer` onaylama belirteci veren uç noktası ile iletişim kurma bilmeniz gerekir. İstemcinin meta veri belirteci veren hakkında bilmeniz gerekir. WCF MEX içinde tanımlanan uç nokta başvurusu meta verileri uzantıları kullanarak, belirteci veren meta verilerine bir başvuru sağlar.

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

### <a name="message-addressing-headers"></a>İleti Addressing üst bilgileri

#### <a name="message-headers"></a>İleti üstbilgileri
WS-Addressing iki sürümü de WCF aşağıdaki ileti üstbilgilerini belirtimleri tarafından belirtilen şekilde kullanır `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, ve `wsa:RelatesTo`.

B3211: Tüm sürümler, WS-Addressing WCF geliştirir. ancak kullanıma hazır, WS-Addressing ileti üstbilgileri üretmez `wsa:FaultTo` ve `wsa:From`.

Bu ileti üstbilgileri ve WCF uygun şekilde işleyecek etkileşim kuran uygulamaları ile WCF uygulamaları ekleyebilirsiniz.

#### <a name="reference-parameters-and-properties"></a>Başvuru parametreleri ve özellikleri

WCF uç nokta başvuru parametreleri ve başvuru özellikleri ilgili özellikleri uygun şekilde işlenmesini uygular.

B3221: WS-Addressing 2004/08 kullanmak için yapılandırıldığında, WCF bitiş noktalarını işlem başvurusu özellikleri ve başvuru parametreleri arasında ayrım yapmaz.

### <a name="message-exchange-patterns"></a>İleti Exchange desenleri
Web hizmeti işlemi çağrısını ilgili iletiler dizisini olarak adlandırılır *ileti değişim deseni*. WCF destekleyen tek yönlü ve istek-yanıt çift yönlü ileti desenleri exchange. Bu bölümde kullanılan ileti değişim deseni bağlı olarak işlenen ileti üzerinde WS-Addressing gereksinimlerini açıklar.

Bu bölümde boyunca ilk iletiyi istek gönderir ve Yanıtlayıcı ilk iletiyi alır.

#### <a name="one-way-message"></a>Tek yönlü mesaj
İletileri desteklemek üzere WCF uç noktasını yapılandırıldığında bir verilen `Action` tek yönlü bir yapıdadır WCF uç noktası aşağıdaki davranışları ve gereksinimleri aşağıda verilmiştir. Aksi belirtilmediği sürece, hem WS Addressing-WCF'de desteklenen sürümleri için davranışları ve kurallar geçerlidir:

- R3311: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`ve uç nokta başvurusu tarafından belirtilen tüm başvuru parametreleri için üstbilgiler. WS-Addressing 2004/08 kullanılır ve [başvurusu Özellikleri] belirtilen uç nokta başvurusu tarafından ilgili üst bilgiler iletiye çok eklenmesi gerekir.

- B3312: İstek sahibinin içerebilir `MessageID`, `ReplyTo`, ve `FaultTo` üstbilgileri. Alıcı altyapı bunları yoksayar ve uygulamaya geçirilir.

- R3313: HTTP kullanılır ve HTTP yanıt oluşturan üzerinde gönderilen ileti, Yanıtlayıcı boş gövdesi ve 202 HTTP durum kodu ile bir HTTP yanıtı göndermeniz gerekir.

     HTTP taşıma kullanımda ve bir ileti tek yönlü işlem anlaşması bildirir, HTTP yanıtı hala altyapı iletileri göndermek için kullanılabilir — örneğin, güvenilir ileti göndermek için bir `SequenceAcknowledgement` bir HTTP yanıt iletisi.

- B3314: WCF Yanıtlayıcı bir hata iletisi tek yönlü bir iletiye yanıt olarak göndermez.

#### <a name="request-reply"></a>İstek-Yanıt
Bir ileti ile WCF uç noktasını yapılandırıldığında bir verilen `Action` istek-yanıt desenler izleyen WCF uç nokta davranışları ve aşağıdaki gereksinimleri aşağıda verilmiştir. Aksi belirtilmediği sürece, hem WS Addressing-WCF'de desteklenen sürümleri için davranışları ve kurallar geçerlidir:

- R3321: İstek sahibinin isteği içermelidir `wsa:To`, `wsa:Action`, `wsa:MessageID`ve tüm başvuru parametreleri başvuru özellikler (veya her ikisi) uç noktası başvuru tarafından belirtilen için üstbilgiler.

- R3322: WS-Addressing 2004/08 kullanıldığında `ReplyTo` ayrıca isteğinde bulunması gerekir.

- R3323: WS-Addressing 1.0 kullanıldığında ve `ReplyTo` isteğindeki eşit [address] özelliği ile bir varsayılan uç nokta başvurusu yok `http://www.w3.org/2005/08/addressing/anonymous` kullanılır.

- R3324: İstek sahibinin içermelidir `wsa:To`, `wsa:Action`, ve `wsa:RelatesTo` tüm başvuru parametreleri başvuru özellikler (veya her ikisi) tarafından belirtilen üstbilgileri yanı sıra yanıt iletisinin üstbilgilerini `ReplyTo` uç nokta başvurusu İstek.

### <a name="web-services-addressing-faults"></a>Adres hatası Web Hizmetleri
R3411: WCF WS-Addressing 2004/08 tarafından tanımlanan aşağıdaki hatalar üretir.

|Kod|Sebep|
|----------|-----------|
|`wsa:DestinationUnreachable`|İle iletinin geldiği bir `ReplyTo` bu kanal için oluşturulan yanıt adresi farklıdır; için üst bilgisinde belirtilen adreste dinleme bitiş noktası yoktur.|
|`wsa:ActionNotSupported`|Altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcısı, belirtilen eylem algılamaz `Action` başlığı.|

R3412: WCF WS-Addressing 1.0 tarafından tanımlanan aşağıdaki hatalar üretir.

|Kod|Sebep|
|----------|-----------|
|`wsa10:InvalidAddressingHeader`|Yinelenen `wsa:To`, `wsa:ReplyTo`, `wsa:From` veya `wsa:MessageID`. Yinelenen `wsa:RelatesTo` aynı `RelationshipType`.|
|`wsa10:MessageAddressingHeaderRequired`|Gerekli Addressing üst bilgisi eksik.|
|`wsa10:DestinationUnreachable`|İle iletinin geldiği bir `ReplyTo` , bu kanal için oluşturulan yanıt adresi farklıdır. Uç nokta için üst bilgisinde belirtilen adreste dinleme yoktur.|
|`wsa10:ActionNotSupported`|Belirtilen eylem `Action` üstbilgi altyapı kanalları ya da uç noktasıyla ilişkili dağıtıcı tarafından tanınmıyor.|
|`wsa10:EndpointUnavailable`|RM kanal uç nokta değil incelenmesi göre sırası işleme gösteren bu hata yeniden gönderir `CreateSequence` ileti adresleme üstbilgileri.|

Yukarıdaki tablolarda kod eşlemeleri için `FaultCode` SOAP 1.1 içinde ve `SubCode` (gönderici ile kod =) SOAP 1.2 içinde.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 bağlama ve WS-Policy onaylar

#### <a name="indicating-use-of-ws-addressing"></a>WS-Addressing kullanımını gösteren
WCF ilke onaylamalarını belirli bir WS-Addressing sürümü için uç nokta destek belirtmek için kullanır.

Aşağıdaki ilke onaylama, uç noktası İlkesi konu WS-PA ve WS-Addressing 2004/08 uç noktasından alınan iletileri kullanmalısınız gösterir.

```xml
<wsap:UsingAddressing />
```

Bu ilke onaylama WS-Addressing 2004/08 belirtimi artırmaktadır.

Bu, gönderilen/alınan iletileri gösterir. aşağıdaki ilke onaylama, WS-Addressing 1.0 kullanmanız gerekir.

```xml
<wsam:Addressing/>
```

Aşağıdaki ilke onay uç noktası İlkesi konu WS-PA ve WS-Addressing 2004/08 uç noktasından alınan iletileri kullanması gerektiğini belirtir.

```xml
<wsaw10:UsingAddressing />
```

`wsaw10:UsingAddressing` Öğesi [WS-Addressing-WSDL'den] ödünç ve WS-Policy bağlamında bu belirtimini uyduğunuzu kullanılır, Bölüm 3.1.2.

Adresleme kullanımını WSDL 1.1, SOAP 1.1 ve SOAP 1.2 HTTP bağlamaları semantiği değiştirmez. Adresleme ve WSDL SOAP 1.x HTTP bağlaması kullanan bir uç noktasına gönderilen bir istek için yanıt bekleniyorsa, örneğin, yanıtı HTTP yanıt kullanarak gönderilmesi gerekir.

Http yanıtı gönderilen yanıtlar için WS-AM onaylama işlemi aşağıdaki gibidir:

```xml
<wsam:AnonymousResponses/>
```

Tam İlkesi onayını şuna benzeyebilir:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Ancak, istekte bulunan taraf ile Yanıtlayıcı Yanıtlayıcı tarafından gönderilen Örneğin, istenmeyen tek yönlü iletileri arasında kurulan iki bağımsız listesiyse HTTP bağlantılarını kalmamasını fayda ileti exchange desenleri vardır.

WCF tarafından bileşik çift yönlü kanalı burada bir kanalın giriş iletileri için kullanılır ve diğer çıkış iletileri için kullanılan iki temel taşıma kanalları oluşturabilir bir özellik sunar. HTTP taşıma söz konusu olduğunda bileşik çift yönlü iki ters HTTP bağlantılarını sağlar. İstek sahibinin Yanıtlayıcı için ileti göndermek için bir bağlantı kullanır ve Yanıtlayıcı diğer istemciye iletileri geri göndermek için kullanır.

Ayrı http istekleri üzerinden gönderilen yanıtlar için ws-am olaydır

```xml
<wsam:NonAnonymousResponses/>
```

Tam İlkesi onayını şuna benzeyebilir:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Yanıtlayıcı ve Yanıtlayıcı istekte bulunan taraf için talep sahibinin akan iletileri için kullanılacak iki ayrı listesiyse HTTP bağlantısı uç noktası İlkesi konu WS-PA WSDL 1.1 SOAP 1.x HTTP bağlantıları kullanan Uç noktalara sahip aşağıdaki onay gerektirir, sırasıyla.

```xml
<cdp:CompositeDuplex/>
```

Önceki deyim aşağıdaki gereksinimlere müşteri adayları `wsa:ReplyTo` istek iletilerinin üstbilgisi:

- R3514: bir uç noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özellik değerine eşit değil `http://www.w3.org/2005/08/addressing/anonymous` uç noktası ile bir ilke alternatif bir WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve varsa bir `wsap10:UsingAddressing` veya `wsap:UsingAddressing` onaylama işlemi eşleşmiş ile `cdp:CompositeDuplex` bağlı.

- R3515: bir uç noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle `[address]` özelliği eşit `http://www.w3.org/2005/08/addressing/anonymous`, veya bir `ReplyTo` tümü, uç nokta ile bir ilke alternatif bir WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve varsa üst bilgisi `wsap10:UsingAddressing` onaylama ve Hayır `cdp:CompositeDuplex` bağlı onaylama.

- R3516: bir uç noktasına gönderilen iletileri olmalıdır istek bir `ReplyTo` üstbilgiyle bir `[address]` özelliği eşit `http://www.w3.org/2005/08/addressing/anonymous` uç noktası ile bir ilke alternatif bir WSDL 1.1 SOAP 1.x HTTP bağlama kullanır ve varsa `wsap:UsingAddressing` onaylama ve hiçbir `cdp:CompositeDuplex`bağlı onaylama.

Bir öğe sunarak benzer protokolü bağlamaları tanımlamak WS-addressing WSDL belirtimi çalışır `<wsaw:Anonymous/>` değerlerle üzerinde gereksinimleri belirtmek için üç metin (gerekli, isteğe bağlı ve yasaklanmış) `wsa:ReplyTo` üst bilgisi (Bölüm 3.2). Ne yazık ki, bu tür bir öğe onaylama kullanarak alternatifleri kesişimi desteklemek için etki alanına özgü uzantıları gerektirdiğinden tür öğe tanımı özellikle, WS-Policy bağlamında onaylama kullanılabilir değil. Böyle bir öğe tanımı değerini de gösterir. `ReplyTo` HTTP aktarımı belirli kolaylaştırır Tel üzerinde uç nokta davranışı aksine başlığı.

#### <a name="action-definition"></a>Eylem tanımı
WS-Addressing 2004/08 tanımlayan bir `wsa:Action` özniteliğini `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` öğeleri. WS-Addressing 1.0 WSDL bağlama (WS-ADDR10-WSDL) benzer bir öznitelik tanımlar `wsaw10:Action`.

İkisi arasındaki tek fark, sırasıyla bölümü, WS-ADDR 3.3.2 ve WS-ADDR10-WSDL 4.4.4 bölümünde açıklanan varsayılan eylem deseni semantiği ' dir.

Aynı paylaşan iki uç nokta uygun olan `portType` (veya WCF terminolojisinde sözleşme) ancak WS-Addressing'ın farklı sürümleri kullanılarak. Ancak bu eylem tarafından tanımlanan koşuluyla, `portType` ve uygulayan uç noktalar genelinde değiştirmemelisiniz `portType`, her iki varsayılan eylem desenleri desteklemesini mümkün olur.

WCF bu controversy çözmek için tek bir sürümünü destekler `Action` özniteliği.

B3521: WCF kullanan `wsaw10:Action` özniteliği `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` WS-ADDR10-belirlemek için WSDL içinde tanımlanan öğeleri `Action` bitiş noktası tarafından kullanılan WS-Addressing sürümü bakılmaksızın karşılık gelen iletiler için URI.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Kullanım uç nokta başvurusu iç WSDL bağlantı noktası
WS ADDR10 WSDL bölümü 4.1 genişletir `wsdl:port` içerecek şekilde öğesi `<wsa10:EndpointReference…/>` WS-Addressing bağlamında uç noktayı tanımlamak için alt öğesi. WCF üzerinde WS-Addressing 2004/08, bu yardımcı genişletir izin vererek `<wsa:EndpointReference…/>` bir alt öğesi olarak görüntülenmesini `wsdl:port`.

- R3531: eklenen ilke alternatif bir uç nokta varsa, bir `<wsaw10:UsingAddressing/>` İlkesi onayını, karşılık gelen `wsdl:port` öğesi bir alt öğe içerebilir `<wsa10:EndpointReference …/>`.

- R3532: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzeyin özniteliği `wsdl:port` / `wsdl:location` öğesi.

- R3533: eklenen ilke alternatif bir uç nokta varsa `<wsap:UsingAddressing/>` İlkesi onayını, karşılık gelen `wsdl:port` öğesi bir alt öğe içerebilir `<wsa:EndpointReference …/>`.

- R3534: Varsa bir `wsdl:port` bir alt öğe içeriyor `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` alt öğe değeri değerini eşleşmelidir `@address` eşdüzeyin özniteliği `wsdl:port` / `wsdl:location` öğesi.

### <a name="composition-with-ws-security"></a>WS-güvenlik ile oluşturma
WS-ADDR ve WS-ADDR10 göre güvenlik göz önünde bulundurarak bölümlerde, tüm adres ileti üstbilgileri ileti gövdesi ile birlikte birbirine bağlamak için oturum açmış olmanız önerilir.

WS-güvenlik ileti bütünlük koruması için kullanıldığında, WS-Addressing ileti üstbilgileri ve bunun yanı sıra üstbilgileri başvuru parametreleri veya özellikleri (veya her ikisi de) sonuçlandı ileti gövdesi ile birlikte oturum açmanız gerekir.

### <a name="examples"></a>Örnekler

#### <a name="one-way-message"></a>Tek yönlü mesaj
Bu senaryoda, gönderenin alıcı için tek yönlü bir ileti gönderir. SOAP 1.2, HTTP 1.1 ve 1.0, W3C WS-Addressing kullanılır.

İstek iletisi yapısı: İleti üstbilgilerini içeren `wsa10:To` ve `wsa10:Action` öğeleri. Belirli bir ileti gövdesini içeren `<app:Ping>` uygulama ad alanından öğesi.

HTTP üstbilgileri: POST hedef URI eşleşen `wsa10:To` öğesi.

Content-Type üstbilgisi değeri olan `application/soap+xml` SOAP 1.2 gerektirdiği. Parametreleri `charset` ve `action` dahil edilir. `action` Content-Type üstbilgisi parametresinin değerini eşleşen `wsa10:Action` ileti üst bilgisi.

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

Alıcı, bir boş bir HTTP yanıtı ve durum 202 ile yanıt verir. HTTP yanıt örneği:

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

## <a name="soap-message-transmission-optimization-mechanism"></a>SOAP ileti aktarım en iyi duruma getirme mekanizması
Bu bölümde, HTTP SOAP MTOM için WCF uygulama ayrıntılarını açıklar. MTOM, SOAP ileti kodlama mekanizması geleneksel metin/XML kodlama veya WCF ikili kodlama aynı sınıfta teknolojisidir. MTOM aşağıdakileri içerir:

- Bir XML encoding ve paketleme mekanizması [XOP] tarafından açıklanan ikili ayrı bölümlere base64 ile kodlanmış ikili verileri içeren XML bilgi öğeleri iyileştirir.

- Bir MIME kapsülleme XOP paketinin XML bilgi kümesi ve her ikili XOP paketin parçası ayrı bir MIME bölümü serileştirir.

- SOAP için uygulanan bir MIME XOP kodlama 1.x Zarf.

- HTTP aktarım bağlama.

MTOM olmayan HTTP taşımaları WCF ile kullanmak mümkündür. Ancak, bu konudaki şu HTTP üzerinde odaklanır.

MTOM biçim belirtimleri MTOM kendisi, XOP ve MIME kapsayan çok sayıda yararlanır. Bu belirtimi kümesi tanılanmasını biçimi ve işleme semantiğine gereksinimlerinin tamamı yeniden oluşturmak biraz zor yapar. Bu bölümde MTOM HTTP bağlaması biçimi ve işleme gereksinimlerini açıklar.

### <a name="mtom-message-encoding"></a>İleti MTOM kodlama

#### <a name="generating-mtom-messages"></a>MTOM iletileri oluşturma
[XOP] bölümü 3.1 bağlamalarında tanımlanmış bir XOP pakete base64 değerler içeren öğe bilgi öğelerle XML kodlama işlemi açıklanır.

Aşağıdaki adımlar dizisini özel MTOM kodlama işlemi açıklanmaktadır:

1. Kodlanmış SOAP Zarfı ile hiçbir öğe bilgi öğe içerdiğinden emin olun bir `[namespace name]` , `http://www.w3.org/2004/08/xop/include` ve `[local name]` , `Include`.

2. Boş bir MIME paketi oluşturun.

3. Orijinal XML bilgi kümesi içinde en iyi duruma getirilmesi öğesi bilgi öğelerini tanımlayın. Öğeleri en iyi duruma getirilmesi karakter oluşturan `[children]` öğesi bilgilerini öğenin kurallı biçiminde olması gerekir `xs:base64Binary` (bkz XSD-2, 3.2.16 base64Binary) ve, satır içi, önceki herhangi bir boşluk karakteri içermemelidir veya boşluk olmayan içeriği takip.

4. Özgün SOAP Zarfı kopyası olan bir XOP SOAP Zarfı oluşturun, ancak her öğe bilgileri çocuğunu önceki adımda tanımlanan öğe yerine bir `xop:Include` öğe bilgi öğe şu şekilde oluşturulur:

    1. Değiştirilen karakter ikili verileri, base64 kodlu veriler olarak işleyerek dönüştürün.

    2. R3133 ve R3134 gereksinimlerini karşılayan benzersiz bir Content-ID üst bilgi değeri oluşturur.

    3. MIME içerik Transfer-Encoding üstbilgi ikili değer oluşturur.

    4. Öğe bilgileri öğe iyileştirilen, ([üst] yeni eklenen `xop:Include` öğe bilgi öğe) sahip bir `xmime:contentType` öznitelik bilgisi öğesi, değeri ile bir MIME Content-Type üstbilgisini oluşturmak `xmime:contentType` özniteliği.

    5. Yeni bir ikili MIME bölümü, işlenen base64 4b Content-ID başlığından, üst bilgi içeriği Transfer-Encoding 4 c, adım 4 d oluşturursa Content-Type üst bilgisi olarak değiştirilen karakter gelen çözülmüş ikili verileri tarafından oluşturulmuş içerik ile oluşturur.

    6. Ekleme bir `href` özniteliğini `xop:Include` değeri CID öğeyle: Content-ID üst bilgi değeri adım 4b'de oluşturulan URI türetilir. Kapsayan Kaldır "\<" ve ">" karakterleri, URL-kalan dize ve ön ek Ekle kaçış `cid:`. Aşağıdaki en düşük karakter kümesi RFC1738 ve RFC2396 tarafından Atlanan gereklidir. Diğer karakterler Atlanan.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Adım 4'teki XOP SOAP Zarfı ile bir kök MIME bölümü oluşturun.

6. HTTP Content-Type üst bilgisi dahil olmak üzere HTTP üst bilgilerini yazın.

7. MIME paket yazın.

#### <a name="processing-mtom-messages"></a>MTOM iletilerini işleme
Bir MTOM işleme iletisi tam önceki açıklanan işlemi tersidir "oluşturma MTOM iletileri" bölümünde:

1. MIME bölümü kök Content-Type olduğundan `application/xop+xml`.

2. SOAP Zarfı MIME bölümü bir XML belgesi olarak paketin kök ayrıştırarak oluşturun. Karakter kodlamasını göre belirlenir `charset` Content-Type MIME bölümü kök parametresi.

3. Oluşturulan SOAP Zarfı içinde her öğe bilgi öğe için olan, kendi [alt] özelliğini tek üyesi olarak bir `xop:Include` öğe bilgi öğe:

    1. Kaldırma `cid:` önek ve tüm URI kaçış dizileri (RFC 2396) değerini unescape `@href` özniteliği `xop:Include` öğesi. Sonuç dizesinde alın "\<", ">".

    2. Adım 3a adımında türetilmiş dizesiyle eşleşen Content-ID üst bilgi değeri ile MIME bölümü bulun.

    3. Değiştirin `xop:Include` görünür öğe bilgi öğe `children` özellik kurallı base64 kodlama temsil eden karakter bilgi öğeleri ile her bir öğenin (bkz XSD-2, 3.2.16 base64Binary) varlık gövdesinin MIME bölümü Adım 3b içinde tanımlanan (etkili bir şekilde değiştirin `xop:Include` paket bölümünden reconstructed veri öğesi bilgi öğe).

#### <a name="http-content-type-header"></a>HTTP Content-Type üstbilgisi
Aşağıdaki biçimi için WCF açıklamalar MTOM belirtimini içinde belirtilen gereksinimleri türetilen bir SOAP iletisinin 1.x MTOM kodlu HTTP Content-Type üstbilgisinin bir listesidir ve MTOM ve RFC 2387 türetilmiştir.

- R4131: Bir HTTP Content-Type üstbilgisi değeri multipart/related (büyük-küçük harf duyarsız) ve parametreleri olmalıdır. Parametre adları büyük/küçük harfe duyarsızdır. Parametre sırası önemli değildir.

- Content-Type üstbilgisi MIME iletileri için tam Backus-Naur Form (BNF) bölümü 5.1, RFC 2045 listelenir.

- R4132: Bir HTTP Content-Type üstbilgisi değeri ile bir tür parametresi olmalıdır `application/xop+xml` çift tırnak işareti içine alınmış.

Çift tırnak işareti kullanma gereksinimi RFC 2387 açık olsa da, tüm multipart/related medya tür parametreleri büyük olasılıkla gibi ayrılmış karakterler içeren metin uygulamasını gözlediğini "\@" veya "/" ve bu nedenle çift tırnak gerekir işaretler.

- R4133: Başlangıç parametresi SOAP içeren MIME bölümünün içerik kimliği-üstbilgisinin değeri ile bir HTTP Content-Type üst bilgisi olmalıdır 1.x Zarf çift tırnak işareti içine alınmış. Başlangıç parametresi atlanırsa, SOAP ilk MIME bölümü içermelidir 1.x Zarf.

- R4134: Kodlanmış SOAP 1.1 MTOM iletisi için bir HTTP Content-Type üstbilgisi değeri çift tırnak işaretleri arasına metin/XML, başlangıç bilgileri parametresiyle içermelidir.

- R4135: SOAP 1.2 MTOM olarak kodlanmış bir ileti için bir HTTP Content-Type üstbilgisi değeri başlangıç bilgileri parametresiyle içermelidir `application/soap+xml`çift tırnak işareti içine alınan.

- R4136: MTOM kodlanmış SOAP 1.x iletisi için HTTP Content-Type üstbilgisi sınır parametresi BNF RFC 2046, 5.1.1 bölümünde tanımlanmış MIME sınır eşleşen (çift tırnak işareti içine alınmış) değerine sahip olması gerekir

    ```
    boundary := 0*69<bchars> bcharsnospace 
    bchars := bcharsnospace / " " 
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+" 
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Örnekler:

     DÜZELTİN

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     DÜZELTİN

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     YANLIŞ

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1" 
    ```

#### <a name="infoset-mime-part"></a>Bilgi kümesi MIME bölümü
SOAP Zarfı XOP MIME paket kök bir parçası olarak saklanır ve genellikle çağrılır 1.x `infoset` bölümü.

- R4141: SOAP Zarfı adlı XOP MIME paketi kök bir parçası olarak kapsüllenmelidir 1.x `infoset` bölümü ve gelen HTTP Content-Type başvurulan.

- R4142: SOAP `Infoset` bölümü şu MIME üst bilgilerini içermesi gerekir: `Content-ID`, `Content-Transfer-Encoding`, ve `Content-Type`.

Content-ID üst bilgisinin biçimi RFC 2045 tanımlanır

```
"Content-ID" ":" msg-id
```

Burada `msg-id` RFC 2822 (yani, RFC 822, RFC 2045 başvurulan yerini alır) olarak tanımlanır:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

ve etkili bir şekilde bir e-posta adresi içine alınmış "\<" ve ">". `[CFWS]` Önek ve sonek 2822 açıklamaları yürütmek için RFC eklendi ve birlikte çalışabilirlik korumak için kullanılmamalıdır.

R4143: Sonrası bilgi kümesi MIME bölümünün içerik kimliği-üstbilgisinin değerini izlemelidir `msg-id` ile RFC 2822 üretimden `[CFWS]` atlanmış önek ve sonek bölümleri.

MIME uygulamaları birkaç esnek içine alınmış değer gereksinimleri "\<" ve ">" e-posta adresi olabilir ve kullanılan `absoluteURI` içine "\<", ">" Ek e-posta adresi. Bu sürüm WCF MIME Content-ID üst bilgisi biçiminde değerleri kullanır:

```
Content-ID: <http://tempuri.org/0> 
```

R4144: İçerik kimliği-üstbilgi değerleri aşağıdaki rahat eşleşen MTOM işlemci kabul etmelidir `msg-id`.

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME bölümünün içerik kodlama iletişim kurmak için içerik Transfer-Encoding üstbilgisi MIME (RFC 2045) sağlar. Content-Transfer-Encoding için tanımlanan varsayılan içerik Transfer-Encoding başlığı büyük birlikte çalışabilirlik için gerekli olan SOAP iletilerin çoğu için uygun değil, bu nedenle 7 bit:

- R4145: SOAP bilgi bölümü içeriği Transfer-Encoding üst bilgisi içermelidir.

- R4146: UTF-8 karakter kodlaması SOAP Zarfı varsa, içeriği Transfer-Encoding üstbilgisinin değerini 8 bit olmalıdır.

- R4147: UTF-16 karakter kodlamasını SOAP Zarfı varsa, içeriği Transfer-Encoding üstbilgisinin değerini ikili olmalıdır.

- [XOP göre] 5 bölümüne,

- R4148: Content-Type üstbilgisi medya türü application/xop + xml SOAP1.1 bilgi bölümü içermelidir ve tür parametreleri = "text/xml" ve karakter kümesi

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: Content-Type üstbilgisi medya türü ile SOAP 1.2 bilgi bölümü içermelidir `application/xop+xml` ve tür parametreleri = "`application/soap+xml`" ve `charset`.

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     XOP açıklarken `charset` parametresi için `application/xop+xml` isteğe bağlı olacak şekilde BP 1.1 gereksinimini benzer birlikte çalışabilirliği için gerekli `charset` parametresi için `text/xml` medya türü.

- R41410: `type` ve `charset` parametreleri SOAP 1.x bilgi bölümü Content-Type üst bilgisi mevcut olmalıdır.

#### <a name="wcf-endpoint-support-for-mtom"></a>MTOM WCF uç nokta desteği
MTOM amacı, bir SOAP ileti base64 ile kodlanmış verileri En İyileştir şifrelemektir. Kısıtlamalar bir listesi verilmiştir:

- R4151: base64 ile kodlanmış verileri içeren herhangi bir öğe bilgi öğe iyileştirilmiş olması olabilir.

- B4152: WCF base64 olarak kodlanmış veriler içeren ve uzunluğu 1024 bayt aşan öğesi bilgi öğelerini iyileştirir.

MTOM kullanacak şekilde yapılandırılmış bir WCF uç nokta her zaman MTOM kodlanmış iletileri gönderir. Hiçbir parçasının gerekli ölçütleri karşılayan bile ileti (bir MIME paketi olarak SOAP Zarfı içeren tek bir MIME bölümü ile seri hale getirilmiş) hala MTOM kodlanır.

### <a name="ws-policy-assertion-for-mtom"></a>MTOM için WS-Policy onaylama
WCF MTOM kullanım bitiş noktası tarafından belirtmek için aşağıdaki İlkesi onayını kullanır:

```xml
<wsoma:OptimizedMimeSerialization ... />
```

- R4211: Önceki İlkesi onayını bir uç noktası İlkesi konu ve uç noktasından alınan ve gönderilen tüm iletilerin MTOM kullanarak iyileştirilmelidir belirtir.

- B4212: MTOM iyileştirme'yi kullanmak üzere yapılandırıldığında, bir WCF uç nokta MTOM ilke onaylama karşılık gelen iliştirilmiş ilke ekler `wsdl:binding`.

### <a name="composition-with-ws-security"></a>WS-güvenlik ile oluşturma
MTOM olan benzer bir kodlama mekanizması `text/xml` ve WCF ikili XML. MTOM sunar doğal bileşim WS-güvenlik ve diğer WS-* protokoller: WS güvenliği kullanılarak güvenli bir ileti MTOM kullanılarak iyileştirilebilir.

### <a name="examples"></a>Örnekler

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 ileti MTOM kullanılarak kodlanır

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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>Güvenli WCF SOAP 1.2 MTOM kullanarak ileti kodlanmış.
Bu örnekte, bir ileti MTOM ve WS-güvenlik kullanarak korumalı bir SOAP 1.2 kullanılarak kodlanır. Kodlama içeriğini için tanımlanan ikili parçaları `BinarySecurityToken`, `CipherValue` , `EncryptedData` karşılık gelen şifrelenmiş imzası ve şifrelenmiş gövdesi. Unutmayın `CipherValue` , `EncryptedKey` uzunluğunu daha az sonra 1024 bayt olduğundan iyileştirme için WCF tarafından tanımlanmadı.

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