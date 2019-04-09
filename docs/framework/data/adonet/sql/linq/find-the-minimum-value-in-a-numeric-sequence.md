---
title: Sayısal Dizideki En Küçük Değeri Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: 84002609c550cc2de76f9948bf77f9fd88261f64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136727"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a>Sayısal Dizideki En Küçük Değeri Bulma
Kullanım <xref:System.Linq.Enumerable.Min%2A> en düşük değer dizisini sayısal değerler döndürülecek işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, en düşük birim fiyatı üründeki bulur.  
  
 Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, çıktı şu şekildedir: `2.5000`.  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek herhangi bir sırada için en düşük freight miktarını bulur.  
  
 Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, çıktı şu şekildedir: `0.0200`.  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Min bulmak için kullanır. `Products` her kategoride en düşük birim fiyatı vardır. Kategoriye göre düzenlenmiş çıktı.  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 Northwind örnek veritabanıyla önceki sorguyu çalıştırırsanız, sonuçlar şuna benzer:  
  
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

- [Toplu Sorgular](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
