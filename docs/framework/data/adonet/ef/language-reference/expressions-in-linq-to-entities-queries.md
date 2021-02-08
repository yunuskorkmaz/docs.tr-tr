---
description: 'Daha fazla bilgi edinin: LINQ to Entities sorgulardaki Ifadeler'
title: LINQ to Entities Sorgu İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 3ab9e04adb7e823538638ae262f0e481b6948a24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786374"
---
# <a name="expressions-in-linq-to-entities-queries"></a>LINQ to Entities Sorgu İfadeleri

Bir ifade, tek bir değer, nesne, yöntem veya ad alanı olarak değerlendirilebilen kodun bir parçadır. İfadeler bir değişmez değer, bir yöntem çağrısı, bir işleç ve işlenenleri veya basit bir ad içerebilir. Basit adlar bir değişkenin adı, tür üyesi, yöntem parametresi, ad alanı veya tür olabilir. İfadeler, diğer ifadeleri parametre olarak kullanan işleçler veya parametreleri diğer Yöntem çağrılarını aç içinde olan Yöntem çağrıları ' nı kullanabilir. Bu nedenle, ifadeler basit ve çok karmaşık olarak değişebilir.  
  
 LINQ to Entities sorgularda, ifadeler, <xref:System.Linq.Expressions> lambda ifadeleri dahil olmak üzere ad alanı içindeki türlerin izin verdiği her şeyi içerebilir. LINQ to Entities sorgularda kullanılabilecek ifadeler, Entity Framework sorgulamak için kullanılabilecek ifadelerin bir üst kümesidir. Entity Framework göre sorguların parçası olan Ifadeler, tarafından desteklenen işlemlerle `ObjectQuery<T>` ve temel alınan veri kaynağıyla sınırlıdır.  
  
 Aşağıdaki örnekte, `Where` yan tümcesindeki karşılaştırma bir ifadedir:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> C# gibi belirli dil yapıları LINQ to Entities bir `unchecked` anlamı yoktur.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Sabit Ifadeler](constant-expressions.md)  
  
 [Karşılaştırma Ifadeleri](comparison-expressions.md)  
  
 [Null Karşılaştırmalar](null-comparisons.md)  
  
 [Başlatma İfadeleri](initialization-expressions.md)  
  
 [İlişkiler, gezinti özellikleri ve yabancı anahtarlar](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](../index.md)
