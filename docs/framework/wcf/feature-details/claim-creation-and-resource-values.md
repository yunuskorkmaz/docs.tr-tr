---
title: Beyan Oluşturma ve Kaynak Değerleri
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: c3f36d607d88b208753066dcbd4e9baa6a2590fa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295138"
---
# <a name="claim-creation-and-resource-values"></a>Beyan Oluşturma ve Kaynak Değerleri

<xref:System.IdentityModel.Claims.Claim>Sınıfı, yerleşik talep türlerinin örneklerini oluşturmak için çeşitli yöntemler sağlar. Bu yöntemlerin her biri, sağlanan kaynakta hiçbir anlam veya biçimlendirme denetimi gerçekleştirmez:  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (bayt dizisinin uzunluğunu veya içeriğini denetlemez)  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (bayt dizisinin uzunluğunu veya içeriğini denetlemez)  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 Geçirilen kaynak değerlerinin doğru biçimde veya doğru türde bilgileri (veya her ikisi de) içerdiğinden emin olmak için yukarıdaki Yöntemler çağrılırken dikkatli olunmalıdır.  
  
 Aşağıdaki yöntemler belirli türleri alır:  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md)
