---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: Dönüşüm işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 7fb9a6c7cfd891e6a4384f081992a6b185951931
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688239"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="ed6d9-102">Metot tabanlı sorgu söz dizimi örnekleri: Dönüşüm işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="ed6d9-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="ed6d9-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, ve <xref:System.Linq.Enumerable.ToList%2A> hemen bir sorgu ifadesini yürütmek için yöntemler.</span><span class="sxs-lookup"><span data-stu-id="ed6d9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="ed6d9-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ed6d9-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="ed6d9-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed6d9-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ed6d9-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="ed6d9-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="ed6d9-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ed6d9-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="ed6d9-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="ed6d9-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="ed6d9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed6d9-109">Example</span></span>  
 <span data-ttu-id="ed6d9-110">Bu örnekte <xref:System.Linq.Enumerable.ToArray%2A> hemen bir sıralı bir dizi içine değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="ed6d9-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="ed6d9-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="ed6d9-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="ed6d9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed6d9-112">Example</span></span>  
 <span data-ttu-id="ed6d9-113">Bu örnekte <xref:System.Linq.Enumerable.ToDictionary%2A> hemen bir dizisi ve ilişkili bir anahtar ifadesi bir sözlükte değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="ed6d9-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="ed6d9-114">ToList</span><span class="sxs-lookup"><span data-stu-id="ed6d9-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="ed6d9-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed6d9-115">Example</span></span>  
 <span data-ttu-id="ed6d9-116">Bu örnekte <xref:System.Linq.Enumerable.ToList%2A> hemen bir dizisi olarak değerlendirmek için bir yöntem bir <xref:System.Collections.Generic.List%601>burada `T` türünde <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="ed6d9-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="ed6d9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed6d9-117">See also</span></span>
- [<span data-ttu-id="ed6d9-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="ed6d9-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="ed6d9-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ed6d9-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="ed6d9-120">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ed6d9-120">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
