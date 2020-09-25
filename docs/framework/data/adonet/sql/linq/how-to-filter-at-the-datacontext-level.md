---
title: 'Nasıl yapılır: DataContext Düzeyinde Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 6fe79febd41c040e430dd772b87ca5624824bb65
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173477"
---
# <a name="how-to-filter-at-the-datacontext-level"></a>Nasıl yapılır: DataContext Düzeyinde Filtreleme

Düzeyinde filtre uygulayabilirsiniz `EntitySets` `DataContext` . Bu tür filtreler, bu örnekle yapılan tüm sorgular için geçerlidir <xref:System.Data.Linq.DataContext> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> müşterilere tarafından önceden yüklenmiş siparişleri filtrelemek için kullanılır `ShippedDate` .  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
