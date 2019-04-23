---
title: Dizideki İlk Öğeyi Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: dca917b3c12b0f9923cc9ea34a2568c412a09831
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081845"
---
# <a name="return-the-first-element-in-a-sequence"></a>Dizideki İlk Öğeyi Döndürme
Kullanım <xref:System.Linq.Enumerable.First%2A> işlecini bir dizideki ilk öğeyi döndürür. Sorgular kullanan <xref:System.Linq.Enumerable.First%2A> hemen çalıştırılır.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteklemediği <xref:System.Linq.Enumerable.Last%2A> işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod ilk bulur `Shipper` tabloda:  
  
 Northwind örnek veritabanına karşı bu sorguyu çalıştırmak, sonuçları vardır.  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tek bulur `Customer` olan `CustomerID` BONAP.  
  
 Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, sonuçları olan `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
