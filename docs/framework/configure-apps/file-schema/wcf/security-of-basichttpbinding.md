---
title: "&lt;basicHttpBinding&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c0ef60cdb53ed504d1738e4e17329f7420943312
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a>&lt;basicHttpBinding&gt; &lt;güvenliği&gt;
Güvenlik özelliklerini tanımlayan [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<basicHttpBinding >  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|İsteğe bağlı. Kullanılan güvenlik türünü belirtir. Varsayılan, `None` değeridir. Bu öznitelik türünde <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>mod özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|-Aktarım sırasında iletileri güvenli değil.|  
|Taşıma|Güvenlik, HTTPS aktarımı kullanılarak sağlanır. SOAP iletilerine HTTPS kullanan güvenli hale getirilir. Hizmet, hizmetin X.509 sertifikası kullanarak istemci kimlik doğrulaması yapılır. İstemci tarafından sağlanan ClientCredentialType kullanılarak doğrulanır. Bkz: [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).|  
|İleti|Güvenlik SOAP ileti güvenliği sağlanır. Varsayılan olarak, gövde imzalı ve şifrelenir. Bu bağlama için sunucu sertifikası, bant dışı istemciye sağlanması sistemi gerektirir. Yalnızca geçerli `ClientCredentialType` Bu bağlama için `Certificate`.|  
|TransportWithMessageCredential|Bütünlük, gizlilik ve sunucu kimlik doğrulama ile taşıma güvenliği sağlanır. İstemci kimlik doğrulaması SOAP iletisi güvenlik yoluyla sağlanır. Bu mod, kullanıcının kullanıcı adı/parola kullanarak kimlik doğrulaması ve ileti aktarma güvenliğini sağlamak için var olan bir HTTP dağıtım olduğunda geçerlidir.|  
|TransportCredentialOnly|Bu mod, ileti bütünlüğü ve gizliliği sağlamaz. Http tabanlı istemci kimlik doğrulaması sağlar. Bu mod dikkatli kullanılmalıdır. Burada taşıma güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması tarafından sağlanan ortamlarda kullanılmalıdır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] altyapı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|Temel HTTP hizmeti Aktarım güvenlik ayarlarını tanımlar. Bu öğe karşılık gelen <xref:System.ServiceModel.HttpTransportSecurity>.|  
|[\<İleti >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|Temel HTTP hizmeti ileti güvenlik ayarlarını tanımlar. Bu öğe karşılık gelen <xref:System.ServiceModel.BasicHttpMessageSecurity>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|Bağlama öğesi [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış. Bu öğe için ek güvenlik ayarlarını yapılandırmanızı sağlar `basicHttpBinding` öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Kimlik Bilgisi Türü Seçme](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
