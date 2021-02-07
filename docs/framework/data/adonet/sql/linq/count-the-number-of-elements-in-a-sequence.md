---
description: 'Hakkında daha fazla bilgi edinin: dizideki öğelerin sayısını sayma'
title: Dizideki Öğe Sayısını Sayma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 91030516098e900229a1e131ea0c9a7d8bef4034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663085"
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
