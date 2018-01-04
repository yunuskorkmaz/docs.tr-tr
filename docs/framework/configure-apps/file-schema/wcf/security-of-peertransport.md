---
title: "&lt;peerTransport&gt; &lt;güvenliği&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d08d839d0eb80c23b96f87cf26d3d68db7d358f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a>&lt;peerTransport&gt; &lt;güvenliği&gt;
Kullanılan kimlik doğrulama ve ileti taşıma için kullanılan güvenlik türünü de dahil olmak üzere bir eş kanalı ile ilişkili güvenlik ayarlarını içerir.  
  
 \<system.serviceModel >  
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
|`None`|Güvenliği devre dışı bırakıldı.|  
|`Transport`|Güvenlik, HTTPS kullanılarak sağlanır.|  
|`Message`|SOAP güvenliği kimlik doğrulama, bütünlüğü ve gizliliği sağlar.|  
|`TransportWithMessageCredential`|HTTPS kimlik doğrulaması ve gizliliği sağlar. SOAP iletilerine zengin kimlik bilgisi türler sağlar.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|Özel bağlama için bir eş taşıma tanımlar. Bu öğeye sahip bir `clientCredentialType` özniteliği olan bir hizmeti kullanılırken kullanılacak kimlik bilgilerini belirtir. Bu öznitelik türünde <xref:System.ServiceModel.PeerTransportCredentialType>.<br /><br /> Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<peerTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|Özel bağlama için bir eş taşıma tanımlar.|  
  
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
