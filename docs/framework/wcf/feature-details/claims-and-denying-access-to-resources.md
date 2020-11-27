---
title: Beyanlar ve Kaynaklara Erişimi Reddetme
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 2c903d5b5aa520b9c79fb8b36912324feaf9a432
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264928"
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="d69bd-102">Beyanlar ve Kaynaklara Erişimi Reddetme</span><span class="sxs-lookup"><span data-stu-id="d69bd-102">Claims and Denying Access to Resources</span></span>

<span data-ttu-id="d69bd-103">Windows Communication Foundation (WCF), talep tabanlı bir yetkilendirme mekanizmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="d69bd-103">Windows Communication Foundation (WCF) supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="d69bd-104">Ayrıca, sistem talepler varlığına göre kaynaklara erişime izin vermek için talepler varlığına göre genellikle kaynaklara erişimi reddeder.</span><span class="sxs-lookup"><span data-stu-id="d69bd-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="d69bd-105">Bu tür sistemler, <xref:System.IdentityModel.Policy.AuthorizationContext> erişim izni verilen talepleri aramadan önce erişimin reddedildiğini belirten talepler için ' i incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="d69bd-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="d69bd-106">Örneğin, bir sistem, bir kaynak için bir kaynağa erişimi, `Age` <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> yalnızca bu kimliğin bir türü, `Under 21` `Name` sağı <xref:System.IdentityModel.Claims.Rights.Identity%2A> ve kaynak değeri olan bir talep olduğunda bir kaynak değeri olan herkese reddedebilir `Mallory` .</span><span class="sxs-lookup"><span data-stu-id="d69bd-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="d69bd-107">Başka bir yöntem de, sistem 21 yaşından eski olan herkese erişimi reddeder ve ad Mallarca olduğunda erişim verir.</span><span class="sxs-lookup"><span data-stu-id="d69bd-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="d69bd-108">Bu anlam doğru şekilde uygulamak için `Age` öncelikle talebi aramak ve Age 'in 21 yaşın altında olup olmadığını anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d69bd-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="d69bd-109">Aksi takdirde, Mallory 21 altındaysa, kaynağa yalnızca talebin temelinde erişim izni verilebilir `Name` .</span><span class="sxs-lookup"><span data-stu-id="d69bd-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d69bd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d69bd-110">See also</span></span>

- [<span data-ttu-id="d69bd-111">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="d69bd-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="d69bd-112">Beyanlar ve Belirteçler</span><span class="sxs-lookup"><span data-stu-id="d69bd-112">Claims and Tokens</span></span>](claims-and-tokens.md)
