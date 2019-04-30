---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleştirme (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: 84bd5f48c993dc5b15104b70081f739a1bec2e5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772131"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleştirme (LINQ to DataSet)
Birleştirme, birbiriyle gezilebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi veri kaynakları hedef sorgularda önemli bir işlemdir. İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağı ile bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerin ilişkidir. Daha fazla bilgi için [standart sorgu işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Join%2A> sorgu yöntemine bir <xref:System.Data.DataSet> yöntemi sorgu söz dizimini kullanarak.  
  
 `FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.  
  
 Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## <a name="join"></a>Birleştirme  
  
### <a name="example"></a>Örnek  
 Bu örnek üzerinde birleştirme gerçekleştirir `Contact` ve `SalesOrderHeader` tablolar.  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a>Örnek  
 Bu örnek üzerinde birleştirme gerçekleştirir `Contact` ve `SalesOrderHeader` sonuçlarına göre gruplandırma tablolar, bağlantı kimliği.  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’e Veri Yükleme](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [LINQ to DataSet Örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [Standart sorgu işleçlerine genel bakış (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Örnekleri katılın](https://go.microsoft.com/fwlink/?LinkId=187357)
- [Veri kümesi örnekleri](https://go.microsoft.com/fwlink/?LinkId=187358)
