---
title: İki Dizinin Küme Kesişimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 3458ebf8f5708496eef6246fa55cf528e8a32bc4
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380067"
---
# <a name="return-the-set-intersection-of-two-sequences"></a>İki Dizinin Küme Kesişimini Döndürme
Kullanım <xref:System.Linq.Queryable.Intersect%2A> işlecini iki dizinin küme kesişimini döndürür.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Intersect%2A> hangi ikisinde tüm ülkeler/bölgeler bir dizisini döndürmek için `Customers` ve `Employees` Canlı.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> işlemdir kümelerinde yalnızca iyi tanımlanmış. Semantiği multisets için tanımlı değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
