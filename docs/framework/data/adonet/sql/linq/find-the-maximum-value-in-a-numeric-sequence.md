---
description: 'Hakkında daha fazla bilgi: sayısal bir dizide en büyük değeri bulma'
title: Sayısal Dizideki En Büyük Değeri Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: ab311f29d776c1ef4647967d391c7e4122ae7d38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672107"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Sayısal Dizideki En Büyük Değeri Bulma

<xref:System.Linq.Enumerable.Max%2A>En yüksek değeri bir sayısal değer dizisinde bulmak için işlecini kullanın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, herhangi bir çalışan için en son işe alım tarihini bulur.  
  
 Bu sorguyu örnek Northwind veritabanında çalıştırırsanız, çıkış şu şekilde olur: `11/15/1994 12:00:00 AM` .  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, her bir ürün için Stoktaki en fazla birimi bulur.  
  
 Bu örneği örnek Northwind veritabanına karşı çalıştırırsanız, çıkış şu şekilde olur: `125` .  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Products` her kategoride en yüksek birim fiyata sahip olan öğesini bulmak Için Max kullanır. Daha sonra çıktı, sonuçları kategoriye göre listeler.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Önceki sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlarınız aşağıdakine benzeyecektir:  
  
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

- [Toplu Sorgular](aggregate-queries.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
