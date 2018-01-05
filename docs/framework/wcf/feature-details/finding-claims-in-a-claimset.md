---
title: "ClaimSet için Beyan Bulma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21a30833e72b1c87f1c65a3deaa44da48c08336e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="36bf3-102">ClaimSet için Beyan Bulma</span><span class="sxs-lookup"><span data-stu-id="36bf3-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="36bf3-103">İçeriği inceleyerek bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talep türlerinin bir ortak talep tabanlı yetkilendirme kullanırken bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="36bf3-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="36bf3-104">İncelemek için bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talepleri varlığını kullanmak <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36bf3-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="36bf3-105">Bu yöntem doğrudan üzerinde yineleme daha iyi performans sağlar <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="36bf3-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="36bf3-106">Aşağıdaki örnek, bu kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="36bf3-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="36bf3-107">Unutmayın `claimType` ve `claimRight` parametreleri olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="36bf3-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="36bf3-108">Bu durumda, parametreleri tüm talep türleri eşleşen ve hakları talep.</span><span class="sxs-lookup"><span data-stu-id="36bf3-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36bf3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="36bf3-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="36bf3-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36bf3-110">See Also</span></span>  
 [<span data-ttu-id="36bf3-111">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="36bf3-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
