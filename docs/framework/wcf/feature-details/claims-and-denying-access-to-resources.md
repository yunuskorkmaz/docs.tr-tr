---
title: Beyanlar ve Kaynaklara Erişimi Reddetme
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 4f48c59090579f4b451f615bb792a4dcb73f6df5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079519"
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="032cc-102">Beyanlar ve Kaynaklara Erişimi Reddetme</span><span class="sxs-lookup"><span data-stu-id="032cc-102">Claims and Denying Access to Resources</span></span>
<span data-ttu-id="032cc-103">Windows Communication Foundation (WCF) bir beyana dayalı yetkilendirme mekanizması destekler.</span><span class="sxs-lookup"><span data-stu-id="032cc-103">Windows Communication Foundation (WCF) supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="032cc-104">Talep varlığını temel alarak kaynaklara erişimine yanı sıra sistemleri genellikle talep varlığını temel alarak kaynaklara erişimi reddetme.</span><span class="sxs-lookup"><span data-stu-id="032cc-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="032cc-105">Bu sistemlere incelemelisiniz <xref:System.IdentityModel.Policy.AuthorizationContext> aramadan önce erişimine izin verilmesinden neden talepler için erişimin reddedilmesi neden talepler için.</span><span class="sxs-lookup"><span data-stu-id="032cc-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="032cc-106">Örneğin, bir sistem bir kaynağa erişim izni olan herkes bir talep türü ile reddetmek, `Age`, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, kaynak değerini `Under 21` yalnızca o kimlik da bir talep türü olduğunda `Name`, sağ <xref:System.IdentityModel.Claims.Rights.Identity%2A>, Kaynak değeri `Mallory`.</span><span class="sxs-lookup"><span data-stu-id="032cc-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="032cc-107">Başka bir deyişle, sistem erişimi herkes tarafından altında 21 yaşında olduğunu ve adı Mallory olduğunda erişim verir engeller.</span><span class="sxs-lookup"><span data-stu-id="032cc-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="032cc-108">Bu doğru uygulamak için anlamsal, aranacak önemlidir `Age` ilk talep ve yaş altında 21 yaşında olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="032cc-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="032cc-109">Mallory 21'altında varsa, aksi takdirde, daha sonra kaynak yalnızca temeline göre erişim verilebilir `Name` talep.</span><span class="sxs-lookup"><span data-stu-id="032cc-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032cc-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="032cc-110">See also</span></span>

- [<span data-ttu-id="032cc-111">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="032cc-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="032cc-112">Beyanlar ve Belirteçler</span><span class="sxs-lookup"><span data-stu-id="032cc-112">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
