---
title: 'Yöntem temelli sorgu sözdizimi örnekler: Projeksiyon (LINQ-DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
ms.openlocfilehash: 5887ae58c142cb4c1835599e6a7b34bf200d7071
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a><span data-ttu-id="13fcf-102">Yöntem temelli sorgu sözdizimi örnekler: Projeksiyon (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="13fcf-102">Method-Based Query Syntax Examples: Projection (LINQ to DataSet)</span></span>
<span data-ttu-id="13fcf-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> yöntemi tabanlı sorgu sözdizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="13fcf-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the method-based query syntax.</span></span>  
  
 <span data-ttu-id="13fcf-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="13fcf-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="13fcf-105">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="13fcf-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="13fcf-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="13fcf-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="13fcf-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="13fcf-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="13fcf-108">Seçim</span><span class="sxs-lookup"><span data-stu-id="13fcf-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="13fcf-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="13fcf-109">Example</span></span>  
 <span data-ttu-id="13fcf-110">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> yöntemi projesine `Name`, `ProductNumber`, ve `ListPrice` anonim türleri dizisi özellikleri.</span><span class="sxs-lookup"><span data-stu-id="13fcf-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to project the `Name`, `ProductNumber`, and `ListPrice` properties to a sequence of anonymous types.</span></span>  <span data-ttu-id="13fcf-111">`ListPrice` Özelliği için yeniden de `Price` sonuç türü.</span><span class="sxs-lookup"><span data-stu-id="13fcf-111">The `ListPrice` property is also renamed to `Price` in the resulting type.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="13fcf-112">SelectMany</span><span class="sxs-lookup"><span data-stu-id="13fcf-112">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="13fcf-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="13fcf-113">Example</span></span>  
 <span data-ttu-id="13fcf-114">Bu örnek kullanır <xref:System.Linq.Enumerable.SelectMany%2A> tümünü seçmek için yöntemi siparişleri where `TotalDue` değerinden 500,00 değil.</span><span class="sxs-lookup"><span data-stu-id="13fcf-114">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="13fcf-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="13fcf-115">Example</span></span>  
 <span data-ttu-id="13fcf-116">Bu örnekte <xref:System.Linq.Enumerable.SelectMany%2A> burada sırasını yapıldı 1 Ekim 2002 veya sonraki sürümlerde tüm siparişleri seçmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="13fcf-116">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="13fcf-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13fcf-117">See Also</span></span>  
 [<span data-ttu-id="13fcf-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="13fcf-118">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="13fcf-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="13fcf-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="13fcf-120">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="13fcf-120">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
