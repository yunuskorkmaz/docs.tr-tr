---
title: "ClaimSet için Beyan Bulma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21a30833e72b1c87f1c65a3deaa44da48c08336e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="finding-claims-in-a-claimset"></a>ClaimSet için Beyan Bulma
İçeriği inceleyerek bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talep türlerinin bir ortak talep tabanlı yetkilendirme kullanırken bir görevdir. İncelemek için bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talepleri varlığını kullanmak <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> yöntemi. Bu yöntem doğrudan üzerinde yineleme daha iyi performans sağlar <xref:System.IdentityModel.Claims.ClaimSet>. Aşağıdaki örnek, bu kullanımını gösterir. Unutmayın `claimType` ve `claimRight` parametreleri olabilir `null`. Bu durumda, parametreleri tüm talep türleri eşleşen ve hakları talep.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
