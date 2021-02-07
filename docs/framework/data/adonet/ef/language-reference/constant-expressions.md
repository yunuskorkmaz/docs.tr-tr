---
description: 'Daha fazla bilgi edinin: sabit Ifadeler'
title: Sabit İfadeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 3c040918df4af6a0302d2435e3564e395044108e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724836"
---
# <a name="constant-expressions"></a>Sabit İfadeler

Sabit bir ifade sabit bir değerden oluşur. Sabit değerler, istemci üzerinde herhangi bir çeviri olmadan doğrudan sabit komut ağacı ifadelerine dönüştürülür. Bu, sabit bir değere neden olan ifadeleri içerir. Bu nedenle, sabitleri içeren tüm ifadeler için veri kaynağı davranışının beklenmelidir. Bu, CLR davranışından farklı davranışa neden olabilir.  
  
 Aşağıdaki örnek, sunucuda değerlendirilen sabit bir ifadeyi gösterir.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities, bir Kullanıcı sınıfının sabit olarak kullanılmasını desteklemez. Ancak, bir Kullanıcı sınıfındaki özellik başvurusu bir sabit kabul edilir ve bir komut ağacı sabit ifadesine dönüştürülür ve veri kaynağında yürütülür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)
