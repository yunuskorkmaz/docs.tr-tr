---
title: Dizideki İlk Öğeyi Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 9faeed754942d7b176872484ac776c1df592bbd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792716"
---
# <a name="return-the-first-element-in-a-sequence"></a>Dizideki İlk Öğeyi Döndürme
Bir dizideki ilk öğeyi döndürmek için işlecinikullanın.<xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.First%2A> Kullanan sorgular hemen yürütülür.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Linq.Enumerable.Last%2A> işlecini desteklemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir tabloda birincni `Shipper` bulur:  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `CustomerID` priap 'ye `Customer` sahip olan tekli bulur.  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar olur `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
