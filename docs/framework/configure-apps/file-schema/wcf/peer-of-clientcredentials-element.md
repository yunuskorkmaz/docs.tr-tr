---
title: "&lt;clientCredentials&gt; Öğesi &lt;eşi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f2fa776711223ace6a4cebce7783b1fa0c148a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a>&lt;clientCredentials&gt; Öğesi &lt;eşi&gt;
Eşler arası istemcileri kimlik doğrulaması yapılırken kullanılan kimlik bilgilerini belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<clientCredentials >  
\<Eş >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|İmzalama ve eşler arası istemcileri için iletileri şifrelemek için kullanılacak bir X.509 sertifikası belirtir. biçimindeki telefon numarasıdır.|  
|[\<peerAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|Eş istemcileri için kimlik doğrulama seçeneklerini belirtir.|  
|[\<messageSenderAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|İleti gönderenler için kimlik doğrulama seçeneklerini belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Bir hizmet için bir istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi Eş düğüm diğer eş düğümleri kimliğini doğrulamak için kullandığı kimlik doğrulama ayarları yanı sıra bir eş düğüm kafes içindeki diğer düğümlere kendi kimliğini doğrulamak için kullandığı kimlik bilgilerini belirtir. Daha fazla bilgi için bkz: [eş kanal ileti kimlik doğrulama](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) ve [eş kanalı uygulamalarını güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [İstemcilerinin güvenliğini sağlama](../../../../../docs/framework/wcf/securing-clients.md)  
 [Eş kanal ileti kimlik doğrulaması](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Eş kanal özel kimlik doğrulama](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Eş kanalı uygulamalarını güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
