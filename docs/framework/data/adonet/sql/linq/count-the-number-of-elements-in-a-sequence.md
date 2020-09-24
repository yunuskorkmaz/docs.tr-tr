---
title: Dizideki Öğe Sayısını Sayma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: d983bc14f4fda04bda0a6f363db4c11f062c4c48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164356"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Dizideki Öğe Sayısını Sayma

<xref:System.Linq.Enumerable.Count%2A>Dizideki öğelerin sayısını saymak için işlecini kullanın.  
  
 Bu sorguyu Northwind örnek veritabanına karşı çalıştırmak bir çıktı üretir `91` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, veritabanındaki sayısını sayar `Customers` .  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, veritabanında Kullanımdan kaldırılmış olan ürünlerin sayısını sayar.  
  
 Bu örneği Northwind örnek veritabanına karşı çalıştırmak, çıkışı üretir `69` .  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplu Sorgular](aggregate-queries.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
