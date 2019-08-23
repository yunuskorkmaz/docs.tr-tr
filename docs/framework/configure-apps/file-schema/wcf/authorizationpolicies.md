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
# <a name="authorizationpolicies"></a><span data-ttu-id="3c161-101">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="3c161-101">\<authorizationPolicies></span></span>
<span data-ttu-id="3c161-102">Bu yapılandırma bölümü, `add` anahtar sözcüğü kullanılarak eklenebilen bir yetkilendirme ilkesi türü koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="3c161-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="3c161-103">Her yetkilendirme ilkesi, bir dize olan `policyType` tek bir gerekli özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="3c161-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="3c161-104">Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c161-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="3c161-105">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="3c161-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="3c161-106">Yetkilendirme ilkesinin nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> . ve [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="3c161-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c161-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c161-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="3c161-108">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="3c161-108">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="3c161-109">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c161-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="3c161-110">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="3c161-110">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="3c161-111">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="3c161-111">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
