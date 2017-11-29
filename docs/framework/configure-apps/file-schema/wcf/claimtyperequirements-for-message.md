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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 747ac641f8602010819baa00033f3663e2e5f678
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a><span data-ttu-id="cdabe-102">&lt;ileti&gt; için &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="cdabe-102">&lt;claimTypeRequirements&gt; for &lt;message&gt;</span></span>
<span data-ttu-id="cdabe-103">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cdabe-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="cdabe-104">Koleksiyon, istemcinin hizmete erişmek için kullandığı verilen belirteç olması gereken tüm gerekli ve isteğe bağlı talepleri belirtmek için hizmet tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdabe-104">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="cdabe-105">Hizmet meta veri gerekli talep türlerini WSDL yayımlama etkinleştirildi, ancak verilen belirteç içeren belirtilen talep türü WCF gerektirmez, kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="cdabe-105">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="cdabe-106">Gerekli talep türlerini mevcut zorlamak isteyen Hizmetleri Yetkilendirme İlkesi'ni kullanarak yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cdabe-106">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="cdabe-107">Federasyon istemcilerde bu koleksiyon için güvenlik belirteci hizmeti istemci isteği için verilen bir belirteç gönderdiği gerekli ve isteğe bağlı talep listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="cdabe-107">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdabe-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdabe-108">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
