---
description: 'Hakkında daha fazla bilgi: Method-Based sorgu söz dizimi örnekleri: projeksiyon (LINQ to DataSet)'
title: 'Method-Based sorgu söz dizimi örnekleri: projeksiyon (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
ms.openlocfilehash: 380c35962ed122f5d4bbe85ba3fbd87cf7d7a3bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754387"
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a><span data-ttu-id="610fd-103">Method-Based sorgu söz dizimi örnekleri: projeksiyon (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="610fd-103">Method-Based Query Syntax Examples: Projection (LINQ to DataSet)</span></span>

<span data-ttu-id="610fd-104">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Select%2A> <xref:System.Linq.Enumerable.SelectMany%2A> <xref:System.Data.DataSet> yöntemi tabanlı sorgu söz dizimini kullanarak bir sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="610fd-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the method-based query syntax.</span></span>  
  
 <span data-ttu-id="610fd-105">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="610fd-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="610fd-106">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="610fd-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="610fd-107">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="610fd-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="610fd-108">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="610fd-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="610fd-109">Şunu seçin:</span><span class="sxs-lookup"><span data-stu-id="610fd-109">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="610fd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="610fd-110">Example</span></span>  

 <span data-ttu-id="610fd-111">Bu örnek,, <xref:System.Linq.Enumerable.Select%2A> `Name` `ProductNumber` ve `ListPrice` özelliklerini bir anonim türler dizisine eklemek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="610fd-111">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to project the `Name`, `ProductNumber`, and `ListPrice` properties to a sequence of anonymous types.</span></span>  <span data-ttu-id="610fd-112">`ListPrice`Özelliği de `Price` elde edilen türde olarak yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="610fd-112">The `ListPrice` property is also renamed to `Price` in the resulting type.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="610fd-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="610fd-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="610fd-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="610fd-114">Example</span></span>  

 <span data-ttu-id="610fd-115">Bu örnek, <xref:System.Linq.Enumerable.SelectMany%2A> `TotalDue` 500,00 ' den küçük olan tüm siparişleri seçmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="610fd-115">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="610fd-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="610fd-116">Example</span></span>  

 <span data-ttu-id="610fd-117">Bu örnek, <xref:System.Linq.Enumerable.SelectMany%2A> 1 ekim 2002 veya sonraki sürümlerde siparişin yapıldığı tüm siparişleri seçmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="610fd-117">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="610fd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="610fd-118">See also</span></span>

- [<span data-ttu-id="610fd-119">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="610fd-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="610fd-120">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="610fd-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="610fd-121">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="610fd-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="610fd-122">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="610fd-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
