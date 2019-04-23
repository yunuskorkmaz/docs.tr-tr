---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Bölümleme (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 35c9c0346c84be7002800c8bf0c7e5eb8f1381e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116707"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="e6096-102">Sorgu İfadesi Söz Dizimi Örnekleri: Bölümleme (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="e6096-102">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>
<span data-ttu-id="e6096-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="e6096-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="e6096-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="e6096-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="e6096-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6096-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e6096-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="e6096-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="e6096-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e6096-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="e6096-108">Atla</span><span class="sxs-lookup"><span data-stu-id="e6096-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="e6096-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6096-109">Example</span></span>  
 <span data-ttu-id="e6096-110">Bu örnekte <xref:System.Linq.Enumerable.Skip%2A> , ancak ilk iki adres Seattle tüm almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6096-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="e6096-111">Take</span><span class="sxs-lookup"><span data-stu-id="e6096-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="e6096-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6096-112">Example</span></span>  
 <span data-ttu-id="e6096-113">Bu örnekte <xref:System.Linq.Enumerable.Take%2A> Seattle ilk üç adresini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6096-113">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="e6096-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6096-114">See also</span></span>

- [<span data-ttu-id="e6096-115">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="e6096-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="e6096-116">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e6096-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="e6096-117">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="e6096-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="e6096-118">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6096-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
