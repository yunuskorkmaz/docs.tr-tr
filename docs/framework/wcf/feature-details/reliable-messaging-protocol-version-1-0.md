---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: f45a0d5e50e9ab8a07a203d2c40ad36ef298a40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-messaging-protocol-version-10"></a>Güvenilir Mesajlaşma Protokolü sürüm 1.0
Bu konu, WS güvenilir Mesajlaşma için Windows Communication Foundation (WCF) uygulama ayrıntılarını kapsar Şubat 2005 (sürüm 1.0) Protokolü HTTP aktarımı kullanarak birlikte çalışma için gerekli. WCF WS güvenilir Mesajlaşma kısıtlamaları ve bu konuda açıklanan açıklamalar izler. WS-ReliableMessaging 1.0 sürümü protokolü ile başlayan uygulandığını unutmayın [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 WS-güvenilir Protokolü WCF tarafından uygulandığına Mesajlaşma Şubat 2005 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Kolaylık olması için konunun aşağıdaki rolleri kullanır:  
  
-   Başlatıcı: WS güvenilir ileti sırası oluşturması başlatan istemci  
  
-   Yanıtlayıcı: başlatanın isteği alan hizmeti  
  
 Bu belgede aşağıdaki tabloda ad alanlarını ve önekleri kullanır.  
  
|önek|Ad Alanı|  
|------------|---------------|  
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>İleti  
  
### <a name="sequence-establishment-messages"></a>Sıra kurma iletileri  
 WCF uygulayan `CreateSequence` ve `CreateSequenceResponse` güvenilir ileti sırası kurmak için iletileri. Aşağıdaki kısıtlamalar geçerlidir:  
  
-   B1101: İsteğe bağlı Expires öğesinde WCF Başlatıcı oluşturmaz `CreateSequence` ileti veya durumda olduğunda `CreateSequence` iletisini içeren bir `Offer` öğesi, isteğe bağlı `Expires` öğesinde `Offer` öğesi.  
  
-   B1102: erişirken `CreateSequence` iletisi, WCF`Responder` alıp gönderen her ikisi de `Expires` var ancak değerlerine kullanmaz öğeleri.  
  
 WS güvenilir Mesajlaşma tanıtır `Offer` iki gruplarıdır oturumu form bağıntılı sıraları oluşturmak için bir mekanizma.  
  
-   R1103: Varsa `CreateSequence` içeren bir `Offer` öğesi, güvenilir Mesajlaşma Yanıtlayıcı gerekir ya da sırası kabul edin ve yanıt `CreateSequenceResponse` içeren bir `wsrm:Accept` öğesi, iki bağıntılı oluşturan gruplarıdır dizileri veya Reddet`CreateSequence` isteği.  
  
-   R1104: `SequenceAcknowledgement` ve ters sıra üzerinde akan uygulama iletileri gönderilir, için `ReplyTo` endpoint başvurusu `CreateSequence`.  
  
-   R1105: `AcksTo` ve `ReplyTo` endpoint başvuran `CreateSequence` octet-wise eşleşen adresi değerlere sahip olmalıdır.  
  
     WCF Yanıtlayıcı doğrular URI kısmı `AcksTo` ve `ReplyTo` EPR'ler özdeş bir dizisini oluşturmadan önce.  
  
-   R1106: `AcksTo` ve `ReplyTo` Endpoint başvurularında `CreateSequence` aynı başvurusu parametre kümesine sahip olmalıdır.  
  
     WCF zorunlu değildir ancak varsayar o [başvuru parametreleri] `AcksTo` ve `ReplyTo` üzerinde `CreateSequence` özdeş ve kullanır [başvuru parametreleri] `ReplyTo` onayları ve ters sıra iletileri için uç nokta başvurusu.  
  
-   R1107: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` ve üzerinde ters sıraları akan uygulama iletileri gönderilir, için `ReplyTo` endpoint başvurusu `CreateSequence`.  
  
-   R1108: iki gruplarıdır zaman serileri teklif mekanizması kullanılarak oluşturulan `[address]` özelliği `wsrm:AcksTo` bitiş noktası başvurusu alt öğesi olan `wsrm:Accept` öğesinin `CreateSequenceResponse` hedef URI byte-wise eşleşmelidir, `CreateSequence`.  
  
-   R1109: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, başlatıcı hem Yanıtlayıcı olarak iletileri için onayları tarafından gönderilen iletilerin gönderileceği aynı uç nokta referansı.  
  
     WS güvenilir Mesajlaşma WCF Başlatıcı hem Yanıtlayıcı arasında güvenilir oturumlar kurmak için kullanır. WCF'ın WS güvenilir Mesajlaşma uygulamasını sağlar güvenilir oturum tek yönlü, istek-yanıt ve tam çift yönlü desenleri Mesajlaşma. WS güvenilir Mesajlaşma `Offer` mekanizmasını `CreateSequence` / `CreateSequenceResponse` iki bağıntılı ters sıraları oluşturmanıza olanak sağlar ve tüm uç noktaları iletisi için uygun bir oturum Protokolü sağlar. WCF güvenlik garantisi uçtan uca koruma oturum tutarlılığı için de dahil olmak üzere oturumunun sağladığından, aynı hedef konumda aynı tarafa hedeflenen iletilerinin geliş emin olmak yararlı olur. Bu ardışık-yedeklemelerini dizisi onayları uygulama iletilerinde de sağlar. Bu nedenle, kısıtlamaları R1104, R1105 ve R1108 WCF için geçerlidir.  
  
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
  
-   B1201:WCF oluşturur ve erişimleri sıra numaraları daha yüksek `xs:long`'s en büyük içermeli değer, 9223372036854775807.  
  
-   B1202:WCF her zaman bir boş bodied son iletisiyle eylem URI'sini oluşturur, http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.  
  
-   B1203: WCF alır ve içeren sırası üstbilgi içeren bir ileti teslim bir `LastMessage` öğesi eylem URI'si değil sürece http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.  
  
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
 WCF kullanan `AckRequested` tutma mekanizması olarak üstbilgi. WCF isteğe bağlı oluşturmaz `MessageNumber` öğesi. İçeren bir ileti alır almaz bir `AckRequested` üstbilgisinin içeren `MessageNumber` öğesi, WCF yoksayar `MessageNumber` aşağıdaki örnekte gösterildiği gibi öğenin değeri.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement üstbilgisi  
 WCF WS güvenilir Mesajlaşma içinde sağlanan dizisi onayları ardışık mekanizması kullanır.  
  
-   R1401: iki gruplarıdır zaman dizileri kullanılarak oluşturulan `Offer` mekanizması, `SequenceAcknowledgement` üstbilgi dahil edilebilir hedeflenen alıcı aktarılan herhangi bir uygulama iletisi.  
  
-   B1402: WCF dizisi iletileri alma önce bir bildirim oluşturduğunuzda gerekir (örneğin, karşılamak için bir `AckRequested` ileti), WCF oluşturur bir `SequenceAcknowledgement` aralığı 0-0, aşağıdaki örnekte gösterildiği gibi içeren üstbilgi.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403: WCF oluşturmayacak `SequenceAcknowledgement` içeren üstbilgileri bir `Nack` öğesi ancak destekler `Nack` öğeleri.  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging hataları  
 WS güvenilir Mesajlaşma hataları WCF uygulaması için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   B1501: WCF oluşturmayacak `MessageNumberRollover` hataları.  
  
-   B1502:WCF uç noktası oluşturabilir `CreateSequenceRefused` hataları belirtiminde açıklandığı gibi.  
  
-   B1503:when hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantı işleyemiyor, WCF ek bir `CreateSequenceRefused` arıza alt kod, `netrm:ConnectionLimitReached`, aşağıdaki örnekte gösterildiği gibi.  
  
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
 WS güvenilir Mesajlaşma WS adresleme kullandığından, WCF WS güvenilir Mesajlaşma uygulaması WS adresleme hatalar oluşmasına neden olabilir. Bu bölüm, WCF açıkça WS güvenilir Mesajlaşma katmanında oluşturur WS adresleme hataları kapsar:  
  
-   Aşağıdakilerden biri doğruysa B1601:WCF hata ileti başlığı adresleme gereken oluşturur:  
  
    -   Bir ileti eksik bir `Sequence` başlığı ve bir `Action` üstbilgi.  
  
    -   A `CreateSequence` ileti eksik bir `MessageId` üstbilgi.  
  
    -   A `CreateSequence` ileti eksik bir `ReplyTo` üstbilgi.  
  
-   B1602:WCF eksik mesaja eylemi desteklenmiyor hataya oluşturur bir `Sequence` başlığı ve bir `Action` tanınan bir WS güvenilir Mesajlaşma belirtiminde değil üstbilgi.  
  
-   B1603:WCF uç nokta incelenmesi temel sıralı işlemez belirtmek için uç nokta kullanılamaz hatası oluşturur `CreateSequence` ileti üstbilgilerini adresleme.  
  
## <a name="protocol-composition"></a>İletişim kuralı oluşturma  
  
### <a name="composition-with-ws-addressing"></a>WS-adresleme ile oluşturma  
 WCF WS adresleme iki sürümlerini destekler: WS adresleme 2004/08 [WS-ADDR] ve W3C WS adresleme 1.0 önerileri [WS-ADDR-CORE] ve [WS ADDR SOAP].  
  
 While WS güvenilir Mesajlaşma belirtimi belirtilenlerden yalnızca WS adresleme 2004/08, onu değil kısıtlamak kullanılacak WS adresleme sürümü. WCF için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   R2101: hem WS adresleme 2004/08 ve WS adresleme 1.0 WS güvenilir Mesajlaşma ile kullanılabilir.  
  
-   R2102:A tek sürümü WS adresleme için kullanılan, belirli bir WS güvenilir Mesajlaşma dizi veya ters sıraları kullanarak bağıntılı çifti boyunca `wsrm:Offer` mekanizması.  
  
### <a name="composition-with-soap"></a>SOAP ile oluşturma  
 WCF SOAP 1.1 ve SOAP 1.2 WS güvenilir Mesajlaşma ile kullanımını destekler.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS güvenliği ve WS-SecureConversation ile oluşturma  
 WCF güvenli aktarım (HTTPS), WS-güvenlik ile oluşturma ve birleşim WS güvenli Konuşmayla kullanarak WS güvenilir Mesajlaşma dizileri için koruma sağlar. WCF için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   R2301: WS güvenilir Mesajlaşma dizisi bütünlüğü yanı sıra bütünlüğünü ve tek bir ileti gizliliğini korumak için WS-güvenli konuşma kullanılmalıdır WCF gerektirir.  
  
-   R2302:AWS-güvenli konuşma oturum WS güvenilir Mesajlaşma sequence(s) kurmadan önce oluşturulması gerekir.  
  
-   R2303: WS güvenilir Mesajlaşma ömrü sıra WS güvenli konuşma oturumunun ömrünü aşarsa `SecurityContextToken` WS güvenli konuşma gerekir yenilendi karşılık gelen konuşma yenileme WS güvenli bağlama kullanarak kullanılarak oluşturulmuştur.  
  
-   B2304:ws-güvenilir Mesajlaşma dizisi veya bağıntılı ters sıraları çifti tek bir WS-SecureConversation oturumla bağlı her zaman.  
  
     WCF kaynağı oluşturur `wsse:SecurityTokenReference` öğesi genişletilebilirlik bölümünü öğesinde `CreateSequence` ileti.  
  
-   WS-güvenli konuşma oluşan R2305:When bir `CreateSequence` ileti içermelidir `wsse:SecurityTokenReference` öğesi.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS güvenilir Mesajlaşma WS-Policy onaylama  
 WCF kullanan WS güvenilir Mesajlaşma WS-Policy onaylama `wsrm:RMAssertion` uç noktaları özellikleri açıklamak için. WCF için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   B3001: WCF iliştirir `wsrm:RMAssertion` WS-Policy onaylama `wsdl:binding` öğeleri. WCF destekleyen iki ekleri `wsdl:binding` ve `wsdl:port` öğeleri.  
  
-   B3002: WCF WS güvenilir Mesajlaşma onaylama aşağıdaki isteğe bağlı özellikleri destekler ve bunları denetim WCF sunar`ReliableMessagingBindingElement`:  
  
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
 WCF WS güvenilir Mesajlaşma genişletilebilirlik dizisi ileti akışı üzerinde isteğe bağlı ek sıkı denetim sağlamak için kullanır.  
  
 Akış denetimi ayarlayarak etkin `ReliableSessionBindingElement`'s `FlowControlEnabled``bool` özelliğine `true`. WCF için uygulama kısıtlamaları listesi aşağıdadır:  
  
-   B4001: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF oluşturan bir `netrm:BufferRemaining` öğesi genişletilmesinde öğesinde `SequenceAcknowledgement` üstbilgi.  
  
-   B4002: Güvenilir Mesajlaşma akış denetimi etkinleştirildiğinde, WCF gerektirmez bir `netrm:BufferRemaining` bulunması öğesi `SequenceAcknowledgement` aşağıdaki örnekte gösterildiği gibi üstbilgi.  
  
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
  
-   B4003: WCF kullanan `netrm:BufferRemaining` kaç tane yeni güvenilir Mesajlaşma hedef iletileri göstermek için arabellek.  
  
-   B4004: WCF güvenilir Mesajlaşma hizmeti güvenilir Mesajlaşma hedef uygulama iletileri hızla alamadığı zaman aktarılan iletilerin sayısını kısıtlar. Hedef arabellek güvenilir Mesajlaşma iletileri ve öğenin değeri 0 olarak bırakır.  
  
-   B4005: WCF oluşturur `netrm:BufferRemaining` tamsayı değerleri 0 ile 4096 (bunlar dahil) arasında ve tamsayı değerleri 0 arasında okur ve `xs:int`'s `maxInclusive` 214748364 (bunlar dahil) değeri.  
  
## <a name="message-exchange-patterns"></a>İleti Exchange desenleri  
 WS güvenilir Mesajlaşma farklı ileti Exchange desenler için kullanıldığında, bu bölümde WCF'in davranışını tanımlar. Her ileti değişim deseni için aşağıdaki iki dağıtım senaryoları değerlendirilir:  
  
-   Olmayan adreslenebilir Başlatıcı: Başlatıcı güvenlik duvarının arkasında olan; Yanıtlayıcı iletileri yalnızca HTTP yanıtları başlatıcıya sunabilir.  
  
-   Adreslenebilir Başlatıcı: HTTP isteklerini Başlatıcı hem Yanıtlayıcı gönderilebilir; diğer bir deyişle, iki ters HTTP bağlantısı kurulabilir.  
  
### <a name="one-way-non-addressable-initiator"></a>Tek yönlü, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF bir HTTP kanalı üzerinden bir sıralı kullanarak bir tek yönlü ileti değişim deseni sağlar. WCF HTTP isteklerini RMD alınan tüm iletileri RMS'ye aktarmak için tüm iletiler RMS'den RMD ve HTTP yanıtı iletmek için kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturan bir `CreateSequence` iletisiyle teklif yok. WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir dizisini oluşturmadan önce bir teklif yok. WCF Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.  
  
#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement  
 WCF Başlatıcısı tüm iletileri yanıtlama onayları işler `CreateSequence` iletisi ve hata iletileri. WCF Yanıtlayıcı her zaman yanıt hem dizisi olarak tek başına bir bildirim oluşturur ve `AckRequested` iletileri.  
  
#### <a name="terminatesequence-message"></a>TerminateSequence iletisi  
 WCF değerlendirir `TerminateSequence` tek yönlü bir işlem olarak HTTP yanıtı anlamına gelen bir boş gövde ve HTTP 202 durum kodu vardır.  
  
### <a name="one-way-addressable-initiator"></a>Tek yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF bir dizisi üzerinde bir gelen ve giden bir Http kanalı kullanılarak bir tek yönlü ileti değişim deseni sağlar. WCF HTTP isteklerini tüm iletileri iletmek için kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturan bir `CreateSequence` iletisiyle teklif yok. WCF Yanıtlayıcı sağlar `CreateSequence` sahip bir dizisini oluşturmadan önce bir teklif yok. WCF Yanıtlayıcı iletir `CreateSequenceResponse` bir HTTP isteği iletisi ele ile `ReplyTo` bitiş noktası başvurusu.  
  
### <a name="duplex-addressable-initiator"></a>Çift yönlü, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF bir gelen ve giden bir HTTP kanalı iki sıraları kullanarak bir iki yönlü tam olarak zaman uyumsuz ileti değişim deseni sağlar. WCF HTTP isteklerini tüm iletileri iletmek için kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle. WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir. WCF gönderir `CreateSequenceResponse` HTTP isteği ele için `CreateSequence`'s `ReplyTo` bitiş noktası başvurusu.  
  
#### <a name="sequence-lifetime"></a>Sıra yaşam süresi  
 WCF iki sıraları tam çift yönlü bir oturum olarak değerlendirir.  
  
 Bir dizi hataları bir arıza oluşturma sırasında WCF hem sıraları alınmasını uzak uç nokta bekler. Bir dizi hataları bir arıza okuma sırasında WCF hem sıraları hataları.  
  
 WCF giden sırası kapatın ve gelen sırası iletileri işlemek devam edin. Buna karşılık, WCF gelen sırası kapatma işlemek ve kendi giden sırasını iletileri göndermeye devam eder.  
  
### <a name="request-reply-non-addressable-initiator"></a>İstek-yanıt, adreslenebilir olmayan Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 İstek-yanıt ileti değişim deseni iki kullanarak üzerinde bir HTTP kanalı dizilerinin ve WCF tek yönlü sağlar. WCF HTTP isteklerini istek sırasının iletileri iletmek için ve HTTP yanıtlarını yanıt sırasının tüm iletileri iletmek için kullanır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle. WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir. WCF Yanıtlayıcı yanıtlar için `CreateSequence` ile istek bir `CreateSequenceResponse` ileti.  
  
#### <a name="one-way-message"></a>Tek yönlü iletisi  
 Tek yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve tek başına bir alan `SequenceAcknowledgement` HTTP yanıt iletisi. `SequenceAcknowledgement` Aktarılan ileti kabul gerekir.  
  
 WCF Yanıtlayıcı onay, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt isteğine yanıt verebilir.  
  
#### <a name="two-way-messages"></a>İki şekilde iletileri  
 İki yönlü ileti değişimi Protokolü başarıyla tamamlamak için WCF Başlatıcı HTTP isteği bir istek sırası iletisinin aktarır ve HTTP yanıtı yanıt sırası iletiyi alır. Yanıt taşımalıdır bir `SequenceAcknowledgement` istek sırası iletisi bildirmeden aktarılan.  
  
 WCF Yanıtlayıcı bir uygulama yanıt, bir hata veya boş gövde ve HTTP 202 durum kodu ile bir yanıt isteğine yanıt verebilir.  
  
 Tek yönlü iletileri varlığını ve uygulama yanıt zamanlama nedeniyle istek sırası ileti sıra numarası ve yanıt ileti sıra numarası hiçbir bağıntı sahiptir.  
  
#### <a name="retrying-replies"></a>Yanıt yeniden deneniyor  
 WCF HTTP istek-yanıt bağıntısı iki yönlü ileti exchange Protokolü bağıntı için kullanır. Bu nedenle, WCF Başlatıcı istek sırası iletisi onaylandığında, ancak yerine HTTP yanıtı bir bildirim, kullanıcı iletisi veya hataya getirirken bir istek sırası iletisi yeniden deneniyor durdurmaz. WCF Yanıtlayıcı yanıt bağıntılı isteğin HTTP isteği leg üzerinde yanıtları yeniden dener.  
  
#### <a name="lastmessage-exchange"></a>LastMessage Exchange  
 WCF Başlatıcı oluşturur ve HTTP isteği leg üzerinde boş bodied son ileti iletir. WCF yanıt gerektiriyor, ancak gerçek yanıt iletisini yok sayıyor. İstek sırasının boş bodied son iletisiyle yanıt sırasının boş bodied son ileti WCF Yanıtlayıcı yanıtlar.  
  
 WCF Yanıtlayıcı içinde eylem URI'si değil son bir ileti alırsa http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF yanıtları son iletiyle. Bir iki yönlü ileti exchange protokol söz konusu olduğunda, son uygulama ileti taşır; bir tek yönlü ileti exchange protokol söz konusu olduğunda, son ileti boştur.  
  
 WCF Yanıtlayıcı onay yanıtı sırasının boş bodied son ileti için gerekli değildir.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Tüm isteklerin geçerli bir yanıt teslim aldıktan sonra WCF Başlatıcı oluşturur ve istek sırasının iletir `TerminateSequence` HTTP isteği leg iletisi. WCF yanıt gerektiriyor, ancak gerçek yanıt iletisini yok sayıyor. WCF Yanıtlayıcı yanıtları istek sırası için 's `TerminateSequence` yanıt sırasının iletisiyle `TerminateSequence` ileti.  
  
 Normal kapatma dizisindeki her ikisi de `TerminateSequence` iletilerini taşıyan tam kapsamlı bir `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>İstek/yanıt, adreslenebilir Başlatıcı  
  
#### <a name="binding"></a>Bağlama  
 WCF iki sıraları üzerinden bir gelen ve giden bir HTTP kanalı kullanılarak bir istek-yanıt ileti değişim deseni sağlar. WCF HTTP isteklerini tüm iletileri iletmek için kullanır. Tüm HTTP yanıtını bir boş gövde ve HTTP 202 durum kodu vardır.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 WCF Başlatıcı oluşturan bir `CreateSequence` bir teklif iletisiyle. WCF Yanıtlayıcı sağlar `CreateSequence` bir dizisini oluşturmadan önce bir teklif sahiptir. WCF gönderir `CreateSequenceResponse` HTTP isteği ele için `CreateSequence`'s `ReplyTo` bitiş noktası başvurusu.  
  
#### <a name="requestreply-correlation"></a>İstek/yanıt bağıntısı  
 Tüm uygulama istek iletileri ayı WCF Başlatıcı sağlar bir `MessageId` ve `ReplyTo` bitiş noktası başvurusu. WCF Başlatıcı geçerlidir `CreateSequence` iletinin `ReplyTo` her uygulama istek iletisi üzerinde uç noktası başvuru. Bu gelen istek iletileri ayı WCF Yanıtlayıcı gerektiren bir `MessageId` ve `ReplyTo`. Her iki uç nokta referansının URI sağlar WCF Yanıtlayıcı `CreateSequence` ve tüm uygulama istek iletilerini aynıdır.
