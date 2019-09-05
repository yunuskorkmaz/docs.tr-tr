---
title: LINQ to Entities Sorgu İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 5262d2bca07525aba6db5303e730c8b358641d52
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250979"
---
# <a name="expressions-in-linq-to-entities-queries"></a>LINQ to Entities Sorgu İfadeleri
Bir ifade, tek bir değer, nesne, yöntem veya ad alanı olarak değerlendirilebilen kodun bir parçadır. İfadeler bir değişmez değer, bir yöntem çağrısı, bir işleç ve işlenenleri veya basit bir ad içerebilir. Basit adlar bir değişkenin adı, tür üyesi, yöntem parametresi, ad alanı veya tür olabilir. İfadeler, diğer ifadeleri parametre olarak kullanan işleçler veya parametreleri diğer Yöntem çağrılarını aç içinde olan Yöntem çağrıları ' nı kullanabilir. Bu nedenle, ifadeler basit ve çok karmaşık olarak değişebilir.  
  
 LINQ to Entities sorgularda, ifadeler, lambda ifadeleri dahil olmak üzere <xref:System.Linq.Expressions> ad alanı içindeki türlerin izin verdiği her şeyi içerebilir. LINQ to Entities sorgularında kullanılabilecek ifadeler, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]sorgulamak için kullanılabilen ifadelerin bir üst kümesidir.  Üzerinde sorguların parçası olan ifadeler, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] tarafından `ObjectQuery<T>` desteklenen işlemlerle ve temel alınan veri kaynağıyla sınırlıdır.  
  
 Aşağıdaki örnekte, `Where` yan tümcesindeki karşılaştırma bir ifadedir:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> Gibi belirli dil yapıları C# `unchecked`LINQ to Entities bir anlamı yoktur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sabit İfadeler](constant-expressions.md)  
  
 [Karşılaştırma İfadeleri](comparison-expressions.md)  
  
 [Null Karşılaştırmalar](null-comparisons.md)  
  
 [Başlatma İfadeleri](initialization-expressions.md)  
  
 [İlişkiler, gezinti özellikleri ve yabancı anahtarlar](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../index.md)
