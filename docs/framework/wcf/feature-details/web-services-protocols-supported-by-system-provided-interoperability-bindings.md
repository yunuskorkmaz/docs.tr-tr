---
title: Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: b77e0bf52e20ce5bd8f1c0deecfc822e9f910675
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648381"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
Windows Communication Foundation (WCF) Web hizmetleri belirtimleri bilinen özellikleri kümesi destekleyen Web Hizmetleri ile çalışmak için yerleşik olarak bulunur. Birlikte çalışabilirlik en iyi uygulamalar için hizmet yapılandırması basitleştirmek için birlikte üç sistem tarafından sağlanan bağlamalar WCF sunar: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, ve <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. İlerletme, yapılandırılmış bilgi standartları (OASIS) standartları için kuruluş birlikte çalışabilirlik için birlikte çalışabilen bir sistem tarafından sağlanan bağlama WCF içerir: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Meta veri yayımlama için WCF iki birlikte çalışabilen sistem tarafından sağlanan bağlamalar içerir: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) ve [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Bu konu, sistem tarafından sağlanan birlikte çalışabilen bağlama desteği özellikleri listeler.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Web Hizmetleri protokolleri desteklenen basicHttpBinding, wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding bağlamalar tarafından  
  
### <a name="all-bindings"></a>Tüm bağlamalar  
 [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ve [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) bağlamaları desteği şu protokoller.  
  
> [!NOTE]
>  Meta veri yayımlama için kullanılan bağlamaları hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "System-Provided meta veri bağlamaları" bölümüne bakın.  
  
|Kategori|Protokol|Belirtimi ve kullanım|  
|--------------|--------------|-----------------------------|  
|Taşıma|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`, ve `WS2007HttpBinding` HTTP ve HTTPS taşımalar kullanın.|  
|İleti|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`, ve `ws2007HttpBinding` ileti aktarım en iyi duruma getirme mekanizması (MTOM) destekler. Varsayılan olarak kullanılmaz. MTOM kullanmak için ayarlanmış `messageEncoding` özniteliğini `"Mtom"`.<br /><br /> Örnek:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Meta Veriler|WSDL 1.1|[WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF Web Hizmetleri Açıklama Dili (WSDL) hizmetleri tanımlamak için kullanır.|  
|Meta Veriler|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> WCF hizmet gereksinimlerini ve özelliklerini açıklayan WS-Policy belirtiminin etki alanına özgü bir onayları birlikte kullanır.|  
|Meta Veriler|WS-Policy 1.5|[WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> WCF hizmet gereksinimlerini ve özelliklerini açıklayan WS-Policy belirtiminin etki alanına özgü bir onayları birlikte kullanır.|  
|Meta Veriler|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> WCF Web Hizmetleri Açıklama Dili (WSDL) çeşitli kapsamları ilke ifadeleri eklemek için WS-PolicyAttachment uygular.|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF XML Şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategori|Protokol|Belirtimi ve kullanım|  
|--------------|--------------|-----------------------------|  
|İleti|SOAP 1.1|[SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Temel Profil 1.1 uygun olarak `basicHttpBinding` öğesi SOAP 1.1 iletisi protokolü uygular.|  
|Güvenlik|WSS SOAP ileti güvenliği 1.0|[WSS SOAP ileti güvenliği 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Temel güvenlik profilini uygun olarak `basicHttpBinding` öğesi, kullanıcı adı/parola ve güvenlik X.509 tabanlı Web Hizmetleri Güvenlik (WSS) SOAP ileti güvenliği 1.0 belirtimi uygular.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP ileti güvenlik UsernameToken profili 1.0|[WSS SOAP ileti güvenlik UsernameToken profili 1.0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP ileti güvenlik X.509 Sertifika belirteci profili 1.0|[WSS SOAP ileti güvenlik X.509 Sertifika belirteci profili 1.0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding  
  
|Kategori|Protokol|Belirtimi ve kullanım|  
|--------------|--------------|-----------------------------|  
|İleti|SOAP 1.2|[Temel bilgileri](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Mesajlaşma framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-Addressing 2005/08|[Adresleme 1.0 - çekirdek Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adresleme 1.0 - SOAP Web hizmeti](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`, Ve `wsDualHttpBinding` zaman uyumsuz Mesajlaşma, ileti bağıntısı ve aktarma-bağımsız adresleme mekanizmaları etkinleştirmek için World Wide Web Consortium (W3C) WS-Addressing önerisini uygulama.<br /><br /> WS - tarafından izin verilen ancak WCF WS-Addressing üst bilgileri, şifrelemeyi desteklemiyor * belirtimleri.|  
|İleti|WS-Addressing 1.0 - meta verileri|[WS-Addressing 1.0 meta verileri](https://www.w3.org/2007/05/addressing/metadata) bu protokolü için destek etkin (varsayılan) 1.2 ayarlayın policyversion ile ServiceMetadata davranışı - ilke sürümü ayarlayarak, wsdl açıklaması WS-Addressing wsdl ile uyumlu olan policyversion 1,5 olarak ayarlama, wsdl açıklaması ws-addressing meta verileri ile uyumludur.<br /><br /> WS - tarafından izin verilen ancak WCF WS-Addressing üst bilgileri, şifrelemeyi desteklemiyor * belirtimleri.|  
|Güvenlik|WSS SOAP ileti güvenliği 1.0|[WSS SOAP ileti güvenliği 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Şu durumlarda kullanın `securityMode` özniteliği "wsSecurityOverHttp" (varsayılan) olarak ayarlanır ve bu parametreleri kullanılarak yapılandırılmış bir `wsSecurity` alt öğesi.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP ileti güvenlik UsernameToken Profil 1.1|[WSS SOAP ileti güvenlik UsernameToken profili 1.0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Şu durumlarda kullanın `wsSecurity` öğenin `authenticationMode` özniteliği, "Username" için ayarlanır.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP ileti güvenlik X.509 sertifikası belirteci Profil 1.1|[WSS SOAP ileti güvenlik X.509 sertifikası belirteci Profil 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Kullanım iletisini koruma için zaman `wsSecurity` öğenin `authenticationMode` "Username", "Sertifika" veya "None" özniteliğini ayarlayın. Ayrıca, bu istemci kimlik doğrulaması için kullanmak, `wsSecurity` öğenin `authenticationMode` özniteliği, "Sertifika" ayarlanır.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP ileti güvenlik Kerberos belirteci Profil 1.1|[WSS SOAP ileti güvenlik Kerberos belirteci Profil 1.1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Kullanım kimlik doğrulaması ve ileti koruma için zaman `wsSecurity` öğenin `authenticationMode` özniteliği, "Windows" için ayarlanır.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Güvenli bir oturum belirtin kullanacağınız olduğunda `security/@mode` özniteliği "İleti" olarak ayarlanmışsa ve `message/@establishSecurityContext` özniteliği "true" (varsayılan) olarak ayarlayın.|  
|Güvenlik|WS-Güven|[WS-Güven](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> WS-SecureConversation (yukarıya bakın) tarafından kullanılır.|  
|Güvenilir Mesajlaşma|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Bağlama kullanmak için yapılandırıldığında kullanın `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|İşlemler|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> İşlem yöneticileri arasındaki iletişim için kullanılır. WCF istemcileri ve Hizmetleri her zaman yerel işlem yöneticileri kullanın.|  
|İşlemler|WS-düzenleme|[WS-düzenleme](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> İşlem bağlamı akışının kullanın, `flowTransactions` "Verilen" veya "Required" özniteliği ayarlayın.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding ve ws2007FederationHttpBinding  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğeleri, üçüncü bir yerde Federasyon senaryoları için destek sağlamak için sunulmuştur şirketlerin, istemcinin kimliğini doğrulamak için kullanılan bir belirteç verir. Tarafından kullanılan protokollerin yanı sıra `wsHttpBinding`, `wsFederationHttpBinding` yararlanır:  
  
- `WS-Trust` belirteç verme için.  
  
- WSS güvenlik onaylama işaretleme dili (SAML) belirteci Profil 1.0 ve 1.1 için en yaygın olarak belirteci biçimi çıkarılır.  
  
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
  
 Daha fazla bilgi için [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Sistem tarafından sağlanan meta veri bağlamaları  
 Aşağıdaki tablo tarafından kullanıma sunulan sistem tarafından sağlanan birlikte çalışabilen bir meta veri bağlamaları ile desteklenen protokolleri açıklar <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> sınıfı.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<MexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) bağlama aşağıdaki protokollerini destekler. Bu bağlama işlemini kullanma hakkında daha fazla bilgi için bkz. [meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategori|Protokol|Belirtimi ve kullanım|  
|--------------|--------------|-----------------------------|  
|Taşıma|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|İleti|SOAP 1.2|[Temel bilgileri](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Mesajlaşma framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-Addressing 2005/08|[Adresleme 1.0 - çekirdek Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adresleme 1.0 - SOAP Web hizmeti](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF XML Şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) aşağıdaki protokollerini destekler. Bu bağlama işlemini kullanma hakkında daha fazla bilgi için bkz. [meta veri yayımlama](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategori|Protokol|Belirtimi ve kullanım|  
|--------------|--------------|-----------------------------|  
|Taşıma|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Aktarım güvenliği etkinleştirilir.|  
|İleti|SOAP 1.2|[Temel bilgileri](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Mesajlaşma framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|İleti|WS-Addressing 2005/08|[Adresleme 1.0 - çekirdek Web Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Adresleme 1.0 - SOAP Web hizmeti](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Meta Veriler|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF XML Şeması, WSDL ve WS-Policy almak için WS-MetadataExchange uygular.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
