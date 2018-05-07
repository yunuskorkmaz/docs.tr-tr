---
title: Bir dizisinde ilk öğesini döndürür
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: fd228b2d7534feca3cff49586ac0d43fbf9bcb1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="return-the-first-element-in-a-sequence"></a>Bir dizisinde ilk öğesini döndürür
Kullanım <xref:System.Linq.Enumerable.First%2A> işleci bir dizisinde ilk öğesini döndürür. Sorgular kullanan <xref:System.Linq.Enumerable.First%2A> hemen çalıştırılır.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteklemediği <xref:System.Linq.Enumerable.Last%2A> işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod ilk bulur `Shipper` bir tabloda:  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, sonuçları demektir.  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tek bulur `Customer` olan `CustomerID` BONAP.  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırırsanız, sonuçları olan `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
