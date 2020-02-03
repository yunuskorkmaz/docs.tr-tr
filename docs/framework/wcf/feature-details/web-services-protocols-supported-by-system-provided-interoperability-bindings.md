---
title: Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 80fa0e501f425bd5b917059e90f2811f075db651
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746903"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
Windows Communication Foundation (WCF), Web Hizmetleri belirtimleri olarak bilinen bir belirtim kümesini destekleyen Web Hizmetleri ile birlikte çalışmak için oluşturulmuştur. WCF, birlikte çalışabilirlik en iyi uygulamalarına yönelik hizmet yapılandırmasını basitleştirmek için, üç adet birlikte çalışabilir sistem tarafından sunulan bağlamaları tanıtır: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>ve <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Yapılandırılmış bilgi standartları (OASU) standartlarına karşı bir kuruluşla birlikte çalışabilirlik için, WCF, birlikte çalışabilen bir sistem tarafından sunulan bağlama içerir: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. WCF, meta veri yayını için iki adet birlikte çalışabilen sistem tarafından sunulan bağlamaları içerir: [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) ve [\<mexhttpsbinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Bu konuda, sistem tarafından sunulan birlikte çalışabilen bağlamaların desteklediği özellikler listelenmiştir.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>BasicHttpBinding, wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding bağlamaları tarafından desteklenen Web Hizmetleri protokolleri  
  
### <a name="all-bindings"></a>Tüm bağlamalar  
 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [\<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)ve [\<WS2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) bağlamaları aşağıdaki protokolleri destekler.  
  
> [!NOTE]
> Meta verileri yayımlamak için kullanılan bağlamalar hakkında daha fazla bilgi için, bu konunun devamındaki "sistem tarafından sunulan meta veri bağlamaları" bölümüne bakın.  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`ve `WS2007HttpBinding` HTTP ve HTTPS aktarımlarını kullanın.|  
|İleti|MTOM|[MTOM](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding`ve `ws2007HttpBinding` destek Ileti Iletimi Iyileştirme mekanizması (MTOM). Varsayılan olarak kullanılmaz. MTOM 'yi kullanmak için `messageEncoding` özniteliğini `"Mtom"`olarak ayarlayın.<br /><br /> Örnek:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Meta Veriler|WSDL 1,1|[WSDL 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF, hizmetleri anlatmak için Web Hizmetleri Açıklama Dili (WSDL) kullanır.|  
|Meta Veriler|WS Ilkesi|[WS Ilkesi](https://www.w3.org/Submission/WS-Policy/)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini anlatmak için WS-Policy belirtimini, etki alanına özgü onaylarla birlikte kullanır.|  
|Meta Veriler|WS-Policy 1,5|[WS-Policy 1,5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini anlatmak için WS-Policy belirtimini, etki alanına özgü onaylarla birlikte kullanır.|  
|Meta Veriler|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF, Web Hizmetleri Açıklama Dili (WSDL) içindeki çeşitli kapsamlara ilke ifadeleri eklemek için WS-PolicyAttachment uygular.|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|İleti|SOAP 1,1|[SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> Temel profil 1,1 ' ye uygun olarak, `basicHttpBinding` öğesi SOAP 1,1 ileti protokolünü uygular.|  
|Güvenlik|WSS SOAP Iletisi güvenliği 1,0|[WSS SOAP Iletisi güvenliği 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Temel güvenlik profiline uygun olarak `basicHttpBinding` öğesi, Kullanıcı adı/parola ve X. 509.440 tabanlı güvenlik için Web Hizmetleri Güvenliği (WSS) SOAP Iletisi güvenlik 1,0 belirtimini uygular.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği UsernameToken profili 1,0|[WSS SOAP Iletisi güvenliği UsernameToken profili 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,0|[WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|İleti|SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|İleti|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`ve `wsDualHttpBinding`, zaman uyumsuz mesajlaşma, ileti bağıntısı ve taşıma bağımsız adresleme mekanizmalarını etkinleştirmek için World Wide Web Konsorsiyumu (W3C) WS-Addressing önerisi uygular.<br /><br /> WCF, WS-* belirtimleri tarafından izin verilse de WS-Addressing üst bilgileri şifrelemesini desteklemez.|  
|İleti|WS-Addressing 1,0-meta veriler|[Ws-Addressing 1,0 meta verileri](https://www.w3.org/2007/05/addressing/metadata/) ServiceMetadata davranışındaki ilke sürümü ayarlanarak etkinleştirilir ve PolicyVersion, 1,2 (varsayılan) olarak ayarlandıysa, WSDL açıklaması WS-Addressing wsdl ile uyumludur, PolicyVersion ayarı 1,5 olarak ayarlanır, WSDL açıklaması ws-Addressing meta verileri ile uyumludur.<br /><br /> WCF, WS-* belirtimleri tarafından izin verilse de WS-Addressing üst bilgileri şifrelemesini desteklemez.|  
|Güvenlik|WSS SOAP Iletisi güvenliği 1,0|[WSS SOAP Iletisi güvenliği 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> `securityMode` özniteliği "wsSecurityOverHttp" (varsayılan) olarak ayarlandığında ve parametreler `wsSecurity` alt öğesi kullanılarak yapılandırıldığında kullanın.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği UsernameToken profili 1,1|[WSS SOAP Iletisi güvenliği UsernameToken profili 1,0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> `wsSecurity` öğenin `authenticationMode` özniteliği "username" olarak ayarlandığında kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,1|[WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> `wsSecurity` öğenin `authenticationMode` özniteliği "username", "Certificate" veya "none" olarak ayarlandığında ileti koruması için kullanın. Ayrıca, `wsSecurity` öğenin `authenticationMode` özniteliği "sertifika" olarak ayarlandığında istemci kimlik doğrulaması için bunu kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği Kerberos belirteç profili 1,1|[WSS SOAP Iletisi güvenliği Kerberos belirteç profili 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> `wsSecurity` öğenin `authenticationMode` özniteliği "Windows" olarak ayarlandığında kimlik doğrulama ve ileti koruması için kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> `security/@mode` özniteliği "Message" olarak ayarlandığında ve `message/@establishSecurityContext` özniteliği "true" (varsayılan) olarak ayarlandığında güvenli bir oturum sağlamak için kullanın.|  
|Güvenlik|WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> WS-SecureConversation tarafından kullanılır (yukarıya bakın).|  
|Güvenilir Mesajlaşma|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Bağlama `reliableSession`kullanmak üzere yapılandırıldığında kullanın.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|İşlemler|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> İşlem yöneticileri arasındaki iletişim için kullanın. WCF istemcileri ve hizmetleri her zaman yerel işlem yöneticilerini kullanır.|  
|İşlemler|WS koordinasyonu|[WS koordinasyonu](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> `flowTransactions` özniteliği "Allowed" veya "Required" olarak ayarlandığında işlem bağlamını akışa almak için kullanın.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding ve ws2007FederationHttpBinding  
 [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve [\<WS2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğeleri, üçüncü bir tarafın bir istemcinin kimliğini doğrulamak için kullanılan bir belirteç verdiği federe senaryolar için destek sağlamak üzere sunulmuştur. `wsHttpBinding`tarafından kullanılan protokollerin yanı sıra `wsFederationHttpBinding` şu şekilde yararlanır:  
  
- belirteç verme için `WS-Trust`.  
  
- En yaygın olarak verilen belirteç biçimi için WSS güvenlik onayları biçimlendirme dili (SAML) belirteç profili 1,0 ve 1,1.  
  
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
  
 Daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Sistem tarafından belirtilen meta veri bağlamaları  
 Aşağıdaki tablolarda, <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> sınıfı tarafından kullanıma sunulan, sistem tarafından sunulan birlikte çalışabilen meta veri bağlamaları tarafından desteklenen protokoller açıklanır.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) bağlama aşağıdaki protokolleri destekler. Bu bağlamayı kullanma hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)|  
|İleti|SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|İleti|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) aşağıdaki protokolleri destekler. Bu bağlamayı kullanma hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> Taşıma güvenliği etkin.|  
|İleti|SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|İleti|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
