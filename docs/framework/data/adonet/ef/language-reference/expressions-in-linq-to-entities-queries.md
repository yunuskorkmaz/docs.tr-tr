---
title: LINQ to Entities sorgu ifadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: f9230e9b5ac0c906652c03111b82df5147267143
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="expressions-in-linq-to-entities-queries"></a>LINQ to Entities sorgu ifadeleri
Tek değer, nesne, yöntemi veya ad alanı için değerlendirilen kodunun bir parçası olan bir ifadedir. İfade, bir hazır değer, bir yöntem çağrısı, bir işleç ve işlenenleri veya basit bir ad içerebilir. Basit adları bir değişken, türü üyesinin, yöntem parametresi, ad alanı veya türü adı olabilir. İfadeler sırayla diğer ifadeleri parametreleri veya yöntem çağrılarını sırayla diğer yöntem çağrıları, parametreleridir olarak kullanma işleçleri kullanabilirsiniz. Bu nedenle, ifadeler basitten için çok karmaşık aralığında değişebilir.  
  
 İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorguları, ifadeleri içerebilir içinde türlerden tarafından izin verilen herhangi bir şey <xref:System.Linq.Expressions> lambda ifadeleri de dahil olmak üzere ad alanı. Kullanılabilir ifadeleri [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorguları kullanılabilir ifadeler bir alt kümesi olan sorguya [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Sorguları parçası olan bir ifade [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] tarafından desteklenen işlemler sınırlıdır `ObjectQuery<T>` ve temel alınan veri kaynağı.  
  
 Aşağıdaki örnekte, buna karşılık `Where` yan tümcesi olan bir ifade:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Belirli bir dil yapıları, C# gibi `unchecked`, hiçbir anlamı sahip [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sabit İfadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Karşılaştırma İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Null Karşılaştırmalar](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Başlatma İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Gezinti özellikleri](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
