---
title: 'Sorgu İfadesi Sözdizimi Örnekleri: Kısıtlama (DATASet için LINQ)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 6ec4eac6c0fb2d044e429e88d50c619aa38de4b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149199"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a>Sorgu İfadesi Sözdizimi Örnekleri: Kısıtlama (DATASet için LINQ)
Bu konudaki örnekler, sorgu <xref:System.Linq.Enumerable.Where%2A> ifadesi sözdizimini kullanarak bir <xref:System.Data.DataSet> sorgu yöntemini nasıl kullanacağımı gösterir.  
  
 Bu `FillDataSet` örneklerde kullanılan yöntem, [Veri Kümesine Veri Yükleme'de](loading-data-into-a-dataset.md)belirtilir.  
  
 Bu konudaki örnekler AdventureWorks örnek veritabanındaki İletişim, Adres, Ürün, SalesOrderHeader ve SalesOrderDetail tablolarını kullanır.  
  
 Bu konudaki örneklerde `using` / `Imports` aşağıdaki ifadeler kullanılır:  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 Daha fazla bilgi için [bkz: Visual Studio'da DataSet Project'e LINQ oluşturun.](how-to-create-a-linq-to-dataset-project-in-vs.md)  
  
## <a name="where"></a>Konum  
  
### <a name="example"></a>Örnek  
 Bu örnek tüm çevrimiçi siparişleri döndürür.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a>Örnek  
 Bu örnek, sipariş miktarının 2'den büyük ve 6'dan küçük olduğu siparişleri döndürür.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a>Örnek  
 Bu örnek, tüm kırmızı renkli ürünleri döndürür.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Enumerable.Where%2A> 1 Aralık 2002'den sonra yapılan siparişleri <xref:System.Data.DataRow.GetChildRows%2A> bulmak için yöntemi kullanır ve sonra her siparişiçin ayrıntıları almak için yöntemi kullanır.  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
