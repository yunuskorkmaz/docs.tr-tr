---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926454"
---
# <a name="authorizationpolicies"></a>\<authorizationPolicies >
Bu yapılandırma bölümü, `add` anahtar sözcüğü kullanılarak eklenebilen bir yetkilendirme ilkesi türü koleksiyonu içerir. Her yetkilendirme ilkesi, bir dize olan `policyType` tek bir gerekli özniteliği içerir. Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir. Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir. Yetkilendirme ilkesinin nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> . ve [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Hizmet İşlemlerine Erişimi Yetkilendirme](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<> Ekle](add-of-authorizationpolicies.md)
- [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md)
