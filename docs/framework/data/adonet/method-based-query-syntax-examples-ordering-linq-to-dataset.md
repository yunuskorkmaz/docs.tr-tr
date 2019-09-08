---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 16a37cb0bc36741ad816d2aa038a1390e3282d9b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794984"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama (LINQ to DataSet)
Bu konudaki örneklerde <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.ThenBy%2A> , veyöntemlerinin<xref:System.Linq.Enumerable.Reverse%2A>sorgu sözdiziminikullanaraksonuçlarısıralamakiçin,veyöntemlerininnasılkullanılacağıgösterilmektedir.<xref:System.Data.DataSet>  
  
 Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.  
  
 Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.  
  
## <a name="orderby"></a>OrderBy  
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Linq.Enumerable.OrderBy%2A> son adları büyük/küçük harfe duyarsız bir sıralama yapmak için özel bir karşılaştırıcı ile yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a>Tersini  
  
### <a name="example"></a>Örnek  
 Bu örnek, 20 <xref:System.Linq.Enumerable.Reverse%2A> Şubat 2002 ' den önceki bir `OrderDate` siparişlerin listesini oluşturmak için yöntemini kullanır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a>ThenBy  
  
### <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> , ilk <xref:System.Linq.Enumerable.ThenBy%2A> olarak liste fiyatına göre sıralama yapmak için özel bir karşılaştırıcı ile Yöntemler ve ardından ürün adları büyük/küçük harf duyarsız azalan sıralaması yapılır.  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart sorgu Işleçlerine genelC#bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
