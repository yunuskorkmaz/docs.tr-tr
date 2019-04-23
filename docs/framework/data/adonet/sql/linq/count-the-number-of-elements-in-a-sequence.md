---
title: Dizideki Öğe Sayısını Sayma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: b39b0a1487c9f250e32b13330f2f70b7e3c7c877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209534"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Dizideki Öğe Sayısını Sayma
Kullanım <xref:System.Linq.Enumerable.Count%2A> işlecini bir dizideki öğelerin sayısı.  
  
 Bu sorgu, Northwind örnek veritabanına karşı çalışan bir çıktısı üretir `91`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sayısını sayar `Customers` veritabanında.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek veritabanındaki üretilmeyen ürünler sayar.  
  
 Bu örnek Northwind örnek veritabanına karşı çalıştırma, bir çıkış üretir `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Toplu Sorgular](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
