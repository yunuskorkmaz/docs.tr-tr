---
description: 'Hakkında daha fazla bilgi <claimTypeRequirements> edinin: <message>'
title: <claimTypeRequirements> bekleniyor <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: a393a075c64f4a46e5ac055b3c417514861c9661
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638905"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="8b2f1-103">\<claimTypeRequirements> bekleniyor \<message></span><span class="sxs-lookup"><span data-stu-id="8b2f1-103">\<claimTypeRequirements> for \<message></span></span>

<span data-ttu-id="8b2f1-104">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-104">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="8b2f1-105">Koleksiyon, hizmet tarafından, istemcinin hizmete erişmek için kullandığı, verilen belirteçte olması gereken gerekli ve isteğe bağlı talepler belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-105">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="8b2f1-106">WSDL yayımlaması etkinse, bu hizmet gerekli talep türlerini meta verilerde kullanıma sunar, ancak WCF verilen belirtecin belirtilen talep türlerini içermesini gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-106">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="8b2f1-107">Gerekli talep türlerini zorlamak isteyen hizmetler, yetkilendirme ilkesi kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-107">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="8b2f1-108">Federasyon istemcilerinde, bu koleksiyon, verilen belirteç için istemcinin isteğindeki güvenlik belirteci hizmetine gönderilen gerekli ve isteğe bağlı taleplerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-108">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b2f1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-109">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
