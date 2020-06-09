---
title: Beyanlar ve Kaynaklara Erişimi Reddetme
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: e5ecb71b7e0596b1732207b50e1b6087528bba3f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587046"
---
# <a name="claims-and-denying-access-to-resources"></a>Beyanlar ve Kaynaklara Erişimi Reddetme
Windows Communication Foundation (WCF), talep tabanlı bir yetkilendirme mekanizmasını destekler. Ayrıca, sistem talepler varlığına göre kaynaklara erişime izin vermek için talepler varlığına göre genellikle kaynaklara erişimi reddeder. Bu tür sistemler, <xref:System.IdentityModel.Policy.AuthorizationContext> erişim izni verilen talepleri aramadan önce erişimin reddedildiğini belirten talepler için ' i incelemelidir.  
  
 Örneğin, bir sistem, bir kaynak için bir kaynağa erişimi, `Age` <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> yalnızca bu kimliğin bir türü, `Under 21` `Name` sağı <xref:System.IdentityModel.Claims.Rights.Identity%2A> ve kaynak değeri olan bir talep olduğunda bir kaynak değeri olan herkese reddedebilir `Mallory` . Başka bir yöntem de, sistem 21 yaşından eski olan herkese erişimi reddeder ve ad Mallarca olduğunda erişim verir. Bu anlam doğru şekilde uygulamak için `Age` öncelikle talebi aramak ve Age 'in 21 yaşın altında olup olmadığını anlamak önemlidir. Aksi takdirde, Mallory 21 altındaysa, kaynağa yalnızca talebin temelinde erişim izni verilebilir `Name` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md)
- [Talepler ve Belirteçler](claims-and-tokens.md)
