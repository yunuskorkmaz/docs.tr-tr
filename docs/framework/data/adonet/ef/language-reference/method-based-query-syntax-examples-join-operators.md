---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri'
description: LINQ to Entities içindeki Yöntem tabanlı sorgu söz dizimini kullanarak bir modeli sorgulamak için JOIN ve Groupjoın yöntemlerini nasıl kullanacağınızı öğrenmek için bu örnekleri kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 7f02379f4ececb75981ab262f22ebdeb510739ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191968"
---
# <a name="method-based-query-syntax-examples-join-operators"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Birleşim İşleçleri

Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir. Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a>GroupJoin  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.GroupJoin%2A> müşteri başına sipariş sayısını bulmak Için SalesOrderHeader ve SalesOrderDetail tabloları üzerinde bir yapar. Bir grup birleşimi, diğer veri kaynağında hiçbir bağıntılı öğe olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren sol dış birleştirmenin eşdeğeridir.  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, iletişim <xref:System.Linq.Enumerable.GroupJoin%2A> başına düşen sipariş sayısını bulmak Için Contact ve SalesOrderHeader tabloları üzerinde bir yapar. Her bir kişinin sıra sayısı ve kimlikleri görüntülenir.  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a>Birleştir  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, Contact ve SalesOrderHeader tabloları üzerinde bir JOIN uygular.  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, Contact ve SalesOrderHeader tabloları üzerinde bir JOIN gerçekleştirerek sonuçları ilgili kişi KIMLIĞINE göre gruplandırıyor.  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
