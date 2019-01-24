---
title: Karşılaştırma ifadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: cca909e67464d08c0bb4ff8a0d0186d9d600ce18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596351"
---
# <a name="comparison-expressions"></a>Karşılaştırma ifadeleri
Bir karşılaştırma ifadesi bir sabit değeri, özellik değeri veya yöntem sonucu eşit, değil eşittir, büyüktür veya başka bir değerden daha az olup olmadığını denetler. Belirli bir karşılaştırma için geçerli değilse [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], bir özel durum oluşturulur. Örtük ve açık, tüm karşılaştırmalar, veri kaynağındaki tüm bileşenleri karşılaştırılabilir olmalarını gerektirir. Karşılaştırma ifadeleri sık sık kullanılır `Where` sorgu sonuçları kısıtlamak için yan tümceler.  
  
 Sorgu ifadesi söz dizimi aşağıdaki örnekte sipariş numarası "SO43663 için" eşit olduğu sonuçları döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 Metot tabanlı sorgu söz dizimi aşağıdaki örnekte sipariş numarası "SO43663 için" eşit olduğu sonuçları döndüren bir sorguyu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 Sorgu ifadesi söz dizimi aşağıdaki örnekte, satış siparişi bilgileri kullanıma sunulduğundan 8 Temmuz 2001 için eşit olduğu döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 Metot tabanlı sorgu söz dizimi aşağıdaki örnekte, satış siparişi bilgileri kullanıma sunulduğundan 8 Temmuz 2001 için eşit olduğu döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 Bir sabit yield deyimleri sunucuda dönüştürülür ve yerel değerlendirmesi yapmak girişimi gerçekleştirilir. Aşağıdaki örnek, bir ifadede kullanır `Where` sabit verir yan tümcesi.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Kullanıcı sınıfı bir sabit olarak kullanma desteği olmamasıdır. Ancak, bir kullanıcı sınıfta bir özellik başvurusu bir sabit olarak kabul edilir ve bir komut ağacı sabit ifade dönüştürülür ve veri kaynağında yürütülen.  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 Sabit bir ifade döndüren yöntemler desteklenmez. Aşağıdaki örnek, bir yöntem içerir `Where` sabit bir değer döndüren yan tümcesi. Bu örnek, çalışma zamanında bir özel durum oluşturur.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to Entities Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
