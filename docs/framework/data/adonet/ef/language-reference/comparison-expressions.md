---
title: "Karşılaştırma ifadeleri"
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
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e6865da677645a404e2116d1e7777106ed55223d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="comparison-expressions"></a>Karşılaştırma ifadeleri
Bir karşılaştırma ifadesi sabit değer, özellik değeri veya yöntem sonucu eşit değil eşit, daha büyük veya başka bir değerden daha az olup olmadığını denetler. Belirli bir karşılaştırma için geçerli değilse [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], bir özel durum. Örtük ve açık, tüm karşılaştırmaları veri kaynağındaki tüm bileşenleri karşılaştırılabilir gerektirir. Karşılaştırma ifadeleri sık kullanıldığı `Where` sorgu sonuçlarını kısıtlamak yan tümceleri.  
  
 Sorgu ifade sözdizimi aşağıdaki örnekte, sipariş numarası "SO43663" eşit olduğu sonuçları döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 Yöntem temelli sorgu söz dizimi aşağıdaki örnekte, sipariş numarası "SO43663" eşit olduğu sonuçları döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 Sorgu ifade sözdizimi aşağıdaki örnekte sunulduğundan 8 Temmuz 2001 için eşit olduğu Satış siparişi bilgileri döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 Yöntem temelli sorgu söz dizimi aşağıdaki örnekte sunulduğundan 8 Temmuz 2001 için eşit olduğu Satış siparişi bilgileri döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 Sunucuda, bir sabit sonucu veren ifadeler dönüştürülür ve yerel değerlendirme yapmak için herhangi bir deneme yapılır. Aşağıdaki örnek, bir ifade kullanır `Where` bir sabit verir yan tümcesi.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]bir kullanıcı sınıfı bir sabit değer olarak kullanılmasını desteklemez. Ancak, bir özellik referansı bir kullanıcı sınıfını bir sabit olarak kabul edilir ve komut ağacı sabit bir ifade için dönüştürülür ve veri kaynağı üzerinde yürütülür.  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 Bir sabit ifadesine döndüren yöntemler desteklenmez. Aşağıdaki örnek, bir yöntem içerir `Where` sabit bir değer döndürür yan tümcesi. Bu örnek, çalışma zamanında bir özel durum oluşturur.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
