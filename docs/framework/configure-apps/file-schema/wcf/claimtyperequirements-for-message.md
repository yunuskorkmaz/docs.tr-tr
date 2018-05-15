---
title: '&lt;ileti&gt; için &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: f4460311f5478f441b819bc8a48540d6feea69b1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="926fb-102">&lt;ileti&gt; için &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="926fb-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="926fb-103">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="926fb-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="926fb-104">Koleksiyon, istemcinin hizmete erişmek için kullandığı verilen belirteç olması gereken tüm gerekli ve isteğe bağlı talepleri belirtmek için hizmet tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="926fb-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="926fb-105">Hizmet meta veri gerekli talep türlerini WSDL yayımlama etkinleştirildi, ancak verilen belirteç içeren belirtilen talep türü WCF gerektirmez, kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="926fb-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="926fb-106">Gerekli talep türlerini mevcut zorlamak isteyen Hizmetleri Yetkilendirme İlkesi'ni kullanarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="926fb-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="926fb-107">Federasyon istemcilerde bu koleksiyon için güvenlik belirteci hizmeti istemci isteği için verilen bir belirteç gönderdiği gerekli ve isteğe bağlı talep listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="926fb-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926fb-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="926fb-108">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
