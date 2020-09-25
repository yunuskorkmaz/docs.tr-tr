---
title: <claimTypeRequirements> bekleniyor <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: e70b036fddbc706c8c16de9a0834140f600aa5ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173802"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="d31ec-102">\<claimTypeRequirements> bekleniyor \<message></span><span class="sxs-lookup"><span data-stu-id="d31ec-102">\<claimTypeRequirements> for \<message></span></span>

<span data-ttu-id="d31ec-103">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31ec-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="d31ec-104">Koleksiyon, hizmet tarafından, istemcinin hizmete erişmek için kullandığı, verilen belirteçte olması gereken gerekli ve isteğe bağlı talepler belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d31ec-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="d31ec-105">WSDL yayımlaması etkinse, bu hizmet gerekli talep türlerini meta verilerde kullanıma sunar, ancak WCF verilen belirtecin belirtilen talep türlerini içermesini gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="d31ec-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="d31ec-106">Gerekli talep türlerini zorlamak isteyen hizmetler, yetkilendirme ilkesi kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d31ec-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="d31ec-107">Federasyon istemcilerinde, bu koleksiyon, verilen belirteç için istemcinin isteğindeki güvenlik belirteci hizmetine gönderilen gerekli ve isteğe bağlı taleplerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d31ec-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d31ec-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d31ec-108">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
