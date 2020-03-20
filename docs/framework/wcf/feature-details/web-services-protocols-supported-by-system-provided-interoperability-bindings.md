---
title: Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: a1e67401a09370a46bc7a3e8546c95467bc18b67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184141"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
Windows Communication Foundation (WCF), Web hizmetleri belirtimleri olarak bilinen bir dizi belirtimi destekleyen Web hizmetleriyle birlikte çalışacak şekilde oluşturulmuştür. Birlikte çalışabilirlik en iyi uygulamalar için hizmet yapılandırmasını basitleştirmek için, WCF <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>üç <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>birlikte çalışabilir sistem sağlanan bağlamaları sunar: , , ve . Yapılandırılmış Bilgi StandartlarınıN İlerlemesi Için Organizasyon (OASIS) standartları ile birlikte çalışabilirlik için <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>WCF, sistem tarafından sağlanan bir birlikte çalışabilir bağlayıcıiçerir: . Meta veri yayını için WCF, sistem tarafından sağlanan iki birlikte çalışabilir bağlama içerir: [ \<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) ve [ \<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Bu konu, sistem tarafından sağlanan birlikte çalışabilir bağlamaların desteklediği özellikleri listeler.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Temel HttpBinding, wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding Bağlayıcılar tarafından desteklenen Web Hizmetleri Protokolleri  
  
### <a name="all-bindings"></a>Tüm Ciltler  
 [ \<Temel>Bağlama, ](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \<ws://>bağlama ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ve [ \<ws2007bağlama>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) bağlamaları aşağıdaki protokolleri destekler.  
  
> [!NOTE]
> Meta verileri yayımlamak için kullanılan bağlamalar hakkında bilgi için, bu konunun ilerleyen bölümlerinde "Sistem Tarafından Sağlanan Meta Veri Bağlamaları" bölümüne bakın.  
  
|Kategori|Protokol|Şartname ve Kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`ve `WS2007HttpBinding` HTTP ve HTTPS aktarımlarını kullanın.|  
|Mesajlaşma|Mtom|[Mtom](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding`ve `ws2007HttpBinding` destek İleti İletisi Optimizasyon Mekanizması (MTOM). Varsayılan olarak kullanılmaz. MTOM'u kullanmak `messageEncoding` için `"Mtom"`özniteliği .<br /><br /> Örnek:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Meta Veriler|WSDL 1.1|[WSDL 1.1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF, hizmetleri açıklamak için Web Hizmetleri Açıklama Dili'ni (WSDL) kullanır.|  
|Meta Veriler|WS-Politikası|[WS-Politikası](https://www.w3.org/Submission/WS-Policy/)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini açıklamak için ws-policy belirtimini etki alanına özgü iddialarla birlikte kullanır.|  
|Meta Veriler|WS-Politikası 1.5|[WS-Politikası 1.5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini açıklamak için ws-policy belirtimini etki alanına özgü iddialarla birlikte kullanır.|  
|Meta Veriler|WS-PolitikaEkleri Eki|[WS-PolitikaEkleri Eki](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF, Web Hizmetleri Açıklama Dili'nde (WSDL) çeşitli kapsamlarda ilke ifadeleri eklemek için WS-PolicyAttachment uygular.|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML Schema, WSDL ve WS-Policy'yi almak için WS-MetadataExchange'i uygular.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategori|Protokol|Şartname ve Kullanım|  
|--------------|--------------|-----------------------------|  
|Mesajlaşma|SABUN 1.1|[SABUN 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> Temel Profil 1.1 `basicHttpBinding` uyarınca, öğe SOAP 1.1 mesaj protokolünü uygular.|  
|Güvenlik|WSS SOAP İleti Güvenliği 1.0|[WSS SOAP İleti Güvenliği 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Temel Güvenlik Profiliuyarınca, `basicHttpBinding` öğe kullanıcı adı/parola ve X.509 tabanlı güvenlik için Web Hizmetleri Güvenliği (WSS) SOAP Message Security 1.0 belirtimini uygular.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP Mesaj Güvenliği Kullanıcı AdıToken Profil 1.0|[WSS SOAP Mesaj Güvenliği Kullanıcı AdıToken Profil 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP İleti Güvenliği X.509 Sertifika Belirteç Profili 1.0|[WSS SOAP İleti Güvenliği X.509 Sertifika Belirteç Profili 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>ws:Binding, ws2007HttpBinding ve wsDualHttpBinding  
  
|Kategori|Protokol|Şartname ve Kullanım|  
|--------------|--------------|-----------------------------|  
|Mesajlaşma|SABUN 1.2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Yardımcılar (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|Mesajlaşma|WS-Adresleme 2005/08|[Web Hizmetleri Adresleme 1.0 - Çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri Adresleme 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> Asynchronous `wsDualHttpBinding` `wsHttpBinding`ileti, ileti korelasyon ve aktarım-nötr adresleme mekanizmaları etkinleştirmek için World Wide Web Konsorsiyumu (W3C) WS-Adresleme önerisini uygulayın. `ws2007HttpBinding`<br /><br /> WCF, WS-* belirtimleri tarafından izin verilse de, WS adresleme üstbilgileri şifrelemesini desteklemez.|  
|Mesajlaşma|WS-Adresleme 1.0 - Meta veriler|[WS-Adresleme 1.0 Meta veriler](https://www.w3.org/2007/05/addressing/metadata/) Bu protokolün desteği ServiceMetadata davranışında ilke sürümünü ayarlayarak etkinleştirilir - politika sürümü 1.2 (varsayılan) olarak ayarlanmış, WSDL açıklaması WS-Adresleme wsdl ile uyumludur, ilke sürümü 1.5 olarak ayarlanmış, WSDL açıklaması ws adresli meta verilerle uyumludur.<br /><br /> WCF, WS-* belirtimleri tarafından izin verilse de, WS adresleme üstbilgileri şifrelemesini desteklemez.|  
|Güvenlik|WSS SOAP İleti Güvenliği 1.0|[WSS SOAP İleti Güvenliği 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> `securityMode` Öznitelik "wsSecurityOverHttp" (varsayılan) olarak ayarlandığında ve parametreler bir `wsSecurity` alt öğe kullanılarak yapılandırıldığında kullanın.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Mesaj Güvenliği Kullanıcı AdıToken Profil 1.1|[WSS SOAP Mesaj Güvenliği Kullanıcı AdıToken Profil 1.0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Öğenin `wsSecurity` `authenticationMode` özniteliği "Kullanıcı Adı" olarak ayarlandığında kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP İleti Güvenliği X.509 Sertifika Belirteç Profili 1.1|[WSS SOAP İleti Güvenliği X.509 Sertifika Belirteç Profili 1.1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> Öğenin `wsSecurity` `authenticationMode` özniteliği "Kullanıcı Adı", "Sertifika" veya "Yok" olarak ayarlandığında ileti koruması için kullanın. Ayrıca, öğenin `wsSecurity` `authenticationMode` özniteliği "Sertifika" olarak ayarlandığında bunu istemci kimlik doğrulaması için kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Mesaj Güvenlik Kerberos Token Profil 1.1|[WSS SOAP Mesaj Güvenlik Kerberos Token Profil 1.1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> Öğenin `wsSecurity` `authenticationMode` özniteliği "Windows" olarak ayarlandığında kimlik doğrulama ve ileti koruması için kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> `security/@mode` Öznitelik "İleti" olarak ayarlandığında ve `message/@establishSecurityContext` öznitelik "true" (varsayılan) olarak ayarlandığında güvenli bir oturum sağlamak için kullanın.|  
|Güvenlik|WS-Güven|[WS-Güven](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> WS-SecureConversation tarafından kullanılır (yukarıya bakın).|  
|Güvenilir Mesajlaşma|WS-Güvenilir Mesajlaşma|[WS-Güvenilir Mesajlaşma](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Bağlama kullanmak için yapılandırıldığınızda `reliableSession`kullanın.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|İşlemler|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> İşlem yöneticileri arasındaki iletişim için kullanın. WCF istemcileri ve hizmetleri her zaman yerel işlem yöneticilerini kullanır.|  
|İşlemler|WS-Koordinasyon|[WS-Koordinasyon](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> `flowTransactions` Öznitelik "İzin Verilen" veya "Gerekli" olarak ayarlandığında hareket bağlamını akış için kullanın.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding ve ws2007FederationHttpBinding  
 wsFederationHttpBinding>ve [ \<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğeleri federe senaryolar için destek sağlamak için tanıtıldı, üçüncü bir taraf bir belirteç bir istemci kimlik doğrulamak için kullanılan sorunları. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Tarafından kullanılan protokollere ek `wsHttpBinding` `wsFederationHttpBinding` olarak, kaldıraçlar:  
  
- `WS-Trust`belirteç verme için.  
  
- WSS Güvenlik İddiaları İşaretleme Dili (SAML) Belirteç Profili 1.0 ve 1.1 en yaygın olarak verilen belirteç biçimi için.  
  
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
  
 Daha fazla bilgi için [Federasyon'a](../../../../docs/framework/wcf/feature-details/federation.md) bakın.  
  
## <a name="system-provided-metadata-bindings"></a>Sistem Sağlanan Meta Veri Bağlamaları  
 Aşağıdaki tablolar, <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> sistem tarafından sağlanan birlikte çalışabilir meta veri bağlamaları tarafından desteklenen protokolleri açıklar.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 mex>bağlama aşağıdaki protokolleri destekler. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) Bu bağlamayı kullanma hakkında daha fazla bilgi için [Yayımlama Meta verileri](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)bölümüne bakın.  
  
|Kategori|Protokol|Şartname ve Kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Mesajlaşma|SABUN 1.2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Yardımcılar (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|Mesajlaşma|WS-Adresleme 2005/08|[Web Hizmetleri Adresleme 1.0 - Çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri Adresleme 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML Schema, WSDL ve WS-Policy'yi almak için WS-MetadataExchange'i uygular.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding>aşağıdaki protokolleri destekler. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Bu bağlamayı kullanma hakkında daha fazla bilgi için [Yayımlama Meta verileri](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)bölümüne bakın.  
  
|Kategori|Protokol|Şartname ve Kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> Aktarım güvenliği etkindir.|  
|Mesajlaşma|SABUN 1.2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Yardımcılar (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|Mesajlaşma|WS-Adresleme 2005/08|[Web Hizmetleri Adresleme 1.0 - Çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri Adresleme 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML Schema, WSDL ve WS-Policy'yi almak için WS-MetadataExchange'i uygular.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Destekli Ciltler](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<temelHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<ws:Bağlama>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBağlayıcı>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBağlama>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBağlama>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
