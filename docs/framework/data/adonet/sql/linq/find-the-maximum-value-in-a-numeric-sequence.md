---
title: "Bir sayısal sırada en büyük değeri Bul"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 387fe8db55da337b970bbac0e6e046b43433b482
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Bir sayısal sırada en büyük değeri Bul
Kullanım <xref:System.Linq.Enumerable.Max%2A> sayısal değerleri sırayla en yüksek değeri bulmak için işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm çalışanlar için işe alma son tarihi bulur.  
  
 Örnek Northwind veritabanına karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çoğu birimleri için herhangi bir ürün stok bulur.  
  
 Bu örnek örnek Northwind veritabanına karşı çalıştırırsanız çıktısı şöyledir: `125`.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bulmak için en çok kullandığı `Products` her kategoride en yüksek birim fiyat sahip. Çıkış, ardından sonuçları kategoriye göre listeler.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Northwind örnek veritabanı karşı önceki sorgu çalıştırırsanız, sonuçları şuna benzer:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Toplu Sorgular](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
