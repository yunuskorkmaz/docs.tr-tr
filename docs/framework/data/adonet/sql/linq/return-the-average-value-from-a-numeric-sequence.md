---
title: Sayısal dizisinden ortalama değerini döndürür
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 3e808b836183a23fa6bd80faeb0d3cfc5921f4cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358862"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a>Sayısal dizisinden ortalama değerini döndürür
<xref:System.Linq.Enumerable.Average%2A> İşleci hesaplar sayısal değerleri dizisi ortalaması.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Çevrilmesi `Average` değerler tamsayı hesaplanan bir çift olarak değil bir tamsayı olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ortalamasını döndürür `Freight` değerler `Orders` tablo.  
  
 Örnek Northwind veritabanı sonuçlarından olacaktır `78.2442`.  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm birim fiyat ortalamasını döndürür `Products` içinde `Products` tablo.  
  
 Örnek Northwind veritabanı sonuçlarından olacaktır `28.8663`.  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Average` bulmak için işleci `Products` olan birim fiyat ait kategorisinin ortalama birim fiyat daha yüksek. Örnek sonuçları grupları görüntüler.  
  
 Bu örnek kullanımı gerektirdiğini unutmayın `var` C# anahtar sözcüğü dönüş türü anonim olduğundan.  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırırsanız, sonuçları aşağıdaki benzemelidir:  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Toplu Sorgular](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
