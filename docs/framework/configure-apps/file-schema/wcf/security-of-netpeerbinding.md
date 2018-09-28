---
title: '&lt;netPeerBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
ms.openlocfilehash: d17d063ffdd354327c2523415b7d9394e723135a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47436303"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a>&lt;netPeerBinding&gt; &lt;güvenliği&gt;
Güvenlik ayarlarını tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), kimlik doğrulaması türü de dahil olmak üzere kullanılan ve güvenlik ileti aktarım için kullanılır.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netPeerBinding >  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|İsteğe bağlı. Bu bağlama ile yapılandırılan eş tarafından kullanılan güvenlik türünü belirtir. Varsayılan değer `Message` şeklindedir. Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mod özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|İleti|SOAP güvenliği, kimlik doğrulaması, bütünlüğü ve gizliliği sağlar.|  
|Yok.|Güvenlik devre dışı bırakıldı.|  
|Taşıma|HTTPS kullanarak güvenliği sağlanır.|  
|TransportWithMessageCredential|HTTPS kimlik doğrulaması ve gizlilik sağlar. SOAP iletilerini zengin kimlik bilgisi türler sağlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|Bu bağlama ile yapılandırılan eşleri tarafından gönderilen güvenli iletiler için aktarım türü tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Tüm bağlama yeteneklerini tanımlar [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenlik ya da ileti veya aktarım özgü olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Kimlik Bilgisi Türü Seçme](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
