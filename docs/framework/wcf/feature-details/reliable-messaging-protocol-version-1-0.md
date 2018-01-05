---
title: "Güvenilir Mesajlaşma Protokolü sürüm 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a32c16067446459817e9943c2d729a67373a0333
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-protocol-version-10"></a>Güvenilir Mesajlaşma Protokolü sürüm 1.0
Bu konuda ele alınmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WS güvenilir Mesajlaşma uygulama ayrıntılarını Şubat 2005 (sürüm 1.0) protokolünü kullanarak HTTP aktarımı birlikte çalışma için gerekli. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS güvenilir Mesajlaşma kısıtlamaları ve bu konuda açıklanan açıklamalar izler. WS-ReliableMessaging 1.0 sürümü protokolü ile başlayan uygulandığını unutmayın [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 WS-güvenilir Protokolü uygulandığına Mesajlaşma Şubat 2005 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tarafından <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Kolaylık olması için konunun aşağıdaki rolleri kullanır:  
  
-   Başlatıcı: WS güvenilir ileti sırası oluşturması başlatan istemci  
  
-   Yanıtlayıcı: başlatanın isteği alan hizmeti  
  
 Bu belgede aşağıdaki tabloda ad alanlarını ve önekleri kullanır.  
  
|önek|Ad Alanı|  
|------------|---------------|  
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/RM|  
|netrm|http://schemas.microsoft.com/ws/2006/05/RM|  
|s|http://www.w3.org/2003/05/SOAP-Envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/Addressing|  
|wsse|http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>İleti  
  
### <a name="sequence-establishment-messages"></a>Sıra kurma iletileri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uygulayan `CreateSequence` ve `CreateSequenceResponse` güvenilir ileti sırası kurmak için iletileri. Aşağıdaki kısıtlamalar geçerlidir:  
  
-   B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı isteğe bağlı Expires öğesinde oluşturmaz `CreateSequence` ileti veya durumda olduğunda `CreateSequence` iletisini içeren bir `Offer` öğesi, isteğe bağlı `Expires` öğesinde `Offer` öğesi.  
  
-   B1102: erişirken `CreateSequence` ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `Responder` alıp gönderen her ikisi de `Expires` var ancak değerlerine kullanmaz öğeleri.  
  
 WS güvenilir Mesajlaşma tanıtır `Offer` iki gruplarıdır oturumu form bağıntılı sıraları oluşturmak için bir mekanizma.  
  
-   R1103: Varsa `CreateSequence` içeren bir `Offer` öğesi, güvenilir Mesajlaşma Yanıtlayıcı gerekir ya da sırası kabul edin ve yanıt `CreateSequenceResponse` içeren bir `wsrm:Accept` öğesi, iki bağıntılı oluşturan gruplarıdır dizileri veya Reddet`CreateSequence` isteği.  
  
-   R1104: `SequenceAcknowledgement` ve ters sıra üzerinde akan uygulama iletileri gönderilir, için `ReplyTo` endpoint başvurusu `CreateSequence`.  
  
-   R1105: `AcksTo` ve `ReplyTo` endpoint başvuran `CreateSequence` octet-wise eşleşen adresi değerlere sahip olmalıdır.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı doğrular URI kısmı `AcksTo` ve `ReplyTo` EPR'ler özdeş bir dizisini oluşturmadan önce.  
  
-   R1106: `AcksTo` ve `ReplyTo` Endpoint başvurularında `CreateSequence` aynı başvurusu parametre kümesine sahip olmalıdır.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zorunlu değildir ancak varsayar o [başvuru parametreleri] `AcksTo` ve `ReplyTo` üzerinde `CreateSequence` özdeş ve kullanır [başvuru parametreleri] `ReplyTo` onayları ve ters sıra iletileri için uç nokta başvurusu.  
  
-   R1107: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` ve üzerinde ters sıraları akan uygulama iletileri gönderilir, için `ReplyTo` endpoint başvurusu `CreateSequence`.  
  
-   R1108: iki gruplarıdır zaman serileri teklif mekanizması kullanılarak oluşturulan `[address]` özelliği `wsrm:AcksTo` bitiş noktası başvurusu alt öğesi olan `wsrm:Accept` öğesinin `CreateSequenceResponse` hedef URI byte-wise eşleşmelidir, `CreateSequence`.  
  
-   R1109: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, başlatıcı hem Yanıtlayıcı olarak iletileri için onayları tarafından gönderilen iletilerin gönderileceği aynı uç nokta referansı.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS güvenilir Mesajlaşma Başlatıcı hem Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s uygulamasını WS güvenilir Mesajlaşma sağlar güvenilir oturum tek yönlü, istek-yanıt ve tam çift yönlü desenleri Mesajlaşma. WS güvenilir Mesajlaşma `Offer` mekanizmasını `CreateSequence` / `CreateSequenceResponse` iki bağıntılı ters sıraları oluşturmanıza olanak sağlar ve tüm uç noktaları iletisi için uygun bir oturum Protokolü sağlar. Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik garanti sağlayan uçtan uca koruma oturum tutarlılığı için de dahil olmak üzere bu tür bir oturum için aynı tarafa yönelik iletilerin aynı hedefte ulaşan emin olmak yararlı olur. Bu ardışık-yedeklemelerini dizisi onayları uygulama iletilerinde de sağlar. R1104, R1105 ve R1108 kısıtlamaları uygulamak bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Örnek olarak bir `CreateSequence` ileti.  
  
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
  
 Örnek olarak bir `CreateSequenceResponse` ileti.  
  
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
  
### <a name="sequence"></a>Sırası  
 Dizilerine uygulama kısıtlamaları listesi aşağıdadır:  
  
-   B1201:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur ve daha yüksek sıra numaraları erişir `xs:long`'s en büyük içermeli değer, 9223372036854775807.  
  
-   B1202:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her zaman bir boş bodied son iletisiyle http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage eylem URI'si oluşturur.  
  
-   B1203: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] alır ve içeren sırası üstbilgi içeren bir ileti teslim bir `LastMessage` öğesi eylem URI'si http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage değil sürece.  
  
 Bir sıra üstbilgisi örneği.  
  
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
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]kullanan `AckRequested` tutma mekanizması olarak üstbilgi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]İsteğe bağlı oluşturmaz `MessageNumber` öğesi. İçeren bir ileti alır almaz bir `AckRequested` üstbilgisinin içeren `MessageNumber` öğesi, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yoksayar `MessageNumber` aşağıdaki örnekte gösterildiği gibi öğenin değeri.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement üstbilgisi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS güvenilir Mesajlaşma içinde sağlanan dizisi bildirimleri için ardışık mekanizması kullanır.  
  
-   R1401: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` üstbilgi dahil edilebilir hedeflenen alıcı aktarılan herhangi bir uygulama iletisi.  
  
-   B1402: Zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dizisi iletileri alma önce onay oluşturmanız gerekir (örneğin karşılamak için bir `AckRequested` ileti), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur bir `SequenceAcknowledgement` aralık 0-0, aşağıda gösterildiği gibi içeriyor üstbilgisi örnek.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturmayacak `SequenceAcknowledgement` içeren üstbilgileri bir `Nack` öğesi ancak destekler `Nack` öğeleri.  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging hataları  
 Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama hatalarının WS güvenilir Mesajlaşma:  
  
-   B1501: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturmayacak `MessageNumberRollover` hataları.  
  
-   B1502:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktası oluşturabilir `CreateSequenceRefused` hataları belirtiminde açıklandığı gibi.  
  
-   B1503:when hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantı işleyemiyor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ek bir oluşturur `CreateSequenceRefused` arıza alt kod, `netrm:ConnectionLimitReached`, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
### <a name="ws-addressing-faults"></a>WS-adresleme hataları  
 WS güvenilir Mesajlaşma WS adresleme kullandığından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS güvenilir Mesajlaşma uygulaması WS adresleme hataları görüntülenebilir. Bu bölümde kapsar WS adresleme hataları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] açıkça WS güvenilir Mesajlaşma katmanında oluşturur:  
  
-   B1601:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] şunlardan biri doğru olduğunda hata ileti başlığı adresleme gereken oluşturur:  
  
    -   Bir ileti eksik bir `Sequence` başlığı ve bir `Action` üstbilgi.  
  
    -   A `CreateSequence` ileti eksik bir `MessageId` üstbilgi.  
  
    -   A `CreateSequence` ileti eksik bir `ReplyTo` üstbilgi.  
  
-   B1602:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] eksik mesaja eylemi desteklenmiyor hataya oluşturur bir `Sequence` başlığı ve bir `Action` tanınan bir WS güvenilir Mesajlaşma belirtiminde değil üstbilgi.  
  
-   B1603:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç nokta incelenmesi temel sıralı işlemez belirtmek için uç nokta kullanılamaz hatası oluşturur `CreateSequence` ileti üstbilgilerini adresleme.  
  
## <a name="protocol-composition"></a>İletişim kuralı oluşturma  
  
### <a name="composition-with-ws-addressing"></a>WS-adresleme ile oluşturma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS-adresleme iki sürümlerini destekler: WS adresleme 2004/08 [WS-ADDR] ve W3C WS adresleme 1.0 önerileri [WS-ADDR-CORE] ve [WS ADDR SOAP].  
  
 While WS güvenilir Mesajlaşma belirtimi belirtilenlerden yalnızca WS adresleme 2004/08, onu değil kısıtlamak kullanılacak WS adresleme sürümü. Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2101: hem WS adresleme 2004/08 ve WS adresleme 1.0 WS güvenilir Mesajlaşma ile kullanılabilir.  
  
-   R2102:A tek sürümü WS adresleme için kullanılan, belirli bir WS güvenilir Mesajlaşma dizi veya ters sıraları kullanarak bağıntılı çifti boyunca `wsrm:Offer` mekanizması.  
  
### <a name="composition-with-soap"></a>SOAP ile oluşturma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]SOAP 1.1 ve SOAP 1.2 WS güvenilir Mesajlaşma ile destekler kullanın.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS güvenliği ve WS-SecureConversation ile oluşturma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve birleşim WS güvenli Konuşmayla kullanarak WS güvenilir Mesajlaşma dizileri için koruma sağlar. Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2301: WS güvenilir Mesajlaşma dizisi bütünlüğü yanı sıra bütünlüğünü ve tek bir ileti gizliliğini korumak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS güvenli konuşma kullanılmalıdır gerektirir.  
  
-   R2302:AWS-güvenli konuşma oturum WS güvenilir Mesajlaşma sequence(s) kurmadan önce oluşturulması gerekir.  
  
-   R2303: WS güvenilir Mesajlaşma ömrü sıra WS güvenli konuşma oturumunun ömrünü aşarsa `SecurityContextToken` WS güvenli konuşma gerekir yenilendi karşılık gelen konuşma yenileme WS güvenli bağlama kullanarak kullanılarak oluşturulmuştur.  
  
-   B2304:ws-güvenilir Mesajlaşma dizisi veya bağıntılı ters sıraları çifti tek bir WS-SecureConversation oturumla bağlı her zaman.  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kaynağı oluşturur `wsse:SecurityTokenReference` öğesi genişletilebilirlik bölümünü öğesinde `CreateSequence` ileti.  
  
-   WS-güvenli konuşma oluşan R2305:When bir `CreateSequence` ileti içermelidir `wsse:SecurityTokenReference` öğesi.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS güvenilir Mesajlaşma WS-Policy onaylama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS güvenilir Mesajlaşma WS-Policy onaylama kullanan `wsrm:RMAssertion` uç noktaları özellikleri açıklamak için. Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iliştirir `wsrm:RMAssertion` WS-Policy onaylama `wsdl:binding` öğeleri. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Her iki ekleri destekler `wsdl:binding` ve `wsdl:port` öğeleri.  
  
-   B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS güvenilir Mesajlaşma onaylama aşağıdaki isteğe bağlı özellikleri destekler ve bunları üzerinde denetim sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableMessagingBindingElement`:  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     Bir örnek verilmiştir.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>Akış Denetim WS güvenilir Mesajlaşma uzantısı  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WS güvenilir Mesajlaşma genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.  
  
 Akış denetimi ayarlayarak etkin `ReliableSessionBindingElement`'s `FlowControlEnabled``bool` özelliğine `true`. Geçerli kısıtlamaları listesi aşağıda verilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B4001: Güvenilir Mesajlaşma akışı denetlemek etkin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturan bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` üstbilgi.  
  
-   B4002: Güvenilir Mesajlaşma akışı denetlemek etkin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gerektirmez bir `netrm:BufferRemaining` bulunması öğesi `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi üstbilgi.  
  
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
  
-   B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanan `netrm:BufferRemaining` kaç tane yeni güvenilir Mesajlaşma hedef iletileri göstermek için arabellek.  
  
-   B4004: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilir Mesajlaşma hizmeti güvenilir Mesajlaşma hedef uygulama iletileri hızla alamadığı zaman gönderilen ileti sayısını kısıtlar. Hedef arabellek güvenilir Mesajlaşma iletileri ve öğenin değeri 0 olarak bırakır.  
  
-   B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile 4096 (bunlar dahil) arasında ve tamsayı değerleri 0 arasında okur ve `xs:int`'s `maxInclusive` 214748364 (bunlar dahil) değeri.  
  
## <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 Bu bölümde açıklanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s davranış WS güvenilir Mesajlaşma farklı ileti Exchange desenler için kullanılır. Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları değerlendirilir:  
  
-   Olmayan adreslenebilir Başlatıcı: Başlatıcı güvenlik duvarının arkasında olan; Yanıtlayıcı iletileri yalnızca HTTP yanıtları başlatıcıya sunabilir.  
  
-   Adreslenebilir Başlatıcı: HTTP isteklerini Başlatıcı hem Yanıtlayıcı gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantısı kurulabilir.  
  
### <a name="one-way-non-addressable-initiator"></a>Tek yönlü, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir HTTP kanalı üzerinden bir sıralı kullanarak bir tek yönlü ileti değişim deseni sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]HTTP isteklerini RMD alınan tüm iletileri RMS'ye aktarmak için tüm iletiler RMS'den RMD ve HTTP yanıtı iletmek için kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` iletisiyle teklif yok. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` sahip bir dizisini oluşturmadan önce bir teklif yok. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcısı tüm iletileri yanıtlama onayları işler `CreateSequence` iletisi ve hata iletileri. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı oluşturur her zaman tek başına bir bildirim yanıt hem sıralı olarak ve `AckRequested` iletileri.  
  
#### <a name="terminatesequence-message"></a>TerminateSequence iletisi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]işler `TerminateSequence` tek yönlü bir işlem olarak HTTP yanıtı anlamına gelen bir boş gövde ve HTTP 202 durum kodu vardır.  
  
### <a name="one-way-addressable-initiator"></a>Tek yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir dizisi üzerinde bir gelen ve giden bir Http kanalı kullanılarak bir tek yönlü ileti değişim deseni sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` iletisiyle teklif yok. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` sahip bir dizisini oluşturmadan önce bir teklif yok. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı iletir `CreateSequenceResponse` bir HTTP isteği iletisi ele ile `ReplyTo` bitiş noktası başvurusu.  
  
### <a name="duplex-addressable-initiator"></a>Çift yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir gelen ve giden bir HTTP kanalı iki sıraları kullanarak bir iki yönlü tam olarak zaman uyumsuz ileti değişim deseni sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]gönderir `CreateSequenceResponse` HTTP isteği ele için `CreateSequence`'s `ReplyTo` bitiş noktası başvurusu.  
  
#### <a name="sequence-lifetime"></a>Sıra yaşam süresi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]iki sıraları tam çift yönlü bir oturum olarak değerlendirir.  
  
 Bir dizi hataları bir arıza oluşturma sırasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem sıraları alınmasını uzak uç nokta bekler. Bir dizi hataları bir arıza okuma sırasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem sıraları hataları.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Giden sırası kapatın ve gelen sırası iletileri işlemeye devam edebilirsiniz. Buna karşılık, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelen sırası kapatma işlemek ve onun giden sırasını iletileri göndermeye devam eder.  
  
### <a name="request-reply-non-addressable-initiator"></a>İstek-yanıt, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]üzerinde bir HTTP kanalı iki kullanarak bir tek yönlü ve istek-yanıt ileti değişim deseni dizilerinin sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]HTTP isteklerini istek sırasının iletileri iletmek için ve yanıt sırasının tüm iletileri iletmek için HTTP yanıtlarını kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.  
  
#### <a name="one-way-message"></a>Tek yönlü iletisi  
 Tek yönlü ileti değişimi Protokolü başarıyla tamamlanması için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi. `SequenceAcknowledgement` Aktarılan ileti kabul gerekir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı isteğine bir bildirim, bir hata ya da yanıtın bir boş gövde ve HTTP 202 durum kodu ile yanıtla.  
  
#### <a name="two-way-messages"></a>İki şekilde iletileri  
 İki yönlü ileti değişimi Protokolü başarıyla tamamlanması için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve HTTP yanıtı yanıt sırası iletiyi alır. Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi bildirmeden aktarılan.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı isteğine bir uygulama yanıt, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt yanıtla.  
  
 Tek yönlü iletileri varlığını ve uygulama yanıt zamanlama nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası hiçbir bağıntı sahiptir.  
  
#### <a name="retrying-replies"></a>Yanıt yeniden deneniyor  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]HTTP istek-yanıt bağıntısı iki yönlü ileti exchange Protokolü bağıntı için kullanır. Bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı değil durdurmak istek sırası iletisi onaylandığında bir istek sırası iletisi yeniden deneniyor, ancak bunun yerine ne zaman HTTP yanıtı taşıyan bir bildirim, kullanıcı iletisi ya da hata. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıt bağıntılı isteğin HTTP isteği leg üzerinde yanıtları yeniden dener.  
  
#### <a name="lastmessage-exchange"></a>LastMessage Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturur ve HTTP isteği leg üzerinde boş bodied son ileti iletir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir yanıt gerektiriyor, ancak gerçek yanıt iletisini yok sayıyor. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıtlar için istek sırasının boş bodied son iletisiyle yanıt sırasının boş bodied son ileti.  
  
 Varsa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı alır, eylem URI'si değil http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, son bir ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] son iletiye verilen yanıtlar. Bir iki yönlü ileti exchange protokol söz konusu olduğunda, son uygulama ileti taşır; bir tek yönlü ileti exchange protokol söz konusu olduğunda, son ileti boştur.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıt sırasının boş bodied son ileti için onay gerektirmez.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Tüm isteklerin geçerli bir yanıt alındığında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturur ve bu isteği sırasının iletir `TerminateSequence` HTTP isteği leg iletisi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir yanıt gerektiriyor, ancak gerçek yanıt iletisini yok sayıyor. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı yanıtları istek sırası için 's `TerminateSequence` yanıt sırasının iletisiyle `TerminateSequence` ileti.  
  
 Normal kapatma dizisindeki her ikisi de `TerminateSequence` iletilerini taşıyan tam kapsamlı bir `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>İstek/yanıt, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]iki sıraları üzerinden bir gelen ve giden bir HTTP kanalı kullanılarak bir istek-yanıt ileti değişim deseni sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]gönderir `CreateSequenceResponse` HTTP isteği ele için `CreateSequence`'s `ReplyTo` bitiş noktası başvurusu.  
  
#### <a name="requestreply-correlation"></a>İstek/yanıt bağıntısı  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı sağlar tüm uygulama istek iletileri ayı bir `MessageId` ve `ReplyTo` bitiş noktası başvurusu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Başlatıcı geçerlidir `CreateSequence` iletinin `ReplyTo` her uygulama istek iletisi üzerinde uç noktası başvuru. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayan gerektiriyorsa, gelen istek iletileri ayı bir `MessageId` ve `ReplyTo`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yanıtlayıcı sağlar, her iki uç nokta referansının URI `CreateSequence` ve tüm uygulama istek iletilerini aynıdır.
