---
title: "&lt;ileti&gt; için &lt;claimTypeRequirements&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 158aad6a6a11bb889df74e1222a8881a1c38803f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="cc308-102">&lt;ileti&gt; için &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="cc308-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="cc308-103">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc308-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="cc308-104">Koleksiyon, istemcinin hizmete erişmek için kullandığı verilen belirteç olması gereken tüm gerekli ve isteğe bağlı talepleri belirtmek için hizmet tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc308-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="cc308-105">Hizmet meta veri gerekli talep türlerini WSDL yayımlama etkinleştirildi, ancak verilen belirteç içeren belirtilen talep türü WCF gerektirmez, kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cc308-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="cc308-106">Gerekli talep türlerini mevcut zorlamak isteyen Hizmetleri Yetkilendirme İlkesi'ni kullanarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc308-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="cc308-107">Federasyon istemcilerde bu koleksiyon için güvenlik belirteci hizmeti istemci isteği için verilen bir belirteç gönderdiği gerekli ve isteğe bağlı talep listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="cc308-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc308-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc308-108">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
