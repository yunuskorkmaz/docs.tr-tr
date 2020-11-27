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
ms.openlocfilehash: c43a47b32a2a3c15d1a51b8b6931ebb021722a64
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268462"
---
# <a name="finding-claims-in-a-claimset"></a>ClaimSet için Beyan Bulma

<xref:System.IdentityModel.Claims.ClaimSet>Belirli bir talep türü için içeriğini incelemek, talep tabanlı yetkilendirme kullanılırken ortak bir görevdir. <xref:System.IdentityModel.Claims.ClaimSet>Belirli talepler hakkında bir durumu incelemek için <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> yöntemini kullanın. Bu yöntem doğrudan üzerinden yinelemekten daha iyi performans sağlar <xref:System.IdentityModel.Claims.ClaimSet> . Aşağıdaki örnekte bu kullanım gösterilmektedir. `claimType`Ve parametrelerinin olabileceğini unutmayın `claimRight` `null` . Bu durumda, parametreler tüm talep türleri ve talep haklarıyla eşleşir.  
  
## <a name="example"></a>Örnek  

 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md)
