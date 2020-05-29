---
title: Güvenilir Mesajlaşma Protokolü sürüm 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 8d192afcffca52136d6d71de49770c5a5ad13895
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202300"
---
# <a name="reliable-messaging-protocol-version-10"></a>Güvenilir Mesajlaşma Protokolü sürüm 1.0

Bu konu, HTTP taşıması kullanılarak birlikte çalışabilirlik için gereken WS-güvenilir mesajlaşma Şubat 2005 (sürüm 1,0) protokolü için Windows Communication Foundation (WCF) uygulama ayrıntılarını ele almaktadır. WCF, bu konuda açıklanan kısıtlamalar ve açıklamalar ile WS-güvenilir mesajlaşma belirtimini izler. WS-ReliableMessaging sürüm 1,0 protokolünün WinFX ile başlayarak uygulandığını unutmayın.

WS-güvenilir mesajlaşma Şubat 2005 protokolü, tarafından WCF 'de uygulanır <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .

Kolaylık olması için, konusu aşağıdaki rolleri kullanır:

- Başlatıcı: WS-güvenilir Ileti sırası oluşturmayı Başlatan istemci

- Yanıtlayıcı: başlatıcısının isteklerini alan hizmet

Bu belge aşağıdaki tablodaki ön ekleri ve ad alanlarını kullanır.

|Ön ek|Ad Alanı|
|------------|---------------|
|WSRM|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|Netra|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|WSA|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|WSO|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a>Mesajlaşma

### <a name="sequence-establishment-messages"></a>Sıra kurulumu Iletileri

WCF `CreateSequence` , `CreateSequenceResponse` güvenilir bir ileti sırası oluşturmak için ve iletilerini uygular. Aşağıdaki kısıtlamalar geçerlidir:

- B1101: WCF başlatıcısı, iletide isteğe bağlı süre sonu öğesini oluşturmaz `CreateSequence` veya `CreateSequence` ileti bir öğesi içerdiğinde, `Offer` öğesinde isteğe bağlı öğe olan durumlarda `Expires` `Offer` .

- B1102: `CreateSequence` iletiye erişirken, WCF, varsa `Responder` her iki öğeyi de gönderir ve alır `Expires` , ancak değerlerini kullanmaz.

WS-güvenilir mesajlaşma, `Offer` bir oturum oluşturan iki dönüştürüce bağıntılı diziyi oluşturma mekanizmasını tanıtır.

- R1103: `CreateSequence` bir öğesi varsa `Offer` , güvenilir mesajlaşma Yanıtlayıcısı diziyi kabul etmeli ve `CreateSequenceResponse` bir `wsrm:Accept` öğesi içeren, iki ilişkili dönüştürme dizisi oluşturan veya isteği reddedecek şekilde yanıt vermelidir `CreateSequence` .

- R1104: `SequenceAcknowledgement` ve convero sıralaması üzerinde akan uygulama iletileri `ReplyTo` , öğesinin uç nokta başvurusuna gönderilmelidir `CreateSequence` .

- R1105: `AcksTo` ve `ReplyTo` içindeki uç nokta başvuruları, `CreateSequence` sekizli temelinde eşleşen adres değerlerine sahip olmalıdır.

  WCF Yanıtlayıcı, ve EPRs 'in URI kısmının `AcksTo` `ReplyTo` bir sıra oluşturmadan önce özdeş olduğunu doğrular.

- R1106: `AcksTo` ve `ReplyTo` içindeki uç nokta başvuruları `CreateSequence` aynı başvuru parametreleri kümesine sahip olmalıdır.

  WCF zorunlu değildir, ancak/üzerindeki [başvuru parametreleri] öğesinin `AcksTo` aynı olduğunu varsayar `ReplyTo` `CreateSequence` ve `ReplyTo` bildirimlerin ve dönüştürüme sırası iletileri için uç nokta başvurusundan [başvuru parametreleri] kullanır.

- R1107: mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` `SequenceAcknowledgement` ve listesiyse dizileri üzerinde akan uygulama iletileri `ReplyTo` , öğesinin uç nokta başvurusuna gönderilmelidir `CreateSequence` .

- R1108: teklif mekanizması kullanılarak iki listesiyse dizisi oluşturulduğunda, `[address]` `wsrm:AcksTo` öğesinin öğesinin bitiş noktası başvurusu alt öğesinin özelliği, öğesinin `wsrm:Accept` `CreateSequenceResponse` hedef URI 'si ile eşleşmelidir `CreateSequence` .

- R1109: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , başlatıcı tarafından gönderilen iletiler ve yanıtlayanın yanıt veren tarafından ileti bildirimleri aynı uç nokta başvurusuna gönderilmelidir.

  WCF, başlatıcı ve Yanıtlayıcı arasında güvenilir oturumlar oluşturmak için WS-güvenilir mesajlaşma kullanır. WCF WS-güvenilir Mesajlaşma uygulamasının tek yönlü, istek-yanıt ve tam çift yönlü mesajlaşma desenleri için güvenilir bir oturum sağlar. Üzerinde WS-güvenilir mesajlaşma `Offer` mekanizması `CreateSequence` / `CreateSequenceResponse` , iki bağıntılı dönüştürme dizisi ayarlamanıza olanak sağlar ve tüm ileti uç noktaları için uygun bir oturum Protokolü sağlar. WCF, oturum bütünlüğü için uçtan uca koruma dahil olmak üzere bu tür bir oturum için güvenlik garantisi sağladığından, aynı tarafa yönelik iletilerin aynı hedefe döndürüldüğünü sağlamak yararlıdır. Bu Ayrıca, uygulama iletilerinde sıralı olarak oluşan bildirimlerin yedeklenmesini sağlar. Bu nedenle, R1104, R1105 ve R1108 kısıtlamaları WCF için geçerlidir.

`CreateSequence`İleti örneği.

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

 `CreateSequenceResponse`İleti örneği.

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

### <a name="sequence"></a>Sequence

Diziler için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- B1201: WCF `xs:long` , en yüksek kapsamlı değer olan 9223372036854775807 ' den fazla olmayan sıra numarası üretir ve erişir.

- B1202: WCF, eylem URI 'SI ile her zaman boş bir BOED son ileti üretir `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .

- B1203: WCF `LastMessage` , eylem URI 'si olmadığı sürece bir öğe içeren bir dizi üst bilgisine sahip bir ileti alır ve gönderir `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .

Sıralı üst bilgi örneği.

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

WCF `AckRequested` üstbilgiyi etkin tut mekanizması olarak kullanır. WCF isteğe bağlı `MessageNumber` öğe oluşturmaz. Öğeyi içeren bir üst bilgiyle bir ileti aldıktan sonra `AckRequested` `MessageNumber` , WCF, `MessageNumber` Aşağıdaki örnekte gösterildiği gibi öğenin değerini yoksayar.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement üstbilgisi

WCF, WS-güvenilir mesajlaşma 'da sunulan sıra bildirimleri için Piggy-Back mekanizmasını kullanır.

- R1401: mekanizma kullanılarak iki listesiyse dizisi oluşturulduğunda `Offer` , `SequenceAcknowledgement` üst bilgi, istenen alıcıya iletilen herhangi bir uygulama iletisine dahil edilebilir.

- B1402: WCF herhangi bir sıra iletisi almadan önce bir onay üretmelidir (örneğin, bir iletiyi karşılamak için `AckRequested` ), WCF, `SequenceAcknowledgement` Aşağıdaki örnekte gösterildiği gibi 0-0 aralığını içeren bir üst bilgi oluşturur.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- B1403: WCF `SequenceAcknowledgement` bir öğesi içeren, `Nack` ancak öğeleri destekleyen üstbilgiler oluşturmaz `Nack` .

### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging hataları

Aşağıda, WS-güvenilir mesajlaşma hatalarının WCF uygulaması için uygulanan kısıtlamaların bir listesi verilmiştir:

- B1501: WCF `MessageNumberRollover` hata oluşturmaz.

- B1502: WCF uç noktası `CreateSequenceRefused` , belirtimde açıklandığı gibi hatalar oluşturabilir.

- B1503: hizmet uç noktası bağlantı sınırına ulaştığında ve yeni bağlantıları işleyemezse, `CreateSequenceRefused` `netrm:ConnectionLimitReached` Aşağıdaki örnekte GÖSTERILDIĞI gibi WCF ek bir hata alt kodu oluşturur.

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

WS-güvenilir mesajlaşma, WS-Addressing kullandığından, WCF WS güvenilir mesajlaşma uygulamaları WS-Addressing hataları oluşturabilir. Bu bölüm, WCF 'nin WS-güvenilir mesajlaşma katmanında açıkça oluşturduğu WS-Addressing hatalarını ele almaktadır:

- B1601: WCF, aşağıdakilerden biri true olduğunda gereken hata Iletisi adresleme üstbilgisini üretir:

  - Bir iletide `Sequence` üst bilgi ve `Action` üst bilgi eksik.

  - Bir `CreateSequence` iletide `MessageId` üst bilgi eksik.

  - Bir `CreateSequence` iletide `ReplyTo` üst bilgi eksik.

- B1602: WCF, bir `Sequence` üst bilgi eksik olan ve `Action` WS güvenilir mesajlaşma belirtiminde tanınmayan bir üstbilgiye sahip olan bir iletiye yanıt olarak desteklenmeyen hata eylemini oluşturur.

- B1603: WCF, hata uç noktasını, `CreateSequence` iletinin adres üst bilgilerini incelemeye göre sırayı işlemediğini göstermek Için kullanılamaz olarak oluşturur.

## <a name="protocol-composition"></a>Protokol oluşturma

### <a name="composition-with-ws-addressing"></a>WS-Addressing oluşturma

WCF iki WS-Addressing sürümü destekler: WS-Addressing 2004/08 [WS-ADDR] ve W3C WS-Addressing 1,0 önerileri [WS-ADDR-CORE] ve [WS-ADDR-SOAP].

WS-güvenilir mesajlaşma belirtiminde yalnızca WS-Addressing 2004/08 bahsetirken, WS-Addressing sürümü kullanılacak şekilde kısıtlanmaz. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- R2101: hem WS-Addressing 2004/08 hem de WS-Addressing 1,0, WS-güvenilir mesajlaşma ile kullanılabilir.

- R2102: tek bir WS-Addressing sürümü, belirli bir WS-Addressing mesajlaşma sırası boyunca veya mekanizması kullanılarak bağıntılı bir convero dizileri çifti olarak kullanılmalıdır `wsrm:Offer` .

### <a name="composition-with-soap"></a>SOAP ile bileşim

WCF, hem SOAP 1,1 hem de WS-güvenilir mesajlaşma ile SOAP 1,2 kullanımını destekler.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>WS-Security ve WS-SecureConversation ile birleştirme

WCF, güvenli aktarım (HTTPS), WS-Security ile bileşim ve WS-Secure konuşmasıyla bileşim kullanılarak WS-güvenilir mesajlaşma dizileri için koruma sağlar. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- R2301: tek tek iletilerin bütünlüğünden ve gizliliğine ek olarak, WS-güvenilir bir mesajlaşma sırasının bütünlüğünü korumak Için, WCF WS-Secure konuşmasının kullanılması gerektiğini gerektirir.

- R2302: AWS-Secure görüşme oturumunun, WS-güvenilir mesajlaşma sırası kurulmadan önce kurulması gerekir.

- R2303: WS-güvenilir mesajlaşma sırası ömrü WS-Secure konuşma oturumunun ömrünü aşarsa, WS-Secure konuşma `SecurityContextToken` kullanılarak belirlenen, karşılık gelen WS-Secure konuşma yenileme bağlaması kullanılarak yenilenir.

- B2304: WS-güvenilir mesajlaşma sırası veya bir çift bağıntılı dönüştürme dizisi her zaman tek bir WS-SecureConversation oturumuna bağlanır.

  WCF kaynağı, `wsse:SecurityTokenReference` iletinin öğe genişletilebilirliği bölümünde öğesini oluşturur `CreateSequence` .

- R2305: WS-Secure konuşmasıyla birlikte kullanıldığında, bir `CreateSequence` ileti `wsse:SecurityTokenReference` öğesini içermelidir.

## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-güvenilir mesajlaşma WS-Ilke onaylama

WCF `wsrm:RMAssertion` uç noktalar özelliklerini anlatmak IÇIN WS-güvenilir mesajlaşma WS-Policy onaylama işlemi kullanır. WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- B3001: WCF `wsrm:RMAssertion` WS-Policy onay onayını `wsdl:binding` öğelere iliştirir. WCF her iki Eki `wsdl:binding` ve `wsdl:port` öğelerini destekler.

- B3002: WCF, WS-güvenilir mesajlaşma onaylama 'nın aşağıdaki isteğe bağlı özelliklerini destekler ve WCF üzerinde denetim sağlar `ReliableMessagingBindingElement` :

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  Bir örnek verilmiştir.

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a>Akış denetimi WS-güvenilir mesajlaşma uzantısı

WCF, sıralı ileti akışı üzerinde isteğe bağlı ek daha sıkı denetim sağlamak için WS-güvenilir mesajlaşma genişletilebilirliği kullanır.

Akış denetimi <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> özelliği olarak ayarlanarak etkinleştirilir `true` . WCF için uygulanan kısıtlamaların listesi aşağıda verilmiştir:

- B4001: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, WCF `netrm:BufferRemaining` öğenin genişletilebilirliği içindeki bir öğe oluşturur `SequenceAcknowledgement` .

- B4002: güvenilir mesajlaşma akış denetimi etkinleştirildiğinde, `netrm:BufferRemaining` `SequenceAcknowledgement` Aşağıdaki örnekte GÖSTERILDIĞI gibi WCF, üst bilgide bir öğe bulunmasını gerektirmez.

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

- B4003: WCF `netrm:BufferRemaining` , güvenilir mesajlaşma hedefinin arabelleğe abileceği yeni ileti sayısını göstermek için kullanır.

- B4004: WCF güvenilir mesajlaşma hizmeti, güvenilir mesajlaşma hedefi uygulaması iletileri hızlı bir şekilde alamadığınızda aktarılan ileti sayısını kısıtlar. Güvenilir Mesajlaşma hedefi iletileri arabelleğe alır ve öğenin değeri 0 ' a düşer.

- B4005: WCF `netrm:BufferRemaining` , dahil 0 ve 4096 arasında tamsayı değerler üretir ve 0 214748364 ile arasında bir tamsayı değeri okur `xs:int` `maxInclusive` .

## <a name="message-exchange-patterns"></a>İleti değişimi desenleri

Bu bölümde, farklı Ileti değişimi desenleri için WS-güvenilir mesajlaşma kullanıldığında WCF 'nin davranışı açıklanmaktadır. Her Ileti değişim deseninin aşağıdaki iki dağıtım senaryosu göz önünde bulundurulmalıdır:

- Adreslenebilir Başlatıcı: Başlatıcı güvenlik duvarının arkasındaysa; Yanıtlayıcı yalnızca HTTP yanıtlarında iletileri başlatıcıya teslim edebilir.

- Adreslenebilir Başlatıcı: Başlatıcı ve Yanıtlayıcı, HTTP istekleri olarak gönderilebilir; diğer bir deyişle, iki listesiyse http bağlantısı kurulabilir.

### <a name="one-way-non-addressable-initiator"></a>Tek yönlü, adreslenebilir olmayan Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, tek bir HTTP kanalı üzerinden tek bir sıra kullanan tek yönlü ileti değişim modelini sağlar. WCF, tüm iletileri RMS 'den RMD 'ye aktarmak için HTTP isteklerini ve RMD 'deki tüm iletileri RMS 'ye aktarmak için HTTP yanıtını kullanır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı, `CreateSequence` teklifi olmayan bir ileti üretir. WCF Yanıtlayıcı, `CreateSequence` bir sıra oluşturmadan önce hiçbir teklif olmamasını sağlar. WCF Yanıtlayıcı `CreateSequence` isteğe bir iletiyle yanıt verir `CreateSequenceResponse` .

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF başlatıcısı, `CreateSequence` ileti ve hata iletileri hariç tüm iletilerin yanıtı hakkında bildirimleri işler. WCF Yanıtlayıcı her zaman hem sıra hem de ileti karşılığında tek başına bir onay üretir `AckRequested` .

#### <a name="terminatesequence-message"></a>TerminateSequence iletisi

WCF `TerminateSequence` tek yönlü bir işlem olarak davranır, yanı HTTP yanıtının boş bir gövdesi ve http 202 durum kodu vardır.

### <a name="one-way-addressable-initiator"></a>Tek yönlü, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, gelen ve giden http kanalı üzerinden tek bir sıra kullanan tek yönlü bir ileti değişim modelini sağlar. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı, `CreateSequence` teklifi olmayan bir ileti üretir. WCF Yanıtlayıcı, `CreateSequence` bir sıra oluşturmadan önce hiçbir teklif olmamasını sağlar. WCF Yanıtlayıcı, `CreateSequenceResponse` iletiyi `ReplyTo` uç nokta başvurusuyla BAHSEDILEN bir http isteği üzerinden iletir.

### <a name="duplex-addressable-initiator"></a>Çift yönlü, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, gelen ve giden HTTP kanalı üzerinden iki sıra kullanan tam zaman uyumsuz iki yönlü bir ileti değişim modelini sağlar. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur. WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar. WCF, `CreateSequenceResponse` ' `CreateSequence` ın uç nokta başvurusuna gönderilen http isteğini gönderir `ReplyTo` .

#### <a name="sequence-lifetime"></a>Sıra ömrü

WCF iki diziyi bir tam çift yönlü oturum olarak değerlendirir.

Bir sıra hatası oluşturan bir hata üretildiğinde, WCF uzak uç noktanın her iki diziyi de hatasına neden bekler. Bir sıra hata veren bir hata okunduktan sonra, WCF hataları her iki diziyi de sıralar.

WCF, giden sırasını kapatabilir ve gelen sırasındaki iletileri işlemeye devam edebilir. Buna karşılık, WCF gelen sıranın kapatılmasını işleyebilir ve giden sırasına göre iletileri gönderilmeye devam edebilir.

### <a name="request-reply-non-addressable-initiator"></a>İstek-yanıt, adreslenebilir olmayan Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, tek yönlü ve istek-yanıt iletisi değişim modelini bir HTTP kanalı üzerinden iki sıra kullanarak sağlar. WCF, istek dizisinin iletilerini aktarmak için HTTP isteklerini kullanır ve yanıt dizisinin iletilerini aktarmak için HTTP yanıtlarını kullanır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur. WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar. WCF Yanıtlayıcı `CreateSequence` isteğe bir iletiyle yanıt verir `CreateSequenceResponse` .

#### <a name="one-way-message"></a>Tek yönlü Ileti

Tek yönlü ileti değişim protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında tek başına bir `SequenceAcknowledgement` ileti alır. , `SequenceAcknowledgement` İletilen iletiyi kabul etmelidir.

WCF Yanıtlayıcı, isteği bir onaylama, hata veya boş bir gövde ve HTTP 202 durum kodu olan bir Yanıt ile yanıtlayabilir.

#### <a name="two-way-messages"></a>İki yönlü Ileti

İki yönlü ileti değişimi protokolünü başarıyla tamamlayabilmeniz için, WCF başlatıcısı HTTP isteğine bir istek sırası iletisi aktarır ve HTTP yanıtında bir yanıt sırası iletisi alır. Yanıt, `SequenceAcknowledgement` iletilen istek sırası iletisini bildiren bir ileti taşımalıdır.

WCF Yanıtlayıcı, isteği bir uygulama yanıtıyla, bir hata veya boş bir gövde ve HTTP 202 durum koduna sahip bir Yanıt ile yanıtlayabilir.

Tek yönlü iletiler ve uygulama yanıtlarının zamanlaması nedeniyle, istek sırası iletisinin sıra numarası ve yanıt iletisinin sıra numarası bağıntı içermez.

#### <a name="retrying-replies"></a>Yanıtları yeniden deneme

WCF, iki yönlü ileti değişimi Protokolü bağıntısı için HTTP isteği-Yanıtla bağıntısını kullanır. Bu nedenle, WCF başlatıcısı istek sırası iletisi kabul edildiğinde, ancak HTTP yanıtı bir onay, kullanıcı iletisi veya hata taşımadığında bir istek sırası iletisinin yeniden denenmediğini durdurur. WCF Yanıtlayıcı, yanıtın bağıntılı olduğu isteğin HTTP isteği bacağı yanıtları yeniden dener.

#### <a name="lastmessage-exchange"></a>LastMessage değişimi

WCF başlatıcısı, HTTP istek baındaki boş bir BOED son ileti oluşturur ve iletir. WCF bir yanıt gerektirir ancak gerçek yanıt iletisini yoksayar. WCF Yanıtlayıcı, istek dizisinin boş-Bodied son iletisi ile yanıt sırasının boş olduğunu ve son iletisini yanıtlar.

WCF Yanıtlayıcı, eylem URI 'sinin olmadığı son bir iletiyi alırsa `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` , WCF son iletiyle yanıt verir. İki yönlü ileti değişimi Protokolü söz konusu olduğunda, son ileti uygulama iletisini taşır; tek yönlü ileti Değişim Protokolü söz konusu olduğunda, son ileti boş olur.

WCF Yanıtlayıcı, yanıt sırasının boş-Bodied son iletisi için bir bildirim gerektirmez.

#### <a name="terminatesequence-exchange"></a>TerminateSequence değişimi

Tüm istekler geçerli bir yanıt aldığında, WCF başlatıcısı, istek dizisinin `TerminateSequence` ILETISINI http istek bacağı ' da oluşturur ve iletir. WCF bir yanıt gerektirir ancak gerçek yanıt iletisini yoksayar. WCF Yanıtlayıcı, istek dizisinin `TerminateSequence` iletisine yanıt sırası iletisi ile yanıt verir `TerminateSequence` .

Normal bir kapalı dizisinde, her iki `TerminateSequence` ileti de tam bir Aralık taşır `SequenceAcknowledgement` .

### <a name="requestreply-addressable-initiator"></a>İstek/yanıt, adreslenebilir Başlatıcı

#### <a name="binding"></a>Bağlama

WCF, gelen ve giden HTTP kanalı üzerinden iki sıra kullanan bir istek-yanıt iletisi değişim modelini sağlar. WCF, tüm iletileri iletmek için HTTP isteklerini kullanır. Tüm HTTP yanıtlarının boş bir gövdesi ve HTTP 202 durum kodu vardır.

#### <a name="createsequence-exchange"></a>CreateSequence değişimi

WCF başlatıcısı, `CreateSequence` bir teklifiyle birlikte bir ileti oluşturur. WCF Yanıtlayıcı, ' `CreateSequence` ın bir sıra oluşturmadan önce bir teklif olmasını sağlar. WCF, `CreateSequenceResponse` ' `CreateSequence` ın uç nokta başvurusuna gönderilen http isteğini gönderir `ReplyTo` .

#### <a name="requestreply-correlation"></a>İstek/yanıt bağıntısı

WCF başlatıcısı, tüm uygulama istek iletilerinin bir `MessageId` ve bir `ReplyTo` uç nokta başvurusu olmasını sağlar. WCF başlatıcısı, `CreateSequence` `ReplyTo` her uygulama isteği iletisinde iletinin bitiş noktası başvurusunu uygular. WCF Yanıtlayıcı, gelen istek iletilerinin bir `MessageId` ve bir olmasını gerektirir `ReplyTo` . WCF Yanıtlayıcı, uç nokta başvurusunun hem hem de `CreateSequence` tüm uygulama istek ILETILERININ URI 'sinin aynı olmasını sağlar.
