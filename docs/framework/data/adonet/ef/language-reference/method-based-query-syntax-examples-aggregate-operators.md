---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplu İşleçler'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: f8754101e7ec55fe5f9836300de1d077e1db2478
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192132"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a>Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Toplu İşleçler

Bu konudaki örneklerde,,,,, <xref:System.Linq.Enumerable.Aggregate%2A> <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.LongCount%2A> <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A> ve <xref:System.Linq.Enumerable.Sum%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir. Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.  
  
 Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a>Ortalama  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Average%2A> ürünlerin ortalama liste fiyatını bulmak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> stilin ürünlerinin ortalama liste fiyatını bulmak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Average%2A> süresi dolan ortalama toplamı bulmak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> kışı kimliği için Ortalama toplamı almak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Average%2A> kişi için ödenecek ortalama toplam olan siparişleri almak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a>Count  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> ürün tablosundaki ürünlerin sayısını döndürmek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Count%2A> Iletişim kimliklerinin bir listesini ve her birinin kaç tane siparişi olduğunu döndürmek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, ürünleri renge göre gruplandırır ve <xref:System.Linq.Enumerable.Count%2A> her renk grubundaki ürün sayısını döndürmek için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a>LongCount  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, iletişim sayısını uzun bir tamsayı olarak alır.  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a>En yüksek değer  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Max%2A> süresi dolan en büyük toplamı almak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> ILETIŞIM kimliği için en fazla toplamı almak üzere yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Max%2A> kışı kimliği için en büyük toplam olan siparişleri almak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a>Min  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Min%2A> süresi dolan en küçük toplamı almak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Min%2A> kışı kimliği için en küçük toplamı almak üzere yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Min%2A> her kişi için en küçük Toplam olan siparişleri almak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a>Toplam  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Sum%2A> SalesOrderDetail tablosundaki toplam sipariş miktarı sayısını almak için yöntemini kullanır.  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a>Örnek  

 Aşağıdaki örnek, her bir <xref:System.Linq.Enumerable.Sum%2A> ILETIŞIM kimliği için bir süre için bu yöntemi kullanır.  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
