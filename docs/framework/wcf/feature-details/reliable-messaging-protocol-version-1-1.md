---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 8ff02bc6953ec1e5030dd0b592a352b7e23ab0d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-messaging-protocol-version-11"></a>Güvenilir Mesajlaşma Protokolü sürüm 1.1
Bu konu, WS-ReliableMessaging için Windows Communication Foundation (WCF) uygulama ayrıntılarını kapsar Şubat 2007 (sürüm 1.1) Protokolü HTTP aktarımı kullanarak birlikte çalışma için gerekli. WCF kısıtlamalar ve bu konuda açıklanan açıklamalar WS-ReliableMessaging belirtimiyle izler. WS-ReliableMessaging sürüm 1.1 protokolünü başlayarak uygulandığını unutmayın [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].  
  
 WS-Protokolü WCF tarafından uygulandığına ReliableMessaging Şubat 2007 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Kolaylık olması için konunun aşağıdaki rolleri kullanır:  
  
-   Başlatıcı: WS güvenilir ileti sırası oluşturması başlatır istemci.  
  
-   Yanıtlayıcı: başlatanın ister hizmeti.  
  
 Bu belgede aşağıdaki tabloda ad alanlarını ve önekleri kullanır.  
  
|önek|Ad Alanı|  
|-|-|  
|wsrm|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|WSP|(WS-Policy 1.2 veya WS-Policy 1.5)|  
  
## <a name="messaging"></a>İleti  
  
### <a name="sequence-creation"></a>Sıra oluşturma  
 WCF uygulayan `CreateSequence` ve `CreateSequenceResponse` güvenilir Mesajlaşma kurmak için iletilerin dizisi. Aşağıdaki kısıtlamalar geçerlidir:  
  
-   B1101: WCF Başlatıcı aynı uç noktası başvuru olarak kullanan `CreateSequence` iletinin `ReplyTo`, `AcksTo` ve `Offer/Endpoint`.  
  
-   R1102: `AcksTo`, `ReplyTo` ve `Offer/Endpoint` endpoint başvuran `CreateSequence` ileti octet-wise eşleşecek şekilde aynı dize Beyanları adresi değerlerle olması gerekir.  
  
    -   WCF Yanıtlayıcı doğrular URI kısmı `AcksTo`, `ReplyTo` ve `Endpoint` uç nokta başvuruları özdeş bir dizisini oluşturmadan önce.  
  
-   R1103: `AcksTo`, `ReplyTo` ve `Offer/Endpoint` endpoint başvuran `CreateSequence` ileti aynı başvurusu parametre kümesine sahip olması gerekir.  
  
    -   WCF zorunlu değildir, ancak bu başvuruyu varsayar parametrelerinin `AcksTo`, `ReplyTo` ve `Offer/Endpoint` endpoint başvuruyor `CreateSequence` özdeş ve kullandığı başvuru parametrelerinden `ReplyTo` için uç nokta başvurusu Katkıda Bulunanlar ve ters sıra iletileri.  
  
-   B1104: WCF Başlatıcı isteğe bağlı oluşturmaz `Expires` veya `Offer/Expires` öğesinde `CreateSequence` ileti.  
  
-   B1105: erişirken `CreateSequence` message, WCF Yanıtlayıcı kullanan `Expires` değeri `CreateSequence` öğesi olarak `Expires` değeri `CreateSequenceResponse` öğesi. Aksi durumda, WCF Yanıtlayıcı okur ve yoksayar `Expires` ve `Offer/Expires` değerleri.  
  
-   B1106: erişirken `CreateSequenceResponse` iletiyi, WCF Başlatıcı okur isteğe bağlı `Expires` değer ancak bunu kullanmaz.  
  
-   B1107: WCF Başlatıcı hem Yanıtlayıcı her zaman isteğe bağlı oluşturmak `IncompleteSequenceBehavior` öğesinde `CreateSequence/Offer` ve `CreateSequenceResponse` öğeleri.  
  
-   B1108: WCF yalnızca kullanır `DiscardFollowingFirstGap` ve `NoDiscard` değerler `IncompleteSequenceBehavior` öğesi.  
  
    -   WS-ReliableMessaging yararlanan `Offer` iki gruplarıdır oturumu form bağıntılı sıraları oluşturmak için bir mekanizma.  
  
-   B1109: Varsa `CreateSequence` içeren bir `Offer` öğesi, tek yönlü WCF Yanıtlayıcı reddeder sunulan dizisi ile yanıt olarak bir `CreateSequenceResponse` olmadan bir `Accept` öğesi.  
  
-   B1110: güvenilir Mesajlaşma Yanıtlayıcı sunulan dizisi reddederse, yeni oluşturulan sıra WCF Başlatıcı hataları.  
  
-   B1111: Varsa `CreateSequence` içermeyen bir `Offer` öğesi, çift yönlü WCF Yanıtlayıcı reddeder sunulan dizisi ile yanıt olarak bir `CreateSequenceRefused` hata.  
  
-   R1112: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `[address]` özelliği `CreateSequenceResponse/Accept/AcksTo` bitiş noktası başvurusu hedef URI eşleşmelidir, `CreateSequence` ileti baytı.  
  
-   R1113: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, Yanıtlayıcı başlatıcıdan akan hem sıraları tüm iletileri gönderileceği aynı uç nokta referansı.  
  
 WCF WS-ReliableMessaging Başlatıcı hem Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır. WCF WS-ReliableMessaging uygulamasını tek yönlü, istek-yanıt ve tam için güvenilir bir oturum sağlar desenleri Mesajlaşma çift yönlü. WS-ReliableMessaging `Offer` mekanizmasını `CreateSequence` ve `CreateSequenceResponse` iki bağıntılı ters dizilerinin ve tüm uç noktaları iletisi için uygun bir oturum protokol sağlar kurun sağlar. WCF güvenlik garantisi uçtan uca koruma oturum tutarlılığı için de dahil olmak üzere oturumunun sağladığından, aynı taraf için yönelik iletilerin aynı hedefe ulaşmasını sağlamak yararlı olur. Bu, "ardışık-yedekleme" dizisi bildirimleri, uygulama iletileri de sağlar. Bu nedenle, kısıtlamaları R1102, R1112 ve R1113 WCF için geçerlidir.  
  
 Örnek olarak bir `CreateSequence` ileti.  
  
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
  
 Örnek olarak bir `CreateSequenceResponse` ileti.  
  
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
  
### <a name="closing-a-sequence"></a>Bir dizi kapatma  
 WCF kullanan `CloseSequence` ve `CloseSequenceResponse` güvenilir Mesajlaşma kaynak tarafından başlatılan bir kapatma iletileri. WCF güvenilir Mesajlaşma hedef kapatma başlatmaz ve WCF güvenilir Mesajlaşma kaynağı güvenilir Mesajlaşma hedef başlatılan bir kapatma desteklemiyor. Aşağıdaki kısıtlamalar geçerlidir:  
  
-   B1201: WCF güvenilir Mesajlaşma kaynağı her zaman gönderir bir `CloseSequence` sırası kapatmaya ileti.  
  
-   B1202: Güvenilir Mesajlaşma kaynak sırası iletilerinin tam aralığının göndermeden önce onay bekler `CloseSequence` ileti.  
  
-   B1203: Güvenilir Mesajlaşma kaynağı her zaman isteğe bağlı içerir `LastMsgNumber` öğesi dizisi iletileri içermediği sürece.  
  
-   R1204: Güvenilir Mesajlaşma hedef kapatma göndererek gerçekleştirmemelidir bir `CloseSequence` ileti.  
  
-   B1205: temel alarak bir `CloseSequence` iletisi, WCF güvenilir Mesajlaşma kaynak sırası eksik olarak değerlendirir ve bir hata gönderir.  
  
 Örnek olarak bir `CloseSequence` ileti.  
  
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
Example CloseSequenceResponse message:  
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
 WCF öncelikli olarak kullandığı `TerminateSequence/TerminateSequenceResponse` tamamladıktan sonra el sıkışma `CloseSequence/CloseSequenceResponse` el sıkışma. WCF güvenilir Mesajlaşma hedef sonlandırma başlatmaz ve güvenilir Mesajlaşma kaynağı güvenilir Mesajlaşma hedef tarafından başlatılan bir sonlandırma desteklemiyor. Aşağıdaki kısıtlamalar geçerlidir:  
  
-   B1301: WCF başlatıcı yalnızca gönderir `TerminateSequence` başarıyla tamamlandıktan sonra ileti `CloseSequence/CloseSequenceResponse` el sıkışma.  
  
-   R1302: WCF doğrular `LastMsgNumber` öğesi tutarlı olduğundan tüm `CloseSequence` ve `TerminateSequence` belirli bir dizi iletileri. Bunun anlamı `LastMsgNumber` ya da tüm mevcut `CloseSequence` ve `TerminateSequence` iletileri ya da mevcut ve tüm aynı `CloseSequence` ve `TerminateSequence` iletileri.  
  
-   B1303: alırken bir `TerminateSequence` sonra ileti `CloseSequence/CloseSequenceResponse` el sıkışması, güvenilir Mesajlaşma hedef yanıt ile bir `TerminateSequenceResponse` ileti. Güvenilir Mesajlaşma kaynak göndermeden önce son bildirim olduğundan `TerminateSequence` ileti, güvenilir Mesajlaşma hedef bilir olmadan emin olabilirsiniz dizisi sona ereceğini ve kaynakları hemen geri kazanır.  
  
-   B1304: alırken bir `TerminateSequence` öncesinde ileti `CloseSequence/CloseSequenceResponse` el sıkışması, WCF güvenilir Mesajlaşma hedef yanıt ile bir `TerminateSequenceResponse` ileti. Güvenilir Mesajlaşma hedef sırada hiçbir tutarsızlıklar olduğunu belirlerse, güvenilir Mesajlaşma hedef önce istemcinin alma olanağı sağlamak için kaynakları, geri kazanma bir uygulama hedef belirtilen süresi bekler Son bildirim. Aksi durumda, güvenilir Mesajlaşma hedef kaynaklar hemen geri kazanır ve uygulama hedef sırası yükselterek şüpheli ile biten gösterir `Faulted` olay.  
  
 Örnek olarak bir `TerminateSequence` ileti.  
  
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
Example TerminateSequenceResponse message:  
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
 Dizilerine uygulama kısıtlamaları listesi aşağıdadır:  
  
-   B1401:WCF oluşturur ve erişimleri sıra numaraları daha yüksek `xs:long`'s en büyük içermeli değer, 9223372036854775807.  
  
 Örnek olarak bir `Sequence` üstbilgi.  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>Bildirim isteği  
 WCF kullanan `AckRequested` tutma mekanizması olarak üstbilgi.  
  
 Örnek olarak bir `AckRequested` üstbilgi.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF WS güvenilir Mesajlaşma içinde sağlanan dizisi bildirimleri için bir "ardışık" mekanizması kullanır. Aşağıdaki kısıtlamalar geçerlidir:  
  
-   R1601: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` üstbilgi dahil edilebilir hedeflenen alıcı aktarılan herhangi bir uygulama iletisi. Uzak uç noktada bir paketle gönderilen erişebilir `SequenceAcknowledgement` üstbilgi.  
  
-   B1602: WCF oluşturmayacak `SequenceAcknowledgement` içeren üstbilgileri `Nack` öğeleri. WCF doğrular ve her `Nack` öğesi bir sıra numarası içeriyor, ancak Aksi halde yoksayar `Nack` öğe ve değer.  
  
 Örnek olarak bir `SequenceAcknowledgement` üstbilgi.  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging hataları  
 WS-ReliableMessaging hataları WCF uygulaması için uygulama kısıtlamaları listesi verilmiştir. Aşağıdaki kısıtlamalar geçerlidir:  
  
-   B1701: WCF oluşturmayacak `MessageNumberRollover` hataları.  
  
-   B1702: hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantı işleyemiyor SOAP 1.2 WCF iç içe bir oluşturur `CreateSequenceRefused` arıza alt kod, `netrm:ConnectionLimitReached`, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
### <a name="ws-addressing-faults"></a>WS-adresleme hataları  
 WS-ReliableMessaging WS adresleme kullandığından, WCF WS-ReliableMessaging uygulama oluşturma ve hatalarını WS adresleme iletme. Bu bölüm, WCF açıkça oluşturur ve WS-ReliableMessaging katmanında iletir WS adresleme hataları kapsar:  
  
-   B1801:WCF oluşturur ve iletir `Message Addressing Header Required` şunlardan biri doğru olduğunda hata:  
  
    -   A `CreateSequence`, `CloseSequence` veya `TerminateSequence` ileti eksik bir `MessageId` üstbilgi.  
  
    -   A `CreateSequence`, `CloseSequence` veya `TerminateSequence` ileti eksik bir `ReplyTo` üstbilgi.  
  
    -   A `CreateSequenceResponse`, `CloseSequenceResponse`, veya `TerminateSequenceResponse` ileti eksik bir `RelatesTo` üstbilgi.  
  
-   B1802:WCF oluşturur ve iletir `Endpoint Unavailable` , dinleme bitiş noktası olduğunu belirtmek için hata adresleme üstbilgilerinde incelenmesi temel sıralı işlem `CreateSequence` ileti.  
  
## <a name="protocol-composition"></a>İletişim kuralı oluşturma  
  
### <a name="composition-with-ws-addressing"></a>WS-adresleme ile oluşturma  
 WCF WS adresleme iki sürümlerini destekler: WS adresleme 2004/08 [WS-ADDR] ve W3C WS adresleme 1.0 önerileri [WS-ADDR-CORE] ve [WS ADDR SOAP].  
  
 While WS-ReliableMessaging belirtimi belirtilenlerden yalnızca WS adresleme 2004/08, onu değil kısıtlamak kullanılacak WS adresleme sürümü. WCF için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   R2101: Hem WS adresleme 2004/08 ve WS adresleme 1.0 WS güvenilir Mesajlaşma ile kullanılabilir.  
  
-   R2102: Belirli bir WS-ReliableMessaging dizi veya ters sıraları kullanarak bağıntılı çifti boyunca WS adresleme tek sürümü kullanılmalıdır `Offer` mekanizması.  
  
### <a name="composition-with-soap"></a>SOAP ile oluşturma  
 WCF SOAP 1.1 ve SOAP 1.2 WS güvenilir Mesajlaşma ile kullanımını destekler.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS güvenliği ve WS-SecureConversation ile oluşturma  
 WCF güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve birleşim WS güvenli Konuşmayla kullanarak WS-ReliableMessaging dizileri için koruma sağlar. WS-ReliableMessaging 1.1 protokolünü, WS-güvenlik 1.1 ve WS güvenli konuşma 1.3 Protokolü birlikte kullanılmalıdır. WCF için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   R2301: bütünlüğü yanı sıra bir WS-ReliableMessaging sırası bütünlüğünü ve tek bir ileti gizliliğini korumak için WCF WS güvenli konuşma kullanılmalıdır gerektirir.  
  
-   R2302:AWS-güvenli konuşma oturum WS-ReliableMessaging sequence(s) kurmadan önce oluşturulması gerekir.  
  
-   R2303: WS-ReliableMessaging ömrü sıra WS güvenli konuşma oturumunun ömrünü aşarsa `SecurityContextToken` WS güvenli konuşma gerekir yenilendi karşılık gelen konuşma yenileme WS güvenli bağlama kullanarak kullanılarak oluşturulmuştur.  
  
-   B2304:WS-ReliableMessaging dizisi veya bağıntılı ters sıraları çifti tek bir WS-SecureConversation oturumla bağlı her zaman.  
  
-   R2305: WS güvenli Konuşmayla oluşur, WCF Yanıtlayıcı gerektiren `CreateSequence` ileti içeren `wsse:SecurityTokenReference` öğesi ve `wsrm:UsesSequenceSTR` üstbilgi.  
  
 Örnek olarak bir `UsesSequenceSTR` üstbilgi.  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>SSL/TLS oturumlarını ile oluşturma  
 WCF ile SSL/TLS oturumları oluşturma desteklemez:  
  
-   B2401: WCF oluşturmayacak `wsrm:UsesSequenceSSL` üstbilgi.  
  
-   R2402: Güvenilir Mesajlaşma Başlatıcı değil göndermelidir bir `CreateSequence` ile ileti bir `wsrm:UsesSequenceSSL` WCF Yanıtlayıcı üstbilgi.  
  
### <a name="composition-with-ws-policy"></a>WS-Policy ile oluşturma  
 WCF WS-Policy iki sürümlerini destekler: WS-Policy 1.2 ve WS-Policy 1.5.  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-ilke onaylama  
 WCF kullanan WS-ReliableMessaging WS-Policy onaylama `wsrm:RMAssertion` uç noktaları özellikleri açıklamak için. WCF için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   B3001: WCF iliştirir `wsrmn:RMAssertion` WS-Policy onaylama `wsdl:binding` öğeleri. WCF destekleyen iki ekleri `wsdl:binding` ve `wsdl:port` öğeleri.  
  
-   B3002: WCF hiçbir zaman oluşturur `wsp:Optional` etiketi.  
  
-   B3003: erişirken `wsrmp:RMAssertion` WS-Policy onaylama WCF yoksayar `wsp:Optional` etiketi ve WS-RM ilkesi zorunlu olarak değerlendirir.  
  
-   R3004: WCF SSL/TLS oturumları oluşturma değil çünkü WCF belirten ilkesini kabul etmiyor `wsrmp:SequenceTransportSecurity`.  
  
-   B3005: WCF oluşturur, her zaman `wsrmp:DeliveryAssurance` öğesi.  
  
-   B3006: WCF her zaman belirtir `wsrmp:ExactlyOnce` teslim güvence.  
  
-   B3007: WCF oluşturur ve WS-ReliableMessaging onaylama aşağıdaki özelliklerini okur ve bunları denetim WCF sunar`ReliableSessionBindingElement`:  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     Örnek olarak bir `RMAssertion`.  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a>Akış Denetim WS-ReliableMessaging uzantısı  
 WCF WS-ReliableMessaging genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.  
  
 Akış denetimi ayarlayarak etkin `ReliableSessionBindingElement`'s `FlowControlEnabled``boolean` özelliğine `true`. WCF için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   B4001: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF oluşturur bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi üstbilgi.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: Güvenilir Mesajlaşma akış denetimi etkin olsa bile, WCF gerektirmez bir `netrm:BufferRemaining` öğesinde `SequenceAcknowledgement` üstbilgi.  
  
-   B4003: WCF güvenilir Mesajlaşma hedef kullanan `netrm:BufferRemaining` kaç tane yeni ona iletileri göstermek için arabellek.  
  
-   B4004:when güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF güvenilir Mesajlaşma kaynağı değerini kullanır `netrm:BufferRemaining` kısıtlama ileti aktarımı için.  
  
-   B4005: WCF oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile 4096 (bunlar dahil) arasında ve tamsayı değerleri 0 arasında okur ve `xs:int`'s `maxInclusive` 214748364 (bunlar dahil) değeri.  
  
## <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 WS-ReliableMessaging farklı ileti Exchange desenler için kullanıldığında, bu bölümde WCF'in davranışını tanımlar. Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları değerlendirilir:  
  
-   Olmayan adreslenebilir Başlatıcı: Başlatıcı duvarıyla korunuyorsa; Yanıtlayıcı iletileri Başlatıcısı yalnızca HTTP yanıtlarını ulaştırabilirsiniz.  
  
-   Adreslenebilir Başlatıcı: HTTP isteklerini Başlatıcı hem Yanıtlayıcı gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantısı kurulabilir.  
  
### <a name="one-way-non-addressable-initiator"></a>Tek yönlü, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF bir HTTP kanalı üzerinden bir sıralı kullanarak bir tek yönlü ileti değişim deseni sağlar. WCF HTTP isteklerini yanıtlayan alınan tüm iletileri Başlatıcı iletmek için tüm iletiler başlatıcıdan Yanıtlayıcı ve HTTP yanıtları iletmek için kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı aktaran bir `CreateSequence` hiçbir ileti `Offer` bir HTTP isteği öğede bekler `CreateSequenceResponse` HTTP yanıt iletisi. WCF Yanıtlayıcı bir sıra oluşturur ve iletir `CreateSequenceResponse` hiçbir ileti `Accept` HTTP yanıtı öğede.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF Başlatıcısı tüm iletileri yanıtlama onayları işler `CreateSequence` iletisi ve hata iletileri. WCF Yanıtlayıcı her zaman tek başına bir bildirim tüm dizisi HTTP yanıtı üzerinde aktarır ve `AckRequested` iletileri.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 WCF Başlatıcı aktaran bir `CloseSequence` bir HTTP isteği iletisi ve bekliyor `CreateSequenceResponse` HTTP yanıt iletisi. WCF Yanıtlayıcı iletir `CloseSequenceResponse` HTTP yanıt iletisi.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 WCF Başlatıcı aktaran bir `TerminateSequence` bir HTTP isteği iletisi ve bekliyor `TerminateSequenceResponse` HTTP yanıt iletisi. WCF Yanıtlayıcı iletir `TerminateSequenceResponse` HTTP yanıt iletisi.  
  
### <a name="one-way-addressable-initiator"></a>Tek yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF sağlayan bir dizi kullanarak bir tek yönlü ileti değişim deseni gelen ve giden bir HTTP kanalı. WCF HTTP isteklerini tüm iletileri iletmek için kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı aktaran bir `CreateSequence` hiçbir ileti `Offer` öğe üzerinde bir HTTP isteği. WCF Yanıtlayıcı bir sıra oluşturur ve iletir `CreateSequenceResponse` hiçbir ileti `Accept` öğe üzerinde bir HTTP isteği.  
  
### <a name="duplex-addressable-initiator"></a>Çift yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF sağlayan iki kullanarak tam olarak zaman uyumsuz, iki yönlü ileti değişim deseni dizilerinin üzerinde bir gelen ve giden bir HTTP kanalı. Bu ileti değişim deseni ile karma `Request/Reply`, `Addressable` sınırlı bir şekilde Başlatıcı ileti değişim deseni. WCF HTTP isteklerini tüm iletileri iletmek için kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı aktaran bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği. WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir `Offer` öğesi, ardından bir sıra oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` öğesi.  
  
#### <a name="sequence-lifetime"></a>Sıra yaşam süresi  
 WCF iki sıraları bir tam çift yönlü oturum olarak değerlendirir.  
  
 Bir dizi hataları bir arıza oluşturma sırasında WCF hem sıraları alınmasını uzak uç nokta bekler. Bir dizi hataları bir arıza okuma sırasında WCF hem sıraları hataları.  
  
 WCF giden sırası kapatın ve gelen sırası iletileri işlemek devam edin. Buna karşılık, WCF gelen sırası kapatma işlemek ve kendi giden sırasını iletileri göndermeye devam eder.  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>İstek-yanıt ve tek yönlü, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 İstek-yanıt ileti değişim deseni iki kullanarak üzerinde bir HTTP kanalı dizilerinin ve WCF tek yönlü sağlar. WCF HTTP isteklerini yanıtlayan alınan tüm iletileri Başlatıcı iletmek için tüm iletiler başlatıcıdan Yanıtlayıcı ve HTTP yanıtları iletmek için kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı aktaran bir `CreateSequence` ile ileti bir `Offer` bir HTTP isteği öğede bekler `CreateSequenceResponse` HTTP yanıt iletisi. WCF Yanıtlayıcı bir sıra oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` HTTP yanıtı öğede.  
  
#### <a name="one-way-message"></a>Tek yönlü iletisi  
 Tek yönlü ileti değişimi başarıyla tamamlamak için WCF Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi. `SequenceAcknowledgement` Aktarılan ileti kabul gerekir.  
  
 WCF Yanıtlayıcı onay, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt isteğine yanıt.  
  
#### <a name="two-way-messages"></a>İki şekilde iletileri  
 İki yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve HTTP yanıtı yanıt sırası iletiyi alır. Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi bildirmeden aktarılan.  
  
 WCF Yanıtlayıcı bir uygulama yanıt, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt isteğine yanıt.  
  
 Tek yönlü iletileri varlığını ve uygulama yanıt zamanlama nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası hiçbir bağıntı sahiptir.  
  
#### <a name="retrying-replies"></a>Yanıt yeniden deneniyor  
 WCF HTTP istek-yanıt bağıntısı iki yönlü ileti exchange Protokolü bağıntı için kullanır. Bu nedenle, WCF Başlatıcı istek sırası iletisi onaylandığında bir istek sırası iletisi yeniden deneniyor durdurmaz ancak yerine HTTP yanıtı zaman taşıyan bir `SequenceAcknowledgement`, uygulama yanıt ya da hata. WCF Yanıtlayıcı yanıt bağıntılı isteğin HTTP yanıtı üzerinde yanıtları yeniden dener.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 Tüm yanıt sırası iletilerinin ve tüm tek yönlü istek sırası iletileri için onayları aldıktan sonra WCF Başlatıcı aktaran bir `CloseSequence` iletisi için bir HTTP isteği istek sırasını ve bekliyor `CloseSequenceResponse` HTTP yanıtı üzerinde.  
  
 İstek sırası örtük olarak kapatılmadan yanıt sırası kapatır. WCF Başlatıcı içerir yanıt sırasının son yani `SequenceAcknowledgement` üzerinde `CloseSequence` ileti ve yanıt sırası yok bir `CloseSequence` exchange.  
  
 WCF Yanıtlayıcı tüm yanıtları onaylanan ve iletir sağlar `CloseSequenceResponse` HTTP yanıt iletisi.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Alındıktan sonra `CloseSequenceResponse` ileti, WCF Başlatıcı iletir bir `TerminateSequence` iletisi için bir HTTP isteği istek sırasını ve bekliyor `TerminateSequenceResponse` HTTP yanıtı üzerinde.  
  
 Gibi `CloseSequence` istek sırası örtük olarak sonlandırma exchange yanıt sırası sonlandırır. WCF Başlatıcı içerir yanıt sırasının son yani `SequenceAcknowledgement` üzerinde `TerminateSequence` ileti ve yanıt sırası yok bir `TerminateSequence` exchange.  
  
 WCF Yanıtlayıcı iletir `TerminateSequenceResponse` HTTP yanıt iletisi.  
  
### <a name="requestreply-addressable-initiator"></a>İstek/yanıt, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF sağlayan iki kullanarak bir istek-yanıt ileti değişim deseni dizilerinin üzerinde bir gelen ve giden bir HTTP kanalı. Bu ileti değişim deseni ile karma `Duplex, Addressable` sınırlı bir şekilde Başlatıcı ileti değişim deseni. WCF HTTP isteklerini tüm iletileri iletmek için kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı aktaran bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği. WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir `Offer` öğesi sonra bir sıra oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` öğesi.  
  
#### <a name="requestreply-correlation"></a>İstek/yanıt bağıntısı  
 Aşağıdaki tüm bağıntılı istekleri ve yanıtları için geçerlidir:  
  
-   WCF sağlar tüm uygulama istek iletileri ayı bir `ReplyTo` bitiş noktası başvurusu ve `MessageId`.  
  
-   WCF geçerlidir yerel uç nokta başvuru her uygulama isteği iletinin `ReplyTo`. Yerel uç nokta başvuru `CreateSequence` iletinin `ReplyTo` başlatıcı ve `CreateSequence` iletinin `To` Yanıtlayıcı için.  
  
-   WCF sağlar, gelen istek iletileri ayı bir `MessageId` ve `ReplyTo`.  
  
-   WCF sağlar `ReplyTo` daha önce tanımlanan tüm uygulama istek iletilerini uç nokta referansının URI'sini eşleşen yerel uç nokta başvuru.  
  
-   WCF sağlar tüm yanıtlar doğru ayı `RelatesTo` ve `To` aşağıdaki üstbilgileri `wsa` bağıntı kuralları istek/yanıt.
