---
title: 'Yöntem Tabanlı Sorgu Sözdizimi Örnekleri: Eleman Operatörleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: e43208d6ae524a1370b936d42508e9c7a7d196e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149513"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a>Yöntem Tabanlı Sorgu Sözdizimi Örnekleri: Eleman Operatörleri (LINQ to DataSet)
Bu konudaki örnekler, sorgu <xref:System.Linq.Enumerable.First%2A> ifadesi <xref:System.Linq.Enumerable.ElementAt%2A> sözdizimini <xref:System.Data.DataRow> <xref:System.Data.DataSet> kullanarak öğeleri almak için nasıl kullanılacağını ve yöntemleri gösterilmektedir.  
  
 Bu `FillDataSet` örneklerde kullanılan yöntem, [Veri Kümesine Veri Yükleme'de](loading-data-into-a-dataset.md)belirtilir.  
  
 Bu konudaki örnekler AdventureWorks örnek veritabanındaki İletişim, Adres, Ürün, SalesOrderHeader ve SalesOrderDetail tablolarını kullanır.  
  
 Bu konudaki örneklerde `using` / `Imports` aşağıdaki ifadeler kullanılır:  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 Daha fazla bilgi için [bkz: Visual Studio'da DataSet Project'e LINQ oluşturun.](how-to-create-a-linq-to-dataset-project-in-vs.md)  
  
## <a name="elementat"></a>Elementat  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.ElementAt%2A> beşinci adresi almak `PostalCode` için yöntem kullanır == "M4B 1V7".  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a>İlk  
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Enumerable.First%2A> ilk adı 'Brooke' olan ilk ilgili kişi dönmek için yöntemi kullanır.  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
