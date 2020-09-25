---
title: 'Yöntem tabanlı sorgu söz dizimi örnekleri: JOIN (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 8bfcd8ae5d81c0d04ca7a43e6d5b25a492266605
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189350"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a>Yöntem tabanlı sorgu söz dizimi örnekleri: JOIN (LINQ to DataSet)

Birleştirme, ilişkisel veritabanı tabloları gibi birbirleriyle gezinebilir ilişki bulunmayan veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir. İki veri kaynağının birleşimi, bir veri kaynağındaki nesnelerin diğer veri kaynağında ortak bir özniteliği paylaşan nesneler ile ilişkilendirilmesi olur. Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Bu konudaki örneklerde, yönteminin <xref:System.Linq.Enumerable.Join%2A> <xref:System.Data.DataSet> sorgu söz dizimini kullanarak sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.  
  
 `FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.  
  
 Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="join"></a>Birleştir  
  
### <a name="example"></a>Örnek  

 Bu örnek, ve tabloları üzerinde bir JOIN gerçekleştirir `Contact` `SalesOrderHeader` .  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a>Örnek  

 Bu örnek, ve tabloları üzerinde bir JOIN gerçekleştirerek `Contact` `SalesOrderHeader` sonuçları ılgılı kişi kimliğine göre gruplandırıyor.  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](linq-to-dataset-examples.md)
- [Standart sorgu Işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Örneklere katılarak](https://go.microsoft.com/fwlink/?LinkId=187357)
- [Veri kümesi örnekleri](https://go.microsoft.com/fwlink/?LinkId=187358)
