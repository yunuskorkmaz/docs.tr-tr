---
title: Dizideki İlk Öğeyi Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 4506ef1a79c8f7e77160df4d55d0f93ee79f5a41
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200348"
---
# <a name="return-the-first-element-in-a-sequence"></a>Dizideki İlk Öğeyi Döndürme

<xref:System.Linq.Enumerable.First%2A>Bir dizideki ilk öğeyi döndürmek için işlecini kullanın. Kullanan sorgular <xref:System.Linq.Enumerable.First%2A> hemen yürütülür.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Linq.Enumerable.Last%2A>işlecini desteklemez.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, bir tabloda birincni bulur `Shipper` :  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `Customer` priap 'ye sahip olan tekli bulur `CustomerID` .  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar olur `ID = BONAP, Contact = Laurence Lebihan` .  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
