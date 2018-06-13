---
title: 'Yöntem temelli sorgu sözdizimi örnekler: Küme işleci (LINQ-DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 2c95125182a352d3cd2b0b4c51ffac3f74fff5a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764820"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a>Yöntem temelli sorgu sözdizimi örnekler: Küme işleci (LINQ-DataSet)
Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, ve <xref:System.Linq.Enumerable.Union%2A> kümeleri veri satır değeri tabanlı karşılaştırma işlemleri gerçekleştirmek için işleçler.[ Veri içine bir veri kümesi yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md) bkz [karşılaştırma DataRow](../../../../docs/framework/data/adonet/comparing-datarows-linq-to-dataset.md) hakkında daha fazla bilgi için <xref:System.Data.DataRowComparer>.  
  
 `FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.  
  
 Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="distinct"></a>Distinct  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.Distinct%2A> yöntemi bir dizisinde yinelenen öğeleri kaldırın.  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a>Dışlama  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.Except%2A> ilk tabloda yer alan ancak ikinci görünür kişiler döndürülecek yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a>Kesiştir  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.Intersect%2A> her iki tabloda görünür kişiler döndürülecek yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a>UNION  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.Union%2A> benzersiz kişiler iki tablo birinden döndürülecek yöntemi.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet’e Veri Yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Standart Sorgu İşleçlerine Genel Bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
