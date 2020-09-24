---
title: Sabit İfadeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 163f73a7682d444214caa213751cb35f8f0e8743
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153046"
---
# <a name="constant-expressions"></a>Sabit İfadeler

Sabit bir ifade sabit bir değerden oluşur. Sabit değerler, istemci üzerinde herhangi bir çeviri olmadan doğrudan sabit komut ağacı ifadelerine dönüştürülür. Bu, sabit bir değere neden olan ifadeleri içerir. Bu nedenle, sabitleri içeren tüm ifadeler için veri kaynağı davranışının beklenmelidir. Bu, CLR davranışından farklı davranışa neden olabilir.  
  
 Aşağıdaki örnek, sunucuda değerlendirilen sabit bir ifadeyi gösterir.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities, bir Kullanıcı sınıfının sabit olarak kullanılmasını desteklemez. Ancak, bir Kullanıcı sınıfındaki özellik başvurusu bir sabit kabul edilir ve bir komut ağacı sabit ifadesine dönüştürülür ve veri kaynağında yürütülür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)
