---
title: 'Yöntem temelli sorgu sözdizimi örnekler: Sıralama (LINQ-DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 9a5a518740191eac067550d35e936a6f4ff09710
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765366"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="9e966-102">Yöntem temelli sorgu sözdizimi örnekler: Sıralama (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="9e966-102">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="9e966-103">Bu konudaki örnekler nasıl kullanılacağını göstermektedir <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, ve <xref:System.Linq.Enumerable.ThenBy%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> ve yöntem sorgu sözdizimini kullanarak sonuçları sıralayın.</span><span class="sxs-lookup"><span data-stu-id="9e966-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="9e966-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="9e966-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="9e966-105">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e966-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9e966-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="9e966-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="9e966-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9e966-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="9e966-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="9e966-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="9e966-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e966-109">Example</span></span>  
 <span data-ttu-id="9e966-110">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> son adları büyük küçük harf duyarsız bir çeşit yapmak için özel bir karşılaştırıcı ile yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9e966-110">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="9e966-111">Ters Çevir</span><span class="sxs-lookup"><span data-stu-id="9e966-111">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="9e966-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e966-112">Example</span></span>  
 <span data-ttu-id="9e966-113">Bu örnekte <xref:System.Linq.Enumerable.Reverse%2A> listesini oluşturmak için yöntem siparişleri nereye `OrderDate` 20 Şub 2002'den daha eski.</span><span class="sxs-lookup"><span data-stu-id="9e966-113">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="9e966-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="9e966-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="9e966-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e966-115">Example</span></span>  
 <span data-ttu-id="9e966-116">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> ve <xref:System.Linq.Enumerable.ThenBy%2A> ilk için özel bir karşılaştırıcı yöntemleriyle sıralama fiyat listesi ve ürün adları büyük küçük harf duyarsız azalan sıralama gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="9e966-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="9e966-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e966-117">See Also</span></span>  
 [<span data-ttu-id="9e966-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="9e966-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="9e966-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="9e966-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="9e966-120">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9e966-120">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
