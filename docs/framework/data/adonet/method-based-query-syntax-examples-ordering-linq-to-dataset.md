---
title: 'Yöntem tabanlı sorgu söz dizimi örnekleri: sıralama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 635b7f6e498e27ef8ca2e133df639f1010184a93
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197878"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a>Yöntem tabanlı sorgu söz dizimi örnekleri: sıralama (LINQ to DataSet)

Bu konudaki örneklerde <xref:System.Linq.Enumerable.OrderBy%2A> ,,  <xref:System.Linq.Enumerable.Reverse%2A> ve <xref:System.Linq.Enumerable.ThenBy%2A> yöntemlerinin sorgu <xref:System.Data.DataSet> söz dizimini kullanarak sonuçları sıralamak için, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.  
  
 `FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.  
  
 Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="orderby"></a>OrderBy  
  
### <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Linq.Enumerable.OrderBy%2A> son adları büyük/küçük harfe duyarsız bir sıralama yapmak için özel bir karşılaştırıcı ile yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a>Reverse  
  
### <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Linq.Enumerable.Reverse%2A> `OrderDate` 20 Şubat 2002 ' den önceki bir siparişlerin listesini oluşturmak için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Örnek  

 Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.ThenBy%2A> , ilk olarak liste fiyatına göre sıralama yapmak için özel bir karşılaştırıcı ile Yöntemler ve ardından ürün adları büyük/küçük harf duyarsız azalan sıralaması yapılır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart sorgu Işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
