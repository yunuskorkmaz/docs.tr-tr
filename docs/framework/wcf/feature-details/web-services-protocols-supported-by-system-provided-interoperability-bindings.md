---
title: Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 963325604f66ddd4f8470933584b7880c86403bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951568"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
Windows Communication Foundation (WCF), Web Hizmetleri belirtimleri olarak bilinen bir belirtim kümesini destekleyen Web Hizmetleri ile birlikte çalışmak için oluşturulmuştur. WCF, birlikte çalışabilirlik en iyi uygulamaları için hizmet yapılandırmasını basitleştirmek amacıyla, birlikte çalışabilen üç sistem tarafından <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>sunulan <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>bağlama sağlar <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>:, ve. Yapılandırılmış bilgi standartları (OASU) standartlarına karşı bir kuruluşla birlikte çalışabilirlik için, WCF, birlikte çalışabilen bir sistem tarafından sağlanmış bağlama içerir: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. WCF, meta veri yayını için iki adet birlikte çalışabilen sistem tarafından sağlanmış bağlamaları içerir: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) ve [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Bu konuda, sistem tarafından sunulan birlikte çalışabilen bağlamaların desteklediği özellikler listelenmiştir.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>BasicHttpBinding, wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding bağlamaları tarafından desteklenen Web Hizmetleri protokolleri  
  
### <a name="all-bindings"></a>Tüm bağlamalar  
 BasicHttpBinding > [, WSHttpBinding>veWS2007HttpBinding>bağlamalarıaşağıdakiprotokolleridestekler\<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
  
> [!NOTE]
> Meta verileri yayımlamak için kullanılan bağlamalar hakkında daha fazla bilgi için, bu konunun devamındaki "sistem tarafından sunulan meta veri bağlamaları" bölümüne bakın.  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding` ve`WS2007HttpBinding` http ve https aktarımlarını kullanın.|  
|İleti|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding` ve`ws2007HttpBinding` destek ileti iletimi iyileştirme mekanizması (MTOM). Varsayılan olarak kullanılmaz. MTOM 'yi kullanmak için `messageEncoding` özniteliğini olarak `"Mtom"`ayarlayın.<br /><br /> Örnek:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Meta Veriler|WSDL 1,1|[WSDL 1,1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF, hizmetleri anlatmak için Web Hizmetleri Açıklama Dili (WSDL) kullanır.|  
|Meta Veriler|WS Ilkesi|[WS Ilkesi](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini anlatmak için WS-Policy belirtimini, etki alanına özgü onaylarla birlikte kullanır.|  
|Meta Veriler|WS-Policy 1,5|[WS-Policy 1,5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini anlatmak için WS-Policy belirtimini, etki alanına özgü onaylarla birlikte kullanır.|  
|Meta Veriler|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> WCF, Web Hizmetleri Açıklama Dili (WSDL) içindeki çeşitli kapsamlara ilke ifadeleri eklemek için WS-PolicyAttachment uygular.|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF, XML şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|İleti|SOAP 1,1|[SOAP 1,1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Temel profil 1,1 ' ye uygun olarak, `basicHttpBinding` öğesi soap 1,1 ileti protokolünü uygular.|  
|Güvenlik|WSS SOAP Iletisi güvenliği 1,0|[WSS SOAP Iletisi güvenliği 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Temel güvenlik profiline uygun olarak `basicHttpBinding` öğesi, Kullanıcı adı/parola ve X. 509.440 tabanlı güvenlik için Web Hizmetleri güvenliği (WSS) soap iletisi güvenlik 1,0 belirtimini uygular.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği UsernameToken profili 1,0|[WSS SOAP Iletisi güvenliği UsernameToken profili 1,0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,0|[WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|İleti|SOAP 1,2|[İlk](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Mesajlaşma çerçevesi](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> , Ve zamanuyumsuz`wsDualHttpBinding` mesajlaşma, ileti bağıntısı ve taşıma için nötr adresleme mekanizmalarını etkinleştirmek üzere World Wide Web Konsorsiyumu (W3C) WS-Addressing önerisi uygular. `wsHttpBinding` `ws2007HttpBinding`<br /><br /> WCF, WS-* belirtimleri tarafından izin verilse de WS-Addressing üst bilgileri şifrelemesini desteklemez.|  
|İleti|WS-Addressing 1,0-meta veriler|[Ws-Addressing 1,0 meta verileri](https://www.w3.org/2007/05/addressing/metadata) ServiceMetadata davranışındaki ilke sürümü ayarlanarak etkinleştirilir ve PolicyVersion, 1,2 (varsayılan) olarak ayarlandığında, WSDL açıklaması WS-Addressing wsdl ile uyumludur, PolicyVersion ayarı 1,5 olarak ayarlanır, WSDL açıklaması ws-Addressing meta verileri ile uyumludur.<br /><br /> WCF, WS-* belirtimleri tarafından izin verilse de WS-Addressing üst bilgileri şifrelemesini desteklemez.|  
|Güvenlik|WSS SOAP Iletisi güvenliği 1,0|[WSS SOAP Iletisi güvenliği 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Özniteliği "wssecurityoverhttp" (varsayılan) olarak ayarlandığında ve parametreler bir `wsSecurity` alt öğe kullanılarak yapılandırıldığında kullanın. `securityMode`<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği UsernameToken profili 1,1|[WSS SOAP Iletisi güvenliği UsernameToken profili 1,0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> `wsSecurity` Öğeninözniteliği"username`authenticationMode` " olarak ayarlandığında kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,1|[WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> `wsSecurity` Öğenin özniteliği "Kullanıcı adı", "sertifika" veya "hiçbiri" olarak ayarlandığında ileti koruması için kullanın. `authenticationMode` Ayrıca, `wsSecurity` `authenticationMode` öğenin özniteliği "sertifika" olarak ayarlandığında istemci kimlik doğrulaması için bunu kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği Kerberos belirteç profili 1,1|[WSS SOAP Iletisi güvenliği Kerberos belirteç profili 1,1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> `wsSecurity` Öğenin özniteliği"Windows"olarakayarlandığındakimlikdoğrulamaveiletikorumasıiçinkullanın.`authenticationMode`<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> `security/@mode` Özniteliği "Message" olarak ayarlandığında `message/@establishSecurityContext` ve özniteliği "true" (varsayılan) olarak ayarlandığında güvenli bir oturum sağlamak için kullanın.|  
|Güvenlik|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> WS-SecureConversation tarafından kullanılır (yukarıya bakın).|  
|Güvenilir Mesajlaşma|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Bağlama kullanılmak `reliableSession`üzere yapılandırıldığında kullanın.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|İşlemler|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> İşlem yöneticileri arasındaki iletişim için kullanın. WCF istemcileri ve hizmetleri her zaman yerel işlem yöneticilerini kullanır.|  
|İşlemler|WS koordinasyonu|[WS koordinasyonu](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> `flowTransactions` Öznitelik "Allowed" veya "Required" olarak ayarlandığında işlem bağlamını akışa almak için kullanın.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding ve ws2007FederationHttpBinding  
 WSFederationHttpBinding > ve [WS2007FederationHttpBinding > öğeleri, üçüncü tarafın bir istemcinin kimliğini doğrulamak için kullanılan bir belirteç verdiği federe senaryolar için destek sağlamak üzere sunulmuştur. \<](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Tarafından `wsHttpBinding`kullanılan protokollerin yanı sıra, `wsFederationHttpBinding` şunları kullanır:  
  
- `WS-Trust`belirteç verme için.  
  
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
 Aşağıdaki tablolarda, <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> sınıfı tarafından sunulan, sistem tarafından sunulan birlikte çalışabilen meta veri bağlamaları tarafından desteklenen protokoller açıklanır.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 MexHttpBinding > bağlama aşağıdaki protokolleri destekler. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) Bu bağlamayı kullanma hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|İleti|SOAP 1,2|[İlk](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Mesajlaşma çerçevesi](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF, XML şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding > aşağıdaki protokolleri destekler. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Bu bağlamayı kullanma hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Taşıma güvenliği etkin.|  
|İleti|SOAP 1,2|[İlk](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Mesajlaşma çerçevesi](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF, XML şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
