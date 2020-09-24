---
title: Türü Genel IEnumerable Öğesine Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c2d34ae708f79d9f920679b3714a100fe8943c38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164421"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Türü Genel IEnumerable Öğesine Dönüştürme

<xref:System.Linq.Enumerable.AsEnumerable%2A>Genel olarak yazılmış bağımsız değişkeni döndürmek için kullanın `IEnumerable` .  
  
## <a name="example"></a>Örnek  

 Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (varsayılan genel kullanılarak `Query` ) sorguyu SQL 'e dönüştürmeye ve sunucuda yürütmeye çalışacaktır. Ancak `where` yan tümce, SQL 'e dönüştürülemeyen Kullanıcı tanımlı bir istemci tarafı yöntemine ( `isValidProduct` ) başvurur.  
  
 Çözüm, genel ' i değiştirmek için istemci tarafı genel <xref:System.Collections.Generic.IEnumerable%601> uygulamasını belirtmektir `where` <xref:System.Linq.IQueryable%601> . Bunu, işlecini çağırarak yapabilirsiniz <xref:System.Linq.Enumerable.AsEnumerable%2A> .  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
