---
description: "Hakkında daha fazla bilgi edinin: bir türü genel IEnumerable 'a dönüştürme"
title: Türü Genel IEnumerable Öğesine Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: 9be9022bce84808e18514937116ea962065dc1a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712525"
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
