---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: dönüştürme'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: 054ef9291a66216b14e2f03ecebd28fb24c6574d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696756"
---
# <a name="method-based-query-syntax-examples-conversion"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme

Bu konudaki örneklerde <xref:System.Linq.Enumerable.ToArray%2A> , <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir. Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a>ToArray  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir <xref:System.Linq.Enumerable.ToArray%2A> diziyi bir diziye anında değerlendirmek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a>ToDictionary  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir <xref:System.Linq.Enumerable.ToDictionary%2A> diziyi ve ilgili anahtar ifadesini bir sözlüğe anında değerlendirmek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a>ToList  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, türünde olduğu <xref:System.Linq.Enumerable.ToList%2A> gibi bir diziyi öğesine hemen değerlendirmek için yöntemini kullanır <xref:System.Collections.Generic.List%601> `T` <xref:System.Data.DataRow> .  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
