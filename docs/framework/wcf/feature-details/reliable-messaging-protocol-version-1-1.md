---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 9320787317131f42c4a82c6114a16fdea87567f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283306"
---
# <a name="reliable-messaging-protocol-version-11"></a>Güvenilir Mesajlaşma Protokolü sürüm 1.1

Bu konuda, HTTP taşıması kullanılarak birlikte çalışabilirlik için gereken WS-ReliableMessaging Şubat 2007 (sürüm 1,1) protokolü için Windows Communication Foundation (WCF) uygulama ayrıntıları ele alınmaktadır. WCF, bu konuda açıklanan kısıtlamalar ve açıklamalar ile WS-ReliableMessaging belirtimini izler. WS-ReliableMessaging sürüm 1,1 protokolünün .NET Framework 3,5 ' den başlayarak uygulandığını unutmayın.

WS-ReliableMessaging Şubat 2007 protokolü, <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>tarafından WCF 'de uygulanır.

Kolaylık olması için, konusu aşağıdaki rolleri kullanır:

- Başlatıcı: WS-güvenilir Ileti sırası oluşturmayı Başlatan istemci.

- Yanıtlayıcı: başlatıcısının isteklerini alan hizmet.

 Bu belge aşağıdaki tablodaki ön ekleri ve ad alanlarını kullanır.

|Prefix|Ad Alanı|
|-|-|
|WSRM|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|Netra|http://schemas.microsoft.com/ws/2006/05/rm|
|s|http://www.w3.org/2003/05/soap-envelope|
|WSA|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|WSO|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|WSP|(WS-Policy 1,2 ya da WS-Policy 1,5)|

## <a name="messaging"></a>İleti

### <a name="sequence-creation"></a>Sıra oluşturma

WCF, güvenilir bir mesajlaşma sırası oluşturmak için `CreateSequence` ve `CreateSequenceResponse` iletilerini uygular. Aşağıdaki kısıtlamalar geçerlidir:

- B1101: WCF başlatıcısı `CreateSequence` iletisinin `ReplyTo`, `AcksTo` ve `Offer/Endpoint`aynı uç nokta başvurusunu kullanır.

- R1102: `CreateSequence` iletisindeki `AcksTo`, `ReplyTo` ve `Offer/Endpoint` uç nokta başvuruları, sekizli temelinde eşleşecek şekilde özdeş dize gösterimlerine sahip adres değerlerine sahip olmalıdır.

  - WCF Yanıtlayıcı, bir sıra oluşturmadan önce `AcksTo`, `ReplyTo` ve `Endpoint` uç nokta başvurularının URI kısmının aynı olduğunu doğrular.

- R1103: `CreateSequence` iletisindeki `AcksTo`, `ReplyTo` ve `Offer/Endpoint` uç nokta başvuruları aynı başvuru parametreleri kümesine sahip olmalıdır.

  - WCF zorunlu değildir, ancak `CreateSequence` başvuru parametrelerinin `AcksTo`, `ReplyTo` ve `Offer/Endpoint` uç nokta başvurularının aynı olduğunu varsayar ve, bildirimlerin ve listesiyse iletileri için `ReplyTo` uç nokta başvurusundan başvuru parametrelerini kullanır.

- B1104: WCF başlatıcısı `CreateSequence` iletisinde isteğe bağlı `Expires` veya `Offer/Expires` öğesi oluşturmaz.

- B1105: `CreateSequence` iletisine erişirken, WCF Yanıtlayıcı, `CreateSequenceResponse` öğesindeki `Expires` değeri olarak `CreateSequence` öğesinde `Expires` değerini kullanır. Aksi takdirde, WCF Yanıtlayıcısı `Expires` ve `Offer/Expires` değerlerini okur ve yoksayar.

- B1106: `CreateSequenceResponse` iletisine erişirken, WCF başlatıcısı isteğe bağlı `Expires` değerini okur, ancak kullanmaz.

- B1107: WCF başlatıcısı ve Yanıtlayıcı, `CreateSequence/Offer` ve `CreateSequenceResponse` öğelerinde her zaman isteğe bağlı `IncompleteSequenceBehavior` öğesini oluşturur.

- B1108: WCF `IncompleteSequenceBehavior` öğesinde yalnızca `DiscardFollowingFirstGap` ve `NoDiscard` değerlerini kullanır.

  - WS-ReliableMessaging, bir oturum oluşturan iki boyutlu bağlantılı diziyi oluşturmak için `Offer` mekanizmasını kullanır.

- B1109: `CreateSequence`, bir `Offer` öğesi içeriyorsa, bir `Accept` öğesi olmadan bir `CreateSequenceResponse` ile yanıt vererek WCF Yanıtlayıcının sunulan sırayı reddettiği şekilde reddeder.

- B1110: güvenilir bir mesajlaşma Yanıtlayıcısı sunulan sırayı reddederse, WCF başlatıcısı yeni oluşturulan sırayı hata.

- B1111: `CreateSequence` bir `Offer` öğesi içermiyorsa, iki yönlü WCF Yanıtlayıcısı, bir `CreateSequenceRefused` hatası ile yanıt vererek sunulan sırayı reddeder.

- R1112: `Offer` mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda, `CreateSequenceResponse/Accept/AcksTo` uç noktası başvurusunun `[address]` özelliği Byte için `CreateSequence` ileti baytının hedef URI 'siyle eşleşmelidir.

- R1113: `Offer` mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda, her iki sıranın de başlatıcıdan yanıtlayanın akışını sağlamak için aynı uç nokta başvurusuna gönderilmesi gerekir.

WCF, başlatıcı ve Yanıtlayıcı arasında güvenilir oturumlar oluşturmak için WS-ReliableMessaging kullanır. WCF WS-ReliableMessaging uygulamasının tek yönlü, istek-yanıt ve tam çift yönlü mesajlaşma desenleri için güvenilir bir oturum sağlar. `CreateSequence` ve `CreateSequenceResponse` üzerindeki WS-ReliableMessaging `Offer` mekanizması, iki bağıntılı dönüştürme sırası oluşturmanıza ve tüm ileti uç noktaları için uygun bir oturum Protokolü sağlamanıza olanak tanır. WCF, oturum bütünlüğü için uçtan uca koruma dahil olmak üzere bu tür bir oturum için güvenlik garantisi sağladığından, aynı tarafa yönelik iletilerin aynı hedefe ulaşmasını sağlamak yararlıdır. Bu Ayrıca, uygulama iletilerinde "Piggy-," sıralı bildirimleri de sağlar. Bu nedenle, R1102, R1112 ve R1113 kısıtlamaları WCF için geçerlidir.

`CreateSequence` iletisine bir örnek.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>
    <wsa:ReplyTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
      </wsrm:AcksTo>
      <wsrm:Offer>
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>
        <wsrm:Endpoint>
          <wsa:Address>http://Business456.com/clientA</wsa:Address>
        </wsrm:Endpoint>
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      </wsrm:Offer>
    </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

`CreateSequenceResponse` iletisine bir örnek.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      <wsrm:Accept>
        <wsrm:AcksTo>
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>
        </wsrm:AcksTo>
      </wsrm:Accept>
    </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="closing-a-sequence"></a>Bir diziyi kapatma

WCF, güvenilir bir mesajlaşma kaynağı tarafından başlatılan kapatmadan `CloseSequence` ve `CloseSequenceResponse` iletilerini kullanır. WCF güvenilir mesajlaşma hedefi kapatmaları başlatmaz ve WCF güvenilir mesajlaşma kaynağı, güvenilir mesajlaşma hedefi ile başlatılan bir kapanışı desteklemez. Aşağıdaki kısıtlamalar geçerlidir:

- B1201: WCF güvenilir mesajlaşma kaynağı, diziyi kapatmak için her zaman bir `CloseSequence` iletisi gönderir.

- B1202: güvenilir mesajlaşma kaynağı, `CloseSequence` iletisini göndermeden önce tam dizi iletilerinin onay gelmesini bekler.

- B1203: güvenilir mesajlaşma kaynağı her zaman isteğe bağlı `LastMsgNumber` öğesi içerir, çünkü dizi ileti içermez.

- R1204: güvenilir mesajlaşma hedefi `CloseSequence` bir ileti göndererek kapatmaları başlatmamalıdır.

- B1205: `CloseSequence` bir ileti aldıktan sonra, WCF güvenilir mesajlaşma kaynağı, diziyi tamamlanmamış olarak değerlendirir ve bir hata gönderir.

 `CloseSequence` iletisine bir örnek.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
    </wsrm:CloseSequence>
  </s:Body>
</s:Envelope>
```

Örnek `CloseSequenceResponse` iletisi:

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:CloseSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence-termination"></a>Sıra sonlandırma

WCF, `CloseSequence/CloseSequenceResponse` el sıkışmasını tamamladıktan sonra `TerminateSequence/TerminateSequenceResponse` el sıkışmasını kullanır. WCF güvenilir mesajlaşma hedefi sonlandırmayı başlatmaz ve güvenilir mesajlaşma kaynağı, güvenilir bir mesajlaşma hedefi tarafından başlatılan sonlandırmayı desteklemez. Aşağıdaki kısıtlamalar geçerlidir:

- B1301: WCF başlatıcısı, `CloseSequence/CloseSequenceResponse` el sıkışmasının başarıyla tamamlanmasından sonra yalnızca `TerminateSequence` iletisi gönderir.

- R1302: WCF `LastMsgNumber` öğesinin belirli bir sıra için tüm `CloseSequence` ve `TerminateSequence` iletileri arasında tutarlı olduğunu doğrular. Bu, `LastMsgNumber` tüm `CloseSequence` ve `TerminateSequence` iletilerinde mevcut olmadığı ya da tüm `CloseSequence` ve `TerminateSequence` iletilerinde aynı olduğu anlamına gelir.

- B1303: `CloseSequence/CloseSequenceResponse` el sıkışması sonrasında `TerminateSequence` bir ileti alınırken, güvenilir mesajlaşma hedefi bir `TerminateSequenceResponse` iletisiyle yanıt verir. Güvenilir Mesajlaşma kaynağında `TerminateSequence` iletisini göndermeden önce son onay bulunduğundan, güvenilir mesajlaşma hedefi, dizinin bittiğini şüpheli olmadan bilir ve kaynakları hemen geri kazanır.

- B1304: `CloseSequence/CloseSequenceResponse` El sıkışmadan önce `TerminateSequence` bir ileti alınırken, WCF güvenilir mesajlaşma hedefi bir `TerminateSequenceResponse` iletisiyle yanıt verir. Güvenilir Mesajlaşma hedefi, dizide herhangi bir tutarsızlık olmadığını belirlerse, güvenilir mesajlaşma hedefi bir uygulamanın hedefi olarak belirtilen süre için geri kazanma kaynaklarından önce bekler ve istemciye alma şansı sağlar son onay. Aksi takdirde, güvenilir mesajlaşma hedefi kaynakları anında geri kazanır ve `Faulted` olayını yükselterek sıranın, dizi ile bitip bitmediğini belirtir.

`TerminateSequence` iletisine bir örnek.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
      </wsrm:TerminateSequence>
  </s:Body>
</s:Envelope>
```

Örnek `TerminateSequenceResponse` iletisi:

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:TerminateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequences"></a>Diziler

Diziler için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- B1401: WCF `xs:long`en yüksek kapsamlı değerden (9223372036854775807) daha yüksek sıra numarası üretir ve erişir.

`Sequence` üst bilgisi örneği.

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a>İstek onayı

WCF `AckRequested` üst bilgisini etkin tut mekanizması olarak kullanır.

`AckRequested` üst bilgisi örneği.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF, WS-güvenilir mesajlaşmada belirtilen sıra bildirimleri için bir "Piggy-Back" mekanizması kullanır. Aşağıdaki kısıtlamalar geçerlidir:

- R1601: `Offer` mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda, `SequenceAcknowledgement` üst bilgisi amaçlanan alıcıya aktarılan herhangi bir uygulama iletisine dahil edilebilir. Uzak uç noktanın, bir PIDA desteklenen `SequenceAcknowledgement` üstbilgisine erişebilmesi gerekir.

- B1602: WCF, `Nack` öğeleri içeren `SequenceAcknowledgement` üst bilgileri oluşturmaz. WCF her bir `Nack` öğesinin bir sıra numarası içerdiğini doğrular, aksi takdirde `Nack` öğesini ve değerini yoksayar.

 `SequenceAcknowledgement` üst bilgisi örneği.

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging hataları

WS-ReliableMessaging hatalarının WCF uygulaması için uygulanan kısıtlamaların listesi aşağıda verilmiştir. Aşağıdaki kısıtlamalar geçerlidir:

- B1701: WCF `MessageNumberRollover` hata oluşturmaz.

- B1702: SOAP 1,2 üzerinde, hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantıları işleyemezse, WCF aşağıdaki örnekte gösterildiği gibi iç içe geçmiş bir `CreateSequenceRefused` `netrm:ConnectionLimitReached`hata alt kodu oluşturur.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>
  </s:Header>
  <s:Body>
    <s:Fault>
      <s:Code>
        <s:Value>s:Receiver</s:Value>
        <s:Subcode>
          <s:Value>wsrm:CreateSequenceRefused</s:Value>
          <s:Subcode>
            <s:Value>netrm:ConnectionLimitReached</s:Value>
          </s:Subcode>
        </s:Subcode>
      </s:Code>
      <s:Reason>
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>
      </s:Reason>
    </s:Fault>
  </s:Body>
</s:Envelope>
```

### <a name="ws-addressing-faults"></a>WS-Addressing hataları

WS-ReliableMessaging WS-Addressing kullandığından WCF WS-ReliableMessaging uygulamasının WS-Addressing hataları oluşturup iletebileceği. Bu bölümde, WCF 'nin WS-ReliableMessaging katmanında açıkça oluşturduğu ve ilettiği WS-Addressing hataları ele alınmaktadır:

- B1801: WCF aşağıdakilerden biri doğru olduğunda `Message Addressing Header Required` hatasını üretir ve iletir:

  - `CreateSequence`, `CloseSequence` veya `TerminateSequence` iletisinde `MessageId` üstbilgisi eksik.

  - `CreateSequence`, `CloseSequence` veya `TerminateSequence` iletisinde `ReplyTo` üstbilgisi eksik.

  - `CreateSequenceResponse`, `CloseSequenceResponse`veya `TerminateSequenceResponse` iletisinde `RelatesTo` üstbilgisi eksik.

- B1802: WCF, `CreateSequence` iletisindeki adresleme üstbilgilerinin incelenmesi temelinde diziyi işleyebilmesinin bir uç nokta dinleme olmadığını belirten `Endpoint Unavailable` hatasını üretir ve iletir.

## <a name="protocol-composition"></a>Protokol oluşturma

### <a name="composition-with-ws-addressing"></a>WS-Addressing oluşturma

WCF iki WS-Addressing sürümü destekler: WS-Addressing 2004/08 [WS-ADDR] ve W3C WS-Addressing 1,0 önerileri [WS-ADDR-CORE] ve [WS-ADDR-SOAP].

WS-ReliableMessaging belirtiminde yalnızca WS-Addressing 2004/08 bahsetirken, WS-Addressing sürümü kullanılacak şekilde kısıtlanmaz. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- R2101: hem WS-Addressing 2004/08 hem de WS-Addressing 1,0, WS-güvenilir mesajlaşma ile kullanılabilir.

- R2102: tek bir WS-Addressing sürümü, belirli bir WS-ReliableMessaging sırası boyunca veya `Offer` mekanizması kullanılarak bağıntılı bir convero dizileri çifti kullanılmalıdır.

### <a name="composition-with-soap"></a>SOAP ile bileşim

WCF, hem SOAP 1,1 hem de WS-güvenilir mesajlaşma ile SOAP 1,2 kullanımını destekler.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-Security ve WS-SecureConversation ile birleştirme

WCF, güvenli aktarım (HTTPS), WS-Security ile bileşim ve WS-Secure konuşmasıyla bileşim kullanarak WS-ReliableMessaging dizileri için koruma sağlar. WS-ReliableMessaging 1,1 protokolü, WS-güvenlik 1,1 ve WS-Secure konuşma 1,3 Protokolü birlikte kullanılmalıdır. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- R2301: tek tek iletilerin bütünlüğünden ve gizliliğine ek olarak bir WS-ReliableMessaging dizisinin bütünlüğünü korumak Için, WCF WS-Secure konuşmasının kullanılması gerektiğini gerektirir.

- R2302: AWS-Secure konuşma oturumunun, WS-ReliableMessaging sırası kurulmadan önce oluşturulması gerekir.

- R2303: WS-ReliableMessaging dizisi ömrü WS-Secure konuşma oturumunun ömrünü aşarsa, WS-Secure konuşması kullanılarak belirlenen `SecurityContextToken`, karşılık gelen WS-Secure konuşma yenileme bağlaması kullanılarak yenilenmelidir.

- B2304: WS-ReliableMessaging sırası veya bir çift bağıntılı dönüştürme dizisi her zaman tek bir WS-SecureConversation oturumuna bağlanır.

- R2305: WS-Secure konuşmasıyla birlikte kullanıldığında, WCF Yanıtlayıcı `CreateSequence` iletisinin `wsse:SecurityTokenReference` öğesini ve `wsrm:UsesSequenceSTR` üst bilgisini içermesini gerektirir.

 `UsesSequenceSTR` üst bilgisi örneği.

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a>SSL/TLS oturumlarıyla bileşim

WCF, SSL/TLS oturumları ile oluşturmayı desteklemez:

- B2401: WCF `wsrm:UsesSequenceSSL` üstbilgisini oluşturmaz.

- R2402: güvenilir bir mesajlaşma başlatıcısı, WCF Yanıtlayıcıa `wsrm:UsesSequenceSSL` üst bilgisine sahip `CreateSequence` bir ileti göndermemelidir.

### <a name="composition-with-ws-policy"></a>WS-Policy ile birleşim

WCF iki WS-Policy sürümünü destekler: WS-Policy 1,2 ve WS-Policy 1,5.

## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-Ilke onaylama

WCF uç noktalar özelliklerini anlatmak için WS-ReliableMessaging WS-Ilke onaylama `wsrm:RMAssertion` kullanır. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- B3001: WCF `wsrmn:RMAssertion` WS-Policy assertion 'ı `wsdl:binding` öğelerine iliştirir. WCF her iki eki de `wsdl:binding` ve `wsdl:port` öğelerini destekler.

- B3002: WCF `wsp:Optional` etiketini hiçbir şekilde oluşturmaz.

- B3003: `wsrmp:RMAssertion` WS-Policy assertion 'a erişirken, WCF `wsp:Optional` etiketini yoksayar ve WS-RM ilkesini zorunlu olarak değerlendirir.

- R3004: WCF, SSL/TLS oturumları ile oluşturulmadığından, WCF `wsrmp:SequenceTransportSecurity`belirten ilkeyi kabul etmez.

- B3005: WCF her zaman `wsrmp:DeliveryAssurance` öğesini oluşturur.

- B3006: WCF her zaman `wsrmp:ExactlyOnce` teslimat güvencesini belirtir.

- B3007: WCF, WS-ReliableMessaging onaylaması 'nın aşağıdaki özelliklerini oluşturur ve okur ve bunlara WCF`ReliableSessionBindingElement`üzerinde denetim sağlar:

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  Bir `RMAssertion`örneği.

  ```xml
  <wsrmp:RMAssertion>
    <wsp:Policy>
      <wsrmp:SequenceSTR/>
      <wsrmp:DeliveryAssurance>
        <wsp:Policy>
          <wsrmp:ExactlyOnce/>
          <wsrmp:InOrder/>
        </wsp:Policy>
      </wsrmp:DeliveryAssurance>
    </wsp:Policy>
    <netrmp:InactivityTimeout Milliseconds="600000"/>
    <netrmp:AcknowledgementInterval Milliseconds="200"/>
  </wsrmp:RMAssertion>
  ```

## <a name="flow-control-ws-reliablemessaging-extension"></a>Akış denetimi WS-ReliableMessaging uzantısı

WCF, sıralı ileti akışı üzerinde isteğe bağlı ek daha sıkı denetim sağlamak için WS-ReliableMessaging genişletilebilirliği kullanır.

Akış denetimi, <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliği `true`olarak ayarlanarak etkinleştirilir. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- B4001: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF, aşağıdaki örnekte gösterildiği gibi `SequenceAcknowledgement` üstbilgisinin öğe genişletilebilirliği içinde bir `netrm:BufferRemaining` öğesi oluşturur.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4002: güvenilir mesajlaşma akışı denetimi etkin olsa bile, WCF `SequenceAcknowledgement` üst bilgisinde `netrm:BufferRemaining` öğesi gerektirmez.

- B4003: WCF güvenilir mesajlaşma hedefi, kaç yeni iletinin arabelleğe alınacağını göstermek için `netrm:BufferRemaining` kullanır.

- B4004: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF güvenilir mesajlaşma kaynağı ileti aktarımını azaltmak için `netrm:BufferRemaining` değerini kullanır.

- B4005: WCF, dahil 0 ile 4096 arasında `netrm:BufferRemaining` tamsayı değerleri üretir ve 0 ile `xs:int``maxInclusive` değeri 214748364 dahil olmak üzere tamsayı değerlerini okur.

## <a name="message-exchange-patterns"></a>İleti değişimi desenleri

Bu bölümde, WS-ReliableMessaging farklı Ileti değişimi desenleri için kullanıldığında WCF 'nin davranışı açıklanmaktadır. Her Ileti değişim deseninin aşağıdaki iki dağıtım senaryosu göz önünde bulundurulmalıdır:

- Adreslenebilir Başlatıcı: Başlatıcı bir güvenlik duvarının arkasında; Yanıtlayıcı yalnızca HTTP yanıtlarında iletileri başlatıcıya teslim edebilir.

- Adreslenebilir Başlatıcı: Başlatıcı ve Yanıtlayıcı, HTTP istekleri olarak gönderilebilir; diğer bir deyişle, iki listesiyse http bağlantısı kurulabilir.

### <a name="one-way-non-addressable-initiator"></a>Tek yönlü, adreslenebilir olmayan Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, tek bir HTTP kanalı üzerinden tek bir sıra kullanan tek yönlü ileti değişim modelini sağlar. WCF, yanıtlayanın tüm iletilerini başlatıcıdan başlatıcıya iletmek için, başlatıcıdan gelen tüm iletileri yanıtlayan ve HTTP yanıtlarına iletmek üzere HTTP isteklerini kullanır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı, HTTP isteğinde `Offer` öğesi olmayan bir `CreateSequence` iletisi iletir ve HTTP yanıtında `CreateSequenceResponse` iletisi bekler. WCF Yanıtlayıcı bir dizi oluşturur ve `CreateSequenceResponse` iletisini HTTP yanıtında `Accept` öğesi olmadan aktarır.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF başlatıcısı, `CreateSequence` ileti ve hata iletileri hariç tüm iletilerin yanıtı hakkında bildirimleri onaylar. WCF Yanıtlayıcı her zaman HTTP yanıtında tüm sıra ve `AckRequested` iletilerine tek başına bir onay iletir.

#### <a name="closesequence-exchange"></a>CloseSequence değişimi

WCF başlatıcısı HTTP isteğine bir `CloseSequence` iletisi iletir ve HTTP yanıtında `CreateSequenceResponse` iletisi bekler. WCF Yanıtlayıcı, `CloseSequenceResponse` iletisini HTTP yanıtında iletir.

#### <a name="terminatesequence-exchange"></a>TerminateSequence değişimi

WCF başlatıcısı HTTP isteğine bir `TerminateSequence` iletisi iletir ve HTTP yanıtında `TerminateSequenceResponse` iletisi bekler. WCF Yanıtlayıcı, `TerminateSequenceResponse` iletisini HTTP yanıtında iletir.

### <a name="one-way-addressable-initiator"></a>Tek yönlü, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, tek yönlü bir ileti değişim modelini bir gelen ve bir giden HTTP kanalı üzerinden tek bir sıra kullanarak sağlar. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı, HTTP isteğinde `Offer` öğesi olmayan bir `CreateSequence` iletisi iletir. WCF Yanıtlayıcı bir dizi oluşturur ve `CreateSequenceResponse` iletisini bir HTTP isteğindeki `Accept` öğesi olmadan aktarır.

### <a name="duplex-addressable-initiator"></a>Çift yönlü, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, bir gelen ve bir giden HTTP kanalı üzerinden iki sıra kullanan tam zaman uyumsuz, iki yönlü bir ileti değişim modelini sağlar. Bu ileti değişim deseninin `Request/Reply`, `Addressable` Başlatıcı iletisi değişim düzeniyle sınırlı bir şekilde karışık olması. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı bir HTTP isteğindeki `Offer` öğesi ile bir `CreateSequence` iletisi iletir. WCF Yanıtlayıcı, `CreateSequence` bir `Offer` öğesi olmasını sağlar, sonra bir dizi oluşturur ve `CreateSequenceResponse` iletisini bir `Accept` öğesiyle iletir.

#### <a name="sequence-lifetime"></a>Sıra ömrü

WCF iki diziyi bir tam çift yönlü oturum olarak değerlendirir.

Bir sıra hatası oluşturan bir hata üretildiğinde, WCF uzak uç noktanın her iki diziyi de hatasına neden bekler. Bir sıra hata veren bir hata okunduktan sonra, WCF hataları her iki diziyi de sıralar.

WCF, giden sırasını kapatabilir ve gelen sırasındaki iletileri işlemeye devam edebilir. Buna karşılık, WCF gelen sıranın kapatılmasını işleyebilir ve giden sırasına göre iletileri gönderilmeye devam edebilir.

### <a name="request-reply-and-one-way-non-addressable-initiator"></a>İstek-yanıt ve tek yönlü, adreslenebilir olmayan Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, tek yönlü ve istek-yanıt iletisi değişim modelini bir HTTP kanalı üzerinden iki sıra kullanarak sağlar. WCF, yanıtlayanın tüm iletilerini başlatıcıdan başlatıcıya iletmek için, başlatıcıdan gelen tüm iletileri yanıtlayan ve HTTP yanıtlarına iletmek üzere HTTP isteklerini kullanır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı bir HTTP isteğindeki `Offer` öğesi ile bir `CreateSequence` iletisi iletir ve HTTP yanıtında `CreateSequenceResponse` iletisi bekler. WCF Yanıtlayıcı bir dizi oluşturur ve `CreateSequenceResponse` iletisini HTTP yanıtında bir `Accept` öğesi ile iletir.

#### <a name="one-way-message"></a>Tek yönlü Ileti

Tek yönlü bir ileti değişimini başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında tek başına `SequenceAcknowledgement` iletisi alır. `SequenceAcknowledgement` aktarılan iletiyi kabul etmelidir.

WCF Yanıtlayıcı, isteği bir onaylama, hata ya da boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.

#### <a name="two-way-messages"></a>İki yönlü Ileti

İki yönlü ileti değişimi protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında bir yanıt sırası iletisi alır. Yanıt, iletilen istek sırası iletisini bildiren bir `SequenceAcknowledgement` taşımalıdır.

WCF Yanıtlayıcı, isteği bir uygulama Yanıtla, bir hata veya boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.

Tek yönlü iletiler ve uygulama yanıtlarının zamanlaması nedeniyle, istek sırası iletisinin sıra numarası ve yanıt iletisinin sıra numarası bağıntı içermez.

#### <a name="retrying-replies"></a>Yanıtları yeniden deneme

WCF, iki yönlü ileti değişimi Protokolü bağıntısı için HTTP isteği-Yanıtla bağıntısını kullanır. Bu nedenle, WCF başlatıcısı istek sırası iletisi kabul edildiğinde, ancak HTTP yanıtı bir `SequenceAcknowledgement`, uygulama yanıtı veya hata taşımadığında bir istek sırası iletisinin yeniden denenmediğini durdurur. WCF Yanıtlayıcı, yanıtın bağıntılı olduğu isteğin HTTP yanıtında yanıtları yeniden dener.

#### <a name="closesequence-exchange"></a>CloseSequence değişimi

Tüm yanıt sırası iletilerini ve tüm tek yönlü istek sırası iletilerini aldıktan sonra, WCF başlatıcısı bir HTTP isteğindeki istek sırası için bir `CloseSequence` iletisi iletir ve HTTP yanıtında `CloseSequenceResponse` bekler.

İstek dizisinin kapatılması, yanıt sırasını örtük olarak kapatır. Bu, WCF başlatıcısının `CloseSequence` iletisindeki yanıt sırasının son `SequenceAcknowledgement` içerdiği ve yanıt sırasının bir `CloseSequence` Exchange 'e sahip olmadığı anlamına gelir.

WCF Yanıtlayıcı tüm yanıtların kabul edilmesini sağlar ve `CloseSequenceResponse` iletisini HTTP yanıtında iletir.

#### <a name="terminatesequence-exchange"></a>TerminateSequence değişimi

`CloseSequenceResponse` iletisini aldıktan sonra, WCF başlatıcısı bir HTTP isteğindeki istek sırası için bir `TerminateSequence` iletisi iletir ve HTTP yanıtında `TerminateSequenceResponse` bekler.

`CloseSequence` değişimi gibi, istek dizisinin sonlandırılması yanıt sırasını dolaylı olarak sonlandırır. Bu, WCF başlatıcısının `TerminateSequence` iletisindeki yanıt sırasının son `SequenceAcknowledgement` içerdiği ve yanıt sırasının bir `TerminateSequence` Exchange 'e sahip olmadığı anlamına gelir.

WCF Yanıtlayıcı, `TerminateSequenceResponse` iletisini HTTP yanıtında iletir.

### <a name="requestreply-addressable-initiator"></a>İstek/yanıt, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, bir gelen ve bir giden HTTP kanalı üzerinden iki sıra kullanarak istek-yanıt iletisi değişim modelini sağlar. Bu ileti değişim deseninin `Duplex, Addressable` Başlatıcı iletisi değişim düzeniyle sınırlı bir şekilde karışık şekilde karışabilir. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı bir HTTP isteğindeki `Offer` öğesi ile bir `CreateSequence` iletisi iletir. WCF Yanıtlayıcı, `CreateSequence` `Offer` bir öğesi olmasını sağlar ve `CreateSequenceResponse` iletisini bir `Accept` öğesiyle iletir.

#### <a name="requestreply-correlation"></a>İstek/yanıt bağıntısı

Tüm bağıntılı istekler ve yanıtlar için aşağıdakiler geçerlidir:

- WCF, tüm uygulama istek iletilerinin `ReplyTo` bir uç nokta başvurusu ve bir `MessageId`almasını sağlar.

- WCF her bir uygulama isteği iletisinin `ReplyTo`için Yerel uç nokta başvurusunu uygular. Yerel uç nokta başvurusu, başlatıcı için `CreateSequence` iletisinin `ReplyTo` ve yanıtlayanın `CreateSequence` iletisinin `To`.

- WCF, gelen istek iletilerinin bir `MessageId` ve `ReplyTo`almasını sağlar.

- WCF, `ReplyTo` uç nokta başvurusunun tüm uygulama istek iletilerinin URI 'sinin, daha önce tanımlanan yerel uç nokta başvurusuyla eşleştiğinden emin olur.

- WCF, tüm yanıtların, istek/yanıt bağıntı kuralları `wsa` takip eden doğru `RelatesTo` ve `To` üstbilgilerini kapsamasını sağlar.
