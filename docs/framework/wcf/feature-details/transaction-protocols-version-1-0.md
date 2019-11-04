---
title: İşlem Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: 5ca0210c15afd6a3fc2e05bc3b9016a1fcd929b7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460279"
---
# <a name="transaction-protocols-version-10"></a>İşlem Protokolleri sürüm 1.0
Windows Communication Foundation (WCF) sürüm 1, WS Atomik Işlem ve WS-koordinasyon protokollerinin 1,0 sürümünü uygular. Sürüm 1,1 hakkında daha fazla bilgi için bkz. [Işlem protokolleri](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Belirtim/belge|Bağlantı|  
|-----------------------------|----------|  
|WS koordinasyonu|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|WS-AtomicTransaction|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 Bu protokol belirtimlerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında ve işlem yöneticileri arasında (aşağıdaki şekle bakın). Özellikler, her iki birlikte çalışabilirlik düzeyi için İleti biçimlerini ve ileti değişimini harika ayrıntılarla anlatmaktadır. Uygulamadan uygulamaya Exchange 'e yönelik belirli güvenlik, güvenilirlik ve kodlamalar, düzenli uygulama alışverişi için olduğu gibi uygulanır. Ancak, işlem yöneticileri arasında başarılı birlikte çalışabilirlik, genellikle kullanıcı tarafından yapılandırılmadığı için belirli bir bağlamada anlaşma gerektirir.  
  
 Bu konu, güvenlik ile WS Atomik Işlem (WS-AT) belirtiminin bir oluşumunu açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar. Bu belgede açıklanan yaklaşım IBM, ıLONA, Sun Microsystems ve diğerleri dahil olmak üzere WS-AT ve WS-koordinasyon uygulamalarıyla başarıyla test edilmiştir.  
  
 Aşağıdaki şekilde iki işlem yöneticisi, Işlem Yöneticisi 1 ve Işlem yöneticisi 2 ile iki uygulama, uygulama 1 ve uygulama 2 arasındaki birlikte çalışabilirlik gösterilmektedir:  
  
 ![İşlem yöneticileri arasındaki etkileşimi gösteren ekran görüntüsü.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Tek bir başlatıcı (I) ve bir katılımcı (P) ile tipik bir WS-koordinasyon/WS-Atomik Işlem senaryosu düşünün. Hem Başlatıcı hem de katılımcı Işlem yöneticilerine (sırasıyla ıSTREAM ve PTM) sahiptir. İki aşamalı yürütmeye bu konuda 2PC adı verilir.  
  
|||  
|-|-|  
|1. Createkoordinattioncontext|12. uygulama Iletisi yanıtı|  
|2. Createkoordinattioncontextresponse|13. COMMIT (tamamlama)|  
|3. yazmaç (tamamlama)|14. Prepare (2PC)|  
|4. RegisterResponse|15. hazırlama (2PC)|  
|5. uygulama Iletisi|16. hazırlandı (2PC)|  
|6. Createkoordinattioncontext WITH bağlamı|17. hazırlandı (2PC)|  
|7. Kayıt (dayanıklı)|18. taahhüt (tamamlama)|  
|8. RegisterResponse|19. COMMIT (2PC)|  
|9. Createkoordinattioncontextresponse|20. COMMIT (2PC)|  
|10. Kayıt (dayanıklı)|21. taahhüt (2PC)|  
|11. RegisterResponse|22. taahhüt (2PC)|  
  
 Bu belge, güvenlik ile WS-AtomicTransaction belirtiminin bir oluşumunu açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar. Bu belgede açıklanan yaklaşım, WS-AT ve WS-koordinasyonun diğer uygulamalarıyla başarıyla test edilmiştir.  
  
 Şekil ve tablo, güvenlik açısından görüş açısından dört ileti sınıfını gösterir:  
  
- Etkinleştirme iletileri (Createkoordinattioncontext ve Createkoordinattioncontextresponse).  
  
- Kayıt iletileri (Register ve RegisterResponse)  
  
- Protokol iletileri (hazırlama, geri alma, tamamlama, Iptal etme vb.).  
  
- Uygulama iletileri.  
  
 İlk üç ileti sınıfı, Işlem yöneticisi iletileri olarak kabul edilir ve bağlama yapılandırması bu konunun ilerleyen kısımlarında "uygulama Ileti değişimi" bölümünde açıklanmaktadır. Dördüncü ileti sınıfı, uygulama iletileri için uygulamadır ve bu konunun ilerleyen kısımlarında "Ileti örnekleri" bölümünde açıklanmaktadır. Bu bölümde, bu sınıfların her biri için WCF tarafından kullanılan protokol bağlamaları açıklanmaktadır.  
  
 Aşağıdaki XML ad alanları ve ilişkili ön ekler Bu belge boyunca kullanılır.  
  
|koy|Ad alanı URI 'SI|  
|------------|-------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|WSA|http://www.w3.org/2004/08/addressing|  
|wscoor|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|WSAT|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|t|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|Gelirken|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|yapamadı|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a>İşlem Yöneticisi bağlamaları  
 R1001: Işlem yöneticileri WS-Atomik Işlem ve WS-koordinasyon ileti alışverişi için SOAP 1,1 ve WS-Addressing 2004/08 kullanmalıdır.  
  
 Uygulama iletileri bu bağlamalarla sınırlı değildir ve daha sonra açıklanır.  
  
### <a name="transaction-manager-https-binding"></a>İşlem Yöneticisi HTTPS bağlama  
 İşlem Yöneticisi HTTPS bağlaması, güvenlik elde etmek ve işlem ağacındaki her gönderici alıcısı çifti arasında güven sağlamak için yalnızca taşıma güvenliğine dayanır.  
  
#### <a name="https-transport-configuration"></a>HTTPS aktarım yapılandırması  
 X. 509.440 sertifikaları, Işlem yöneticisi kimliğini oluşturmak için kullanılır. İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi uygulama ayrıntısı olarak bırakılır:  
  
- R1111: tel üzerinden sunulan X. 509.440 sertifikalarının, kaynak makinenin tam etki alanı adı (FQDN) ile eşleşen bir konu adı olması gerekir.  
  
- B1112: X. 509.440 konu adı denetimlerinin başarılı olması için sistemdeki her gönderici alıcısı çifti arasında DNS işlevsel olmalıdır.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Etkinleştirme ve kayıt bağlama yapılandırması  
 WCF, HTTPS üzerinden bağıntı ile istek/yanıt çift yönlü bağlamayı gerektirir. (İstek/yanıt iletisi değişim desenlerinin bağıntısı ve açıklamaları hakkında daha fazla bilgi için bkz. WS Atomik Işlem, Bölüm 8.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>2PC protokol bağlama yapılandırması  
 WCF, HTTPS üzerinden tek yönlü (Datagram) iletileri destekler. İletiler arasındaki bağıntı uygulama ayrıntısı olarak kalır.  
  
 B2131: uygulamalar, WCF 2PC iletilerinin bağıntısını elde etmek için WS-Addressing bölümünde açıklandığı gibi `wsa:ReferenceParameters` desteklemelidir.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Transaction Manager karışık güvenlik bağlama  
 Bu, kimlik oluşturma amacıyla WS koordinasyonu verilen belirteç modeliyle birleştirilmiş aktarım güvenliği kullanan alternatif (karışık mod) bağlamadır.  Etkinleştirme ve kayıt, iki bağlama arasında farklı olan tek öğelerdir.  
  
#### <a name="https-transport-configuration"></a>HTTPS aktarım yapılandırması  
 X. 509.440 sertifikaları, Işlem yöneticisi kimliğini oluşturmak için kullanılır. İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi uygulama ayrıntısı olarak bırakılır.  
  
#### <a name="activation-message-binding-configuration"></a>Etkinleştirme Iletisi bağlama yapılandırması  
 Etkinleştirme Iletileri genellikle bir uygulama ve kendi yerel Işlem yöneticisi arasında gerçekleştiğinden birlikte çalışabilirliğe katılmaz.  
  
 B1221: WCF etkinleştirme iletileri için çift yönlü HTTPS bağlamasını ( [mesajlaşma protokollerinde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır) kullanır. İstek ve yanıt iletisi, WS-Addressing 2004/08 kullanılarak bağıntılı.  
  
 WS Atomik Işlem belirtimi, Bölüm 8, bağıntı ve ileti değişimi desenleri hakkında daha fazla ayrıntı açıklamaktadır.  
  
- R1222: `CreateCoordinationContext`aldıktan sonra, düzenleyicinin ilişkili gizli dizi `STx`bir `SecurityContextToken` vermesi gerekir. Bu belirteç, WS-Trust belirtimindeki bir `t:IssuedTokens` üst bilgisi içinde döndürülür.  
  
- R1223: etkinleştirme mevcut bir düzenleme bağlamında gerçekleşirse, var olan bağlamla ilişkili `SecurityContextToken` olan `t:IssuedTokens` üst bilgisinin `CreateCoordinationContext` iletisinde akışı gerekir.  
  
 Giden `wscoor:CreateCoordinationContextResponse` iletisine eklemek için yeni bir `t:IssuedTokens` üst bilgisi oluşturulmalıdır.  
  
#### <a name="registration-message-binding-configuration"></a>Kayıt Iletisi bağlama yapılandırması  
 B1231: WCF çift yönlü HTTPS bağlamasını kullanır ( [mesajlaşma protokollerinde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır). İstek ve yanıt iletisi, WS-Addressing 2004/08 kullanılarak bağıntılı.  
  
 WS-AtomicTransaction, Bölüm 8, ileti değişim desenlerinin bağıntı ve açıklamaları hakkında daha fazla ayrıntı açıklamaktadır.  
  
 R1232: giden `wscoor:Register` iletileri, [Güvenlik protokollerinde](../../../../docs/framework/wcf/feature-details/security-protocols.md)açıklanan `IssuedTokenOverTransport` kimlik doğrulama modunu kullanmalıdır.  
  
 `wsse:Timestamp` öğesi, verilen `SecurityContextToken STx` kullanılarak imzalanmalıdır. Bu imza, belirli bir işlemle ilişkili belirtecin bir kanıtıdır ve işlemde bir katılımcı listesini doğrulamak için kullanılır. RegistrationResponse iletisi HTTPS üzerinden geri gönderilir.  
  
#### <a name="2pc-protocol-binding-configuration"></a>2PC protokol bağlama yapılandırması  
 WCF, HTTPS üzerinden tek yönlü (Datagram) iletileri destekler. İletiler arasındaki bağıntı uygulama ayrıntısı olarak kalır.  
  
 B2131: uygulamalar, WCF 2PC iletilerinin bağıntısını elde etmek için WS-Addressing bölümünde açıklandığı gibi `wsa:ReferenceParameters` desteklemelidir.  
  
## <a name="application-message-exchange"></a>Uygulama Iletisi değişimi  
 Bağlama aşağıdaki güvenlik gereksinimlerini karşıladığı sürece, uygulamalar uygulamadan uygulamaya iletiler için herhangi bir bağlamayı kullanabilir.  
  
- R2001: uygulamadan uygulamaya iletileri ileti üstbilgisindeki `CoordinationContext` birlikte `t:IssuedTokens` üst bilgisini Flow olmalıdır.  
  
- R2002: `t:IssuedToken` bütünlük ve gizliliği sağlanmalıdır.  
  
 `CoordinationContext` üst bilgisi `wscoor:Identifier`içerir. `xsd:AnyURI` tanımı hem mutlak hem de göreli URI 'lerin kullanılmasına izin verdiğinden, WCF yalnızca, mutlak URI 'Ler olan `wscoor:Identifiers`destekler.  
  
 `wscoor:CoordinationContext` `wscoor:Identifier` göreli bir URI ise, hatalar işlem WCF hizmetlerinden döndürülür.  
  
## <a name="message-examples"></a>İleti örnekleri  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Createkoordinattioncontext Isteği/yanıt Iletileri  
 Aşağıdaki iletiler bir istek/yanıt modelini izler.  
  
#### <a name="createcoordinationcontext"></a>Createkoordinattioncontext  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a>Createkoordinattioncontextresponse  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a>Kayıt Iletileri  
 Aşağıdaki iletiler kayıt mesajlardır.  
  
#### <a name="register"></a>Yazmaç  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a>Yanıtı Kaydet  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a>İki aşamalı tamamlama Protokolü Iletisi  
 Aşağıdaki ileti, iki aşamalı tamamlama (2PC) protokolüyle ilişkilidir.  
  
#### <a name="commit"></a>Uygulayın  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a>Uygulama Iletileri  
 Aşağıdaki iletiler uygulama mesajlardır.  
  
#### <a name="application-message-request"></a>Uygulama iletisi-Istek  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
