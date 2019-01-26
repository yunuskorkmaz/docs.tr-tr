---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 02a0815f62999c27507ed5e1610f090e944c135a
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55073219"
---
# <a name="reliable-messaging-protocol-version-10"></a>Güvenilir Mesajlaşma Protokolü sürüm 1.0
WS-Reliable Mesajlaşma için bu konuda Windows Communication Foundation (WCF) uygulama ayrıntılarını kapsayan Şubat 2005 (sürüm 1.0) Protokolü HTTP aktarımı kullanarak birlikte çalışma için gerekli. WCF WS-Reliable Mesajlaşma kısıtlamaları ve bu konuda açıklanan açıklamalar izler. İle başlayarak WS-ReliableMessaging sürüm 1.0 protokolü uygulandığını unutmayın [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 WS-Reliable Protokolü WCF uygulandığına Mesajlaşma Şubat 2005 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Kolaylık olması için konunun aşağıdaki rolleri kullanır:  
  
-   Başlatıcı: WS güvenilir ileti sırası oluşturma başlatan istemci  
  
-   Yanıtlayıcı: başlatanın isteği aldığı hizmeti  
  
 Bu belge, aşağıdaki tabloda ad alanlarını ve önekleri kullanır.  
  
|Ön eki|Ad Alanı|  
|------------|---------------|  
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>İleti  
  
### <a name="sequence-establishment-messages"></a>Dizisi kurma iletileri  
 WCF uygulayan `CreateSequence` ve `CreateSequenceResponse` iletileri güvenilir ileti dizisi oluşturmak için. Aşağıdaki kısıtlamalar uygulanır:  
  
-   B1101: WCF Başlatıcı isteğe bağlı süre sonu öğesinde oluşturmaz `CreateSequence` ileti veya durumlarda olduğunda `CreateSequence` iletisini içeren bir `Offer` öğesi, isteğe bağlı `Expires` öğesinde `Offer` öğesi.  
  
-   B1102: Erişirken `CreateSequence` iletisi, WCF`Responder` gönderir ve her ikisi de alır `Expires` öğeler var ancak bunların değerlerini kullanmaz.  
  
 WS-Reliable Mesajlaşma tanıtır `Offer` iki oturum form bağıntılı dizileri gruplarıdır kurmak için bir mekanizma.  
  
-   R1103: Varsa `CreateSequence` içeren bir `Offer` öğesi, güvenilir Mesajlaşma Yanıtlayıcı gerekir ya da dizisi kabul edin ve yanıt `CreateSequenceResponse` içeren bir `wsrm:Accept` iki bağıntılı oluşturan öğesini gruplarıdır dizileri veya Reddet`CreateSequence`istek.  
  
-   R1104: `SequenceAcknowledgement` ve ters sırası akan uygulama iletileri için gönderilmelidir `ReplyTo` uç nokta başvurusu `CreateSequence`.  
  
-   R1105: `AcksTo` ve `ReplyTo` uç nokta başvurularının `CreateSequence` octet-wise eşleşen adresi değerlere sahip olmalıdır.  
  
     WCF Yanıtlayıcı doğrular URI kısmı `AcksTo` ve `ReplyTo` EPR'ler özdeş bir dizisini oluşturmadan önce.  
  
-   R1106: `AcksTo` ve `ReplyTo` uç nokta başvuruları `CreateSequence` başvuru parametrelerinin aynı olmalıdır.  
  
     WCF mecbur kılmaz ancak varsayar, [başvuru parametreleri] `AcksTo` ve `ReplyTo` üzerinde `CreateSequence` özdeş ve kullanır [başvuru parametreleri] `ReplyTo` onayları ve ters sıra iletileri için uç nokta başvurusu.  
  
-   R1107: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması `SequenceAcknowledgement` listesiyse dizileri üzerinde akan uygulama iletileri gönderilen, için ve `ReplyTo` uç nokta başvurusu `CreateSequence`.  
  
-   R1108: İki ters dizileri teklif mekanizması kullanılarak oluşturulduğunda `[address]` özelliği `wsrm:AcksTo` uç nokta başvurusu alt öğesi `wsrm:Accept` öğesinin `CreateSequenceResponse` hedefiniURIbyte-wiseeşleşmelidir`CreateSequence`.  
  
-   R1109: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması, başlatıcı hem Yanıtlayıcı olarak iletilere katkıda bulunanlar tarafından gönderilen iletiler için aynı uç nokta başvurusu gönderilmelidir.  
  
     WS-Reliable Mesajlaşma WCF Başlatıcı hem Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır. WCF'ın WS-Reliable Mesajlaşma uygulaması sağlayan güvenilir oturum için tek yönlü, istek-yanıt ve tam çift yönlü Mesajlaşma desenleri. WS-Reliable Mesajlaşma `Offer` mekanizmasını `CreateSequence` / `CreateSequenceResponse` iki bağıntılı listesiyse dizileri oluşturmanıza olanak sağlar ve tüm uç noktalar iletisi için uygun bir oturumu Protokolü sağlar. WCF oturum tutarlılığı için uçtan uca koruma dahil olmak üzere oturum için güvenlik garantisi sunduğundan, aynı hedefe yönelik aynı tarafa iletilerinin geliş emin olmak pratik bir yöntemdir. Bu uygulama iletilerinde ardışık-yedekleme, sıralı onayları da sağlar. Bu nedenle, kısıtlamaları R1104 R1105 ve R1108 WCF için geçerlidir.  
  
 Örneği bir `CreateSequence` ileti.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence  
    </a:Action>  
    <a:ReplyTo>  
      <a:Address>          
         http://Business456.com/clientA        
      </a:Address>  
    </a:ReplyTo>  
    <a:MessageID>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:MessageID>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
       <wsa:Address>  
         http://Business456.com/clientA  
       </wsa:Address>  
     </wsrm:AcksTo>  
     <wsrm:Offer>  
      <wsrm:Identifier>  
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496  
      </wsrm:Identifier>  
     </wsrm:Offer>  
   </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 Örneği bir `CreateSequenceResponse` ileti.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse  
    </a:Action>  
    <a:RelatesTo>  
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
    </a:RelatesTo>  
    <a:To s:mustUnderstand="1">  
      http://Business456.com/clientA  
    </a:To>  
  </s:Header>  
  <s:Body>  
   <wsrm:CreateSequenceResponse>  
    <Identifier>  
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386  
    </Identifier>  
    <Accept>  
    <AcksTo>  
      <a:Address>  
        http://BusinessABC.com/serviceA  
      </a:Address>  
    </AcksTo>  
    </Accept>  
   </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence"></a>Dizisi  
 Dizilerine uygulama kısıtlamaları listesi verilmiştir:  
  
-   B1201:WCF oluşturur ve erişimleri numaraları daha yüksek sıralı `xs:long`'s maksimum kapsamlı değeri, 9223372036854775807.  
  
-   B1202:WCF her zaman bir boş gövdeli son iletisi ' % s'eylemi URI'si ile oluşturur, `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.  
  
-   B1203: WCF alır ve sunan bir ileti içeren bir dizisi üst bilgisiyle bir `LastMessage` öğesi ' % s'eylemi URI'si değil sürece `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.  
  
 Bir örnek dizisi üst bilgisi.  
  
```xml  
<wsrm:Sequence>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
  <wsrm:MessageNumber>  
    10  
  </wsrm:MessageNumber>  
  <wsrm:LastMessage/>  
 </wsrm:Sequence>  
```  
  
### <a name="ackrequested-header"></a>AckRequested üstbilgisi  
 WCF kullanan `AckRequested` tutma mekanizması olarak başlığı. WCF isteğe bağlı oluşturmaz `MessageNumber` öğesi. Bir mesajı almak bağlı bir `AckRequested` içeren üstbilgi `MessageNumber` WCF öğesini yoksayar `MessageNumber` öğenin değeri, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement üstbilgisi  
 WCF WS-Reliable Mesajlaşma sağlanan sıralı onayları için ardışık mekanizması kullanır.  
  
-   R1401: İki ters sıraları kullanarak kurulduğunda `Offer` mekanizması `SequenceAcknowledgement` üst bilgisi için hedeflenen alıcı aktarılan herhangi bir uygulama iletisi içinde eklenmesi.  
  
-   B1402: Ne zaman WCF gerekir Oluşturma sırası iletileri alma önce bir bildirim (örneğin, karşılamak için bir `AckRequested` ileti), WCF oluşturur bir `SequenceAcknowledgement` aralığı 0-0, aşağıdaki örnekte gösterildiği gibi içeren üstbilgi.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403: WCF oluşturmaz `SequenceAcknowledgement` içeren üst bilgiler bir `Nack` öğesi ancak destekler `Nack` öğeleri.  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging hataları  
 WS-Reliable Mesajlaşma hataları WCF uygulaması için geçerli olan sınırlamalar listesi verilmiştir:  
  
-   B1501: WCF oluşturmaz `MessageNumberRollover` hataları.  
  
-   B1502:WCF uç noktası oluşturabilir `CreateSequenceRefused` Belirtimi'nde açıklanan hataları.  
  
-   B1503:when hizmet uç noktası, bağlantı sınırına ulaştığında ve yeni bağlantı işlenemiyor, ek bir WCF oluşturur `CreateSequenceRefused` alt kod, hata `netrm:ConnectionLimitReached`aşağıdaki örnekte gösterildiği gibi.  
  
    ```xml  
    <s:Envelope>  
      <s:Header>  
        <wsa:Action>  
          http://schemas.xmlsoap.org/ws/2005/08/addressing/fault  
        </wsa:Action>  
      </s:Header>  
      <s:Body>  
        <s:Fault>  
          <s:Code>  
            <s:Value>  
              s:Receiver  
            </s:Value>  
            <s:Subcode>  
              <s:Value>  
                wsrm:CreateSequenceRefused  
              </s:Value>  
              <s:Subcode>  
                <s:Value>  
                  netrm:ConnectionLimitReached  
                </s:Value>  
              </s:Subcode>  
            </s:Subcode>  
          </s:Code>  
          <s:Reason>  
            <s:Text xml:lang="en">  
              [Reason]  
            </s:Text>  
          </s:Reason>  
        </s:Fault>  
      </s:Body>  
    </s:Envelope>  
    ```  
  
### <a name="ws-addressing-faults"></a>WS-Addressing hataları  
 WS-Reliable Mesajlaşma WS-Addressing kullandığından WCF WS-Reliable Mesajlaşma uygulaması WS-Addressing hatalarının oluşmasına neden olabilir. Bu bölüm, WCF WS-Reliable Mesajlaşma katmanında açıkça oluşturur WS-Addressing hataları kapsar:  
  
-   Aşağıdakilerden biri doğruysa B1601:WCF ileti adresleme üstbilgi gereken hata oluşturur:  
  
    -   Bir ileti eksik bir `Sequence` başlığı ve bir `Action` başlığı.  
  
    -   A `CreateSequence` ileti eksik bir `MessageId` başlığı.  
  
    -   A `CreateSequence` ileti eksik bir `ReplyTo` başlığı.  
  
-   B1602:WCF eksik olduğunu belirten bir ileti girilecek yanıt eylemi desteklenmiyor hatası oluşturur bir `Sequence` başlığı ve bir `Action` tanınan bir WS-Reliable Mesajlaşma belirtiminde değil başlığı.  
  
-   Uç nokta incelenmesi göre sırası işlemez belirtmek için kullanılabilir uç nokta hatası B1603:WCF oluşturur `CreateSequence` ileti üstbilgileri adresleme.  
  
## <a name="protocol-composition"></a>İletişim kuralı oluşturma  
  
### <a name="composition-with-ws-addressing"></a>WS-Addressing ile oluşturma  
 WCF WS-Addressing iki sürümlerini destekler: WS-Addressing 2004/08 WS-ADDR ve W3C WS-Addressing 1.0 önerileri [WS-ADDR-CORE] ve [WS-ADDR SOAP].  
  
 While WS-Reliable Mesajlaşma belirtimi bahsetmeleri yalnızca WS-Addressing 2004/08, onu kısıtlamaz kullanılacak WS-Addressing sürümü. WCF için uygulanan kısıtlamaları listesi verilmiştir:  
  
-   R2101: hem WS-Addressing 2004/08 ve WS-Addressing 1.0 WS-Reliable Mesajlaşma ile kullanılabilir.  
  
-   R2102:A tek sürüm, WS-Addressing kullanılan, WS-Reliable Mesajlaşma belirli bir dizi veya bir çift ters dizileri kullanılarak bağıntılı boyunca `wsrm:Offer` mekanizması.  
  
### <a name="composition-with-soap"></a>SOAP ile oluşturma  
 WCF SOAP 1.1 ve SOAP 1.2 WS-Reliable Mesajlaşma ile destekler.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-güvenlik ve WS-SecureConversation ile oluşturma  
 WCF ile WS-Secure Conversation güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve oluşturma'yı kullanarak dizileri WS-Reliable Mesajlaşma için koruma sağlar. WCF için uygulanan kısıtlamaları listesi verilmiştir:  
  
-   R2301: bütünlüğü yanı sıra bir WS-Reliable Mesajlaşma dizisi bütünlüğünü ve tek tek iletilerin gizliliğini korumak için WS-Secure Conversation kullanılmalıdır WCF gerektirir.  
  
-   R2302:AWS-Secure Conversation oturumu WS-Reliable Mesajlaşma sequence(s) kurmadan önce oluşturulması gerekir.  
  
-   R2303: WS-Reliable Mesajlaşma dizisi ömrü oturumunun ömrü, WS-Secure Conversation aşarsa `SecurityContextToken` kullanarak WS-Secure Conversation gerekir yenilenmiş karşılık gelen WS-Secure konuşma yenileme bağlama kullanılarak oluşturulmuş.  
  
-   B2304:ws-güvenilir Mesajlaşma dizisi veya bir çift bağlantılı listesiyse dizileri tek bir WS-SecureConversation oturumuna bağlı her zaman.  
  
     WCF kaynağının oluşturduğu `wsse:SecurityTokenReference` öğesi öğe genişletilebilirlik bölümünde `CreateSequence` ileti.  
  
-   WS-Secure Conversation ile oluşan R2305:When bir `CreateSequence` ileti içermelidir `wsse:SecurityTokenReference` öğesi.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-Reliable Mesajlaşma WS-Policy onaylama  
 WCF kullanan WS-Reliable Mesajlaşma WS-Policy onaylama `wsrm:RMAssertion` uç noktaları özelliklerini tanımlamak için. WCF için uygulanan kısıtlamaları listesi verilmiştir:  
  
-   B3001: WCF ekler `wsrm:RMAssertion` WS-Policy onaylama için `wsdl:binding` öğeleri. WCF destekleyen iki ek `wsdl:binding` ve `wsdl:port` öğeleri.  
  
-   B3002: WCF WS-Reliable Mesajlaşma onaylama aşağıdaki isteğe bağlı özelliklerini destekler ve bunlar üzerindeki denetimi WCF sağlar`ReliableMessagingBindingElement`:  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     Bir örnek verilmiştir.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>WS-Reliable Mesajlaşma akışı kontrol uzantısı  
 WCF WS-Reliable Mesajlaşma genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.  
  
 Akış denetimi etkin ayarlayarak <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliğini `true`. WCF için uygulanan kısıtlamaları listesi verilmiştir:  
  
-   B4001: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF oluşturur bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` başlığı.  
  
-   B4002: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF gerektirmez bir `netrm:BufferRemaining` bulunması öğesi `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi başlığı.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        http://fabrikam123.com/abc  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>  
        8  
      </netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4003: WCF kullanan `netrm:BufferRemaining` kaç yeni güvenilir Mesajlaşma hedef iletileri göstermek için ara belleğe alabilir.  
  
-   B4004: WCF güvenilir Mesajlaşma hizmeti hedef uygulama güvenilir Mesajlaşma iletileri hızlı bir şekilde zaman gönderilen ileti sayısını kısıtlar. Hedef arabelleği güvenilir Mesajlaşma iletileri ve öğenin değeri 0 olarak bırakır.  
  
-   B4005: WCF oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile kapsamlı 4096 arasında ve 0 arasında tamsayı değerlerini okur ve `xs:int`'s `maxInclusive` 214748364 kapsamlı değeri.  
  
## <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 Bu bölümde, WS-Reliable Mesajlaşma için farklı ileti Exchange desenleri kullanıldığında WCF'ın davranışını tanımlar. Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları olarak kabul edilir:  
  
-   Adreslenebilir olmayan Başlatıcı: Başlatıcı güvenlik duvarı ardında kaldığı; Yanıtlayıcı, yalnızca HTTP yanıtları için Başlatıcı iletileri teslim edebilirsiniz.  
  
-   Başlatıcı adreslenebilir: Başlatıcı hem Yanıtlayıcı HTTP isteklerini gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantı kurulur.  
  
### <a name="one-way-non-addressable-initiator"></a>Tek yönlü, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF bir HTTP kanalı üzerinden bir dizisi kullanırken bir yönlü ileti değişim deseni sağlar. WCF HTTP isteklerini RMD gelen tüm iletileri RMS'ye aktarmaya tüm ileti RMS RMD ve HTTP yanıtı aktarmaya kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle teklif yok. WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce herhangi bir teklif vardır. WCF Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF Başlatıcı yanıtlama bir onayları tüm iletileri işleyen `CreateSequence` iletisi ve hata iletileri. WCF Yanıtlayıcı her zaman yanıt hem dizisi olarak tek başına bir bildirim oluşturur ve `AckRequested` iletileri.  
  
#### <a name="terminatesequence-message"></a>TerminateSequence iletisi  
 WCF işler `TerminateSequence` , tek yönlü bir işlem olarak HTTP yanıtını bir boş gövdesi ve 202 HTTP durum kodu sahiptir yani.  
  
### <a name="one-way-addressable-initiator"></a>Tek yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF bir dizi üzerinde bir gelen ve giden bir Http kanalı kullanan tek yönlü ileti değişim deseni sağlar. WCF HTTP isteklerini tüm ileti aktarmaya kullanır. Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle teklif yok. WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce herhangi bir teklif vardır. WCF Yanıtlayıcı iletir `CreateSequenceResponse` bir HTTP isteği iletisi ele ile `ReplyTo` uç nokta başvurusu.  
  
### <a name="duplex-addressable-initiator"></a>Çift yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF iki diziyi bir gelen ve giden bir HTTP kanalı kullanarak iki yönlü tam olarak zaman uyumsuz ileti değişim deseni sağlar. WCF HTTP isteklerini tüm ileti aktarmaya kullanır. Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle bir teklif. WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce bir teklif vardır. WCF gönderir `CreateSequenceResponse` yönelik HTTP isteği için `CreateSequence`'s `ReplyTo` uç nokta başvurusu.  
  
#### <a name="sequence-lifetime"></a>Dizisi ömrü  
 WCF iki sıranın tam çift yönlü bir oturum olarak değerlendirir.  
  
 Bir sıralı hataları bir hata oluşturma sırasında uzak uç noktanın hem dizileri hata WCF bekliyor. Bir sıralı hataları bir hataya okuma sırasında WCF hem dizileri hataları.  
  
 WCF giden kendi dizisi kapatın ve gelen kendi sıra üzerinde iletileri işleme devam edebilirsiniz. Buna karşılık, WCF gelen dizisi kapatma işlemi ve bu giden kendi sıra üzerinde iletileri göndermeye devam edebilirsiniz.  
  
### <a name="request-reply-non-addressable-initiator"></a>İstek-yanıt, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF tek yönlü sağlar ve istek-yanıt ileti değişim deseni iki kullanarak tek HTTP kanalı serileri. WCF HTTP isteklerini isteği sırasının ileti aktarmaya ve HTTP yanıtlarını yanıt sırasının ileti aktarmaya kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle bir teklif. WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce bir teklif vardır. WCF Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.  
  
#### <a name="one-way-message"></a>Tek yönlü mesaj  
 WCF Başlatıcı bir tek yönlü mesaj değişimi Protokolü başarıyla tamamlamak için bir istek sırası iletisi HTTP isteğini iletir ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi. `SequenceAcknowledgement` Aktarılan iletiyi kabul etmeniz gerekir.  
  
 WCF Yanıtlayıcı bir bildirim, bir hata veya bir boş gövdesi ve 202 HTTP durum kodu ile bir yanıt isteğine yanıt verebilir.  
  
#### <a name="two-way-messages"></a>İki şekilde iletileri  
 İki yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteğini bir istek sırası iletisi aktarır ve HTTP yanıtını yanıt sırası iletisi alır. Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi sıkan aktarılan.  
  
 WCF Yanıtlayıcı bir uygulama yanıt, bir hata veya bir boş gövdesi ve 202 HTTP durum kodu ile bir yanıt isteğine yanıt verebilir.  
  
 Tek yönlü iletileri varlığını ve uygulama yanıt zamanlaması nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası ile hiçbir bağıntısı vardır.  
  
#### <a name="retrying-replies"></a>Yanıt yeniden deneniyor  
 WCF için iki yönlü ileti exchange Protokolü bağıntısı HTTP isteği-yanıt bağıntısı kullanır. Bu nedenle, WCF Başlatıcı bir istek sırası iletisi istek sırası iletisi onaylandığında, ancak yerine HTTP yanıtını bir bildirim, kullanıcı iletisi veya hata getirirken yeniden deneniyor durdurmaz. WCF Yanıtlayıcı yanıt, yanıt bağıntılı isteğin HTTP isteği oluşturan üzerinde yeniden dener.  
  
#### <a name="lastmessage-exchange"></a>LastMessage Exchange  
 WCF Başlatıcı oluşturur ve bir HTTP isteği oluşturan üzerinde boş bodied son ileti iletir. WCF bir yanıt gerektirir, ancak gerçek bir yanıt iletisi yok sayar. WCF Yanıtlayıcı isteği sırasının boş gövdeli son iletiye yanıt sırasının boş gövdeli son ileti ile yanıt verir.  
  
 WCF Yanıtlayıcı, ' % s'eylemi URI'si değil bir son ileti alırsa `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, son bir ileti ile WCF yanıtlar. İki yönlü ileti değişimi Protokolü söz konusu olduğunda, uygulama iletisi son iletiyi taşır; tek yönlü mesaj değişimi Protokolü söz konusu olduğunda, son iletinin boştur.  
  
 WCF Yanıtlayıcı yanıt sırasının boş gövdeli son iletisi için bir onay gerektirmez.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Tüm istekler geçerli bir yanıt alındığında, bu WCF Başlatıcı oluşturur ve istek sırasının iletir `TerminateSequence` HTTP isteği oluşturan iletisi. WCF bir yanıt gerektirir, ancak gerçek bir yanıt iletisi yok sayar. WCF Yanıtlayıcı isteği sırasının için yanıtlar `TerminateSequence` iletisiyle yanıt sırasının `TerminateSequence` ileti.  
  
 Normal kapatma dizideki her ikisi de `TerminateSequence` iletilerini taşıyan çeşitli `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>İstek/yanıt, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF iki diziyi üzerinde bir gelen ve giden bir HTTP kanalı kullanılarak bir istek-yanıt ileti değişim deseni sağlar. WCF HTTP isteklerini tüm ileti aktarmaya kullanır. Tüm HTTP yanıtlarını bir boş gövdesi ve 202 HTTP durum kodu ' var.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturur bir `CreateSequence` iletisiyle bir teklif. WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisi oluşturmadan önce bir teklif vardır. WCF gönderir `CreateSequenceResponse` yönelik HTTP isteği için `CreateSequence`'s `ReplyTo` uç nokta başvurusu.  
  
#### <a name="requestreply-correlation"></a>İstek/yanıt bağıntısı  
 Tüm uygulama istek iletileri ayı WCF Başlatıcı sağlar bir `MessageId` ve `ReplyTo` uç nokta başvurusu. WCF Başlatıcı geçerli `CreateSequence` iletinin `ReplyTo` her uygulama istek iletisinde uç nokta başvurusu. WCF Yanıtlayıcı, gelen istek iletisi ayı gerektiren bir `MessageId` ve `ReplyTo`. Her iki uç nokta referansının URI sağlar WCF Yanıtlayıcı `CreateSequence` ve tüm uygulama istek iletilerinin aynıdır.
