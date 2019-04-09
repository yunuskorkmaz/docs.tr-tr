---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 9e7b845d39495dba1d1a19af95faf308b8b8c0fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188257"
---
# <a name="userprincipalname"></a>\<userPrincipalName >
Kullanıcı asıl adı (istemci tarafından doğrulanacak UPN) bir hizmetin belirtir.  
  
 UPN ayarlama hakkında daha fazla bilgi için bkz. [kimlik doğrulama ile hizmet kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
\<Kimliği >  
\<userPrincipalName >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|value|Bir kullanıcı hesabı adı (bazen kullanıcı oturum açma adı olarak adlandırılır) ve kullanıcı hesabının bulunduğu etki alanını tanıtan bir etki alanı adı. Bu, bir Windows etki alanında oturum açma için standart kullanımdır. Biçim: someone@example.com (olduğu gibi bir e-posta adresi).|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|İstemci tarafından doğrulanacak bir hizmetin kimliğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu kimlik ile bir uç noktayı bağlayan güvenli bir Windows Communication Foundation (WCF) istemci, SSPI kimlik doğrulama uç noktası ile gerçekleştirirken UPN kullanır.  
  
## <a name="example"></a>Örnek  
 İstemci tarafından doğrulanacak UPN hizmeti aşağıdaki yapılandırma kodunu belirtir.  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
