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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8213931a7509378fde6df19eeb189abd8a81e96
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="claim-creation-and-resource-values"></a>Beyan Oluşturma ve Kaynak Değerleri
<xref:System.IdentityModel.Claims.Claim> Sınıfı, yerleşik örneklerini oluşturmaya türleri talepleri için çeşitli yöntemler sağlar. Bu yöntemlerin aşağıdaki Hayır anlamsal gerçekleştirmek veya sağlanan kaynağında Denetimi Biçimlendir:  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A>(uzunluk veya bayt dizisi içeriğini denetlemez)  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A>(uzunluk veya bayt dizisi içeriğini denetlemez)  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 Dikkatli değerleri geçirilen kaynak doğru biçimi olan veya doğru tür bilgileri (veya her ikisi de) içeren emin olmak için yukarıdaki yöntemleri çağrılırken olunmalıdır.  
  
 Aşağıdaki yöntemlerden belirli tür alın:  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
