---
title: 'Yöntem tabanlı sorgu söz dizimi örnekleri: projeksiyon (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
ms.openlocfilehash: 2790ed3e7f8fc2fe6a5c920be8a79402692d6282
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147911"
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a><span data-ttu-id="7275e-102">Yöntem tabanlı sorgu söz dizimi örnekleri: projeksiyon (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7275e-102">Method-Based Query Syntax Examples: Projection (LINQ to DataSet)</span></span>

<span data-ttu-id="7275e-103">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Select%2A> <xref:System.Linq.Enumerable.SelectMany%2A> <xref:System.Data.DataSet> yöntemi tabanlı sorgu söz dizimini kullanarak bir sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7275e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the method-based query syntax.</span></span>  
  
 <span data-ttu-id="7275e-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7275e-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7275e-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7275e-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7275e-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="7275e-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7275e-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7275e-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="7275e-108">Şunu seçin:</span><span class="sxs-lookup"><span data-stu-id="7275e-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="7275e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7275e-109">Example</span></span>  

 <span data-ttu-id="7275e-110">Bu örnek,, <xref:System.Linq.Enumerable.Select%2A> `Name` `ProductNumber` ve `ListPrice` özelliklerini bir anonim türler dizisine eklemek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7275e-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to project the `Name`, `ProductNumber`, and `ListPrice` properties to a sequence of anonymous types.</span></span>  <span data-ttu-id="7275e-111">`ListPrice`Özelliği de `Price` elde edilen türde olarak yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7275e-111">The `ListPrice` property is also renamed to `Price` in the resulting type.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="7275e-112">SelectMany</span><span class="sxs-lookup"><span data-stu-id="7275e-112">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="7275e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7275e-113">Example</span></span>  

 <span data-ttu-id="7275e-114">Bu örnek, <xref:System.Linq.Enumerable.SelectMany%2A> `TotalDue` 500,00 ' den küçük olan tüm siparişleri seçmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7275e-114">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="7275e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="7275e-115">Example</span></span>  

 <span data-ttu-id="7275e-116">Bu örnek, <xref:System.Linq.Enumerable.SelectMany%2A> 1 ekim 2002 veya sonraki sürümlerde siparişin yapıldığı tüm siparişleri seçmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7275e-116">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7275e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7275e-117">See also</span></span>

- [<span data-ttu-id="7275e-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="7275e-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="7275e-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="7275e-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="7275e-120">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="7275e-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7275e-121">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7275e-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
