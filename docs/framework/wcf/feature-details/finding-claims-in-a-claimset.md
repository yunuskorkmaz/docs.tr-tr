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
ms.openlocfilehash: 1954da20d382630f965582fcc01bbaf72665720a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595459"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="b0fd6-102">ClaimSet için Beyan Bulma</span><span class="sxs-lookup"><span data-stu-id="b0fd6-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="b0fd6-103"><xref:System.IdentityModel.Claims.ClaimSet>Belirli bir talep türü için içeriğini incelemek, talep tabanlı yetkilendirme kullanılırken ortak bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="b0fd6-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="b0fd6-104"><xref:System.IdentityModel.Claims.ClaimSet>Belirli talepler hakkında bir durumu incelemek için <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b0fd6-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="b0fd6-105">Bu yöntem doğrudan üzerinden yinelemekten daha iyi performans sağlar <xref:System.IdentityModel.Claims.ClaimSet> .</span><span class="sxs-lookup"><span data-stu-id="b0fd6-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="b0fd6-106">Aşağıdaki örnekte bu kullanım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b0fd6-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="b0fd6-107">`claimType`Ve parametrelerinin olabileceğini unutmayın `claimRight` `null` .</span><span class="sxs-lookup"><span data-stu-id="b0fd6-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="b0fd6-108">Bu durumda, parametreler tüm talep türleri ve talep haklarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b0fd6-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0fd6-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0fd6-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b0fd6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0fd6-110">See also</span></span>

- [<span data-ttu-id="b0fd6-111">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="b0fd6-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
