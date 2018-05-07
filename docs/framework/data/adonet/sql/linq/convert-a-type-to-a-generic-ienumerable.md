---
title: Bir tür için genel bir IEnumerable Dönüştür
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: e1d8036dd7ef4e1f59e2af46ac101135c39ef0c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Bir tür için genel bir IEnumerable Dönüştür
Kullanım <xref:System.Linq.Enumerable.AsEnumerable%2A> genel yazılan bağımsız değişkenini döndürmesine izin `IEnumerable`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (genel varsayılan kullanarak `Query`) SQL sorgu dönüştürmek ve sunucuda yürütmek isteriz. Ancak `where` yan tümcesinde başvuruda bulunan bir kullanıcı tarafından tanımlanan istemci-tarafı yöntemi (`isValidProduct`), hangi dönüştürülemiyor SQL.  
  
 İstemci-tarafı genel belirtmek için çözümdür <xref:System.Collections.Generic.IEnumerable%601> uyarlamasını `where` genel değiştirmek için <xref:System.Linq.IQueryable%601>. Harekete geçirerek bunu <xref:System.Linq.Enumerable.AsEnumerable%2A> işleci.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
