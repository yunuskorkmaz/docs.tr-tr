---
title: ClaimSet için Beyan Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 7ca22d701277e71e509e6b291eb59a0223a0250c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488604"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="1c12c-102">ClaimSet için Beyan Bulma</span><span class="sxs-lookup"><span data-stu-id="1c12c-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="1c12c-103">İçeriği inceleyerek bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talep türlerinin bir ortak talep tabanlı yetkilendirme kullanırken bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="1c12c-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="1c12c-104">İncelemek için bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talepleri varlığını kullanmak <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c12c-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="1c12c-105">Bu yöntem doğrudan üzerinde yineleme daha iyi performans sağlar <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="1c12c-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="1c12c-106">Aşağıdaki örnek, bu kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c12c-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="1c12c-107">Unutmayın `claimType` ve `claimRight` parametreleri olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="1c12c-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="1c12c-108">Bu durumda, parametreleri tüm talep türleri eşleşen ve hakları talep.</span><span class="sxs-lookup"><span data-stu-id="1c12c-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c12c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c12c-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1c12c-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c12c-110">See Also</span></span>  
 [<span data-ttu-id="1c12c-111">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="1c12c-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
