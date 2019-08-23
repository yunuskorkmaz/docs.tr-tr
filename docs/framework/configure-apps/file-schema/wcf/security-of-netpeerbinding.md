---
title: <security> / <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936622"
---
# <a name="security-of-netpeerbinding"></a>\<\<netpeerbinding > Güvenlik >
Kullanılan kimlik doğrulaması türü ve ileti aktarımı için kullanılan güvenlik dahil olmak üzere [ \<NetPeerTcpBinding >](netpeertcpbinding.md)güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlama >  
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
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|İsteğe bağlı. Bu bağlama ile yapılandırılan eşler tarafından kullanılan güvenlik türünü belirtir. Varsayılan değer `Message` şeklindedir. Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`Message`|SOAP Güvenliği kimlik doğrulama, bütünlük ve gizlilik sağlar.|  
|Yok.|Güvenlik devre dışı bırakıldı.|  
|Aktarım|Güvenlik, HTTPS kullanılarak sağlanır.|  
|TransportWithMessageCredential|HTTPS kimlik doğrulaması ve gizlilik sağlar. SOAP iletileri zengin kimlik bilgisi türleri sağlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Taşıma >](transport-of-netpeertcpbinding.md)|Bu bağlama ile yapılandırılan eşler tarafından gönderilen güvenli iletiler için taşıma türünü tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../misc/binding.md)|[ \<NetPeerTcpBinding >](netpeertcpbinding.md)'ın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenlik, ileti ya da aktarım özel olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Kimlik Bilgisi Türü Seçme](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
