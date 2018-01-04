---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34bfaeb563bd4979bf29a5e45a60730eb38700b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserprincipalnamegt"></a>&lt;userPrincipalName&gt;
Kullanıcı asıl adı (istemci tarafından doğrulanmasını UPN), bir hizmetin belirtir.  
  
 UPN ayarlama hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
\<Kimliği >  
\<userPrincipalName >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|value|(Bazen kullanıcı oturum açma adı olarak adlandırılır) bir kullanıcı hesabı adı ve kullanıcı hesabının bulunduğu etki alanını tanımlayan bir etki alanı adı. Bu bir Windows etki alanında oturum açmak için standart kullanımdır. Biçim: someone@example.com (olduğu gibi bir e-posta adresi).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenli [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Bu kimliğe sahip bir uç nokta bağlandığı istemcisi, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken UPN kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma kodunu istemci tarafından doğrulanmasını UPN hizmetinin belirtir.  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
