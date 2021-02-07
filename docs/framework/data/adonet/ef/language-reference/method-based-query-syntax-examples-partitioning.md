---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: bölümleme'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Bölümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 914dacb5b82b9ce452d4d1d7a97262de5803a9fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696691"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="f102f-103">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Bölümleme</span><span class="sxs-lookup"><span data-stu-id="f102f-103">Method-Based Query Syntax Examples: Partitioning</span></span>

<span data-ttu-id="f102f-104">Bu konudaki örneklerde <xref:System.Linq.Enumerable.Skip%2A> , <xref:System.Linq.Enumerable.Take%2A> sorgu ifadesi sözdizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f102f-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="f102f-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f102f-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f102f-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="f102f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="f102f-107">Atla</span><span class="sxs-lookup"><span data-stu-id="f102f-107">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="f102f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f102f-108">Example</span></span>  

 <span data-ttu-id="f102f-109">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Skip%2A> Ilgili kişi tablosunun ilk beş kişisiyle tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f102f-109">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="f102f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f102f-110">Example</span></span>  

 <span data-ttu-id="f102f-111">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Skip%2A> Seattle 'daki ilk iki adres hariç tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f102f-111">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="f102f-112">Take</span><span class="sxs-lookup"><span data-stu-id="f102f-112">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="f102f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f102f-113">Example</span></span>  

 <span data-ttu-id="f102f-114">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Take%2A> iletişim tablosundan yalnızca ilk beş kişiyi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f102f-114">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="f102f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f102f-115">Example</span></span>  

 <span data-ttu-id="f102f-116">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Take%2A> Seattle 'daki ilk üç adresi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f102f-116">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="f102f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f102f-117">See also</span></span>

- [<span data-ttu-id="f102f-118">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="f102f-118">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
