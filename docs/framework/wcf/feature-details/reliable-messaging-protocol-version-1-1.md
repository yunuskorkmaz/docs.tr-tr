---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: ad0a77842c10965749eab4e76bb123938e07e9d5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144727"
---
# <a name="reliable-messaging-protocol-version-11"></a>Güvenilir Mesajlaşma Protokolü sürüm 1.1

Bu konuda, HTTP taşıması kullanılarak birlikte çalışabilirlik için gereken WS-ReliableMessaging Şubat 2007 (sürüm 1,1) protokolü için Windows Communication Foundation (WCF) uygulama ayrıntıları ele alınmaktadır. WCF, bu konuda açıklanan kısıtlamalar ve açıklamalar ile WS-ReliableMessaging belirtimini izler. WS-ReliableMessaging sürüm 1,1 protokolünün .NET Framework 3,5 ' den başlayarak uygulandığını unutmayın.

WS-ReliableMessaging Şubat 2007 protokolü, tarafından WCF 'de uygulanır <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .

Kolaylık olması için, konusu aşağıdaki rolleri kullanır:

- Başlatıcı: WS-güvenilir Ileti sırası oluşturmayı Başlatan istemci.

- Yanıtlayıcı: başlatıcısının isteklerini alan hizmet.

 Bu belge aşağıdaki tablodaki ön ekleri ve ad alanlarını kullanır.

|Ön ek|Ad Alanı|
|-|-|
|WSRM|`http://docs.oasis-open.org/ws-rx/wsrm/200702`|
|Netra|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|WSA|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|WSO|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|
|wsrmp|`http://docs.oasis-open.org/ws-rx/wsrmp/200702`|
|netrmp|`http://schemas.microsoft.com/ws-rx/wsrmp/200702`|
|WSP|(WS-Policy 1,2 ya da WS-Policy 1,5)|

## <a name="messaging"></a>Mesajlaşma

### <a name="sequence-creation"></a>Sıra oluşturma

WCF `CreateSequence` , `CreateSequenceResponse` güvenilir bir mesajlaşma sırası oluşturmak için ve iletilerini uygular. Aşağıdaki kısıtlamalar geçerlidir:

- B1101: WCF başlatıcısı, `CreateSequence` ileti `ReplyTo` `AcksTo` ve ile aynı uç nokta başvurusunu kullanır `Offer/Endpoint` .

- R1102: `AcksTo` `ReplyTo` `Offer/Endpoint` ileti içindeki ve uç nokta başvurularının, `CreateSequence` sekizli temelinde eşleşecek şekilde özdeş dize gösterimlerine sahip adres değerleri olmalıdır.

  - WCF Yanıtlayıcı, `AcksTo` `ReplyTo` `Endpoint` bir sıra oluşturmadan önce ve uç nokta başvurularının URI bölümünün özdeş olduğunu doğrular.

- R1103: `AcksTo` `ReplyTo` `Offer/Endpoint` ileti içindeki ve uç nokta başvuruları `CreateSequence` aynı başvuru parametreleri kümesine sahip olmalıdır.

  - WCF zorunlu değildir, ancak ' ın başvuru parametrelerinin `AcksTo` `ReplyTo` ve `Offer/Endpoint` bitiş noktası başvurularının aynı olduğunu varsayar `CreateSequence` ve, `ReplyTo` bildirimlerin ve listesiyse iletileri için uç nokta başvurusundan başvuru parametrelerini kullanır.

- B1104: WCF Başlatıcısı `Expires` ileti içinde isteğe bağlı veya öğe oluşturmaz `Offer/Expires` `CreateSequence` .

- B1105: `CreateSequence` iletiye erişirken, WCF Yanıtlayıcı öğesindeki `Expires` değeri `CreateSequence` `Expires` öğesindeki değer olarak kullanır `CreateSequenceResponse` . Aksi takdirde, WCF Yanıtlayıcı ve değerlerini okur ve `Expires` yoksayar `Offer/Expires` .

- B1106: `CreateSequenceResponse` iletiye erişirken, WCF başlatıcısı isteğe bağlı değeri okur, `Expires` ancak kullanmaz.

- B1107: WCF başlatıcısı ve Yanıtlayıcı her zaman `IncompleteSequenceBehavior` ve öğelerinde isteğe bağlı öğesini oluşturur `CreateSequence/Offer` `CreateSequenceResponse` .

- B1108: WCF yalnızca `DiscardFollowingFirstGap` `NoDiscard` öğesi içindeki ve değerlerini kullanır `IncompleteSequenceBehavior` .

  - WS-ReliableMessaging, `Offer` bir oturum oluşturan iki dönüştürüce bağıntılı diziyi oluşturmak için mekanizmayı kullanır.

- B1109: `CreateSequence` bir öğesi varsa `Offer` , WCF Yanıtlayıcının bir öğesi olmadan bir ile yanıt vererek sunulan sırayı reddettiğini bir şekilde alır `CreateSequenceResponse` `Accept` .

- B1110: güvenilir bir mesajlaşma Yanıtlayıcısı sunulan sırayı reddederse, WCF başlatıcısı yeni oluşturulan sırayı hata.

- B1111: `CreateSequence` bir `Offer` öğesi içermiyorsa, ıkı yönlü WCF Yanıtlayıcısı bir hatayla yanıt vererek sunulan sırayı reddeder `CreateSequenceRefused` .

- R1112: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , `[address]` `CreateSequenceResponse/Accept/AcksTo` uç nokta başvurusunun özelliği `CreateSequence` byte için ileti baytının hedef URI 'siyle eşleşmelidir.

- R1113: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , her iki sıranın üzerindeki tüm iletilerin aynı uç nokta başvurusuna gönderilmesi gerekir.

WCF, başlatıcı ve Yanıtlayıcı arasında güvenilir oturumlar oluşturmak için WS-ReliableMessaging kullanır. WCF WS-ReliableMessaging uygulamasının tek yönlü, istek-yanıt ve tam çift yönlü mesajlaşma desenleri için güvenilir bir oturum sağlar. Ve üzerindeki WS-ReliableMessaging `Offer` mekanizması `CreateSequence` , `CreateSequenceResponse` iki bağıntılı dönüştürme dizisi ayarlamanıza ve tüm ileti uç noktaları için uygun bir oturum Protokolü sağlar. WCF, oturum bütünlüğü için uçtan uca koruma dahil olmak üzere bu tür bir oturum için güvenlik garantisi sağladığından, aynı tarafa yönelik iletilerin aynı hedefe ulaşmasını sağlamak yararlıdır. Bu Ayrıca, uygulama iletilerinde "Piggy-," sıralı bildirimleri de sağlar. Bu nedenle, R1102, R1112 ve R1113 kısıtlamaları WCF için geçerlidir.

`CreateSequence`İleti örneği.

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

`CreateSequenceResponse`İleti örneği.

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

WCF, `CloseSequence` `CloseSequenceResponse` güvenilir bir mesajlaşma kaynağı tarafından başlatılan kapatmalar için ve iletilerini kullanır. WCF güvenilir mesajlaşma hedefi kapatmaları başlatmaz ve WCF güvenilir mesajlaşma kaynağı, güvenilir mesajlaşma hedefi ile başlatılan bir kapanışı desteklemez. Aşağıdaki kısıtlamalar geçerlidir:

- B1201: WCF güvenilir mesajlaşma kaynağı, `CloseSequence` diziyi kapatmak için her zaman bir ileti gönderir.

- B1202: güvenilir mesajlaşma kaynağı iletiyi göndermeden önce tam dizi iletilerinin onay istemini bekler `CloseSequence` .

- B1203: güvenilir mesajlaşma kaynağı, dizi ileti içermiyorsa her zaman isteğe bağlı `LastMsgNumber` öğeyi içerir.

- R1204: güvenilir mesajlaşma hedefi bir ileti göndererek kapatmaları başlatmamalıdır `CloseSequence` .

- B1205: bir ileti alındıktan sonra `CloseSequence` , WCF güvenilir mesajlaşma kaynağı, diziyi tamamlanmamış olarak değerlendirir ve bir hata gönderir.

 `CloseSequence`İleti örneği.

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

Örnek `CloseSequenceResponse` ileti:

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

WCF öncelikle `TerminateSequence/TerminateSequenceResponse` el sıkışma tamamlandıktan sonra el sıkışmasını kullanır `CloseSequence/CloseSequenceResponse` . WCF güvenilir mesajlaşma hedefi sonlandırmayı başlatmaz ve güvenilir mesajlaşma kaynağı, güvenilir bir mesajlaşma hedefi tarafından başlatılan sonlandırmayı desteklemez. Aşağıdaki kısıtlamalar geçerlidir:

- B1301: WCF başlatıcısı yalnızca `TerminateSequence` el sıkışma başarıyla tamamlandıktan sonra iletiyi gönderir `CloseSequence/CloseSequenceResponse` .

- R1302: WCF, `LastMsgNumber` `CloseSequence` `TerminateSequence` belirtilen bir sıra için, öğenin tüm ve iletileri arasında tutarlı olduğunu doğrular. Bu, `LastMsgNumber` tüm `CloseSequence` ve `TerminateSequence` iletilerde bulunmayan ya da tüm `CloseSequence` ve iletilerle aynı `TerminateSequence` olduğu anlamına gelir.

- B1303: `TerminateSequence` el sıkışma sonrasında bir ileti alındığında `CloseSequence/CloseSequenceResponse` , güvenilir mesajlaşma hedefi bir iletiyle yanıt verir `TerminateSequenceResponse` . Güvenilir Mesajlaşma kaynağında iletiyi göndermeden önce son onay bulunduğundan `TerminateSequence` , güvenilir mesajlaşma hedefi, dizinin bittiğini şüpheli olmadan bilir ve kaynakları hemen geri kazanır.

- B1304: `TerminateSequence` El sıkışmadan önce bir ileti alındığında `CloseSequence/CloseSequenceResponse` , WCF güvenilir mesajlaşma hedefi bir iletiyle yanıt verir `TerminateSequenceResponse` . Güvenilir Mesajlaşma hedefi dizide herhangi bir tutarsızlık olmadığını belirlerse, güvenilir mesajlaşma hedefi, istemcinin son onayı almasına izin vermek için, geri kazanma kaynaklarından önce uygulama hedefi belirtilen bir süre bekler. Aksi takdirde, güvenilir mesajlaşma hedefi geri kazanır kaynakları hemen ve olay, etkinliğin bir hata vererek şüpheli şekilde sona erdiğini uygulamanın hedefini gösterir `Faulted` .

`TerminateSequence`İleti örneği.

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

Örnek `TerminateSequenceResponse` ileti:

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

- B1401: WCF `xs:long` , en yüksek kapsamlı değer olan 9223372036854775807 ' den fazla olmayan sıra numarası üretir ve erişir.

`Sequence`Üst bilgi örneği.

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a>İstek onayı

WCF `AckRequested` üstbilgiyi etkin tut mekanizması olarak kullanır.

`AckRequested`Üst bilgi örneği.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF, WS-güvenilir mesajlaşmada belirtilen sıra bildirimleri için bir "Piggy-Back" mekanizması kullanır. Aşağıdaki kısıtlamalar geçerlidir:

- R1601: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , `SequenceAcknowledgement` üst bilgi, istenen alıcıya iletilen herhangi bir uygulama iletisine dahil edilebilir. Uzak uç noktanın, bir pıof tarafından desteklenen bir üstbilgiye erişebilmesi gerekir `SequenceAcknowledgement` .

- B1602: WCF `SequenceAcknowledgement` öğeleri içeren üst bilgiler oluşturmaz `Nack` . WCF her `Nack` bir öğenin bir sıra numarası içerdiğini doğrular, aksi takdirde `Nack` öğe ve değeri yoksayar.

 `SequenceAcknowledgement`Üst bilgi örneği.

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging hataları

WS-ReliableMessaging hatalarının WCF uygulaması için uygulanan kısıtlamaların listesi aşağıda verilmiştir. Aşağıdaki kısıtlamalar geçerlidir:

- B1701: WCF `MessageNumberRollover` hata oluşturmaz.

- B1702: SOAP 1,2 üzerinde, hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantıları işleyemezse, WCF `CreateSequenceRefused` `netrm:ConnectionLimitReached` Aşağıdaki örnekte gösterildiği gibi iç içe geçmiş bir hata alt kodu oluşturur.

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

- B1801: WCF, `Message Addressing Header Required` aşağıdakilerden biri doğru olduğunda hatayı oluşturur ve iletir:

  - Bir `CreateSequence` `CloseSequence` veya `TerminateSequence` iletisinde `MessageId` üstbilgi eksik.

  - Bir `CreateSequence` `CloseSequence` veya `TerminateSequence` iletisinde `ReplyTo` üstbilgi eksik.

  - Bir `CreateSequenceResponse` , `CloseSequenceResponse` veya `TerminateSequenceResponse` iletisinde `RelatesTo` üst bilgi eksik.

- B1802: WCF hatayı üretir ve iletir `Endpoint Unavailable` . Bu, iletideki adresleme üstbilgilerinin incelenmesi temelinde diziyi işleyebilmesinin bir uç nokta dinleme olmadığını gösterir `CreateSequence` .

## <a name="protocol-composition"></a>Protokol oluşturma

### <a name="composition-with-ws-addressing"></a>WS-Addressing oluşturma

WCF iki WS-Addressing sürümü destekler: WS-Addressing 2004/08 [WS-ADDR] ve W3C WS-Addressing 1,0 önerileri [WS-ADDR-CORE] ve [WS-ADDR-SOAP].

WS-ReliableMessaging belirtiminde yalnızca WS-Addressing 2004/08 bahsetirken, WS-Addressing sürümü kullanılacak şekilde kısıtlanmaz. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- R2101: hem WS-Addressing 2004/08 hem de WS-Addressing 1,0, WS-güvenilir mesajlaşma ile kullanılabilir.

- R2102: tek bir WS-Addressing sürümü, belirli bir WS-ReliableMessaging sırası boyunca veya mekanizması kullanılarak bağıntılı bir convero dizileri çifti kullanılmalıdır `Offer` .

### <a name="composition-with-soap"></a>SOAP ile bileşim

WCF, hem SOAP 1,1 hem de WS-güvenilir mesajlaşma ile SOAP 1,2 kullanımını destekler.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-Security ve WS-SecureConversation ile birleştirme

WCF, güvenli aktarım (HTTPS), WS-Security ile bileşim ve WS-Secure konuşmasıyla bileşim kullanarak WS-ReliableMessaging dizileri için koruma sağlar. WS-ReliableMessaging 1,1 protokolü, WS-güvenlik 1,1 ve WS-Secure konuşma 1,3 Protokolü birlikte kullanılmalıdır. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- R2301: tek tek iletilerin bütünlüğünden ve gizliliğine ek olarak bir WS-ReliableMessaging dizisinin bütünlüğünü korumak Için, WCF WS-Secure konuşmasının kullanılması gerektiğini gerektirir.

- R2302: AWS-Secure konuşma oturumunun, WS-ReliableMessaging sırası kurulmadan önce oluşturulması gerekir.

- R2303: WS-ReliableMessaging dizisi ömrü WS-Secure konuşma oturumunun ömrünü aşarsa, WS-Secure konuşma `SecurityContextToken` kullanılarak belirlenen, karşılık gelen WS-Secure konuşma yenileme bağlaması kullanılarak yenilenir.

- B2304: WS-ReliableMessaging sırası veya bir çift bağıntılı dönüştürme dizisi her zaman tek bir WS-SecureConversation oturumuna bağlanır.

- R2305: WS-Secure konuşmasıyla birlikte kullanıldığında, WCF Yanıtlayıcı `CreateSequence` iletinin `wsse:SecurityTokenReference` öğesini ve başlığını içermesini gerektirir `wsrm:UsesSequenceSTR` .

 `UsesSequenceSTR`Üst bilgi örneği.

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a>SSL/TLS oturumlarıyla bileşim

WCF, SSL/TLS oturumları ile oluşturmayı desteklemez:

- B2401: WCF `wsrm:UsesSequenceSSL` üstbilgiyi oluşturmaz.

- R2402: güvenilir bir mesajlaşma Başlatıcısı `CreateSequence` , `wsrm:UsesSequenceSSL` bir WCF Yanıtlayıcının üst bilgisine sahip bir ileti göndermemelidir.

### <a name="composition-with-ws-policy"></a>WS-Policy ile birleşim

WCF iki WS-Policy sürümünü destekler: WS-Policy 1,2 ve WS-Policy 1,5.

## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-Ilke onaylama

WCF, uç nokta yeteneklerini belirtmek için WS-ReliableMessaging WS-Ilke onaylama Işlemi kullanır `wsrm:RMAssertion` . WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- B3001: WCF `wsrmn:RMAssertion` WS-Policy onay onayını `wsdl:binding` öğelere iliştirir. WCF her iki Eki `wsdl:binding` ve `wsdl:port` öğelerini destekler.

- B3002: WCF hiçbir şekilde `wsp:Optional` etiket oluşturmaz.

- B3003: `wsrmp:RMAssertion` WS-Policy assertion 'a erişirken, WCF `wsp:Optional` etiketi YOKSAYAR ve WS-RM ilkesini zorunlu olarak değerlendirir.

- R3004: WCF, SSL/TLS oturumları ile oluşturulmadığından, WCF tarafından belirten ilkeyi kabul etmez `wsrmp:SequenceTransportSecurity` .

- B3005: WCF her zaman `wsrmp:DeliveryAssurance` öğesini oluşturur.

- B3006: WCF her zaman `wsrmp:ExactlyOnce` Teslimat güvencesini belirtir.

- B3007: WCF, WS-ReliableMessaging onaylaması 'nın aşağıdaki özelliklerini oluşturur ve okur ve WCF üzerinde denetim sağlar `ReliableSessionBindingElement` :

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  Bir örneği `RMAssertion` .

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

Akış denetimi <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliği olarak ayarlanarak etkinleştirilir `true` . WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- B4001: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF, `netrm:BufferRemaining` `SequenceAcknowledgement` Aşağıdaki örnekte gösterildiği gibi, üstbilginin öğe genişletilebilirliği içinde bir öğe oluşturur.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4002: güvenilir mesajlaşma akışı denetimi etkin olsa bile, WCF `netrm:BufferRemaining` üst bilgide bir öğe gerektirmez `SequenceAcknowledgement` .

- B4003: WCF güvenilir mesajlaşma hedefi `netrm:BufferRemaining` , kaç yeni iletinin arabelleğe alınacağını göstermek için kullanır.

- B4004: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF güvenilir mesajlaşma kaynağı `netrm:BufferRemaining` ileti aktarımını azaltmak için değerini kullanır.

- B4005: WCF `netrm:BufferRemaining` , dahil 0 ve 4096 arasında tamsayı değerler üretir ve 0 214748364 ile arasında bir tamsayı değeri okur `xs:int` `maxInclusive` .

## <a name="message-exchange-patterns"></a>İleti değişimi desenleri

Bu bölümde, WS-ReliableMessaging farklı Ileti değişimi desenleri için kullanıldığında WCF 'nin davranışı açıklanmaktadır. Her Ileti değişim deseninin aşağıdaki iki dağıtım senaryosu göz önünde bulundurulmalıdır:

- Adreslenebilir Başlatıcı: Başlatıcı bir güvenlik duvarının arkasında; Yanıtlayıcı yalnızca HTTP yanıtlarında iletileri başlatıcıya teslim edebilir.

- Adreslenebilir Başlatıcı: Başlatıcı ve Yanıtlayıcı, HTTP istekleri olarak gönderilebilir; diğer bir deyişle, iki listesiyse http bağlantısı kurulabilir.

### <a name="one-way-non-addressable-initiator"></a>Tek yönlü, adreslenebilir olmayan Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, tek bir HTTP kanalı üzerinden tek bir sıra kullanan tek yönlü ileti değişim modelini sağlar. WCF, yanıtlayanın tüm iletilerini başlatıcıdan başlatıcıya iletmek için, başlatıcıdan gelen tüm iletileri yanıtlayan ve HTTP yanıtlarına iletmek üzere HTTP isteklerini kullanır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF Başlatıcısı `CreateSequence` http isteğinde hiçbir öğe içermeyen bir ileti iletir `Offer` ve `CreateSequenceResponse` http yanıtında ileti bekler. WCF Yanıtlayıcı bir sıra oluşturur ve `CreateSequenceResponse` ILETIYI `Accept` http yanıtında hiçbir öğe olmadan iletir.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF başlatıcısı, `CreateSequence` ileti ve hata iletileri hariç tüm iletilerin yanıtı hakkında bildirimleri işler. WCF Yanıtlayıcı her zaman HTTP yanıtında tüm sıra ve iletilere tek başına bir onay aktarır `AckRequested` .

#### <a name="closesequence-exchange"></a>CloseSequence değişimi

WCF Başlatıcısı `CloseSequence` HTTP isteğine bir ileti iletir ve `CreateSequenceResponse` http yanıtında ileti bekler. WCF Yanıtlayıcı `CloseSequenceResponse` ILETIYI http yanıtında iletir.

#### <a name="terminatesequence-exchange"></a>TerminateSequence değişimi

WCF Başlatıcısı `TerminateSequence` HTTP isteğine bir ileti iletir ve `TerminateSequenceResponse` http yanıtında ileti bekler. WCF Yanıtlayıcı `TerminateSequenceResponse` ILETIYI http yanıtında iletir.

### <a name="one-way-addressable-initiator"></a>Tek yönlü, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, tek yönlü bir ileti değişim modelini bir gelen ve bir giden HTTP kanalı üzerinden tek bir sıra kullanarak sağlar. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı, `CreateSequence` http isteğinde hiçbir öğe bulunmayan bir ileti iletir `Offer` . WCF Yanıtlayıcı bir dizi oluşturur ve `CreateSequenceResponse` iletiyi `Accept` bir http isteği üzerinde hiçbir öğe olmadan iletir.

### <a name="duplex-addressable-initiator"></a>Çift yönlü, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, bir gelen ve bir giden HTTP kanalı üzerinden iki sıra kullanan tam zaman uyumsuz, iki yönlü bir ileti değişim modelini sağlar. Bu ileti değişim `Request/Reply` `Addressable` şekli, Başlatıcı ileti değişim düzeniyle sınırlı bir şekilde karışık olabilir. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı bir `CreateSequence` http isteğindeki öğesi ile bir ileti iletir `Offer` . WCF Yanıtlayıcı `CreateSequence` öğesinin bir öğesi olmasını sağlar `Offer` , sonra bir dizi oluşturur ve `CreateSequenceResponse` iletiyi bir öğesi ile iletir `Accept` .

#### <a name="sequence-lifetime"></a>Sıra ömrü

WCF iki diziyi bir tam çift yönlü oturum olarak değerlendirir.

Bir sıra hatası oluşturan bir hata üretildiğinde, WCF uzak uç noktanın her iki diziyi de hatasına neden bekler. Bir sıra hata veren bir hata okunduktan sonra, WCF hataları her iki diziyi de sıralar.

WCF, giden sırasını kapatabilir ve gelen sırasındaki iletileri işlemeye devam edebilir. Buna karşılık, WCF gelen sıranın kapatılmasını işleyebilir ve giden sırasına göre iletileri gönderilmeye devam edebilir.

### <a name="request-reply-and-one-way-non-addressable-initiator"></a>İstek-yanıt ve tek yönlü, adreslenebilir olmayan Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, tek yönlü ve istek-yanıt iletisi değişim modelini bir HTTP kanalı üzerinden iki sıra kullanarak sağlar. WCF, yanıtlayanın tüm iletilerini başlatıcıdan başlatıcıya iletmek için, başlatıcıdan gelen tüm iletileri yanıtlayan ve HTTP yanıtlarına iletmek üzere HTTP isteklerini kullanır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı bir `CreateSequence` http isteğindeki öğesi olan bir ileti iletir `Offer` ve `CreateSequenceResponse` http yanıtında ileti bekler. WCF Yanıtlayıcı bir dizi oluşturur ve `CreateSequenceResponse` ILETIYI `Accept` http yanıtında bir öğe ile iletir.

#### <a name="one-way-message"></a>Tek yönlü Ileti

Tek yönlü bir ileti değişimini başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında tek başına bir ileti alır `SequenceAcknowledgement` . , `SequenceAcknowledgement` İletilen iletiyi kabul etmelidir.

WCF Yanıtlayıcı, isteği bir onaylama, hata ya da boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.

#### <a name="two-way-messages"></a>İki yönlü Ileti

İki yönlü ileti değişimi protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında bir yanıt sırası iletisi alır. Yanıt, `SequenceAcknowledgement` iletilen istek sırası iletisini bildiren bir ileti taşımalıdır.

WCF Yanıtlayıcı, isteği bir uygulama Yanıtla, bir hata veya boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.

Tek yönlü iletiler ve uygulama yanıtlarının zamanlaması nedeniyle, istek sırası iletisinin sıra numarası ve yanıt iletisinin sıra numarası bağıntı içermez.

#### <a name="retrying-replies"></a>Yanıtları yeniden deneme

WCF, iki yönlü ileti değişimi Protokolü bağıntısı için HTTP isteği-Yanıtla bağıntısını kullanır. Bu nedenle, WCF başlatıcısı istek sırası iletisi kabul edildiğinde, ancak HTTP yanıtı bir `SequenceAcknowledgement` , uygulama yanıtı veya hata taşımadığında bir istek sırası iletisini yeniden denemeyi durdurmaz. WCF Yanıtlayıcı, yanıtın bağıntılı olduğu isteğin HTTP yanıtında yanıtları yeniden dener.

#### <a name="closesequence-exchange"></a>CloseSequence değişimi

Tüm yanıt sırası iletilerini ve tüm tek yönlü istek sırası iletilerini aldıktan sonra, WCF Başlatıcısı `CloseSequence` istek sırası için BIR http isteği iletisi iletir ve `CloseSequenceResponse` http yanıtı üzerinde bekler.

İstek dizisinin kapatılması, yanıt sırasını örtük olarak kapatır. Bu, WCF başlatıcısının ileti üzerine yanıt sırasının son halini içerdiği `SequenceAcknowledgement` `CloseSequence` ve yanıt sırasının bir Exchange 'e sahip olmadığı anlamına gelir `CloseSequence` .

WCF Yanıtlayıcı tüm yanıtların kabul edilmesini sağlar ve `CloseSequenceResponse` ILETIYI http yanıtında iletir.

#### <a name="terminatesequence-exchange"></a>TerminateSequence değişimi

İleti alındıktan sonra `CloseSequenceResponse` , WCF Başlatıcısı `TerminateSequence` istek sırası IÇIN bir HTTP isteğine bir ileti ILETIR ve `TerminateSequenceResponse` http yanıtı üzerinde bekler.

Exchange gibi `CloseSequence` , istek dizisinin sonlandırılması yanıt sırasını örtük olarak sonlandırır. Bu, WCF başlatıcısının ileti üzerine yanıt sırasının son halini içerdiği `SequenceAcknowledgement` `TerminateSequence` ve yanıt sırasının bir Exchange 'e sahip olmadığı anlamına gelir `TerminateSequence` .

WCF Yanıtlayıcı `TerminateSequenceResponse` ILETIYI http yanıtında iletir.

### <a name="requestreply-addressable-initiator"></a>İstek/yanıt, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, bir gelen ve bir giden HTTP kanalı üzerinden iki sıra kullanarak istek-yanıt iletisi değişim modelini sağlar. Bu ileti değişim deseninin, `Duplex, Addressable` Başlatıcı iletisi değişim düzeniyle sınırlı bir şekilde karışık olması olabilir. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı bir `CreateSequence` http isteğindeki öğesi ile bir ileti iletir `Offer` . WCF Yanıtlayıcı, `CreateSequence` `Offer` öğesinin bir öğesi olmasını ve iletiyi bir öğe ile iletmesini sağlar `CreateSequenceResponse` `Accept` .

#### <a name="requestreply-correlation"></a>İstek/yanıt bağıntısı

Tüm bağıntılı istekler ve yanıtlar için aşağıdakiler geçerlidir:

- WCF, tüm uygulama istek iletilerinin bir `ReplyTo` uç nokta başvurusu ve bir almasını sağlar `MessageId` .

- WCF her uygulama isteği iletisi için Yerel uç nokta başvurusunu uygular `ReplyTo` . Yerel uç nokta başvurusu, `CreateSequence` `ReplyTo` Başlatıcı için Ileti ve `CreateSequence` `To` yanıtlayanın iletisi olur.

- WCF gelen istek iletilerinin bir `MessageId` ve bir almasını sağlar `ReplyTo` .

- WCF, `ReplyTo` tüm uygulama istek ILETILERININ URI 'sinin, daha önce tanımlanan yerel uç nokta başvurusuyla eşleştiğinden emin olmanızı sağlar.

- WCF, tüm yanıtların `RelatesTo` `To` `wsa` istek/yanıt bağıntı kurallarını izleyen doğru ve üst bilgileri kapsamasını sağlar.
