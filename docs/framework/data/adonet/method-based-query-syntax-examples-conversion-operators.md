---
title: 'Yöntem tabanlı sorgu söz dizimi örnekleri: dönüştürme Işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: b3c746f715f40f4c134185fa0cf8e6e115e0067b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164655"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="144ba-102">Yöntem tabanlı sorgu söz dizimi örnekleri: dönüştürme Işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="144ba-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="144ba-103">Bu konudaki örneklerde <xref:System.Linq.Enumerable.ToArray%2A> ,, <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> yöntemlerinin hemen bir sorgu ifadesini yürütmek için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="144ba-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="144ba-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="144ba-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="144ba-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="144ba-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="144ba-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="144ba-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="144ba-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="144ba-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="144ba-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="144ba-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="144ba-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="144ba-109">Example</span></span>  

 <span data-ttu-id="144ba-110">Bu örnek, bir <xref:System.Linq.Enumerable.ToArray%2A> diziyi bir diziye anında değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="144ba-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="144ba-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="144ba-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="144ba-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="144ba-112">Example</span></span>  

 <span data-ttu-id="144ba-113">Bu örnek, bir <xref:System.Linq.Enumerable.ToDictionary%2A> diziyi ve ilgili anahtar ifadesini bir sözlüğe anında değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="144ba-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="144ba-114">ToList</span><span class="sxs-lookup"><span data-stu-id="144ba-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="144ba-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="144ba-115">Example</span></span>  

 <span data-ttu-id="144ba-116">Bu örnek, <xref:System.Linq.Enumerable.ToList%2A> bir diziyi <xref:System.Collections.Generic.List%601> ' ın ' de, nerede tür olduğunu hemen değerlendirmek için yöntemini kullanır `T` <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="144ba-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="144ba-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="144ba-117">See also</span></span>

- [<span data-ttu-id="144ba-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="144ba-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="144ba-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="144ba-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="144ba-120">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="144ba-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="144ba-121">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="144ba-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
