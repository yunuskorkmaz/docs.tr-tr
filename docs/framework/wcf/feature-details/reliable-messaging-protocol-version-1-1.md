---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 6b8732e0b48797c219b53bb8bf70e1ba57e25c42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933997"
---
# <a name="reliable-messaging-protocol-version-11"></a>Güvenilir Mesajlaşma Protokolü sürüm 1.1
Bu konu, Windows Communication Foundation (WCF) uygulama ayrıntılarını WS-ReliableMessaging içermektedir. Şubat 2007 (sürüm 1.1) Protokolü HTTP aktarımı kullanarak birlikte çalışma için gerekli. WCF WS-ReliableMessaging kısıtlamaları ve bu konuda açıklanan açıklamalar izler. İle başlayarak WS-ReliableMessaging sürüm 1.1 protokolünü uygulandığını unutmayın [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].  
  
 WS-ReliableMessaging protokolü WCF uygulandığına Şubat 2007 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Kolaylık olması için konunun aşağıdaki rolleri kullanır:  
  
-   Başlatan: WS güvenilir ileti sırası oluşturma başlatan istemci.  
  
-   Yanıtlayıcı: Hizmet başlatanın isteği alır.  
  
 Bu belge, aşağıdaki tabloda ad alanlarını ve önekleri kullanır.  
  
|Ön eki|Ad Alanı|  
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
  
### <a name="sequence-creation"></a>Dizisi oluşturma  
 WCF uygulayan `CreateSequence` ve `CreateSequenceResponse` iletileri güvenilir bir Mesajlaşma kurmak için sıra. Aşağıdaki kısıtlamalar uygulanır:  
  
-   B1101: WCF başlatıcı olarak aynı uç nokta başvurusu kullanır `CreateSequence` iletinin `ReplyTo`, `AcksTo` ve `Offer/Endpoint`.  
  
-   R1102: `AcksTo`, `ReplyTo` Ve `Offer/Endpoint` uç nokta başvurularının `CreateSequence` ileti octet-wise eşleşecek şekilde aynı dize temsilleri adresi değerlerle sahip olmalıdır.  
  
    -   WCF Yanıtlayıcı doğrular URI kısmı `AcksTo`, `ReplyTo` ve `Endpoint` uç nokta başvuruları özdeş bir dizisini oluşturmadan önce.  
  
-   R1103: `AcksTo`, `ReplyTo` Ve `Offer/Endpoint` uç nokta başvurularının `CreateSequence` ileti başvuru parametrelerinin aynı olmalıdır.  
  
    -   WCF zorunlu değildir, ancak bu başvuruyu varsayar parametrelerinin `AcksTo`, `ReplyTo` ve `Offer/Endpoint` uç nokta başvuruda bulunan `CreateSequence` aynıdır ve başvuru parametreleri kullanan `ReplyTo` için uç nokta başvurusu onayları ve ters sıra iletileri.  
  
-   B1104: WCF Başlatıcı isteğe bağlı oluşturmaz `Expires` veya `Offer/Expires` öğesinde `CreateSequence` ileti.  
  
-   B1105: Erişirken `CreateSequence` WCF Yanıtlayıcı ileti kullanan `Expires` değerini `CreateSequence` öğesi olarak `Expires` değerini `CreateSequenceResponse` öğesi. Aksi durumda, WCF Yanıtlayıcı okur ve yoksayar `Expires` ve `Offer/Expires` değerleri.  
  
-   B1106: Erişirken `CreateSequenceResponse` ileti WCF Başlatıcı okur isteğe bağlı `Expires` değer ancak bunları kullanmaz.  
  
-   B1107: WCF Başlatıcı hem Yanıtlayıcı her zaman isteğe bağlı Oluştur `IncompleteSequenceBehavior` öğesinde `CreateSequence/Offer` ve `CreateSequenceResponse` öğeleri.  
  
-   B1108: WCF kullanan yalnızca `DiscardFollowingFirstGap` ve `NoDiscard` değerler `IncompleteSequenceBehavior` öğesi.  
  
    -   WS-ReliableMessaging yararlanan `Offer` iki oturum form bağıntılı dizileri gruplarıdır kurmak için bir mekanizma.  
  
-   B1109: Varsa `CreateSequence` içeren bir `Offer` öğesi, tek yönlü WCF Yanıtlayıcı reddeder sunulan dizisi ile yanıt vererek bir `CreateSequenceResponse` olmadan bir `Accept` öğesi.  
  
-   B1110: Güvenilir bir Mesajlaşma Yanıtlayıcı sunulan dizisi reddederse, WCF Başlatıcı yeni kurulan dizisi hataları.  
  
-   B1111: Varsa `CreateSequence` içermeyen bir `Offer` öğe, çift yönlü WCF Yanıtlayıcı reddeder sunulan dizisi ile yanıt vererek bir `CreateSequenceRefused` hata.  
  
-   R1112: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması `[address]` özelliği `CreateSequenceResponse/Accept/AcksTo` uç nokta Başvurusu ' % s'hedef URI eşleşmelidir, `CreateSequence` ileti baytı.  
  
-   R1113: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması, her iki dizileri için Yanıtlayıcı başlatıcıdan akan tüm iletileri aynı uç nokta başvurusu gönderilmelidir.  
  
 WCF WS-ReliableMessaging Başlarıcı ve Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır. Güvenilir oturum açmak için tek yönlü, istek-yanıt ve tam WCF WS-ReliableMessaging uygulamasını sağlar çift yönlü Mesajlaşma desenleri. WS-ReliableMessaging `Offer` mekanizmasını `CreateSequence` ve `CreateSequenceResponse` iki bağıntılı listesiyse serileri ve tüm uç noktalar iletisi için uygun bir oturumu Protokolü sağlar bilgisayarlarıyla oluşturmanıza imkan tanır. WCF oturum tutarlılığı için uçtan uca koruma dahil olmak üzere oturum için güvenlik garantisi sunduğundan, aynı hedefe yönelik aynı taraf iletiler ulaşmasını sağlamak pratik bir yöntemdir. Bu, "ardışık-yedekleme" dizisi bildirimleri, uygulama iletilerinde de sağlar. Bu nedenle, kısıtlamaları R1102 R1112 ve R1113 WCF için geçerlidir.  
  
 Örneği bir `CreateSequence` ileti.  
  
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
  
 Örneği bir `CreateSequenceResponse` ileti.  
  
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
 WCF kullanan `CloseSequence` ve `CloseSequenceResponse` iletileri güvenilir Mesajlaşma kaynak tarafından başlatılan bir kapatma işlemi için. WCF güvenilir Mesajlaşma hedef kapatma başlatılmaz ve WCF güvenilir Mesajlaşma kaynak güvenilir Mesajlaşma hedef tarafından başlatılan bir kapatma desteklemez. Aşağıdaki kısıtlamalar uygulanır:  
  
-   B1201: WCF güvenilir Mesajlaşma kaynağı her zaman gönderdiği bir `CloseSequence` dizisi kapatmak için ileti.  
  
-   B1202: Güvenilir Mesajlaşma kaynak göndermeden önce onay sırası iletilerin tam aralığının bekler `CloseSequence` ileti.  
  
-   B1203: Güvenilir Mesajlaşma kaynağı her zaman isteğe bağlı içerir `LastMsgNumber` öğe dizisi iletileri içermediği sürece.  
  
-   R1204: Güvenilir Mesajlaşma hedef kapatma göndererek gerçekleştirmemelidir bir `CloseSequence` ileti.  
  
-   B1205: Alma bağlı bir `CloseSequence` ileti WCF güvenilir Mesajlaşma kaynak dizisi eksik olarak değerlendirir ve bir hata gönderir.  
  
 Örneği bir `CloseSequence` ileti.  
  
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
  
### <a name="sequence-termination"></a>Sonlandırma sırası  
 WCF öncelikle kullanır `TerminateSequence/TerminateSequenceResponse` tamamladıktan sonra el sıkışması `CloseSequence/CloseSequenceResponse` anlaşması. WCF güvenilir Mesajlaşma hedef sonlandırma başlatılmaz ve güvenilir Mesajlaşma kaynak, hedef tarafından başlatılan bir güvenilir Mesajlaşma sonlandırma desteklemez. Aşağıdaki kısıtlamalar uygulanır:  
  
-   B1301: Yalnızca WCF Başlatıcı gönderir `TerminateSequence` ileti başarıyla tamamlanmasından sonra `CloseSequence/CloseSequenceResponse` anlaşması.  
  
-   R1302: WCF doğrular `LastMsgNumber` öğedir tutarlı tamamında `CloseSequence` ve `TerminateSequence` iletileri için belirli bir dizi. Diğer bir deyişle `LastMsgNumber` değil tüm mevcut `CloseSequence` ve `TerminateSequence` iletileri veya mevcut ve tüm aynı `CloseSequence` ve `TerminateSequence` iletileri.  
  
-   B1303: Alırken bir `TerminateSequence` sonra ileti `CloseSequence/CloseSequenceResponse` güvenilir Mesajlaşma hedef el sıkışması, yanıt veren ile bir `TerminateSequenceResponse` ileti. Güvenilir Mesajlaşma kaynak göndermeden önce son onayı olduğundan `TerminateSequence` ileti güvenilir Mesajlaşma hedef bilir olmadan emin olabilirsiniz dizisi sona ereceğini ve kaynaklara hemen geri kazanır.  
  
-   B1304: Alırken bir `TerminateSequence` öncesinde ileti `CloseSequence/CloseSequenceResponse` WCF güvenilir Mesajlaşma hedef el sıkışması, yanıt veren ile bir `TerminateSequenceResponse` ileti. Güvenilir Mesajlaşma hedef dizideki tutarsızlık olduğunu belirlerse, güvenilir Mesajlaşma hedef istemcinin alma olanağı sağlamak için kaynakları tekrar kullanılabilir hale getirme önce bir uygulamayı hedef belirtilen saat bekler son onayı. Aksi halde, güvenilir Mesajlaşma hedef kaynaklar hemen geri kazanır ve uygulama hedef sıra yükselterek şüpheli ile biten gösterir `Faulted` olay.  
  
 Örneği bir `TerminateSequence` ileti.  
  
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
 Dizilerine uygulama kısıtlamaları listesi verilmiştir:  
  
-   B1401:WCF oluşturur ve erişimleri numaraları daha yüksek sıralı `xs:long`'s maksimum kapsamlı değeri, 9223372036854775807.  
  
 Örneği bir `Sequence` başlığı.  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>İstek onayı  
 WCF kullanan `AckRequested` tutma mekanizması olarak başlığı.  
  
 Örneği bir `AckRequested` başlığı.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF WS-Reliable Mesajlaşma sağlanan sıralı onayları için bir "ardışık" mekanizması kullanır. Aşağıdaki kısıtlamalar uygulanır:  
  
-   R1601: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması `SequenceAcknowledgement` üst bilgisi için hedeflenen alıcı aktarılan herhangi bir uygulama iletisi içinde eklenmesi. Uzak uç noktada bir paketle gönderilen erişebilir `SequenceAcknowledgement` başlığı.  
  
-   B1602: WCF oluşturmaz `SequenceAcknowledgement` içeren üst bilgiler `Nack` öğeleri. WCF doğrular ve her `Nack` öğesi bir sıra numarası içeriyor, ancak Aksi halde yoksayar `Nack` öğe ve değer.  
  
 Örneği bir `SequenceAcknowledgement` başlığı.  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging hataları  
 Bir listesi WS-ReliableMessaging hataları WCF uygulaması için geçerli olan sınırlamalar aşağıda verilmiştir. Aşağıdaki kısıtlamalar uygulanır:  
  
-   B1701: WCF oluşturmaz `MessageNumberRollover` hataları.  
  
-   B1702: Hizmet uç noktası, bağlantı sınırına ulaştığında ve yeni bağlantı işlenemiyor, SOAP 1.2 WCF iç içe bir oluşturur `CreateSequenceRefused` alt kod, hata `netrm:ConnectionLimitReached`aşağıdaki örnekte gösterildiği gibi.  
  
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
 WS-Addressing WS-ReliableMessaging kullandığından WCF WS-ReliableMessaging uygulama oluşturabilir ve WS-Addressing hataları iletme. Bu bölüm, WCF açıkça oluşturur ve WS-ReliableMessaging katmanında iletir WS-Addressing hataları kapsar:  
  
-   B1801:WCF oluşturur ve iletir `Message Addressing Header Required` aşağıdakilerden biri doğruysa, hata:  
  
    -   A `CreateSequence`, `CloseSequence` veya `TerminateSequence` ileti eksik bir `MessageId` başlığı.  
  
    -   A `CreateSequence`, `CloseSequence` veya `TerminateSequence` ileti eksik bir `ReplyTo` başlığı.  
  
    -   A `CreateSequenceResponse`, `CloseSequenceResponse`, veya `TerminateSequenceResponse` ileti eksik bir `RelatesTo` başlığı.  
  
-   B1802:WCF oluşturur ve iletir `Endpoint Unavailable` , dinleme bitiş noktası yoktur belirtmek için hata adresleme üstbilgilerinde incelenmesi göre sırası işleyebilir `CreateSequence` ileti.  
  
## <a name="protocol-composition"></a>İletişim kuralı oluşturma  
  
### <a name="composition-with-ws-addressing"></a>WS-Addressing ile oluşturma  
 WCF WS-Addressing iki sürümlerini destekler: WS-Addressing 2004/08 WS-ADDR ve W3C WS-Addressing 1.0 önerileri [WS-ADDR-CORE] ve [WS-ADDR SOAP].  
  
 While WS-ReliableMessaging belirtimi bahsetmeleri yalnızca WS-Addressing 2004/08, onu kısıtlamaz kullanılacak WS-Addressing sürümü. WCF için uygulanan kısıtlamaları listesi verilmiştir:  
  
-   R2101: WS-Addressing 2004/08 hem WS-Addressing 1.0 WS-Reliable Mesajlaşma ile kullanılabilir.  
  
-   R2102: Belirli bir WS-ReliableMessaging dizisi veya bir çift ters dizileri kullanılarak bağıntılı boyunca bir tek WS-Addressing sürümü kullanılmalıdır `Offer` mekanizması.  
  
### <a name="composition-with-soap"></a>SOAP ile oluşturma  
 WCF SOAP 1.1 ve SOAP 1.2 WS-Reliable Mesajlaşma ile kullanılmasını destekler.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-güvenlik ve WS-SecureConversation ile oluşturma  
 WCF ile WS-Secure Conversation güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve oluşturma'yı kullanarak WS-ReliableMessaging dizileri için koruma sağlar. WS-ReliableMessaging 1.1 protokolü, WS-güvenlik 1.1 ve WS-Secure konuşma 1.3 Protokolü birlikte kullanılmalıdır. WCF için uygulanan kısıtlamaları listesi verilmiştir:  
  
-   R2301: Bir WS-ReliableMessaging dizisini bütünlüğünün yanı sıra bütünlüğünü ve tek tek iletilerin gizliliğini korumak için WS-Secure Conversation kullanılmalıdır WCF gerektirir.  
  
-   R2302:AWS-Secure Conversation oturumu WS-ReliableMessaging sequence(s) kurmadan önce oluşturulması gerekir.  
  
-   R2303: WS-ReliableMessaging dizisi ömrü oturumunun ömrü, WS-Secure Conversation aşarsa `SecurityContextToken` kullanarak WS-Secure Conversation gerekir yenilenmiş karşılık gelen WS-Secure konuşma yenileme bağlama kullanılarak oluşturulmuş.  
  
-   B2304:WS-ReliableMessaging dizisi veya bir çift bağlantılı listesiyse dizileri tek bir WS-SecureConversation oturumuna bağlı her zaman.  
  
-   R2305: WS-Secure Conversation ile oluşan, gerektiren WCF Yanıtlayıcı `CreateSequence` iletisi içeren `wsse:SecurityTokenReference` öğesi ve `wsrm:UsesSequenceSTR` başlığı.  
  
 Örneği bir `UsesSequenceSTR` başlığı.  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>SSL/TLS oturumlarını ile oluşturma  
 WCF ile SSL/TLS oturumları oluşturma desteklemez:  
  
-   B2401: WCF oluşturmaz `wsrm:UsesSequenceSSL` başlığı.  
  
-   R2402: Güvenilir bir Mesajlaşma Başlatıcı değil göndermelisiniz bir `CreateSequence` ile ileti bir `wsrm:UsesSequenceSSL` WCF Yanıtlayıcı için üst bilgi.  
  
### <a name="composition-with-ws-policy"></a>WS-Policy ile oluşturma  
 WCF WS-Policy iki sürümlerini destekler: WS-Policy 1.2 ve WS-Policy 1.5.  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-ilke onaylama  
 WCF kullanan WS-ReliableMessaging WS-Policy onaylama `wsrm:RMAssertion` uç noktaları özelliklerini tanımlamak için. WCF için uygulanan kısıtlamaları listesi verilmiştir:  
  
-   B3001: WCF ekler `wsrmn:RMAssertion` WS-Policy onaylama için `wsdl:binding` öğeleri. WCF destekleyen iki ek `wsdl:binding` ve `wsdl:port` öğeleri.  
  
-   B3002: WCF hiçbir zaman oluşturur `wsp:Optional` etiketi.  
  
-   B3003: Erişirken `wsrmp:RMAssertion` WCF WS-Policy onaylama yoksayar `wsp:Optional` etiketleyin ve WS-RM ilke zorunlu olarak değerlendirir.  
  
-   R3004: WCF ile SSL/TLS oturumlarını compose değil çünkü belirten ilke WCF kabul etmiyor `wsrmp:SequenceTransportSecurity`.  
  
-   B3005: WCF her zaman oluşturur `wsrmp:DeliveryAssurance` öğesi.  
  
-   B3006: WCF her zaman belirtir `wsrmp:ExactlyOnce` teslim güvencesi.  
  
-   B3007: WCF oluşturur ve WS-ReliableMessaging onaylama aşağıdaki özelliklerini okur ve bunlar üzerindeki denetimi WCF sağlar`ReliableSessionBindingElement`:  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     Örneği bir `RMAssertion`.  
  
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
 WCF WS-ReliableMessaging genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.  
  
 Akış denetimi etkin ayarlayarak <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliğini `true`. WCF için uygulanan kısıtlamaları listesi verilmiştir:  
  
-   B4001: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF oluşturur bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi başlığı.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: Güvenilir Mesajlaşma akış denetimi etkinleştirilmiş olsa, WCF gerektirmez bir `netrm:BufferRemaining` öğesinde `SequenceAcknowledgement` başlığı.  
  
-   B4003: WCF güvenilir Mesajlaşma hedef kullanan `netrm:BufferRemaining` kaç yeni, iletileri göstermek için ara belleğe alabilir.  
  
-   B4004:when güvenilir Mesajlaşma akış denetimi etkin olduğunda, WCF güvenilir Mesajlaşma kaynak değerini kullanır `netrm:BufferRemaining` kısıtlama ileti aktarım için.  
  
-   B4005: WCF oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile kapsamlı 4096 arasında ve 0 arasında tamsayı değerlerini okur ve `xs:int`'s `maxInclusive` 214748364 kapsamlı değeri.  
  
## <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 Bu bölümde, WS-ReliableMessaging farklı ileti Exchange desenleri için kullanıldığında, WCF'ın davranışını tanımlar. Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları olarak kabul edilir:  
  
-   Adreslenebilir olmayan Başlatıcı: Başlatıcı bir güvenlik duvarı ardında kaldığı; Yanıtlayıcı Başlatıcısı yalnızca HTTP yanıtları için ileti teslim edebilirsiniz.  
  
-   Başlatıcı adreslenebilir: Başlatıcı hem Yanıtlayıcı HTTP isteklerini gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantı kurulur.  
  
### <a name="one-way-non-addressable-initiator"></a>Tek yönlü, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF bir HTTP kanalı üzerinden bir dizisi kullanırken bir yönlü ileti değişim deseni sağlar. WCF HTTP isteklerini yanıtlayan gelen tüm iletileri Başlatıcı iletmek için tüm ileti başlatıcıdan Yanıtlayıcı ve HTTP yanıtları aktarmaya kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı ileten bir `CreateSequence` ileti olmadan `Offer` öğe üzerinde bir HTTP isteği ve bekliyor `CreateSequenceResponse` HTTP yanıt iletisi. WCF Yanıtlayıcı bir dizisini oluşturur ve iletir `CreateSequenceResponse` ileti olmadan `Accept` HTTP yanıtını öğesi.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF Başlatıcı yanıtlama bir onayları tüm iletileri işleyen `CreateSequence` iletisi ve hata iletileri. WCF Yanıtlayıcı her zaman HTTP yanıtını tüm dizisi için tek başına bir bildirim gönderir ve `AckRequested` iletileri.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 WCF Başlatıcı ileten bir `CloseSequence` bekliyor ve bir HTTP isteği iletisi `CreateSequenceResponse` HTTP yanıt iletisi. WCF Yanıtlayıcı iletir `CloseSequenceResponse` HTTP yanıt iletisi.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 WCF Başlatıcı ileten bir `TerminateSequence` bekliyor ve bir HTTP isteği iletisi `TerminateSequenceResponse` HTTP yanıt iletisi. WCF Yanıtlayıcı iletir `TerminateSequenceResponse` HTTP yanıt iletisi.  
  
### <a name="one-way-addressable-initiator"></a>Tek yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF sağlayan bir dizisi üzerinde kullanırken bir yönlü ileti değişim deseni gelen ve giden bir HTTP kanalı. WCF HTTP isteklerini tüm ileti aktarmaya kullanır. Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı ileten bir `CreateSequence` ileti olmadan `Offer` öğe üzerinde bir HTTP isteği. WCF Yanıtlayıcı bir dizisini oluşturur ve iletir `CreateSequenceResponse` ileti olmadan `Accept` öğe üzerinde bir HTTP isteği.  
  
### <a name="duplex-addressable-initiator"></a>Çift yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF sağlayan iki kullanarak tam olarak zaman uyumsuz, çift yönlü ileti değişim deseni dizilerinin üzerinde bir gelen ve giden bir HTTP kanalı. Bu ileti değişim deseni ile karışık `Request/Reply`, `Addressable` sınırlı bir şekilde Başlatıcı ileti değişim deseni. WCF HTTP isteklerini tüm ileti aktarmaya kullanır. Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı ileten bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği. WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir `Offer` öğesi, ardından bir dizi oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` öğesi.  
  
#### <a name="sequence-lifetime"></a>Dizisi ömrü  
 WCF iki diziyi bir tam yönlü oturum olarak değerlendirir.  
  
 Bir sıralı hataları bir hata oluşturma sırasında uzak uç noktanın hem dizileri hata WCF bekliyor. Bir sıralı hataları bir hataya okuma sırasında WCF hem dizileri hataları.  
  
 WCF giden kendi dizisi kapatın ve gelen kendi sıra üzerinde iletileri işleme devam edebilirsiniz. Buna karşılık, WCF gelen dizisi kapatma işlemi ve bu giden kendi sıra üzerinde iletileri göndermeye devam edebilirsiniz.  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>İstek-yanıt ve tek yönlü, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF tek yönlü sağlar ve istek-yanıt ileti değişim deseni iki kullanarak tek HTTP kanalı serileri. WCF HTTP isteklerini yanıtlayan gelen tüm iletileri Başlatıcı iletmek için tüm ileti başlatıcıdan Yanıtlayıcı ve HTTP yanıtları aktarmaya kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı ileten bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği ve bekliyor `CreateSequenceResponse` HTTP yanıt iletisi. WCF Yanıtlayıcı bir dizisini oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` HTTP yanıtını öğesi.  
  
#### <a name="one-way-message"></a>Tek yönlü mesaj  
 WCF Başlatıcı bir tek yönlü mesaj alışverişi başarıyla tamamlamak için bir istek sırası iletisi HTTP isteğini iletir ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi. `SequenceAcknowledgement` Aktarılan iletiyi kabul etmeniz gerekir.  
  
 WCF Yanıtlayıcı bir bildirim, bir hata veya bir boş gövdesi ve 202 HTTP durum kodu ile bir yanıt isteğine yanıt.  
  
#### <a name="two-way-messages"></a>İki şekilde iletileri  
 İki yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteğini bir istek sırası iletisi aktarır ve HTTP yanıtını yanıt sırası iletisi alır. Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi sıkan aktarılan.  
  
 WCF Yanıtlayıcı bir uygulama yanıt, bir hata veya bir boş gövdesi ve 202 HTTP durum kodu ile bir yanıt isteğine yanıt.  
  
 Tek yönlü iletileri varlığını ve uygulama yanıt zamanlaması nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası ile hiçbir bağıntısı vardır.  
  
#### <a name="retrying-replies"></a>Yanıt yeniden deneniyor  
 WCF için iki yönlü ileti exchange Protokolü bağıntısı HTTP isteği-yanıt bağıntısı kullanır. Bu nedenle, WCF Başlatıcı istek sırası iletisi onaylandığında bir istek sırası iletisi yeniden deneniyor durdurmaz ancak yerine ne zaman HTTP yanıtı yürüten bir `SequenceAcknowledgement`, uygulama yanıtı veya hata. WCF Yanıtlayıcı yanıt, yanıt bağıntılı isteğin HTTP yanıtını yeniden dener.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 Tüm yanıt sırası iletileri ve tüm one-way isteğini sırası iletileri için onayları aldıktan sonra WCF Başlatıcı ileten bir `CloseSequence` iletisi için HTTP isteğinde istek sırası ve bekliyor `CloseSequenceResponse` HTTP yanıtını.  
  
 İstek sırası örtük olarak kapatılmadan yanıt sırası kapatır. WCF Başlatıcı içerir yanıt sırasının son yani `SequenceAcknowledgement` üzerinde `CloseSequence` iletisi ve yanıt sırası yok bir `CloseSequence` exchange.  
  
 Tüm yanıtlar onaylanmalarını ve iletir WCF Yanıtlayıcı sağlar `CloseSequenceResponse` HTTP yanıt iletisi.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Alma sonra `CloseSequenceResponse` WCF Başlatıcı ileti iletir bir `TerminateSequence` iletisi için HTTP isteğinde istek sırası ve bekliyor `TerminateSequenceResponse` HTTP yanıtını.  
  
 Gibi `CloseSequence` değişimi, örtük olarak istek sırası sonlandırma yanıt sırası sonlandırır. WCF Başlatıcı içerir yanıt sırasının son yani `SequenceAcknowledgement` üzerinde `TerminateSequence` iletisi ve yanıt sırası yok bir `TerminateSequence` exchange.  
  
 WCF Yanıtlayıcı iletir `TerminateSequenceResponse` HTTP yanıt iletisi.  
  
### <a name="requestreply-addressable-initiator"></a>İstek/yanıt, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF sağlayan iki kullanarak istek-yanıt ileti değişim deseni dizilerinin üzerinde bir gelen ve giden bir HTTP kanalı. Bu ileti değişim deseni ile karışık `Duplex, Addressable` sınırlı bir şekilde Başlatıcı ileti değişim deseni. WCF HTTP isteklerini tüm ileti aktarmaya kullanır. Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı ileten bir `CreateSequence` ile ileti bir `Offer` öğe üzerinde bir HTTP isteği. WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir `Offer` öğesi, ardından bir dizi oluşturur ve iletir `CreateSequenceResponse` ile ileti bir `Accept` öğesi.  
  
#### <a name="requestreply-correlation"></a>İstek/yanıt bağıntısı  
 Aşağıdaki, tüm ilişkili istekleri ve yanıtları için geçerlidir:  
  
-   WCF sağlar, tüm uygulama istek iletileri ayı bir `ReplyTo` uç nokta başvurusu ve `MessageId`.  
  
-   WCF her uygulama istek iletisi kullanıcının yerel uç nokta başvurusu geçerli `ReplyTo`. Yerel uç nokta başvurusu `CreateSequence` iletinin `ReplyTo` başlatıcısının ve `CreateSequence` iletinin `To` Yanıtlayıcı için.  
  
-   WCF sağlar, gelen istek iletisi ayı bir `MessageId` ve `ReplyTo`.  
  
-   WCF sağlar `ReplyTo` daha önce tanımlanan tüm uygulama istek iletisi uç nokta Başvurusu'nın URI eşleşen yerel uç nokta başvurusu.  
  
-   WCF sağlar tüm yanıtlar doğru ayı `RelatesTo` ve `To` aşağıdaki üst bilgileri `wsa` bağıntı kuralları istek/yanıt.
