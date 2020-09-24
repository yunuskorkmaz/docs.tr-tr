---
title: Sayısal Dizideki En Küçük Değeri Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: 2ffff8b69839d5c1e70e81f9fc6f3a97f57ac6c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155984"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a>Sayısal Dizideki En Küçük Değeri Bulma

<xref:System.Linq.Enumerable.Min%2A>Bir sayısal değer dizisinden en küçük değeri döndürmek için işlecini kullanın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, herhangi bir ürünün en düşük birim fiyatını bulur.  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `2.5000` .  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek herhangi bir sipariş için en düşük navlun miktarını bulur.  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `0.0200` .  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Products` her kategoride en düşük birim fiyatına sahip olan öğesini bulmak Için min kullanır. Çıktı kategoriye göre düzenlenir.  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 Önceki sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlarınız aşağıdakine benzeyecektir:  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplu Sorgular](aggregate-queries.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
