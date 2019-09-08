---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme Işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 3e2a72a2bb0921828bdd90fe437987fddfc995b5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783699"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="16d79-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme Işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="16d79-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="16d79-103">Bu konudaki örneklerde <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, ve <xref:System.Linq.Enumerable.ToList%2A> yöntemlerinin hemen bir sorgu ifadesini yürütmek için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="16d79-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="16d79-104">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="16d79-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="16d79-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16d79-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="16d79-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="16d79-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="16d79-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16d79-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="16d79-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="16d79-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="16d79-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="16d79-109">Example</span></span>  
 <span data-ttu-id="16d79-110">Bu örnek, <xref:System.Linq.Enumerable.ToArray%2A> bir diziyi bir diziye anında değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16d79-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="16d79-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="16d79-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="16d79-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="16d79-112">Example</span></span>  
 <span data-ttu-id="16d79-113">Bu örnek, <xref:System.Linq.Enumerable.ToDictionary%2A> bir diziyi ve ilgili anahtar ifadesini bir sözlüğe anında değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16d79-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="16d79-114">ToList</span><span class="sxs-lookup"><span data-stu-id="16d79-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="16d79-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="16d79-115">Example</span></span>  
 <span data-ttu-id="16d79-116">Bu örnek, bir <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Collections.Generic.List%601>diziyi ' ın ' de, nerede `T` tür <xref:System.Data.DataRow>olduğunu hemen değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16d79-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="16d79-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16d79-117">See also</span></span>

- [<span data-ttu-id="16d79-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="16d79-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="16d79-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="16d79-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="16d79-120">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="16d79-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="16d79-121">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16d79-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
