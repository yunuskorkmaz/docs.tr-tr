---
title: Sabit İfadeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: cc3a214a2faa06c79ee0794b0158381bff0c4b0b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539894"
---
# <a name="constant-expressions"></a>Sabit İfadeler
Sabit bir ifade bir sabit değerini içerir. Sabit değerleri, sabit komut ağaç ifadeleri, istemcideki herhangi bir çeviri olmadan doğrudan dönüştürülür. Bu, bir sabit değer ifadeleri içerir. Bu nedenle, veri kaynağı davranışı sabitleri içeren tüm ifadeler için beklenmelidir. Bu CLR davranışından farklıdır davranışa neden olabilir.  
  
 Aşağıdaki örnek, sunucu üzerinde değerlendirilen sabit bir ifade gösterir.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities kullanıcı sınıfı bir sabit olarak kullanma desteği olmamasıdır. Ancak, bir kullanıcı sınıfta bir özellik başvurusu bir sabit olarak kabul edilir ve bir komut ağacı sabit ifade dönüştürülür ve veri kaynağında yürütülen.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
