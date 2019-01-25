---
title: 'Sorgu ifadesi söz dizimi örnekleri: Öğe işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: 8690e4ec79dbe4b728695b073299ca3d21e7f098
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632601"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="a2e0c-102">Sorgu ifadesi söz dizimi örnekleri: Öğe işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="a2e0c-102">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="a2e0c-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.First%2A> ve <xref:System.Linq.Enumerable.ElementAt%2A> almak için yöntemleri <xref:System.Data.DataRow> öğelerden bir <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a2e0c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="a2e0c-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="a2e0c-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="a2e0c-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2e0c-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a2e0c-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="a2e0c-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="a2e0c-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="a2e0c-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="a2e0c-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="a2e0c-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="a2e0c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2e0c-109">Example</span></span>  
 <span data-ttu-id="a2e0c-110">Bu örnekte <xref:System.Linq.Enumerable.ElementAt%2A> beşinci adresini almak için yöntemi burada `PostalCode` "M4B 1V7" ==.</span><span class="sxs-lookup"><span data-stu-id="a2e0c-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="a2e0c-111">ilk</span><span class="sxs-lookup"><span data-stu-id="a2e0c-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="a2e0c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2e0c-112">Example</span></span>  
 <span data-ttu-id="a2e0c-113">Bu örnekte <xref:System.Linq.Enumerable.First%2A> ilk kişinin ilk adı döndürülecek yöntemdir 'Brooke'.</span><span class="sxs-lookup"><span data-stu-id="a2e0c-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="a2e0c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e0c-114">See also</span></span>
- [<span data-ttu-id="a2e0c-115">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="a2e0c-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="a2e0c-116">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="a2e0c-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="a2e0c-117">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a2e0c-117">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
