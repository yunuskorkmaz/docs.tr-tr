---
title: <claimTypeRequirements> için <message>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: db6717022bf3af0c4922818668595dd3937e9c71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106568"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="00a2c-102">\<claimTypeRequirements > için \<iletisi ></span><span class="sxs-lookup"><span data-stu-id="00a2c-102">\<claimTypeRequirements> for \<message></span></span>
<span data-ttu-id="00a2c-103">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="00a2c-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="00a2c-104">Koleksiyon hizmeti tarafından İstemcinin hizmete erişmek için kullandığı verilen belirteç olması gerekli ve isteğe bağlı talepleri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00a2c-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="00a2c-105">Hizmet meta verilerinde gerekli talep türlerinin WSDL yayımlama etkinleştirildi, ancak WCF verilen belirteç içeren belirli talep türlerini gerektirmeyen kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="00a2c-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="00a2c-106">Gerekli talep türlerinin bulunduğunu zorunlu isteyen Hizmetleri Yetkilendirme İlkesi'ni kullanarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="00a2c-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="00a2c-107">Federasyon istemcilerde istemci isteğindeki güvenlik belirteci hizmeti verilen bir belirteç için gönderilen gerekli ve isteğe bağlı talepler listesinin bu koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="00a2c-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a2c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00a2c-108">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
