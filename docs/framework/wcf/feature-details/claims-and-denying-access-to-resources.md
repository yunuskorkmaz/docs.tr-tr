---
title: Beyanlar ve Kaynaklara Erişimi Reddetme
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: a53affe5e21b5ef532e7094eed032b44f5a5ea7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="claims-and-denying-access-to-resources"></a>Beyanlar ve Kaynaklara Erişimi Reddetme
Windows Communication Foundation (WCF) bir talep tabanlı yetkilendirme mekanizması destekler. Talep varlığını temel alarak kaynaklara erişimine yanı sıra sistemleri genellikle talep varlığını temel alarak kaynaklara erişimini. Bu sistemlere incelemelisiniz <xref:System.IdentityModel.Policy.AuthorizationContext> erişimine izin verilmeden neden talepler için aramadan önce erişimlerin sonucunda talepler için.  
  
 Örneğin, bir sistem bir kaynağa erişimi olan herkes bir talep türü ile reddetmek, `Age`, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>ve kaynak değerini `Under 21` yalnızca kimliğini de talep türü olduğunda `Name`, sağ <xref:System.IdentityModel.Claims.Rights.Identity%2A>, Kaynak değerini `Mallory`. Başka bir deyişle, sistem erişim herkese altında 21 yaşında olduğunu ve Mallory adı şu olduğunda erişim verir reddeder. Bunu doğru şekilde uygulamak için anlamsal, aranacak önemlidir `Age` ilk talep ve yaşın altında 21 yaşında olup olmadığını belirler. Mallory altında 21 ise, aksi takdirde, ardından kaynak erişim yalnızca temeline göre verilebilir `Name` talep.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Talepler ve Belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
