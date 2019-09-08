---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Projeksiyon (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
ms.openlocfilehash: 6617531c8a236eb034e6a063b7a1530c02d6e37b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794815"
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Projeksiyon (LINQ to DataSet)
Bu konudaki örneklerde, yöntemi tabanlı sorgu söz dizimini kullanarak <xref:System.Linq.Enumerable.Select%2A> bir <xref:System.Linq.Enumerable.SelectMany%2A> <xref:System.Data.DataSet> sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.  
  
 Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.  
  
 Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.  
  
## <a name="select"></a>Seçim  
  
### <a name="example"></a>Örnek  
 <xref:System.Linq.Enumerable.Select%2A> Bu örnek `Name`, ,`ProductNumber`ve özelliklerinibiranonimtürlerdizisineeklemek`ListPrice` için yöntemini kullanır.  Özelliği de elde edilen türde olarak `Price` yeniden adlandırılır. `ListPrice`  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a>SelectMany  
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Enumerable.SelectMany%2A> 500,00 ' den küçük `TotalDue` olan tüm siparişleri seçmek için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Enumerable.SelectMany%2A> 1 Ekim 2002 veya sonraki sürümlerde siparişin yapıldığı tüm siparişleri seçmek için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart sorgu Işleçlerine genelC#bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
