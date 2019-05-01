---
title: İşlem Protokolleri
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 3f4824ac6098f33b7bde4f29d3e0950783dfd213
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918898"
---
# <a name="transaction-protocols"></a>İşlem Protokolleri
Windows Communication Foundation (WCF), WS-Atomic işlem ve WS-koordinasyon protokollerini kullanır.  
  
|Belirtimi/belge|Sürüm|Bağlantı|  
|-----------------------------|-------------|----------|  
|WS-düzenleme|1.0<br /><br /> 1.1|<https://go.microsoft.com/fwlink/?LinkId=96104><br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|WS-AtomicTransaction|1.0<br /><br /> 1.1|<https://go.microsoft.com/fwlink/?LinkId=96080><br /><br /> https://go.microsoft.com/fwlink/?LinkId=96081|  
  
 Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında arasında işlem yöneticileri (aşağıdaki şekilde bakın). Her iki birlikte çalışabilirlik düzeyleri için exchange ileti biçimleri ve ileti ayrıntılarını özellikleri açıklanmaktadır. Normal uygulama exchange gibi belirli güvenlik, güvenilirlik ve kodlamaları uygulama uygulaması exchange için geçerlidir. Ancak, kullanıcı tarafından genellikle yapılandırılmamış olduğundan işlem yöneticileri başarılı birlikte çalışabilirliği belirli bağlama üzerinde sözleşmesi gerektirir.  
  
 Bu konu, WS-Atomic işlem (WS-AT) belirtimi bileşimi ile güvenlik açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bir bağlama tanımlar. Bu belgede açıklanan yaklaşımı başarıyla WS-AT ve WS-koordinasyon diğer uygulamaları ile test edilmiştir IBM, IONA, Sun Microsystems ve diğerleri gibi.  
  
 Aşağıdaki şekil, hareket yöneticisi 1 ve hareket yöneticisi 2, iki işlem yöneticileri ve uygulama 1 ve 2 uygulama olmak üzere iki uygulama arasında birlikte çalışabilirliği gösterir:  
  
 ![Yöneticileri işlem arasındaki etkileşimi gösteren ekran görüntüsü.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Bir başlatıcı (ı) ve bir katılımcı (P) tipik bir WS-koordinasyon/WS-Atomic işlem senaryoyu ele alalım. Hem Başlatıcı hem de katılımcı sahip işlem yöneticileri (ITM ve PTM, sırasıyla). İki aşamalı tamamlama bu konudaki 2PC olarak adlandırılır.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Uygulama ileti yanıtı|  
|2. CreateCoordinationContextResponse|13. İşleme (tamamlama)|  
|3. Kayıt (tamamlama)|14. (2PC) hazırlama|  
|4. RegisterResponse|15. (2PC) hazırlama|  
|5. Uygulama iletisi|16. Hazırlanan (2PC)|  
|6. Bağlamla CreateCoordinationContext|17. Hazırlanan (2PC)|  
|7. Kayıt (Durable)|18. Taahhüt edilen (tamamlama)|  
|8. RegisterResponse|19. Kayıt (2PC)|  
|9. CreateCoordinationContextResponse|20. Kayıt (2PC)|  
|10. Kayıt (Durable)|21. Taahhüt edilen (2PC)|  
|11. RegisterResponse|22. Taahhüt edilen (2PC)|  
  
 Bu belge, güvenlik ile WS-AtomicTransaction belirtiminin bir bileşim açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bir bağlama tanımlar. Bu belgede açıklanan yaklaşımı başarıyla WS-AT ve WS-koordinasyon diğer uygulamaları ile test edilmiştir.  
  
 Şekil ve tabloda dört güvenlik görüş iletilerden sınıflarını göstermektedir:  
  
- Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).  
  
- Kayıt iletileri (kayıt ve RegisterResponse)  
  
- Protokol iletileri (hazırlama, geri alma, işleme, iptal edildi ve benzeri).  
  
- Uygulama iletileri.  
  
 İlk üç ileti sınıflarını hareket yöneticisi iletileri kabul edilir ve bunların bağlama yapılandırması "Uygulama ileti değişimi" Bu konunun ilerleyen bölümlerinde açıklanmıştır. İletinin dördüncü sınıfını uygulamaya ileti ve "İleti örnekler" bölümünde bu konunun ilerleyen bölümlerinde açıklanmıştır. Bu bölümde, bu sınıfların her biri için WCF tarafından kullanılan protokolü bağlamalarını açıklanmaktadır.  
  
 Aşağıdaki XML ad alanları ve ilişkili ön ekleri, bu belge boyunca kullanılır.  
  
|Ön eki|Sürüm|Namespace URI'si|  
|------------|-------------|-------------------|  
|s11||<https://go.microsoft.com/fwlink/?LinkId=96014>|  
|wsa|Öncesi 1.0<br /><br /> 1.0|http://www.w3.org/2004/08/addressing<br /><br /> <https://go.microsoft.com/fwlink/?LinkId=96022>|  
|wscoor|1.0<br /><br /> 1.1|<https://go.microsoft.com/fwlink/?LinkId=96078><br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|wsat|1.0<br /><br /> 1.1|<https://go.microsoft.com/fwlink/?LinkId=96080><br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96081](https://go.microsoft.com/fwlink/?LinkId=96081)|  
|t|1.3 öncesi<br /><br /> 1.3|<https://go.microsoft.com/fwlink/?LinkId=96082><br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96100](https://go.microsoft.com/fwlink/?LinkId=96100)|  
|o||<https://go.microsoft.com/fwlink/?LinkId=96101>|  
|xsd||<https://go.microsoft.com/fwlink/?LinkId=96102>|  
  
## <a name="transaction-manager-bindings"></a>İşlem Yöneticisi bağlamaları  
 R1001: İşlem yöneticileri WS-AT 1.0 işlemde katılan, WS-Atomic işlem ve WS-koordinasyon ileti alışverişlerinde SOAP 1.1 ve WS-Addressing 2004/08 kullanmalısınız.  
  
 R1002: İşlem yöneticileri WS-AT 1.1 işlemde katılan, WS-Atomic işlem ve WS-koordinasyon ileti alışverişlerinde SOAP 1.1 ve WS-Addressing 2005/08 kullanmalısınız.  
  
 Uygulama iletileri, bu bağlamaları için kısıtlı değildir ve daha sonra açıklanmıştır.  
  
### <a name="transaction-manager-https-binding"></a>İşlem Yöneticisi HTTPS bağlama  
 İşlem Yöneticisi HTTPS bağlaması güvenliği sağlamak ve işlem ağacında her gönderenin alıcı çifti arasında güven oluşturma için yalnızca Aktarım güvenliği kullanır.  
  
#### <a name="https-transport-configuration"></a>HTTPS aktarımı yapılandırması  
 X.509 sertifikaları, hareket yöneticisi kimliğini oluşturmak için kullanılır. İstemci/sunucu kimlik doğrulaması ve yetkilendirme istemci/sunucu uygulama ayrıntısı bırakılır:  
  
- R1111: Kablo üzerinden sunulan X.509 sertifikaları, kaynak makinenin tam etki alanı adını (FQDN) eşleşen bir konu adı olmalıdır.  
  
- B1112: DNS başarılı olması için her gönderenin alıcı çifti arasında X.509 konu adı denetimleri için sistemdeki işlevsel olması gerekir.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Etkinleştirme ve yapılandırma bağlama kaydı  
 WCF HTTPS üzerinden istek/yanıt bağıntısı ile çift yönlü bağlama gerektirir. (WS-Atomic işlem, Bölüm 8 bağıntı ve istek/yanıt iletisi exchange desenlerinin açıklamaları hakkında daha fazla bilgi için bkz.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>2PC Protokolü bağlama yapılandırması  
 WCF HTTPS üzerinden tek yönlü (veri birimi) iletileri destekler. İletileri arasında bağıntı uygulama ayrıntısı bırakılır.  
  
 B1131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-WCF'ın 2PC iletilerinin bağıntı elde etmek için Addressing içinde açıklandığı gibi.  
  
### <a name="transaction-manager-mixed-security-binding"></a>İşlem Yöneticisi karma güvenliği bağlama  
 Bir alternatif kimlik kurulması amacıyla WS-koordinasyon verilen belirteç modeli ile birlikte bu kullanımları aktarım güvenliği bağlama (karışık mod) budur. Etkinleştirme ve kayıt iki bağlaması arasında farklılık gösteren yalnızca öğelerdir.  
  
#### <a name="https-transport-configuration"></a>HTTPS aktarımı yapılandırması  
 X.509 sertifikaları, hareket yöneticisi kimliğini oluşturmak için kullanılır. İstemci/sunucu kimlik doğrulaması ve yetkilendirme istemci/sunucu uygulama ayrıntısı bırakılır.  
  
#### <a name="activation-message-binding-configuration"></a>Etkinleştirme ileti bağlama yapılandırması  
 Genellikle kendi yerel hareket yöneticisi ile bir uygulama arasında gerçekleştiği için etkinleştirme iletileri birlikte çalışabilirlik genellikle katılmaz.  
  
 B1221: WCF çift yönlü bir HTTPS bağlama kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) etkinleştirme iletileri. WS-Addressing 2004/08 WS-AT 1.0 ve WS-Addressing 2005/08 için WS-AT 1.1 kullanarak istek ve yanıt iletilerinin ilişkilendirilir.  
  
 WS-Atomic işlem belirtimi, Bölüm 8, bağıntı ve ileti exchange desenleri hakkında daha fazla ayrıntıları açıklanır.  
  
- R1222: Alma bağlı bir `CreateCoordinationContext`, düzenleyici dağıtmalı bir `SecurityContextToken` ile ilişkili gizli `STx`. Bu belirteç içinde döndürülen bir `t:IssuedTokens` WS-Güven belirtimini takip başlığı.  
  
- R1223: Etkinleştirme var olan bir düzenleme bağlamı içinde ortaya çıkarsa `t:IssuedTokens` üstbilgiyle `SecurityContextToken` var olan ilişkili bağlam gerekir akışını `CreateCoordinationContext` ileti.  
  
 Yeni bir `t:IssuedTokens` üstbilgi giden eklemek için oluşturulacak `wscoor:CreateCoordinationContextResponse` ileti.  
  
#### <a name="registration-message-binding-configuration"></a>Kayıt iletisi bağlama yapılandırması  
 B1231: WCF çift yönlü bir HTTPS bağlama kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). WS-Addressing 2004/08 WS-AT 1.0 ve WS-Addressing 2005/08 için WS-AT 1.1 kullanarak istek ve yanıt iletilerinin ilişkilendirilir.  
  
 WS-AtomicTransaction, Bölüm 8 açıklar daha fazla ayrıntı bağıntı ve açıklamaları ileti exchange desenleri hakkında.  
  
 R1232: Giden `wscoor:Register` iletileri kullanmalıdır `IssuedTokenOverTransport` kimlik doğrulama modu açıklanan [güvenlik protokollerini](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 `wsse:Timestamp` Öğesi kullanılarak imzalanmalıdır `SecurityContextToken STx` verildi. Bu imza, belirli bir işlemle ilişkili belirtecin kanıtını olduğu ve işlemde kaydetme katılımcı kimliğini doğrulamak için kullanılır. HTTPS üzerinden RegistrationResponse ileti gönderilir.  
  
#### <a name="2pc-protocol-binding-configuration"></a>2PC Protokolü bağlama yapılandırması  
 WCF HTTPS üzerinden tek yönlü (veri birimi) iletileri destekler. İletileri arasında bağıntı uygulama ayrıntısı bırakılır.  
  
 B1241: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-WCF'ın 2PC iletilerinin bağıntı elde etmek için Addressing içinde açıklandığı gibi.  
  
## <a name="application-message-exchange"></a>Uygulama ileti değişimi  
 Uygulamaları bağlama aşağıdaki güvenlik gereksinimlerini karşıladığı sürece herhangi belirli bağlama-uygulamaya iletileri için kullanılacak ücretsizdir:  
  
- R2001: Uygulama uygulama iletileri gerekir akış `t:IssuedTokens` başlığı ile birlikte `CoordinationContext` iletisinin üst bilgisindeki.  
  
- R2002: Bütünlüğü ve gizliliği `t:IssuedToken` sağlanmalıdır.  
  
 `CoordinationContext` Üst bilgiyi içeren `wscoor:Identifier`. While tanımını `xsd:AnyURI` mutlak ve göreli URI'ler kullanımına izin verir WCF yalnızca destekler `wscoor:Identifiers`, mutlak bir URI'leri olduğu.  
  
 B2003: Varsa `wscoor:Identifier` , `wscoor:CoordinationContext` göreli bir URI işlem WCF hizmetlerinden hatalar döndürülür.  
  
## <a name="message-examples"></a>İleti örnekleri  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>CreateCoordinationContext istek/yanıt iletilerini  
 Aşağıdaki ileti, istek/yanıt deseni izler.  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a>CreateCoordinationContext WSCoor 1.0 ile  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a>CreateCoordinationContext WSCoor 1.1 ile  
  
```xml  
<s:Envelope>   
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a>Güven Pre-1.3 ve WSCoor 1.0 ile CreateCoordinationContextResponse  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a>Güven 1.3 ve WSCoor 1.1 ile CreateCoordinationContextResponse  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->   
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>   
<t:IssuedTokens>   
<wst:RequestSecurityTokenResponse   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
</wst:RequestedSecurityToken>   
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
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
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
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
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>   
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>   
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>   
</wscoor:CoordinationContext>   
</wscoor:CreateCoordinationContextResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="registration-messages"></a>Kayıt iletileri  
 Aşağıdaki iletileri, kayıt iletileri edilir.  
  
#### <a name="register-with-wscoor-10"></a>WSCoor 1.0 ile kaydetme  
  
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
  
#### <a name="register-with-wscoor-11"></a>1.1 WSCoor ile kaydetme  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>   
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
<wssu:Identifier> http://fabrikam123.com/SCTi  
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
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>   
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>   
</ds:Reference>   
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>   
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
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
  
#### <a name="register-response-with-wscoor-10"></a>Yanıt WSCoor 1.0 ile kaydetme  
  
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
  
#### <a name="register-response-with-wscoor-11"></a>Yanıt WSCoor 1.1 ile kaydetme  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
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
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>   
</wscoor:RegisterResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a>İki aşaması yürütme protokol iletileri  
 Aşağıdaki ileti iki aşamalı kayıt (2PC) protokolüne ilişkilendirir.  
  
#### <a name="commit-with-wsat-10"></a>WSAT 1.0 ile işleme  
  
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
  
#### <a name="commit-with-wsat-11"></a>1.1 WSAT ile işleme  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
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
  
### <a name="application-messages"></a>Uygulama iletileri  
 Aşağıdaki iletileri uygulama iletileri edilir.  
  
#### <a name="application-message-request"></a>Uygulama isteği iletisi  
  
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
