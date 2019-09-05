---
title: Türü Genel IEnumerable Öğesine Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: c92f65c22fe4b4128a171c757bb9e9c0ccbc3fee
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247728"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Türü Genel IEnumerable Öğesine Dönüştürme
<xref:System.Linq.Enumerable.AsEnumerable%2A> Genel`IEnumerable`olarak yazılmış bağımsız değişkeni döndürmek için kullanın.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (varsayılan genel `Query`kullanılarak) sorguyu SQL 'e dönüştürmeye ve sunucuda yürütmeye çalışacaktır. Ancak yan tümce, SQL 'e dönüştürülemeyen Kullanıcı tanımlı bir istemci tarafı yöntemine`isValidProduct`() başvurur. `where`  
  
 Çözüm, genel <xref:System.Collections.Generic.IEnumerable%601> `where` 'ideğiştirmekiçinistemcitarafıgenel<xref:System.Linq.IQueryable%601>uygulamasını belirtmektir. Bunu, <xref:System.Linq.Enumerable.AsEnumerable%2A> işlecini çağırarak yapabilirsiniz.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
