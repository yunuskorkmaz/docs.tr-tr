---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Işleç ayarlama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 481c0ed7e39b8f958ccdae01e4589d54b3ff2446
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783582"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Işleç ayarlama (LINQ to DataSet)
Bu konudaki örneklerde, veri satırı kümelerinde değer tabanlı karşılaştırma <xref:System.Linq.Enumerable.Distinct%2A>işlemleri <xref:System.Linq.Enumerable.Except%2A>gerçekleştirmek <xref:System.Linq.Enumerable.Intersect%2A>için, <xref:System.Linq.Enumerable.Union%2A> , ve işleçlerinin nasıl kullanılacağı gösterilmektedir.[ Veri kümesine veri yükleme](loading-data-into-a-dataset.md) hakkında <xref:System.Data.DataRowComparer>daha fazla bilgi Için bkz. [DataRow karşılaştırması](comparing-datarows-linq-to-dataset.md) .  
  
 Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.  
  
 Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.  
  
## <a name="distinct"></a>Distinct  
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Enumerable.Distinct%2A> bir dizideki yinelenen öğeleri kaldırmak için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a>Dışlama  
  
### <a name="example"></a>Örnek  
 Bu örnek, ilk <xref:System.Linq.Enumerable.Except%2A> tabloda görünen ancak ikincide olmayan kişileri döndürmek için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a>Kesiştir  
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Enumerable.Intersect%2A> her iki tabloda görünen kişileri döndürmek için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a>UNION  
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Enumerable.Union%2A> iki tablodan birindeki benzersiz kişileri döndürmek için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart sorgu Işleçlerine genelC#bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
