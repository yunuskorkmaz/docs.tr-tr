---
title: Dizideki Öğeleri Sıralama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: b594e756b099aa94e1043fd4256da3eff46d0d95
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155763"
---
# <a name="sort-elements-in-a-sequence"></a>Dizideki Öğeleri Sıralama

Bir <xref:System.Linq.Enumerable.OrderBy%2A> veya daha fazla anahtara göre bir diziyi sıralamak için işlecini kullanın.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , ve gibi basit temel türler tarafından sıralamayı destekleyecek şekilde tasarlanmıştır `string` `int` . Anonim türler gibi karmaşık çok değerli sınıfların sıralamasını desteklemez. Ayrıca, `byte` veri türlerini desteklemez.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Employees` işe alma tarihine göre sıralanır.  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `where` `Orders` nakliye tarafından sevk edilen sıralama için kullanır `London` .  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek `Products` birim fiyatına göre en yüksekten en düşüğe göre sıralanır.  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `OrderBy` `Customers` şehir ve sonra kişi adına göre sıralamak için bir bileşik kullanır.  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek `EmployeeID 1` `ShipCountry` , öğesinden ve daha sonra en düşük navlun Için olan siparişleri sıralar.  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek,, <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.Max%2A> ve işleçlerini birleştirerek, <xref:System.Linq.Enumerable.GroupBy%2A> `Products` her kategoride en yüksek birim fiyatına sahip olan öğesini bulur ve sonra grubu kategori kimliğine göre sıralar.  
  
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

- [Sorgu örnekleri](query-examples.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
