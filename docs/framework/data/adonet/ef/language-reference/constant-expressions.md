---
title: Sabit ifadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: c9d4fa345f708ab5997b03e4e9726875d041ca21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565949"
---
# <a name="constant-expressions"></a>Sabit ifadeleri
Sabit bir ifade bir sabit değerini içerir. Sabit değerleri, sabit komut ağaç ifadeleri, istemcideki herhangi bir çeviri olmadan doğrudan dönüştürülür. Bu, bir sabit değer ifadeleri içerir. Bu nedenle, veri kaynağı davranışı sabitleri içeren tüm ifadeler için beklenmelidir. Bu CLR davranışından farklıdır davranışa neden olabilir.  
  
 Aşağıdaki örnek, sunucu üzerinde değerlendirilen sabit bir ifade gösterir.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Kullanıcı sınıfı bir sabit olarak kullanma desteği olmamasıdır. Ancak, bir kullanıcı sınıfta bir özellik başvurusu bir sabit olarak kabul edilir ve bir komut ağacı sabit ifade dönüştürülür ve veri kaynağında yürütülen.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to Entities Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
