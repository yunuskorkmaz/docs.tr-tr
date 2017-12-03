---
title: "Beyanlar ve Kaynaklara Erişimi Reddetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 00d6a797b8099313c15d075457ee757c1f22f744
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="4a7da-102">Beyanlar ve Kaynaklara Erişimi Reddetme</span><span class="sxs-lookup"><span data-stu-id="4a7da-102">Claims and Denying Access to Resources</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="4a7da-103">bir talep tabanlı yetkilendirme mekanizması destekler.</span><span class="sxs-lookup"><span data-stu-id="4a7da-103"> supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="4a7da-104">Talep varlığını temel alarak kaynaklara erişimine yanı sıra sistemleri genellikle talep varlığını temel alarak kaynaklara erişimini.</span><span class="sxs-lookup"><span data-stu-id="4a7da-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="4a7da-105">Bu sistemlere incelemelisiniz <xref:System.IdentityModel.Policy.AuthorizationContext> erişimine izin verilmeden neden talepler için aramadan önce erişimlerin sonucunda talepler için.</span><span class="sxs-lookup"><span data-stu-id="4a7da-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="4a7da-106">Örneğin, bir sistem bir kaynağa erişimi olan herkes bir talep türü ile reddetmek, `Age`, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>ve kaynak değerini `Under 21` yalnızca kimliğini de talep türü olduğunda `Name`, sağ <xref:System.IdentityModel.Claims.Rights.Identity%2A>, Kaynak değerini `Mallory`.</span><span class="sxs-lookup"><span data-stu-id="4a7da-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="4a7da-107">Başka bir deyişle, sistem erişim herkese altında 21 yaşında olduğunu ve Mallory adı şu olduğunda erişim verir reddeder.</span><span class="sxs-lookup"><span data-stu-id="4a7da-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="4a7da-108">Bunu doğru şekilde uygulamak için anlamsal, aranacak önemlidir `Age` ilk talep ve yaşın altında 21 yaşında olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="4a7da-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="4a7da-109">Mallory altında 21 ise, aksi takdirde, ardından kaynak erişim yalnızca temeline göre verilebilir `Name` talep.</span><span class="sxs-lookup"><span data-stu-id="4a7da-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7da-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a7da-110">See Also</span></span>  
 [<span data-ttu-id="4a7da-111">Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme</span><span class="sxs-lookup"><span data-stu-id="4a7da-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="4a7da-112">Beyanlar ve belirteçler</span><span class="sxs-lookup"><span data-stu-id="4a7da-112">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
