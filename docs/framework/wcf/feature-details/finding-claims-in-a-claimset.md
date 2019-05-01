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
ms.openlocfilehash: 42e6ee682220913f872da337eb41f6c290082988
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856433"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="37e0f-102">ClaimSet için Beyan Bulma</span><span class="sxs-lookup"><span data-stu-id="37e0f-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="37e0f-103">İçeriği İnceleme bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talep türlerinin genel talep tabanlı yetkilendirme kullanırken bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="37e0f-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="37e0f-104">İncelemek için bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talepleri varlığını kullanan <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="37e0f-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="37e0f-105">Bu yöntem, doğrudan üzerinde yineleme daha iyi performans sağlar. <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="37e0f-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="37e0f-106">Aşağıdaki örnek, bu kullanımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="37e0f-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="37e0f-107">Unutmayın `claimType` ve `claimRight` parametreleri olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="37e0f-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="37e0f-108">Bu durumda, parametrelerle eşleşen tüm talep türleri ve hak iddia.</span><span class="sxs-lookup"><span data-stu-id="37e0f-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37e0f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="37e0f-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="37e0f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37e0f-110">See also</span></span>

- [<span data-ttu-id="37e0f-111">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="37e0f-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
