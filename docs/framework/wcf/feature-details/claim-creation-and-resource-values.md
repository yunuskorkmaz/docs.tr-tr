---
title: "Beyan Oluşturma ve Kaynak Değerleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a553a33f4747e2e5ed51f675a8db2d90da65fb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="290d0-102">Beyan Oluşturma ve Kaynak Değerleri</span><span class="sxs-lookup"><span data-stu-id="290d0-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="290d0-103"><xref:System.IdentityModel.Claims.Claim> Sınıfı, yerleşik örneklerini oluşturmaya türleri talepleri için çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="290d0-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="290d0-104">Bu yöntemlerin aşağıdaki Hayır anlamsal gerçekleştirmek veya sağlanan kaynağında Denetimi Biçimlendir:</span><span class="sxs-lookup"><span data-stu-id="290d0-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <span data-ttu-id="290d0-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A>(uzunluk veya bayt dizisi içeriğini denetlemez)</span><span class="sxs-lookup"><span data-stu-id="290d0-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <span data-ttu-id="290d0-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A>(uzunluk veya bayt dizisi içeriğini denetlemez)</span><span class="sxs-lookup"><span data-stu-id="290d0-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="290d0-107">Dikkatli değerleri geçirilen kaynak doğru biçimi olan veya doğru tür bilgileri (veya her ikisi de) içeren emin olmak için yukarıdaki yöntemleri çağrılırken olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="290d0-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="290d0-108">Aşağıdaki yöntemlerden belirli tür alın:</span><span class="sxs-lookup"><span data-stu-id="290d0-108">The following methods take specific types:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="290d0-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="290d0-109">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="290d0-110">Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme</span><span class="sxs-lookup"><span data-stu-id="290d0-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
