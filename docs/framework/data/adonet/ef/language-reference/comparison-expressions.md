---
title: Karşılaştırma İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: d92020f353393eee683e578f4306cd4a2f214152
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197852"
---
# <a name="comparison-expressions"></a>Karşılaştırma İfadeleri

Karşılaştırma ifadesi sabit bir değer, özellik değeri veya yöntem sonucunun eşit, eşit, büyük veya başka bir değerden küçük olup olmadığını denetler. Belirli bir karşılaştırma LINQ to Entities için geçerli değilse, bir özel durum oluşturulur. Örtülü ve açık olan tüm karşılaştırmalar, tüm bileşenlerin veri kaynağında karşılaştırılabilir olmasını gerektirir. `Where`Sorgu sonuçlarını kısıtlamak için yan tümcelerde Karşılaştırma ifadeleri sık kullanılır.  
  
 Sorgu ifadesi sözdiziminde aşağıdaki örnek, satış siparişi numarasının "SO43663" değerine eşit olduğu sonuçlara döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, satış siparişi numarasının "SO43663" değerine eşit olduğu sonuçlara döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 Sorgu ifadesi sözdiziminde aşağıdaki örnek, sevk tarihinin 8 Temmuz 2001 ' e eşit olduğu satış siparişi bilgilerini döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 Yöntem tabanlı sorgu sözdiziminde aşağıdaki örnek, sevk tarihinin 8 Temmuz 2001 ' e eşit olduğu satış siparişi bilgilerini döndüren bir sorgu gösterir:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 Bir sabit değer veren ifadeler sunucuda dönüştürülür ve yerel değerlendirme yapmaya yönelik bir girişim yapılmaz. Aşağıdaki örnek, `Where` bir sabiti veren yan tümcesinde bir ifade kullanır.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities, bir Kullanıcı sınıfının sabit olarak kullanılmasını desteklemez. Ancak, bir Kullanıcı sınıfındaki özellik başvurusu bir sabit kabul edilir ve bir komut ağacı sabit ifadesine dönüştürülür ve veri kaynağında yürütülür.  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 Sabit bir ifade döndüren yöntemler desteklenmez. Aşağıdaki örnek, `Where` bir sabiti döndüren yan tümcedeki bir yöntemi içerir. Bu örnek, çalışma zamanında bir özel durum oluşturur.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)
