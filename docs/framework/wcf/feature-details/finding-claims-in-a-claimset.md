---
description: 'Hakkında daha fazla bilgi edinin: bir ClaimSet içinde talepler bulma'
title: ClaimSet için Beyan Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 3ac4553e50f98f54e0a23aa9d759d7ae2f7caa8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802937"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="1c012-103">ClaimSet için Beyan Bulma</span><span class="sxs-lookup"><span data-stu-id="1c012-103">Finding Claims in a ClaimSet</span></span>

<span data-ttu-id="1c012-104"><xref:System.IdentityModel.Claims.ClaimSet>Belirli bir talep türü için içeriğini incelemek, talep tabanlı yetkilendirme kullanılırken ortak bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="1c012-104">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="1c012-105"><xref:System.IdentityModel.Claims.ClaimSet>Belirli talepler hakkında bir durumu incelemek için <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c012-105">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="1c012-106">Bu yöntem doğrudan üzerinden yinelemekten daha iyi performans sağlar <xref:System.IdentityModel.Claims.ClaimSet> .</span><span class="sxs-lookup"><span data-stu-id="1c012-106">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="1c012-107">Aşağıdaki örnekte bu kullanım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c012-107">The following example demonstrates this usage.</span></span> <span data-ttu-id="1c012-108">`claimType`Ve parametrelerinin olabileceğini unutmayın `claimRight` `null` .</span><span class="sxs-lookup"><span data-stu-id="1c012-108">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="1c012-109">Bu durumda, parametreler tüm talep türleri ve talep haklarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="1c012-109">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c012-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c012-110">Example</span></span>  

 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1c012-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c012-111">See also</span></span>

- [<span data-ttu-id="1c012-112">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="1c012-112">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
