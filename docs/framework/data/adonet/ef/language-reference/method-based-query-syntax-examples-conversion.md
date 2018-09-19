---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: 5f1ef8680bc6826f4e8b1beb1e49fce3a15c40c9
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45987714"
---
# <a name="method-based-query-syntax-examples-conversion"></a>Metot tabanlı sorgu söz dizimi örnekleri: dönüştürme
Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) metot tabanlı sorgu söz dizimini kullanarak. Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.  
  
 Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a>ToArray  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Linq.Enumerable.ToArray%2A> hemen bir sıralı bir dizi içine değerlendirmek için bir yöntem.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a>ToDictionary  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Linq.Enumerable.ToDictionary%2A> hemen bir dizisi ve ilişkili bir anahtar ifadesi bir sözlükte değerlendirmek için bir yöntem.  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a>ToList  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Linq.Enumerable.ToList%2A> hemen bir dizisi olarak değerlendirmek için bir yöntem bir <xref:System.Collections.Generic.List%601>burada `T` türünde <xref:System.Data.DataRow>.  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
