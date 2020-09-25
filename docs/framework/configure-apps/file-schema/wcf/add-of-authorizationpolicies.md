---
title: <add> / <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 39cb89340907743c727a425bb2f140ac34842e3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181680"
---
# <a name="add-of-authorizationpolicies"></a>\<add> / \<authorizationPolicies>

Talep dönüştürme için bir yetkilendirme ilkesi belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`policyType`|Gerekli dize özniteliği.<br /><br /> Windows Communication Foundation (WCF) erişim denetimi modeli, bir yetkilendirme ilkelerinin kümesini tür olarak sağlamayı destekler. Bu öznitelik, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir. Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|Yetkilendirme ilkesi türleri koleksiyonunu belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Her yetkilendirme ilkesi `policyType` , bir dize olan tek bir gerekli özniteliği içerir. Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir. Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir. Yetkilendirme ilkesinin nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> . ve [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Hizmet İşlemlerine Erişimi Yetkilendirme](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md)
