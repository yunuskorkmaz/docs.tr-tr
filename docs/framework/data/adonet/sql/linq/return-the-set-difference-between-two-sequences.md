---
title: İki sıranın arasında ayarlanmış farkı döndürür
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 282ec36a2ad489e77db9fb5b338d3189c3001f03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609037"
---
# <a name="return-the-set-difference-between-two-sequences"></a>İki sıranın arasında ayarlanmış farkı döndürür
Kullanım <xref:System.Linq.Queryable.Except%2A> iki dizileri arasında ayarlanmış farkı döndürülecek işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Except%2A> , tüm ülkeler bir dizisini döndürmek için `Customers` hangi yok, ancak canlı `Employees` Canlı.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemdir kümelerinde yalnızca iyi tanımlanmış. Semantiği multisets için tanımlı değil.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
