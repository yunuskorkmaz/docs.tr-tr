---
title: "Bir sayısal sırada en küçük değeri Bul"
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
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9cc16b09912cb9cc695fc350d9fd4530ea99e794
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a>Bir sayısal sırada en küçük değeri Bul
Kullanım <xref:System.Linq.Enumerable.Min%2A> sayısal değerleri dizisinden en düşük değer döndürmek için işleci.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, en düşük birim fiyatı tüm ürün bulur.  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `2.5000`.  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, en düşük herhangi bir sırada nakliye tutarını bulur.  
  
 Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `0.0200`.  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Min bulmak için kullanır. `Products` her kategoride en düşük birim fiyatı sahip. Çıktı kategoriye göre düzenlenmiş.  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 Northwind örnek veritabanı karşı önceki sorgu çalıştırırsanız, sonuçları şuna benzer:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Toplu Sorgular](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
