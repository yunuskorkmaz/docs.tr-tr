---
title: Dizideki Öğe Sayısını Sayma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 74e24aeb64b0097cba3975e76475034e6bb9544d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247699"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Dizideki Öğe Sayısını Sayma
Dizideki öğelerin sayısını saymak için işlecinikullanın.<xref:System.Linq.Enumerable.Count%2A>  
  
 Bu sorguyu Northwind örnek veritabanına karşı çalıştırmak bir çıktı `91`üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veritabanındaki sayısını `Customers` sayar.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veritabanında Kullanımdan kaldırılmış olan ürünlerin sayısını sayar.  
  
 Bu örneği Northwind örnek veritabanına karşı çalıştırmak, çıkışı `69`üretir.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplu Sorgular](aggregate-queries.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
