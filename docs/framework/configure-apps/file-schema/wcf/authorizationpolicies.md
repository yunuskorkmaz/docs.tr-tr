---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 2910f47b85ee67694cae0c3a725c3c7c7b3803c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122831"
---
# <a name="authorizationpolicies"></a><span data-ttu-id="754e1-101">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="754e1-101">\<authorizationPolicies></span></span>
<span data-ttu-id="754e1-102">Bu yapılandırma bölümü kullanılarak eklenen yetkilendirme ilkesi türü koleksiyonu içerir `add` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="754e1-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="754e1-103">Gereken tek bir her yetkilendirme ilkesi içeren `policyType` dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="754e1-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="754e1-104">Öznitelik, bir giriş talep kümesini talep başka bir dizi dönüşümünü sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="754e1-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="754e1-105">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="754e1-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="754e1-106">Bir yetkilendirme ilkesi birlikte nasıl çalıştığı hakkında daha fazla bilgi için bkz. <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve [yetkilendirme ilkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="754e1-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754e1-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="754e1-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="754e1-108">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="754e1-108">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="754e1-109">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="754e1-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="754e1-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="754e1-110">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [<span data-ttu-id="754e1-111">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="754e1-111">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
