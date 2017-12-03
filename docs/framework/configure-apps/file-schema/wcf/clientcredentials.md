---
title: '&lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 834853d8a922148d2810cd391a64a281f2f9ae3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcredentialsgt"></a>&lt;clientCredentials&gt;
Bir hizmet için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<clientCredentials >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<clientCredentials type="String"  
      supportInteractive="Boolean" >  
   <clientCertificate>  
   </clientCertificate>  
   <digest>  
   </digest>  
   <isuedToken>  
   </isuedToken>  
   <peer>  
   </peer>  
   <serviceCertificate>  
   </serviceCertificate>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</clientCredentials>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`supportInteractive`|Etkileşimli bir kullanıcı çalışma zamanında istemci kimlik bilgilerini seçme dahil olup olmadığını belirten bir Boole değeri. Varsayılan değer `true` şeklindedir.|  
|`type`|Bu yapılandırma öğesi türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|Hizmeti için istemci kimlik doğrulaması için kullanılan sertifikayı belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.|  
|[\<httpDigest >](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|Hizmeti için istemci kimlik doğrulaması için kullanılan bir Özet belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.|  
|[\<IssuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|İçin bir güvenli belirteç hizmeti (STS) istemci kimlik doğrulaması için kullanılan özel bir belirteç türü belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.|  
|[\<Eş >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|Geçerli bir eş kimlik bilgilerini belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerCredentialElement>.|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|İstemci hizmete kimlik doğrulaması için kullanılan sertifikayı belirtir ve sertifika seçeneklerini ayarlamak için bir yapı sağlar. Bu sertifika, sağlanan-bant hizmetinden istemciye olması gerekir. Bu öğe türünde <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.|  
|[\<Windows >](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|Windows kimlik bilgilerini belirtir. Kimlik bilgisi geçerli iş parçacığının varsayılandır. Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsClientElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İstemci kimlik bilgileri, karşılıklı kimlik doğrulaması gerekli olduğu durumlarda Hizmetleri için istemci kimlik doğrulaması için kullanılır. Bu yapılandırma bölümü de senaryolar için hizmet sertifikaları belirtmek için İstemci Hizmeti'ne hizmetin sertifikayla iletileri burada güvenlik altına almanız gerekir kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [Güvenlik davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [İstemcilerinin güvenliğini sağlama](../../../../../docs/framework/wcf/securing-clients.md)
