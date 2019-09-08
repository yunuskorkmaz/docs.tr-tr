---
title: Dizideki Öğeleri Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 21fa2f9e1dc2f255fe94f2420ba90a809ab5b05e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792668"
---
# <a name="sort-elements-in-a-sequence"></a>Dizideki Öğeleri Sıralama
Bir veya daha fazla anahtara göre bir diziyi sıralamak için işlecinikullanın.<xref:System.Linq.Enumerable.OrderBy%2A>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ve gibi basit temel türler `string` `int`tarafından sıralamayı destekleyecek şekilde tasarlanmıştır. Anonim türler gibi karmaşık çok değerli sınıfların sıralamasını desteklemez. Ayrıca, veri türlerini desteklemez `byte` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, işe `Employees` alma tarihine göre sıralanır.  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, nakliye `where` `London` tarafından sevk `Orders` edilen sıralama için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek birim fiyatına `Products` göre en yüksekten en düşüğe göre sıralanır.  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, şehir ve sonra `OrderBy` kişi adına `Customers` göre sıralamak için bir bileşik kullanır.  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `ShipCountry`, öğesinden ve daha `EmployeeID 1` sonra en düşük navlun için olan siparişleri sıralar.  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.GroupBy%2A>veişleçlerini birleştirerek, her kategoride en yüksek birim fiyatına sahip olanöğesinibulurvesonragrubukategorikimliğinegöresıralar.`Products`  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 Önceki sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar aşağıdakine benzeyecektir:  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
