---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 76bc4751a25e82a731e136f838d12b8d1c1d691f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119567"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="2cded-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Sıralama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="2cded-102">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="2cded-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, ve <xref:System.Linq.Enumerable.ThenBy%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve yöntem sorgu sözdizimini kullanarak sonuçları sıralayabilir.</span><span class="sxs-lookup"><span data-stu-id="2cded-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="2cded-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="2cded-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="2cded-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2cded-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2cded-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="2cded-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="2cded-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2cded-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="2cded-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="2cded-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="2cded-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cded-109">Example</span></span>  
 <span data-ttu-id="2cded-110">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> son adlarını büyük küçük harf duyarsız bir sıralama yapmak için özel bir karşılaştırıcı ile yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2cded-110">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="2cded-111">geriye doğru</span><span class="sxs-lookup"><span data-stu-id="2cded-111">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="2cded-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cded-112">Example</span></span>  
 <span data-ttu-id="2cded-113">Bu örnekte <xref:System.Linq.Enumerable.Reverse%2A> listesini oluşturmak için gereken yöntemini siparişleri nerede `OrderDate` 20 Şubat 2002 ' daha eski.</span><span class="sxs-lookup"><span data-stu-id="2cded-113">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="2cded-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="2cded-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="2cded-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2cded-115">Example</span></span>  
 <span data-ttu-id="2cded-116">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> ve <xref:System.Linq.Enumerable.ThenBy%2A> ilk için özel bir karşılaştırıcı yöntemleriyle liste fiyatı göre sıralayın ve ardından ürün adları büyük/küçük harfe azalan sıralama gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="2cded-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="2cded-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cded-117">See also</span></span>

- [<span data-ttu-id="2cded-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="2cded-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="2cded-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="2cded-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="2cded-120">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="2cded-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="2cded-121">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cded-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
