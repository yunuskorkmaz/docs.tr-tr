---
title: "Beyanlar ve Kaynaklara Erişimi Reddetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b94c8b77cd659438ec26129137dd9b8cab056b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="claims-and-denying-access-to-resources"></a>Beyanlar ve Kaynaklara Erişimi Reddetme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bir talep tabanlı yetkilendirme mekanizması destekler. Talep varlığını temel alarak kaynaklara erişimine yanı sıra sistemleri genellikle talep varlığını temel alarak kaynaklara erişimini. Bu sistemlere incelemelisiniz <xref:System.IdentityModel.Policy.AuthorizationContext> erişimine izin verilmeden neden talepler için aramadan önce erişimlerin sonucunda talepler için.  
  
 Örneğin, bir sistem bir kaynağa erişimi olan herkes bir talep türü ile reddetmek, `Age`, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>ve kaynak değerini `Under 21` yalnızca kimliğini de talep türü olduğunda `Name`, sağ <xref:System.IdentityModel.Claims.Rights.Identity%2A>, Kaynak değerini `Mallory`. Başka bir deyişle, sistem erişim herkese altında 21 yaşında olduğunu ve Mallory adı şu olduğunda erişim verir reddeder. Bunu doğru şekilde uygulamak için anlamsal, aranacak önemlidir `Age` ilk talep ve yaşın altında 21 yaşında olup olmadığını belirler. Mallory altında 21 ise, aksi takdirde, ardından kaynak erişim yalnızca temeline göre verilebilir `Name` talep.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Beyanlar ve belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
