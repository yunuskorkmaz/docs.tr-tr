---
title: Sayısal Diziden Ortalama Değer Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 1f113a475bb350640aef7a6b4d7a70b32509d1e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200413"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a>Sayısal Diziden Ortalama Değer Döndürme

<xref:System.Linq.Enumerable.Average%2A>İşleci bir sayısal değer dizisinin ortalamasını hesaplar.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Average` Tamsayı değerlerinin çevirisi, Double olarak değil, tamsayı olarak hesaplanır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek `Freight` tablodaki değerlerin ortalamasını döndürür `Orders` .  
  
 Örnek Northwind veritabanının sonuçları olacaktır `78.2442` .  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, tablosundaki tüm birim fiyatının ortalamasını döndürür `Products` `Products` .  
  
 Örnek Northwind veritabanının sonuçları olacaktır `28.8663` .  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Average` `Products` birim fiyatının ait olduğu kategorinin ortalama birim fiyatından daha yüksek olan olanları bulmak için işlecini kullanır. Örnek, sonuçları gruplar halinde görüntüler.  
  
 Bu örnek, `var` dönüş türü anonim olduğundan, C# dilinde anahtar sözcüğünün kullanılmasını gerektirdiğini unutmayın.  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar aşağıdakine benzemelidir:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplu Sorgular](aggregate-queries.md)
