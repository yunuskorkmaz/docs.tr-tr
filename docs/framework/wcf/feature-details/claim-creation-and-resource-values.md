---
title: Beyan Oluşturma ve Kaynak Değerleri
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: ca1bb8ccbc77e2b026a65a9cef56118e8b86dbb3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704075"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="171aa-102">Beyan Oluşturma ve Kaynak Değerleri</span><span class="sxs-lookup"><span data-stu-id="171aa-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="171aa-103"><xref:System.IdentityModel.Claims.Claim> Sınıfı yerleşik örneklerini oluşturmaya talep türleri için çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="171aa-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="171aa-104">Bu yöntemlerin aşağıdaki Hayır anlam gerçekleştirmek veya sağlanan kaynak denetimi biçimi:</span><span class="sxs-lookup"><span data-stu-id="171aa-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <span data-ttu-id="171aa-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (uzunluk veya bayt dizisinin içeriğini denetlemez)</span><span class="sxs-lookup"><span data-stu-id="171aa-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <span data-ttu-id="171aa-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (uzunluk veya bayt dizisinin içeriğini denetlemez)</span><span class="sxs-lookup"><span data-stu-id="171aa-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="171aa-107">Bakım değerleri geçirilen kaynak doğru biçimde olduğundan veya bilgileri (veya her ikisi) doğru türünü içeren emin olmak için yukarıdaki yöntemleri çağrılırken edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="171aa-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="171aa-108">Aşağıdaki yöntemleri belirli türlerini alır:</span><span class="sxs-lookup"><span data-stu-id="171aa-108">The following methods take specific types:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="171aa-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="171aa-109">See also</span></span>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="171aa-110">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="171aa-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
