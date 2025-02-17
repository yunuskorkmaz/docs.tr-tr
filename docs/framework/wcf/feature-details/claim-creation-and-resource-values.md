---
description: 'Daha fazla bilgi edinin: talep oluşturma ve kaynak değerleri'
title: Beyan Oluşturma ve Kaynak Değerleri
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: 20763c683c5bf5734a21a4315576a8f9f354ff35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734990"
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
