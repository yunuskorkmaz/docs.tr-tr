---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 8f09983aa90be666cc13ae4eba018db2ae706daa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760603"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="f9486-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="f9486-102">Method-Based Query Syntax Examples: Grouping</span></span>
<span data-ttu-id="f9486-103">Bu konudaki örnekler nasıl kullanılacağını size gösterir `GroupBy` sorgu yöntemine [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f9486-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="f9486-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f9486-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f9486-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="f9486-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="f9486-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9486-106">Example</span></span>  
 <span data-ttu-id="f9486-107">Aşağıdaki örnekte `GroupBy` döndürülecek yöntemi `Address` posta koduna göre gruplandırılan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f9486-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="f9486-108">Anonim bir tür yansıtılan sonuçları.</span><span class="sxs-lookup"><span data-stu-id="f9486-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="f9486-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9486-109">Example</span></span>  
 <span data-ttu-id="f9486-110">Aşağıdaki örnekte `GroupBy` döndürülecek yöntemi `Contact` kişinin soyadı ilk harfini tarafından gruplandırılmış olan nesneler.</span><span class="sxs-lookup"><span data-stu-id="f9486-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="f9486-111">Sonuçları da son adının ilk harfi sıralanır ve anonim bir tür yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="f9486-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="f9486-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9486-112">Example</span></span>  
 <span data-ttu-id="f9486-113">Aşağıdaki örnekte `GroupBy` döndürülecek yöntemi `SalesOrderHeader` müşteri kimliğine göre gruplandırılmış nesneleri</span><span class="sxs-lookup"><span data-stu-id="f9486-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="f9486-114">Ayrıca, her müşteri için satış sayısı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f9486-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f9486-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9486-115">See also</span></span>

- [<span data-ttu-id="f9486-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="f9486-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
