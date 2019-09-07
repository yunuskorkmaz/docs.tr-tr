---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Bölümlendirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
ms.openlocfilehash: 168fea5ffe6b8fbb4c08b95578beebbdee171c9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398485"
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="93c56-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="93c56-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="93c56-103">Bu konudaki örneklerde <xref:System.Linq.Enumerable.Skip%2A>, sorgu ifadesi sözdizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak <xref:System.Linq.Enumerable.Take%2A> için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="93c56-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="93c56-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="93c56-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="93c56-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="93c56-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="93c56-106">Atla</span><span class="sxs-lookup"><span data-stu-id="93c56-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="93c56-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="93c56-107">Example</span></span>  
 <span data-ttu-id="93c56-108">Aşağıdaki örnek, ilgili kişi <xref:System.Linq.Enumerable.Skip%2A> tablosunun ilk beş kişisiyle tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93c56-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="93c56-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="93c56-109">Example</span></span>  
 <span data-ttu-id="93c56-110">Aşağıdaki örnek, Seattle 'daki <xref:System.Linq.Enumerable.Skip%2A> ilk iki adres hariç tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93c56-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="93c56-111">Take</span><span class="sxs-lookup"><span data-stu-id="93c56-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="93c56-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="93c56-112">Example</span></span>  
 <span data-ttu-id="93c56-113">Aşağıdaki örnek, iletişim tablosundan <xref:System.Linq.Enumerable.Take%2A> yalnızca ilk beş kişiyi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93c56-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="93c56-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="93c56-114">Example</span></span>  
 <span data-ttu-id="93c56-115">Aşağıdaki örnek, Seattle 'daki <xref:System.Linq.Enumerable.Take%2A> ilk üç adresi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93c56-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="93c56-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93c56-116">See also</span></span>

- [<span data-ttu-id="93c56-117">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="93c56-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
