---
title: <add> / <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 532f7f1a74cb3af24d7a1bc26046be901f3cf025
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205244"
---
# <a name="add-of-authorizationpolicies"></a>\<Ekle >, \<authorizationPolicies >
Talep dönüştürme için bir yetkilendirme ilkesi belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<davranışı >  
\<serviceAuthorization >  
\<authorizationPolicies >  
\<Ekle >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`policyType`|Gerekli dize özniteliği.<br /><br /> Windows Communication Foundation (WCF) erişim denetimi modeli, sağlama türü olarak yetkilendirme ilkeleri kümesini destekler. Bu öznitelik, bir giriş talep kümesini talep başka bir dizi dönüşümünü sağlayan bir yetkilendirme ilkesi belirtir. Erişim denetimi verilen veya reddedilen oturum tabanlı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<authorizationPolicies >](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|Yetkilendirme İlkesi türü koleksiyonu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Gereken tek bir her yetkilendirme ilkesi içeren `policyType` dize özniteliği. Öznitelik, bir giriş talep kümesini talep başka bir dizi dönüşümünü sağlayan bir yetkilendirme ilkesi belirtir. Erişim denetimi verilen veya reddedilen oturum tabanlı. Bir yetkilendirme ilkesi birlikte nasıl çalıştığı hakkında daha fazla bilgi için bkz. <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve [yetkilendirme ilkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Hizmet İşlemlerine Erişimi Yetkilendirme](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [Yetkilendirme İlkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md)
