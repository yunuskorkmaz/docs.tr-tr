---
title: '&lt;authorizationPolicies&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e33dca28f11b564f622ff1c202827c693f0874c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltauthorizationpoliciesgt"></a><span data-ttu-id="86c4e-102">&lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="86c4e-102">&lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="86c4e-103">Bu yapılandırma bölümü kullanılarak eklenebilir yetkilendirme ilkesi türleri koleksiyonunu içeren `add` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="86c4e-103">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="86c4e-104">Her bir yetkilendirme ilkesi gereken tek bir içeren `policyType` bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="86c4e-104">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="86c4e-105">Öznitelik, bir giriş talep kümesini bir dönüştürme talep başka bir dizi içine sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="86c4e-105">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="86c4e-106">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="86c4e-106">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="86c4e-107">Bir yetkilendirme ilkesi nasıl çalıştığı hakkında daha fazla bilgi için bkz: <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve [yetkilendirme ilkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="86c4e-107">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c4e-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86c4e-108">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="86c4e-109">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="86c4e-109">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="86c4e-110">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="86c4e-110">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="86c4e-111">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="86c4e-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="86c4e-112">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="86c4e-112">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
