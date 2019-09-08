---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: JOIN Işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
ms.openlocfilehash: c150cb14c567590daa7ffb2ea77893598977bdf9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794868"
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a>Sorgu İfadesi Söz Dizimi Örnekleri: JOIN Işleçleri (LINQ to DataSet)
Birleştirme, ilişkisel veritabanı tabloları gibi birbirleriyle gezinebilir ilişki bulunmayan veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir. İki veri kaynağının birleşimi, bir veri kaynağındaki nesnelerin diğer veri kaynağında ortak bir özniteliği paylaşan nesneler ile ilişkilendirilmesi olur. Daha fazla bilgi için bkz. [Standart sorgu işleçlerineC#genel bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçleri genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Bu konudaki örneklerde, sorgu ifadesi söz dizimini kullanarak bir <xref:System.Linq.Enumerable.GroupJoin%2A> <xref:System.Data.DataSet> sorgusu <xref:System.Linq.Enumerable.Join%2A> sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.  
  
 Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.  
  
 Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.  
  
## <a name="groupjoin"></a>GroupJoin  
  
### <a name="example"></a>Örnek  
 Bu örnek, `SalesOrderHeader` müşteri <xref:System.Linq.Enumerable.GroupJoin%2A> başına sipariş sayısını `SalesOrderDetail` bulmak için ve tabloları üzerinde bir gerçekleştirir. Bir grup birleşimi, diğer veri kaynağında hiçbir bağıntılı öğe olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren sol dış birleştirmenin eşdeğeridir.  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a>Örnek  
 Bu örnek, `Contact` ve <xref:System.Linq.Enumerable.GroupJoin%2A> `SalesOrderHeader` tabloları üzerinde bir yapar. Bir grup birleşimi, diğer veri kaynağında hiçbir bağıntılı öğe olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren sol dış birleştirmenin eşdeğeridir.  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a>Birleştirme  
  
### <a name="example"></a>Örnek  
 Bu örnek, `SalesOrderHeader` Ağustos ayına ait çevrimiçi siparişleri `SalesOrderDetail` almak için ve tabloları üzerinde bir JOIN işlemini gerçekleştirir.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart sorgu Işleçlerine genelC#bakış ()](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
