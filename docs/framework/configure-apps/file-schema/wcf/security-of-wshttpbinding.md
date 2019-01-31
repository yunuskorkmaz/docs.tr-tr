---
title: <security> , <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: 0de9ade585a2170aa1def9898581aedddc651bd7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258467"
---
# <a name="security-of-wshttpbinding"></a>\<Güvenlik >, \<wsHttpBinding >
Güvenlik özelliklerini gösteren [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<wsHttpBinding>  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|-İsteğe bağlı. Uygulanan güvenlik türünü belirtir. Varsayılan, `Message` değeridir.<br />-Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mod özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Hiçbiri|Güvenlik devre dışı bırakıldı.|  
|Taşıma|HTTPS kullanarak güvenliği sağlanır. Hizmet SSL sertifikaları ile yapılandırılması gerekir. İleti tamamen HTTPS kullanan güvenli ve hizmetin SSL sertifikası kullanarak istemci tarafından doğrulanır. İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentials` özniteliği. ' ın [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).|  
|İleti|SOAP ileti güveliği kullanarak güvenliği sağlanır. Varsayılan olarak, SOAP gövdesi şifreli ve imza var. Çeşitli hizmet kimlik bilgilerini kullanmak için algoritma paketini olan bant dışı istemci kullanılabilir olup gibi özellikler, bu mod sunar ve ileti gövdesi Security.Message özelliği uygulamak için koruma düzeyini. İstemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.|  
|TransportWithMessageCredential|Bu modda, HTTPS kimlik doğrulaması bütünlüğü ve gizliliği sağlar ve istemci kimlik doğrulaması SOAP ileti güvenliği sağlar. Varsayılan olarak, istemci kimlik doğrulaması, oturum başına bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|Taşıma güvenlik ayarlarını tanımlar. Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü.|  
|[\<İleti >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türü.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|HTTP taşıma uygulamalar için güvenli bir bağlama.|  
  
## <a name="remarks"></a>Açıklamalar  
 WSHttpBinding sınıfı WS - uygulama hizmetleri ile birlikte çalışabilirlik için tasarlanmış * belirtimleri. Bu bağlama için Aktarım güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) olan.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../../../docs/framework/misc/binding.md)
