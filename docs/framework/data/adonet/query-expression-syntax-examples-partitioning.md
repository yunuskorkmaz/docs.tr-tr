---
title: 'Sorgu Ifadesi söz dizimi örnekleri: bölümleme (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: beb5f361-1ac8-44fb-afa1-2aacea15f166
ms.openlocfilehash: 9f907d16c78b550fbc11cc2cfad3c8249966a2f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189038"
---
# <a name="query-expression-syntax-examples-partitioning-linq-to-dataset"></a><span data-ttu-id="d2059-102">Sorgu Ifadesi söz dizimi örnekleri: bölümleme (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d2059-102">Query Expression Syntax Examples: Partitioning (LINQ to DataSet)</span></span>

<span data-ttu-id="d2059-103">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Linq.Enumerable.Take%2A> <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak bir sorgusu sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2059-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="d2059-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2059-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="d2059-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2059-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d2059-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="d2059-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="d2059-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d2059-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="d2059-108">Atla</span><span class="sxs-lookup"><span data-stu-id="d2059-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="d2059-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2059-109">Example</span></span>  

 <span data-ttu-id="d2059-110">Bu örnek, <xref:System.Linq.Enumerable.Skip%2A> Seattle 'daki ilk iki adres hariç tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d2059-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="d2059-111">Take</span><span class="sxs-lookup"><span data-stu-id="d2059-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="d2059-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2059-112">Example</span></span>  

 <span data-ttu-id="d2059-113">Bu örnek, <xref:System.Linq.Enumerable.Take%2A> Seattle 'daki ilk üç adresi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d2059-113">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="d2059-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2059-114">See also</span></span>

- [<span data-ttu-id="d2059-115">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="d2059-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="d2059-116">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="d2059-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="d2059-117">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="d2059-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d2059-118">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2059-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
