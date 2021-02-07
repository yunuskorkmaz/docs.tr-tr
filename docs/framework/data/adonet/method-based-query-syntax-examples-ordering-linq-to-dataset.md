---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: sıralama (LINQ to DataSet)'
title: 'Method-Based sorgu söz dizimi örnekleri: sıralama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: d655ff52fe30a9af15245a4c9989062107bb6842
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672666"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="663ed-103">Method-Based sorgu söz dizimi örnekleri: sıralama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="663ed-103">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>

<span data-ttu-id="663ed-104">Bu konudaki örneklerde <xref:System.Linq.Enumerable.OrderBy%2A> ,,  <xref:System.Linq.Enumerable.Reverse%2A> ve <xref:System.Linq.Enumerable.ThenBy%2A> yöntemlerinin sorgu <xref:System.Data.DataSet> söz dizimini kullanarak sonuçları sıralamak için, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="663ed-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="663ed-105">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="663ed-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="663ed-106">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="663ed-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="663ed-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="663ed-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="663ed-108">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="663ed-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="663ed-109">OrderBy</span><span class="sxs-lookup"><span data-stu-id="663ed-109">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="663ed-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="663ed-110">Example</span></span>  

 <span data-ttu-id="663ed-111">Bu örnek, <xref:System.Linq.Enumerable.OrderBy%2A> son adları büyük/küçük harfe duyarsız bir sıralama yapmak için özel bir karşılaştırıcı ile yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="663ed-111">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="663ed-112">Reverse</span><span class="sxs-lookup"><span data-stu-id="663ed-112">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="663ed-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="663ed-113">Example</span></span>  

 <span data-ttu-id="663ed-114">Bu örnek, <xref:System.Linq.Enumerable.Reverse%2A> `OrderDate` 20 Şubat 2002 ' den önceki bir siparişlerin listesini oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="663ed-114">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="663ed-115">ThenBy</span><span class="sxs-lookup"><span data-stu-id="663ed-115">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="663ed-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="663ed-116">Example</span></span>  

 <span data-ttu-id="663ed-117">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.ThenBy%2A> , ilk olarak liste fiyatına göre sıralama yapmak için özel bir karşılaştırıcı ile Yöntemler ve ardından ürün adları büyük/küçük harf duyarsız azalan sıralaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="663ed-117">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="663ed-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="663ed-118">See also</span></span>

- [<span data-ttu-id="663ed-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="663ed-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="663ed-120">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="663ed-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="663ed-121">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="663ed-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="663ed-122">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="663ed-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
