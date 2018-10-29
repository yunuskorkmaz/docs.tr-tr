---
title: '&lt;peerTransport&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: c7a2a2cde58dac87b1b378fe2ac8148493c1cf09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200463"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a>&lt;peerTransport&gt; &lt;güvenliği&gt;
İle kullanılan kimlik doğrulaması ve ileti aktarım için kullanılan güvenlik türü de dahil olmak üzere, eş kanaldan ilgili güvenlik ayarlarını içerir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<peerTransport >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`mode`|Uygulanacak güvenlik türünü belirtir. İleti varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mod özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenlik devre dışı bırakıldı.|  
|`Transport`|HTTPS kullanarak güvenliği sağlanır.|  
|`Message`|SOAP güvenliği, kimlik doğrulaması, bütünlüğü ve gizliliği sağlar.|  
|`TransportWithMessageCredential`|HTTPS kimlik doğrulaması ve gizlilik sağlar. SOAP iletilerini zengin kimlik bilgisi türler sağlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|Özel bağlama için bir eş tanımlar. Bu öğeyi bir `clientCredentialType` özniteliği bir hizmetle etkileşim kurulurken kullanılacak kimlik bilgilerini belirtir. Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.<br /><br /> Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<peerTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|Özel bağlama için bir eş tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Aktarım Güvenliği](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
