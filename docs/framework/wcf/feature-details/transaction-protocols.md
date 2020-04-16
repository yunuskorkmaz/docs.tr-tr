---
title: İşlem Protokolleri
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 8f16f7a6c13ca557ce4160d927ef6f075a79b4c8
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464036"
---
# <a name="transaction-protocols"></a>İşlem Protokolleri
Windows Communication Foundation (WCF), WS-Atomik İşlem ve WS-Koordinasyon protokollerini uygular.  
  
|Belirtim/Belge|Sürüm|Bağlantı|  
|-----------------------------|-------------|----------|  
|WS-Koordinasyon|1.0<br /><br /> 1.1|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|WS-AtomicTransaction|1.0<br /><br /> 1.1|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında ve işlem yöneticileri arasında (aşağıdaki şekilden bakın). Belirtimler, her iki birlikte çalışabilirlik düzeyi için ileti biçimlerini ve ileti alışverişini ayrıntılı olarak açıklar. Uygulama-uygulama değişimi için belirli güvenlik, güvenilirlik ve kodlamalar, düzenli uygulama değişimi için olduğu gibi geçerlidir. Ancak, işlem yöneticileri arasında başarılı birlikte çalışabilirlik, genellikle kullanıcı tarafından yapılandırılmadığından, belirli bağlama üzerinde anlaşma gerektirir.  
  
 Bu konu, WS-Atomic Transaction (WS-AT) belirtiminin güvenlikle ilgili bir bileşimini açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar. Bu belgede açıklanan yaklaşım, IBM, IONA, Sun Microsystems ve diğerleri de dahil olmak üzere WS-AT ve WS-Coordination'un diğer uygulamalarıyla başarıyla test edilmiştir.  
  
 Aşağıdaki şekil, iki işlem yöneticisi, İşlem Yöneticisi 1 ve İşlem Yöneticisi 2 ve iki uygulama, Uygulama 1 ve Uygulama 2 arasındaki birlikte çalışabilirliği gösterir:  
  
 ![Hareket yöneticileri arasındaki etkileşimi gösteren ekran görüntüsü.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Bir Başlatıcı (I) ve bir Katılımcı (P) ile tipik bir WS-Coordination/WS-Atomic Transaction senaryosudüşünün. Hem Başlatıcı hem de Katılımcı'nın Işlem Yöneticileri (sırasıyla ITM ve PTM) vardır. İki aşamalı taahhüt bu konuda 2PC olarak adlandırılır.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Uygulama Mesajı Yanıtı|  
|2. CreateCoordinationContextResponse|13. Taahhüt (Tamamlama)|  
|3. Kayıt (Tamamlama)|14. Hazırlayın (2PC)|  
|4. RegisterResponse|15. Hazırlayın (2PC)|  
|5. Uygulama Mesajı|16. Hazırlanan (2PC)|  
|6. Bağlam ile Koordinasyon Bağlamı Oluşturma|17. Hazırlanan (2PC)|  
|7. Kayıt (Dayanıklı)|18. Taahhüt (Tamamlama)|  
|8. RegisterResponse|19. Taahhüt (2PC)|  
|9. CreateCoordinationContextResponse|20. Taahhüt (2PC)|  
|10. Kayıt (Dayanıklı)|21. Taahhüt (2PC)|  
|11. RegisterResponse|22. Taahhüt (2PC)|  
  
 Bu belge, WS-AtomicTransaction belirtiminin güvenlikle ilgili bir bileşimini açıklar ve işlem yöneticileri arasında iletişim için kullanılan güvenli bağlamayı açıklar. Bu belgede açıklanan yaklaşım, WS-AT ve WS-Coordination'un diğer uygulamalarıyla başarıyla test edilmiştir.  
  
 Şekil ve tablo, güvenlik açısından dört ileti sınıfını gösterir:  
  
- Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).  
  
- Kayıt mesajları (Kayıt ve Kayıt Yanıtı)  
  
- Protokol iletileri (Hazırla, Geri Alma, Commit, İptal vb.)  
  
- Uygulama iletileri.  
  
 İlk üç ileti sınıfı İşlem Yöneticisi iletileri olarak kabul edilir ve bağlama yapılandırmaları daha sonra bu konunun "Uygulama İletisi Değişimi"nde açıklanır. Dördüncü sınıf ileti, uygulama iletilerine uygulamadır ve daha sonra bu konunun "İleti Örnekleri" bölümünde açıklanmıştır. Bu bölümde, WCF tarafından bu sınıfların her biri için kullanılan protokol bağlamaları açıklanmaktadır.  
  
 Bu belge boyunca aşağıdaki XML Ad Alanları ve ilişkili önekleri kullanılır.  
  
|Ön ek|Sürüm|Namespace URI|  
|------------|-------------|-------------------|  
|s11||<https://schemas.xmlsoap.org/soap/envelope/>|  
|Wsa|1.0 Öncesi<br /><br /> 1.0|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|wscoor|1.0<br /><br /> 1.1|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|wsat|1.0<br /><br /> 1.1|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|t|1.3'ün öncesi<br /><br /> 1.3|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|o||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|Xsd||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a>İşlem Yöneticisi Bağlamaları  
 R1001: WS-AT 1.0 işlemine katılan işlem yöneticileri, WS-Atomik İşlem ve WS-Koordinasyon ileti alışverişi için SOAP 1.1 ve WS-Addressing 2004/08'i kullanmalıdır.  
  
 R1002: WS-AT 1.1 işlemine katılan işlem yöneticileri, WS-Atomik İşlem ve WS-Koordinasyon ileti alışverişi için SOAP 1.1 ve WS-Addressing 2005/08'i kullanmalıdır.  
  
 Uygulama iletileri bu bağlamalarla sınırlandırılmamıştır ve daha sonra açıklanır.  
  
### <a name="transaction-manager-https-binding"></a>İşlem Yöneticisi HTTPS Ciltleme  
 İşlem yöneticisi HTTPS bağlama, güvenliği sağlamak ve hareket ağacındaki her gönderen-alıcı çifti arasında güven oluşturmak için yalnızca aktarım güvenliğine dayanır.  
  
#### <a name="https-transport-configuration"></a>HTTPS Aktarım Yapılandırması  
 X.509 sertifikaları İşlem Yöneticisi Kimliğini oluşturmak için kullanılır. İstemci/sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi bir uygulama ayrıntısı olarak bırakılır:  
  
- R1111: Tel üzerinde sunulan X.509 sertifikaları, kaynak makinenin tam nitelikli alan adı (FQDN) eşleşen bir konu adı olmalıdır.  
  
- B1112: DNS, x.509 konu adı denetimleri için sistemdeki her gönderen-alıcı çifti arasında işlevsel olmalıdır.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Etkinleştirme ve Kayıt Bağlama Yapılandırması  
 WCF, HTTPS üzerinden korelasyon içeren istek/yanıt çift yönlü bağlama gerektirir. (İstek/yanıt iletisi değişim şekillerinin korelasyon ve açıklamaları hakkında daha fazla bilgi için bkz.  
  
#### <a name="2pc-protocol-binding-configuration"></a>2PC Protokol Bağlama Yapılandırması  
 WCF, HTTPS üzerinden tek yönlü (datagram) iletileri destekler. İletiler arasındaki korelasyon bir uygulama ayrıntısı olarak bırakılır.  
  
 B1131: WCF'nin 2PC iletilerinin korelasyonuna ulaşmak için uygulamalar WS-Addressing'de açıklandığı şekilde desteklenmelidir. `wsa:ReferenceParameters`  
  
### <a name="transaction-manager-mixed-security-binding"></a>İşlem Yöneticisi Karışık Güvenlik Bağlama  
 Bu, kimlik kuruluş amaçları için WS-Koordinasyon Verilen Belirteç modeliyle birlikte taşıma güvenliğini kullanan alternatif (karma mod) bağlayıcıdır. Etkinleştirme ve Kayıt, iki bağlama arasında farklılık gösteren tek öğelerdir.  
  
#### <a name="https-transport-configuration"></a>HTTPS Aktarım Yapılandırması  
 X.509 sertifikaları İşlem Yöneticisi Kimliğini oluşturmak için kullanılır. İstemci/Sunucu kimlik doğrulaması gereklidir ve istemci/sunucu yetkilendirmesi bir uygulama ayrıntısı olarak bırakılır.  
  
#### <a name="activation-message-binding-configuration"></a>Etkinleştirme İleti bağlama yapılandırması  
 Etkinleştirme İletileri genellikle bir uygulama ve yerel İşlem Yöneticisi arasında meydana geldiğinden, genellikle birlikte çalışabilirlik katılmaz.  
  
 B1221: WCF, Etkinleştirme iletileri için çift yönlü HTTPS bağlama [(Mesajlaşma Protokolleri'nde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanan) kullanır. İstek ve Yanıt iletileri WS-At 1.0 için WS-Adresleme 2004/08 ve WS-AT 1.1 için WS-Addressing 2005/08 kullanılarak ilişkilidir.  
  
 WS-Atomik İşlem belirtimi, Bölüm 8, korelasyon ve ileti alışverişi desenleri hakkında daha fazla ayrıntı açıklar.  
  
- R1222: Bir `CreateCoordinationContext`aldıktan sonra, Koordinatör `SecurityContextToken` ilişkili bir `STx`sır ile bir sorunu olmalıdır. Bu belirteç, `t:IssuedTokens` WS-Trust belirtimini izleyen bir üstbilgi içinde döndürülür.  
  
- R1223: Etkinleştirme varolan bir Koordinasyon Bağlamı içinde `SecurityContextToken` gerçekleşirse, varolan `CreateCoordinationContext` Bağlam ile ilişkili `t:IssuedTokens` üstbilginin iletiüzerinde akması gerekir.  
  
 Giden `wscoor:CreateCoordinationContextResponse` `t:IssuedTokens` iletiye iliştirmek için yeni bir üstbilgi oluşturulmalıdır.  
  
#### <a name="registration-message-binding-configuration"></a>Kayıt İletisi Bağlama Yapılandırması  
 B1231: WCF çift yönlü HTTPS bağlama kullanır [(Mesajlaşma Protokolleri'nde](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)açıklanmıştır). İstek ve Yanıt iletileri WS-At 1.0 için WS-Adresleme 2004/08 ve WS-AT 1.1 için WS-Addressing 2005/08 kullanılarak ilişkilidir.  
  
 WS-AtomicTransaction, Bölüm 8, korelasyon ve ileti alışverişi desenleri açıklamaları hakkında daha fazla bilgi açıklar.  
  
 R1232: Giden `wscoor:Register` iletiler Güvenlik `IssuedTokenOverTransport` [Protokolleri'nde](../../../../docs/framework/wcf/feature-details/security-protocols.md)açıklanan kimlik doğrulama modunu kullanmalıdır.  
  
 `SecurityContextToken STx` Öğe, `wsse:Timestamp` verilen kullanılarak imzalanmalıdır. Bu imza, belirli bir işlemle ilişkili belirteç sahibi olduğunun kanıtıdır ve harekette kaydolan bir katılımcının kimliğini doğrulamak için kullanılır. RegistrationResponse iletisi HTTPS üzerinden geri gönderilir.  
  
#### <a name="2pc-protocol-binding-configuration"></a>2PC Protokol Bağlama Yapılandırması  
 WCF, HTTPS üzerinden tek yönlü (datagram) iletileri destekler. İletiler arasındaki korelasyon bir uygulama ayrıntısı olarak bırakılır.  
  
 B1241: WCF'nin 2PC iletilerinin korelasyonuna ulaşmak için uygulamalar WS-Addressing'de açıklandığı şekilde desteklenmelidir. `wsa:ReferenceParameters`  
  
## <a name="application-message-exchange"></a>Uygulama İletisi Değişimi  
 Uygulamalar, aşağıdaki güvenlik gereksinimlerini karşıladığı sürece, uygulamadan uygulamaya iletiler için belirli bir bağlamayı kullanmakta serbesttir:  
  
- R2001: Uygulama dan uygulama iletileri `t:IssuedTokens` üstbilgi ile `CoordinationContext` birlikte iletinin üstbilgi de akmalıdır.  
  
- R2002: Bütünlük ve gizlilik `t:IssuedToken` sağlanmalıdır.  
  
 Üstbilgi. `CoordinationContext` `wscoor:Identifier` Tanımı hem `xsd:AnyURI` mutlak hem de göreceli URI kullanımına izin `wscoor:Identifiers`verirken, WCF yalnızca mutlak URI'leri destekler.  
  
 B2003: `wscoor:Identifier` Göreceli uri `wscoor:CoordinationContext` ise, hatalar işlemsel WCF hizmetlerinden iade edilecektir.  
  
## <a name="message-examples"></a>İleti Örnekleri  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>CreateCoordinationContext İstek/Yanıt İletileri  
 Aşağıdaki iletiler bir istek/yanıt deseni izler.  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a>WSCoor 1.0 ile CreateCoordinationContext  
  
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
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a>WSCoor 1.1 ile CreateCoordinationContext  
  
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
<wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
<wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a>Güven 1.3 ve WSCoor 1.1 ile KoordinasyonBağlam Yanıtı Oluşturma  
  
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
  
### <a name="registration-messages"></a>Kayıt Mesajları  
 Aşağıdaki iletiler kayıt iletileridir.  
  
#### <a name="register-with-wscoor-10"></a>WSCoor 1.0 ile kaydolun  
  
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
  
#### <a name="register-with-wscoor-11"></a>WSCoor 1.1 ile kaydolun  
  
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
  
#### <a name="register-response-with-wscoor-10"></a>WSCoor 1.0 ile Yanıt Kaydol  
  
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
  
#### <a name="register-response-with-wscoor-11"></a>WSCoor 1.1 ile Yanıt Kaydol  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a>İki Aşamalı Commit Protokol İletileri  
 Aşağıdaki ileti, iki aşamalı commit (2PC) protokolü ile ilgilidir.  
  
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
  
#### <a name="commit-with-wsat-11"></a>WSAT 1.1 ile işleme  
  
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
  
### <a name="application-messages"></a>Uygulama Mesajları  
 Aşağıdaki iletiler uygulama iletileridir.  
  
#### <a name="application-message-request"></a>Uygulama mesajı-İstek  
  
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
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
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
