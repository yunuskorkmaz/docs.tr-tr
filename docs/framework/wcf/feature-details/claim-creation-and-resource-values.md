---
title: Beyan Oluşturma ve Kaynak Değerleri
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: 5c2904f68ba50df99504e2f70c9170490ca54f73
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645566"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="bec8a-102">Beyan Oluşturma ve Kaynak Değerleri</span><span class="sxs-lookup"><span data-stu-id="bec8a-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="bec8a-103"><xref:System.IdentityModel.Claims.Claim> Sınıfı yerleşik örneklerini oluşturmaya talep türleri için çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bec8a-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="bec8a-104">Bu yöntemlerin aşağıdaki Hayır anlam gerçekleştirmek veya sağlanan kaynak denetimi biçimi:</span><span class="sxs-lookup"><span data-stu-id="bec8a-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="bec8a-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (uzunluk veya bayt dizisinin içeriğini denetlemez)</span><span class="sxs-lookup"><span data-stu-id="bec8a-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="bec8a-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (uzunluk veya bayt dizisinin içeriğini denetlemez)</span><span class="sxs-lookup"><span data-stu-id="bec8a-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="bec8a-107">Bakım değerleri geçirilen kaynak doğru biçimde olduğundan veya bilgileri (veya her ikisi) doğru türünü içeren emin olmak için yukarıdaki yöntemleri çağrılırken edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bec8a-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="bec8a-108">Aşağıdaki yöntemleri belirli türlerini alır:</span><span class="sxs-lookup"><span data-stu-id="bec8a-108">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="bec8a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bec8a-109">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="bec8a-110">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="bec8a-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
