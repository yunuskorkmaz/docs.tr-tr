---
title: "Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bfc4342435580796423056889b1c3bd22153740
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Web hizmetleri belirtimleri bilinen belirtim kümesi desteği Web Hizmetleri ile birlikte çalışmak için yerleşik olarak bulunur. Birlikte çalışabilirlik en iyi yöntemler, hizmet yapılandırmasını basitleştirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] üç birlikte çalışabilir sistem tarafından sağlanan bağlamalar sunar: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, ve <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Terfi, yapılandırılmış bilgi standartları (OASIS) standartları için kuruluş ile birlikte çalışabilirlik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir birlikte çalışabilen sistem tarafından sağlanan bir bağlamayı içerir: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Meta veri yayımlama için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iki birlikte çalışabilir sistem tarafından sağlanan bağlamaları içerir: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) ve [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Bu konu, sistem tarafından sağlanan birlikte çalışabilir bağlamalar destek özellikleri listeler.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Web Hizmetleri protokolleri desteklenen basicHttpBinding, wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding bağlamaları tarafından  
  
### <a name="all-bindings"></a>Tüm bağlamaları  
 [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ve [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) bağlamaları desteği aşağıdaki protokollerden.  
  
> [!NOTE]
>  Meta veri yayımlamak için kullanılan bağlamaları hakkında daha fazla bilgi için bu konunun devamındaki "System-Provided meta veri bağlamaları" bölümüne bakın.  
  
|Kategori|Protokol|Belirtimi ve kullanımı|  
|--------------|--------------|-----------------------------|  
|Taşıma|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`, ve `WS2007HttpBinding` HTTP ve HTTPS aktarımları kullanın.|  
|İleti|MTOM|[MTOM](http://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`, ve `ws2007HttpBinding` ileti iletim en iyi duruma getirme mekanizmasını (MTOM) destekler. Varsayılan olarak kullanılmaz. MTOM kullanmak üzere ayarlanmış `messageEncoding` özniteliğini `"Mtom"`.<br /><br /> Örnek:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Meta Veriler|WSDL 1.1|[WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Web Hizmetleri Açıklama Dili (WSDL) hizmetleri tanımlamak için kullanır.|  
|Meta Veriler|WS-ilke|[WS-ilke](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]etki alanına özgü onaylar birlikte WS-Policy belirtimi hizmet gereksinimlerini ve özelliklerini tanımlamak için kullanır.|  
|Meta Veriler|WS-Policy 1.5|[WS-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]etki alanına özgü onaylar birlikte WS-Policy belirtimi hizmet gereksinimlerini ve özelliklerini tanımlamak için kullanır.|  
|Meta Veriler|WS-PolicyAttachment|[WS-PolicyAttachment](http://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]çeşitli kapsamlar Web Hizmetleri Açıklama Dili (WSDL) ilke ifadeleri eklemek için WS-PolicyAttachment uygular.|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]XML Şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategori|Protokol|Belirtimi ve kullanımı|  
|--------------|--------------|-----------------------------|  
|İleti|SOAP 1.1|[SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Temel Profil 1.1 uygun olarak `basicHttpBinding` öğesi SOAP 1.1 iletisi protokolünü uygular.|  
|Güvenlik|WSS SOAP iletisi güvenlik 1.0|[WSS SOAP iletisi güvenlik 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Temel güvenlik profili, uygun olarak `basicHttpBinding` öğesi, kullanıcı adı/parola ve X.509 tabanlı güvenlik için Web Services Güvenlik (WSS) SOAP iletisi güvenlik 1.0 belirtimi uygular.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP iletisi güvenlik UsernameToken profili 1.0|[WSS SOAP iletisi güvenlik UsernameToken profili 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP iletisi güvenlik X.509 sertifikası belirteci profili 1.0|[WSS SOAP iletisi güvenlik X.509 sertifikası belirteci profili 1.0](http://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding  
  
|Kategori|Protokol|Belirtimi ve kullanımı|  
|--------------|--------------|-----------------------------|  
|İleti|SOAP 1.2|[Primer](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [İleti framework](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-adresleme 2005/08|[Adresleme 1.0 - çekirdek Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adresleme 1.0 - SOAP Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`, Ve `wsDualHttpBinding` zaman uyumsuz ileti, ileti bağıntısı ve Aktarım Tarafsız adresleme mekanizmaları etkinleştirmek için World Wide Web Konsorsiyumu (W3C) WS-adresleme öneriyi uygulamayı.<br /><br /> WS - tarafından izin verilen rağmen WCF WS adresleme üstbilgilerinin şifrelemeyi desteklemiyor * belirtimleri.|  
|İleti|WS-adresleme 1.0 - meta verileri|[WS-adresleme 1.0 meta veri](http://www.w3.org/2007/05/addressing/metadata) bu protokolü desteği, 1.2 (varsayılan) ayarlamak policyversion ile ServiceMetadata davranışını - ilke sürümü ayarlayarak etkinleştirildiğinde, wsdl açıklamasıdır WS adresleme wsdl ile uyumlu olan 1,5 olarak ayarlama policyversion wsdl tanımını ws adresleme meta verileri ile uyumludur.<br /><br /> WS - tarafından izin verilen rağmen WCF WS adresleme üstbilgilerinin şifrelemeyi desteklemiyor * belirtimleri.|  
|Güvenlik|WSS SOAP iletisi güvenlik 1.0|[WSS SOAP iletisi güvenlik 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Şu durumlarda kullanın `securityMode` özniteliği "wsSecurityOverHttp" (varsayılan) olarak ayarlanmış ve parametreleri kullanılarak yapılandırılmış bir `wsSecurity` alt öğesi.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP iletisi güvenlik UsernameToken Profil 1.1|[WSS SOAP iletisi güvenlik UsernameToken profili 1.0](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Şu durumlarda kullanın `wsSecurity` öğenin `authenticationMode` özniteliği "Username" olarak ayarlanmış.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP iletisi güvenlik X.509 sertifikası belirteci Profil 1.1|[WSS SOAP iletisi güvenlik X.509 sertifikası belirteci Profil 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> İleti koruma kullanılmak zaman `wsSecurity` öğenin `authenticationMode` özniteliği "Username", "Sertifika" veya "Hiçbiri" olarak ayarlanmış. Ayrıca, bu istemci kimlik doğrulaması için kullanmak, `wsSecurity` öğenin `authenticationMode` özniteliği "Sertifika" olarak ayarlanmış.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP iletisi güvenlik Kerberos belirteci Profil 1.1|[WSS SOAP iletisi güvenlik Kerberos belirteci Profil 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Kullanım kimlik doğrulaması ve ileti koruması için zaman `wsSecurity` öğenin `authenticationMode` özniteliği "Windows" olarak ayarlanmış.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WS-SecureConversation|[WS-SecureConversation](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Güvenli bir oturum sağlamak için kullanın, `security/@mode` özniteliği "İletiye" olarak ayarlanmış ve `message/@establishSecurityContext` özniteliği "true" (varsayılan)'olarak ayarlayın.|  
|Güvenlik|WS-Trust|[WS-Trust](http://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> WS-SecureConversation (yukarıya bakın) tarafından kullanılır.|  
|Güvenilir Mesajlaşma|WS-ReliableMessaging|[WS-ReliableMessaging](http://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Bağlama kullanmak üzere yapılandırıldığında kullanın `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|İşlemler|WS-AtomicTransaction|[WS-AtomicTransaction](http://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> İşlem yöneticileri arasındaki iletişim için kullanın. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]istemcileri ve Hizmetleri her zaman yerel işlem yöneticileri kullanın.|  
|İşlemler|WS-düzenleme|[WS-düzenleme](http://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> İşlem bağlamı akış kullanmasını zaman `flowTransactions` özniteliği "İzin verilen" veya "Gerekli" olarak ayarlanmış.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding ve ws2007FederationHttpBinding  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğeleri üçüncü burada Federasyon senaryoları için destek sağlamak için sunulan taraf bir istemci kimlik doğrulaması için kullanılan bir belirteci verir. Tarafından kullanılan protokoller yanı sıra `wsHttpBinding`, `wsFederationHttpBinding` yararlanır:  
  
-   `WS-Trust`belirteç yayını için.  
  
-   WSS güvenlik onaylar biçimlendirme dili (SAML) belirteci profili 1.0 ve 1.1 en yaygın olarak belirteci biçimi verdi.  
  
 Örnek:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"   
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =   
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federasyon](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Sistem tarafından sağlanan meta veri bağlama  
 Aşağıdaki tablolar tarafından sunulan sistem tarafından sağlanan birlikte çalışabilir meta veri bağlamaları tarafından desteklenen protokolleri açıklamaktadır <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> sınıfı.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<MexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) bağlama aşağıdaki protokollerini destekler. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu bağlama bkz [meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategori|Protokol|Belirtimi ve kullanımı|  
|--------------|--------------|-----------------------------|  
|Taşıma|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)|  
|İleti|SOAP 1.2|[Primer](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [İleti framework](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-adresleme 2005/08|[Adresleme 1.0 - çekirdek Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adresleme 1.0 - SOAP Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]XML Şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) aşağıdaki protokollerini destekler. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bu bağlama bkz [meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategori|Protokol|Belirtimi ve kullanımı|  
|--------------|--------------|-----------------------------|  
|Taşıma|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Taşıma güvenliği etkin.|  
|İleti|SOAP 1.2|[Primer](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [İleti framework](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-adresleme 2005/08|[Adresleme 1.0 - çekirdek Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adresleme 1.0 - SOAP Web Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]XML Şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
 [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)  
 [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)  
 [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
