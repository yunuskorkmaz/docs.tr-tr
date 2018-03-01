---
title: "Beyanlar ve Kaynaklara Erişimi Reddetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 156856ddd1a4c3b1d8f77a8a61f7e0336f993839
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="claims-and-denying-access-to-resources"></a>Beyanlar ve Kaynaklara Erişimi Reddetme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bir talep tabanlı yetkilendirme mekanizması destekler. Talep varlığını temel alarak kaynaklara erişimine yanı sıra sistemleri genellikle talep varlığını temel alarak kaynaklara erişimini. Bu sistemlere incelemelisiniz <xref:System.IdentityModel.Policy.AuthorizationContext> erişimine izin verilmeden neden talepler için aramadan önce erişimlerin sonucunda talepler için.  
  
 Örneğin, bir sistem bir kaynağa erişimi olan herkes bir talep türü ile reddetmek, `Age`, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>ve kaynak değerini `Under 21` yalnızca kimliğini de talep türü olduğunda `Name`, sağ <xref:System.IdentityModel.Claims.Rights.Identity%2A>, Kaynak değerini `Mallory`. Başka bir deyişle, sistem erişim herkese altında 21 yaşında olduğunu ve Mallory adı şu olduğunda erişim verir reddeder. Bunu doğru şekilde uygulamak için anlamsal, aranacak önemlidir `Age` ilk talep ve yaşın altında 21 yaşında olup olmadığını belirler. Mallory altında 21 ise, aksi takdirde, ardından kaynak erişim yalnızca temeline göre verilebilir `Name` talep.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Talepler ve Belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
