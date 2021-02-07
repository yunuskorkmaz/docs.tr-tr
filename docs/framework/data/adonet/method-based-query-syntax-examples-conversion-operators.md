---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: dönüştürme Işleçleri (LINQ to DataSet)'
title: 'Method-Based sorgu söz dizimi örnekleri: dönüştürme Işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 958e5c0ac1d1d8a98e6099ffcad055e78f07b23e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672744"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a>Method-Based sorgu söz dizimi örnekleri: dönüştürme Işleçleri (LINQ to DataSet)

Bu konudaki örneklerde <xref:System.Linq.Enumerable.ToArray%2A> ,, <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> yöntemlerinin hemen bir sorgu ifadesini yürütmek için nasıl kullanılacağı gösterilmektedir.  
  
 `FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.  
  
 Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="toarray"></a>ToArray  
  
### <a name="example"></a>Örnek  

 Bu örnek, bir <xref:System.Linq.Enumerable.ToArray%2A> diziyi bir diziye anında değerlendirmek için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a>ToDictionary  
  
### <a name="example"></a>Örnek  

 Bu örnek, bir <xref:System.Linq.Enumerable.ToDictionary%2A> diziyi ve ilgili anahtar ifadesini bir sözlüğe anında değerlendirmek için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a>ToList  
  
### <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Linq.Enumerable.ToList%2A> bir diziyi <xref:System.Collections.Generic.List%601> ' ın ' de, nerede tür olduğunu hemen değerlendirmek için yöntemini kullanır `T` <xref:System.Data.DataRow> .  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart sorgu Işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
