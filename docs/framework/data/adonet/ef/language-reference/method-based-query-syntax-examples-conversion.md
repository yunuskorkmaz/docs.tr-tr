---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: e2b5ae3b7c7733216f18914c497d080fe8d71a8e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192093"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="52c29-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="52c29-102">Method-Based Query Syntax Examples: Conversion</span></span>

<span data-ttu-id="52c29-103">Bu konudaki örneklerde <xref:System.Linq.Enumerable.ToArray%2A> , <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="52c29-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="52c29-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="52c29-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="52c29-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="52c29-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="52c29-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="52c29-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="52c29-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="52c29-107">Example</span></span>  

 <span data-ttu-id="52c29-108">Aşağıdaki örnek, bir <xref:System.Linq.Enumerable.ToArray%2A> diziyi bir diziye anında değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="52c29-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="52c29-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="52c29-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="52c29-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="52c29-110">Example</span></span>  

 <span data-ttu-id="52c29-111">Aşağıdaki örnek, bir <xref:System.Linq.Enumerable.ToDictionary%2A> diziyi ve ilgili anahtar ifadesini bir sözlüğe anında değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="52c29-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="52c29-112">ToList</span><span class="sxs-lookup"><span data-stu-id="52c29-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="52c29-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="52c29-113">Example</span></span>  

 <span data-ttu-id="52c29-114">Aşağıdaki örnek, türünde olduğu <xref:System.Linq.Enumerable.ToList%2A> gibi bir diziyi öğesine hemen değerlendirmek için yöntemini kullanır <xref:System.Collections.Generic.List%601> `T` <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="52c29-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="52c29-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c29-115">See also</span></span>

- [<span data-ttu-id="52c29-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="52c29-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
