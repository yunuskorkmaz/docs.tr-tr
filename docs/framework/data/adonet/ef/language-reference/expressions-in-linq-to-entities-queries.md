---
title: LINQ to Entities sorgularında ifadelerinde
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: dccf3ab1a619222cdf2db54673718eb103aee2fb
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331728"
---
# <a name="expressions-in-linq-to-entities-queries"></a>LINQ to Entities sorgularında ifadelerinde
Tek değer, nesne, yöntemi veya ad alanı için değerlendirilen kodun bir parçasını ifadesidir. Değişmez değer, bir yöntem çağrısı, bir işleci ve işlenenleri veya basit bir ad ifadeleri içerebilir. Basit adları bir değişken, tür üyesi, yöntem parametresi, ad alanı veya tür adı olabilir. İfadeler sırayla parametreleri veya diğer sırayla yöntem çağrılarını parametreleri olan yöntem çağrıları diğer ifadeler kullanan işleçlerini kullanabilirsiniz. Bu nedenle, ifadeleri basitten çok karmaşık değişebilir.  
  
 İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu ifadeleri içerebilir türler tarafından izin verilen herhangi bir şey <xref:System.Linq.Expressions> ad alanı, lambda ifadeleri de dahil olmak üzere. Kullanılabilir ifadeler [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgulardır kullanılabilir ifadeler kümesi için sorgu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Sorguları parçası olan ifadeleri [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] tarafından desteklenen operations sınırlıdır `ObjectQuery<T>` ve temel alınan veri kaynağı.  
  
 Aşağıdaki örnekte, Karşılaştırmada `Where` yan tümcesi ise bir ifade:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Belirli dil yapılarını, C# gibi `unchecked`, hiçbir anlamı olmayan [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sabit İfadeler](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Karşılaştırma İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Null Karşılaştırmalar](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Başlatma İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Gezinti özellikleri](https://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
