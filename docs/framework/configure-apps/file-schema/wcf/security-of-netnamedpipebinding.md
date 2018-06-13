---
title: '&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 74bf0d14b0acfd8a5382575d2ee1e51174b6b6b8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752799"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a>&lt;netNamedPipeBinding&gt; &lt;güvenliği&gt;
Bağlama için güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netNamedPipeBinding>  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|Bu bağlama uygulanan güvenlik türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Bu güvenlik devre dışı bırakır.<br />-Taşıma: Güvenlik temel tabanlı taşıma güvenliği sağlanır. Bu mod koruma düzeyiyle denetlemek mümkündür.<br />-Taşıma varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.NetNamedPipeSecurityMode>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|taşıma|Taşıma için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|Bağlama öğesi [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Kimlik Bilgisi Türü Seçme](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
