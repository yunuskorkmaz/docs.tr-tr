---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: Küme işleci (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 75918450d3e08436578b1535316f19d2adf32695
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43476241"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a>Metot tabanlı sorgu söz dizimi örnekleri: Küme işleci (LINQ to DataSet)
Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, ve <xref:System.Linq.Enumerable.Union%2A> veri satırları kümelerinin değer tabanlı karşılaştırma işlemleri gerçekleştirmek için işleçleri.[ Verileri içine bir DataSet yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) bkz [DataRow karşılaştırma](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) hakkında daha fazla bilgi için <xref:System.Data.DataRowComparer>.  
  
 `FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.  
  
 Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için [nasıl yapılır: bir LINQ to DataSet proje Visual Studio'da oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="distinct"></a>Distinct  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.Distinct%2A> yöntemi bir dizideki yinelenen öğeleri kaldırın.  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a>Dışlama  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.Except%2A> görünen kişileri ilk tablonun ancak ikinci döndürmek için yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a>Kesiştir  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.Intersect%2A> her iki tabloda görünen kişileri döndürmek için yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a>UNION  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.Union%2A> benzersiz kişiler iki tablo birini döndürmek için yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet’e Veri Yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Standart Sorgu İşleçlerine Genel Bakış](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
