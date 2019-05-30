---
title: İki Dizi Arasındaki Küme Farkını Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 5bb7d797ad2adc4374f7a10c11d66be69feeb7a1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380042"
---
# <a name="return-the-set-difference-between-two-sequences"></a>İki Dizi Arasındaki Küme Farkını Döndürme
Kullanım <xref:System.Linq.Queryable.Except%2A> iki dizileri arasında ayarlanmış farkı döndürülecek işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Except%2A> , tüm ülkeler/bölgeler bir dizisini döndürmek için `Customers` hangi yok, ancak canlı `Employees` Canlı.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemdir kümelerinde yalnızca iyi tanımlanmış. Semantiği multisets için tanımlı değil.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
