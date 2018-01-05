---
title: "İşlem Protokolleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13784a3a5062705abba1b3bbb33a04e66bd22072
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols"></a>İşlem Protokolleri
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu protokollerini kullanır.  
  
|Belirtim/belgesi|Sürüm|Bağlantı|  
|-----------------------------|-------------|----------|  
|WS-düzenleme|1.0<br /><br /> 1.1|[http://go.microsoft.com/fwlink/?LinkId=96104](http://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96079](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|WS-AtomicTransaction|1.0<br /><br /> 1.1|[http://go.microsoft.com/fwlink/?LinkId=96080](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> http://go.microsoft.com/fwlink/?LinkId=96081|  
  
 Bu protokol belirtimleri üzerinde birlikte çalışabilirlik iki düzeyde gereklidir: uygulamalar arasında arasında işlem yöneticileri (Aşağıdaki şekle bakın). İletisi ve ileti formatları için her iki birlikte çalışabilirlik düzeylerini exchange harika ayrıntılı özellikleri açıklanmaktadır. Normal uygulama exchange için yaptığınız gibi belirli güvenlik, güvenilirlik ve kodlamaları uygulama uygulaması exchange için geçerlidir. Ancak, kullanıcı tarafından genellikle yapılandırılmadığı için işlem yöneticileri başarılı işlerliği belirli bağlama anlaşmasında gerektirir.  
  
 Bu konu, WS-Atomic işlem (WS-AT) belirtimi bileşimi ile güvenliği açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bağlama açıklar. Bu belgede açıklanan yaklaşım başarıyla WS-AT ve Web Hizmetleri koordinasyonu diğer uygulamaları ile test edilmiştir IBM, IONA, Sun Microsystems ve diğerleri de dahil olmak üzere.  
  
 Aşağıdaki şekil, İşlem Yöneticisi 1 ve işlem yöneticisi 2, iki işlem yöneticileri ve uygulama 1 ve uygulama 2 iki uygulama arasındaki birlikte çalışabilirlik gösterilmektedir.  
  
 ![İşlem protokolleri](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")  
  
 Bir başlatıcı (ı) ve bir katılımcı (P) tipik bir WS-düzenleme/WS-Atomic işlem senaryoyu göz önünde bulundurun. Hem Başlatıcı hem de katılımcı olan işlem yöneticileri (ITM ve PTM, sırasıyla). İki aşamalı yürütme için bu konudaki 2PC olarak adlandırılır.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Uygulama ileti yanıtı|  
|2. CreateCoordinationContextResponse|13. Yürütme (tamamlanma)|  
|3. YAZMAÇ (tamamlanma)|14. (2PC) hazırlama|  
|4. RegisterResponse|15. (2PC) hazırlama|  
|5. Uygulama iletisi|16. Hazırlanan (2PC)|  
|6. Bağlamına sahip CreateCoordinationContext|17. Hazırlanan (2PC)|  
|7. YAZMAÇ (dayanıklı)|18. Kaydedilmiş (tamamlanma)|  
|8. RegisterResponse|19. Kayıt (2PC)|  
|9. CreateCoordinationContextResponse|20. Kayıt (2PC)|  
|10. YAZMAÇ (dayanıklı)|21. Kaydedilmiş (2PC)|  
|11. RegisterResponse|22. Kaydedilmiş (2PC)|  
  
 Bu belge WS-AtomicTransaction belirtiminin bir birleşim ile güvenliği açıklar ve işlem yöneticileri arasındaki iletişim için kullanılan güvenli bağlama açıklar. Bu belgede açıklanan yaklaşım başarıyla WS-AT ve Web Hizmetleri koordinasyonu diğer uygulamaları ile test edilmiştir.  
  
 Şekil ve tabloda güvenlik görüş iletilerden dört sınıflarını gösterir:  
  
-   Etkinleştirme iletileri (CreateCoordinationContext ve CreateCoordinationContextResponse).  
  
-   Kayıt iletiler (kaydetme ve RegisterResponse)  
  
-   Protokol iletileri (hazırlama, geri alma, kaydetme, iptal edildi vb.).  
  
-   Uygulama iletileri.  
  
 İlk üç ileti sınıfları işlem yöneticisi iletileri kabul edilir ve bağlama yapılandırmalarını "Uygulama ileti değişimi" Bu konunun ilerleyen bölümlerinde açıklanmıştır. İletinin dördüncü sınıfını uygulamaya iletileri ve bu konunun devamındaki "İletisi örnekler" bölümünde açıklanan. Bu bölümde tarafından bu sınıfların her biri için kullanılan protokolü bağlamaları açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Aşağıdaki XML ad alanları ve ilişkili önekleri bu belge boyunca kullanılır.  
  
|önek|Sürüm|Namespace URI|  
|------------|-------------|-------------------|  
|S11||[http://go.microsoft.com/fwlink/?LinkId=96014](http://go.microsoft.com/fwlink/?LinkId=96014)|  
|wsa|Öncesi 1.0<br /><br /> 1.0|http://www.w3.org/2004/08/Addressing<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96022](http://go.microsoft.com/fwlink/?LinkId=96022)|  
|wscoor|1.0<br /><br /> 1.1|[http://go.microsoft.com/fwlink/?LinkId=96078](http://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96079](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|WSAT|1.0<br /><br /> 1.1|[http://go.microsoft.com/fwlink/?LinkId=96080](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96081](http://go.microsoft.com/fwlink/?LinkId=96081)|  
|t|Öncesi 1.3<br /><br /> 1.3|[http://go.microsoft.com/fwlink/?LinkId=96082](http://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96100](http://go.microsoft.com/fwlink/?LinkId=96100)|  
|O||[http://go.microsoft.com/fwlink/?LinkId=96101](http://go.microsoft.com/fwlink/?LinkId=96101)|  
|XSD||[http://go.microsoft.com/fwlink/?LinkId=96102](http://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a>İşlem Yöneticisi bağlamaları  
 R1001: WS-AT 1.0 işlemde katılan işlem yöneticileri SOAP 1.1 ve WS adresleme 2004/08 WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu ileti alışverişlerinde için kullanmanız gerekir.  
  
 R1002: WS-AT 1.1 işlemde katılan işlem yöneticileri SOAP 1.1 ve WS adresleme 2005/08 WS-Atomic işlemleri ve Web Hizmetleri koordinasyonu ileti alışverişlerinde için kullanmanız gerekir.  
  
 Uygulama iletileri bu bağlamaların kısıtlı değildir ve daha sonra açıklanmaktadır.  
  
### <a name="transaction-manager-https-binding"></a>İşlem Yöneticisi HTTPS bağlama  
 İşlem Yöneticisi HTTPS bağlamasını güvenliği sağlamak ve işlem ağacında her gönderenin alıcı çifti arasında güven oluşturmak için yalnızca taşıma güvenliği kullanır.  
  
#### <a name="https-transport-configuration"></a>HTTPS taşıma yapılandırması  
 X.509 sertifikaları işlem yöneticisi kimliğini oluşturmak için kullanılır. İstemci/sunucu kimlik doğrulaması gerekli değildir ve istemci/sunucu yetkilendirme uygulama ayrıntı olarak kalır:  
  
-   R1111: kablo üzerinden sunulan X.509 sertifikaları kaynak makinenin tam etki alanı adını (FQDN) ile eşleşen bir konu adına sahip olmalıdır.  
  
-   B1112: DNS başarılı olması için her gönderenin alıcı çifti arasında X.509 konu adı denetimleri için sistemdeki işlevsel olması gerekir.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Etkinleştirme ve yapılandırma bağlama kayıt  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]İstek/yanıt çift yönlü bağıntı bağlamayla HTTPS üzerinden gerektirir. (WS-Atomic işlemleri, Bölüm 8 bağıntı ve istek/yanıt iletisi exchange desenleri açıklamalarını hakkında daha fazla bilgi için bkz.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>2PC Protokolü bağlama yapılandırması  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tek yönlü (datagram) iletileri HTTPS üzerinden destekler. Bağıntı iletileri arasında bir uygulama ayrıntı olarak kalır.  
  
 B1131: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-bağıntı elde etmek için adresleme içinde açıklandığı gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s 2PC iletileri.  
  
### <a name="transaction-manager-mixed-security-binding"></a>İşlem Yöneticisi güvenlik bağlama karma  
 Bu kimlik kurulması amacıyla Web Hizmetleri koordinasyonu verilen belirteç modeli ile birlikte bu kullanımları taşıma güvenliği bağlama bir alternatif (karma mod) olur. Etkinleştirme ve kayıt arasında iki bağlamaları farklı yalnızca öğelerdir.  
  
#### <a name="https-transport-configuration"></a>HTTPS taşıma yapılandırması  
 X.509 sertifikaları işlem yöneticisi kimliğini oluşturmak için kullanılır. İstemci/sunucu kimlik doğrulaması gerekli değildir ve istemci/sunucu yetkilendirme uygulama ayrıntı olarak kalır.  
  
#### <a name="activation-message-binding-configuration"></a>Etkinleştirme ileti bağlama yapılandırması  
 Genellikle bir uygulama ve onun yerel işlem yöneticisi arasında gerçekleştirildiği için etkinleştirme iletiler birlikte çalışabilirlik genellikle katılma.  
  
 B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çift yönlü HTTPS bağlamasını kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) etkinleştirme iletileri için. İstek ve yanıt iletileri için WS-AT 1.1 WS adresleme 2004/08 WS-AT 1.0 ve WS adresleme 2005/08 kullanarak bağıntılı olan.  
  
 WS-Atomic işlem belirtimi, Bölüm 8, Ayrıntılar bağıntı ve ileti exchange desenleri hakkında daha fazla açıklar.  
  
-   R1222: temel alarak bir `CreateCoordinationContext`, düzenleyici dağıtmalı bir `SecurityContextToken` ile ilişkili gizli `STx`. Bu belirteç içinde döndürülen bir `t:IssuedTokens` WS-Trust belirtimine aşağıdaki üstbilgi.  
  
-   R1223: Etkinleştirme var olan bir düzenleme bağlamı içinde ortaya çıkarsa `t:IssuedTokens` üstbilgiyle `SecurityContextToken` var olan ilişkili gerekir içerik akışını `CreateCoordinationContext` ileti.  
  
 Yeni bir `t:IssuedTokens` giden eklemek için üstbilgi oluşturulacağı `wscoor:CreateCoordinationContextResponse` ileti.  
  
#### <a name="registration-message-binding-configuration"></a>Kayıt iletisi bağlama yapılandırması  
 B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çift yönlü HTTPS bağlamasını kullanır (açıklanan [Mesajlaşma protokolleri](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). İstek ve yanıt iletileri için WS-AT 1.1 WS adresleme 2004/08 WS-AT 1.0 ve WS adresleme 2005/08 kullanarak bağıntılı olan.  
  
 WS-AtomicTransaction, Bölüm 8, açıklar daha fazla ayrıntı bağıntı ve ileti exchange desenleri açıklamalarını hakkında.  
  
 R1232: Giden `wscoor:Register` iletileri kullanmalıdır `IssuedTokenOverTransport` kimlik doğrulama modu açıklanan [güvenlik protokolleri](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 `wsse:Timestamp` Öğesi kullanılarak imzalanmalıdır `SecurityContextToken``STx` verilmiş. Bu imza belirli işlemle ilişkili belirtecinin kanıtını olup işlemde kaydetme katılımcı kimliğini doğrulamak için kullanılır. RegistrationResponse ileti HTTPS üzerinden gönderilir.  
  
#### <a name="2pc-protocol-binding-configuration"></a>2PC Protokolü bağlama yapılandırması  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tek yönlü (datagram) iletileri HTTPS üzerinden destekler. Bağıntı iletileri arasında bir uygulama ayrıntı olarak kalır.  
  
 B1241: Uygulamaları desteklemelidir `wsa:ReferenceParameters` WS-bağıntı elde etmek için adresleme içinde açıklandığı gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s 2PC iletileri.  
  
## <a name="application-message-exchange"></a>Uygulama ileti değişimi  
 Uygulamaları bağlama aşağıdaki güvenlik gereksinimlerini karşılayan sürece herhangi belirli uygulama uygulaması iletileri için bu bağlamayı kullanmak boş şunlardır:  
  
-   R2001: Uygulama uygulaması iletileri akış gerekir `t:IssuedTokens` başlığı ile birlikte `CoordinationContext` ileti üstbilgisinde.  
  
-   R2002: Bütünlüğü ve gizliliği `t:IssuedToken` sağlanmalıdır.  
  
 `CoordinationContext` Üst bilgiyi içeren `wscoor:Identifier`. While tanımını `xsd:AnyURI` mutlak veya göreli URI, kullanılmasına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yalnızca destekler `wscoor:Identifiers`, mutlak URI olduğu.  
  
 B2003: Varsa `wscoor:Identifier` , `wscoor:CoordinationContext` göreli bir URI hataları döndürülecek gelen işlem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.  
  
## <a name="message-examples"></a>İleti örnekleri  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>CreateCoordinationContext istek/yanıt iletilerini  
 Aşağıdaki ileti, bir istek/yanıt yol izler.  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a>CreateCoordinationContextResponse güven 1.3 ve WSCoor 1.1  
  
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
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-     wssecurity-utility-1.0.xsd"   
xmlns:wst=http://docs.oasis-open.org/ws-sx/ws-trust/200512  
xmlns:wsc=http://schemas.xmlsoap.org/ws/2005/02/sc  
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
  ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedAttachedReference>   
<wst:RequestedUnattachedReference>   
<wsse:SecurityTokenReference>   
<wsse:Reference  
 ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
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
 Aşağıdaki iletileri kayıt iletileri edilir.  
  
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
  
#### <a name="register-response-with-wscoor-11"></a>Yanıt 1.1 WSCoor ile kaydetme  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a>İki aşama yürütme Protokolü iletileri  
 Aşağıdaki ileti iki aşamalı kayıt (2PC) protokolüne ilişkilendirir.  
  
#### <a name="commit-with-wsat-10"></a>WSAT 1.0 ile Yürüt  
  
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
  
#### <a name="commit-with-wsat-11"></a>1.1 WSAT ile Yürüt  
  
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
  
#### <a name="application-message-request"></a>Uygulama iletiyi-isteği  
  
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
