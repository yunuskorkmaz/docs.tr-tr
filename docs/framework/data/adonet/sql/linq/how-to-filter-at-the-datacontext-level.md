---
title: 'Nasıl yapılır: DataContext Düzeyinde Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 343cffa9b1c034068e5abcc652e936f89ee6a992
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084589"
---
# <a name="how-to-filter-at-the-datacontext-level"></a>Nasıl yapılır: DataContext Düzeyinde Filtreleme
Filtre uygulayabilirsiniz `EntitySets` adresindeki `DataContext` düzeyi. İle yapılan tüm sorguları gibi filtreler uygulamak <xref:System.Data.Linq.DataContext> örneği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> müşteriler tarafından önceden yüklenmiş siparişleri filtrelemek üzere kullanılan `ShippedDate`.  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
