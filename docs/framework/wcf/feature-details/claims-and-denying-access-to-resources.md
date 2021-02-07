---
description: 'Daha fazla bilgi edinin: talepler ve kaynaklara erişimi reddetme'
title: Beyanlar ve Kaynaklara Erişimi Reddetme
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 0bbef26b0df06305db4ce460da4ba6177c79f56a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734977"
---
# <a name="claims-and-denying-access-to-resources"></a>Beyanlar ve Kaynaklara Erişimi Reddetme

Windows Communication Foundation (WCF), talep tabanlı bir yetkilendirme mekanizmasını destekler. Ayrıca, sistem talepler varlığına göre kaynaklara erişime izin vermek için talepler varlığına göre genellikle kaynaklara erişimi reddeder. Bu tür sistemler, <xref:System.IdentityModel.Policy.AuthorizationContext> erişim izni verilen talepleri aramadan önce erişimin reddedildiğini belirten talepler için ' i incelemelidir.  
  
 Örneğin, bir sistem, bir kaynak için bir kaynağa erişimi, `Age` <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> yalnızca bu kimliğin bir türü, `Under 21` `Name` sağı <xref:System.IdentityModel.Claims.Rights.Identity%2A> ve kaynak değeri olan bir talep olduğunda bir kaynak değeri olan herkese reddedebilir `Mallory` . Başka bir yöntem de, sistem 21 yaşından eski olan herkese erişimi reddeder ve ad Mallarca olduğunda erişim verir. Bu anlam doğru şekilde uygulamak için `Age` öncelikle talebi aramak ve Age 'in 21 yaşın altında olup olmadığını anlamak önemlidir. Aksi takdirde, Mallory 21 altındaysa, kaynağa yalnızca talebin temelinde erişim izni verilebilir `Name` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md)
- [Beyanlar ve Belirteçler](claims-and-tokens.md)
