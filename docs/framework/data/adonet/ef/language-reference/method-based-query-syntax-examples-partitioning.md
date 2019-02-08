---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: Bölümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 181564de997e9a799aafa660a16b32a6ceb91d4a
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827165"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="0ddd9-102">Metot tabanlı sorgu söz dizimi örnekleri: Bölümleme</span><span class="sxs-lookup"><span data-stu-id="0ddd9-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="0ddd9-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Take%2A> sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0ddd9-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="0ddd9-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0ddd9-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0ddd9-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="0ddd9-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="0ddd9-106">Atla</span><span class="sxs-lookup"><span data-stu-id="0ddd9-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ddd9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ddd9-107">Example</span></span>  
 <span data-ttu-id="0ddd9-108">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Skip%2A> tüm almak için yöntemi ancak kişi tablonun ilk beş kişi.</span><span class="sxs-lookup"><span data-stu-id="0ddd9-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="0ddd9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ddd9-109">Example</span></span>  
 <span data-ttu-id="0ddd9-110">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Skip%2A> , ancak ilk iki adres Seattle tüm almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ddd9-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="0ddd9-111">Take</span><span class="sxs-lookup"><span data-stu-id="0ddd9-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ddd9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ddd9-112">Example</span></span>  
 <span data-ttu-id="0ddd9-113">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Take%2A> ilgili kişi tablosundan yalnızca ilk beş kişileri almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ddd9-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="0ddd9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ddd9-114">Example</span></span>  
 <span data-ttu-id="0ddd9-115">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Take%2A> Seattle ilk üç adresini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ddd9-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="0ddd9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ddd9-116">See also</span></span>
- [<span data-ttu-id="0ddd9-117">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="0ddd9-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
