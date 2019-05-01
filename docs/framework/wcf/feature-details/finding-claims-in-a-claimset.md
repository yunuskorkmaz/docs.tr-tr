---
title: ClaimSet için Beyan Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 42e6ee682220913f872da337eb41f6c290082988
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856433"
---
# <a name="finding-claims-in-a-claimset"></a>ClaimSet için Beyan Bulma
İçeriği İnceleme bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talep türlerinin genel talep tabanlı yetkilendirme kullanırken bir görevdir. İncelemek için bir <xref:System.IdentityModel.Claims.ClaimSet> belirli talepleri varlığını kullanan <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> yöntemi. Bu yöntem, doğrudan üzerinde yineleme daha iyi performans sağlar. <xref:System.IdentityModel.Claims.ClaimSet>. Aşağıdaki örnek, bu kullanımı gösterir. Unutmayın `claimType` ve `claimRight` parametreleri olabilir `null`. Bu durumda, parametrelerle eşleşen tüm talep türleri ve hak iddia.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
