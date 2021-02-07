---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: dönüştürme'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: 054ef9291a66216b14e2f03ecebd28fb24c6574d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696756"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="7f587-103">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="7f587-103">Method-Based Query Syntax Examples: Conversion</span></span>

<span data-ttu-id="7f587-104">Bu konudaki örneklerde <xref:System.Linq.Enumerable.ToArray%2A> , <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7f587-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="7f587-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="7f587-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7f587-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="7f587-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="7f587-107">ToArray</span><span class="sxs-lookup"><span data-stu-id="7f587-107">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="7f587-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f587-108">Example</span></span>  

 <span data-ttu-id="7f587-109">Aşağıdaki örnek, bir <xref:System.Linq.Enumerable.ToArray%2A> diziyi bir diziye anında değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f587-109">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="7f587-110">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="7f587-110">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="7f587-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f587-111">Example</span></span>  

 <span data-ttu-id="7f587-112">Aşağıdaki örnek, bir <xref:System.Linq.Enumerable.ToDictionary%2A> diziyi ve ilgili anahtar ifadesini bir sözlüğe anında değerlendirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f587-112">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="7f587-113">ToList</span><span class="sxs-lookup"><span data-stu-id="7f587-113">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="7f587-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f587-114">Example</span></span>  

 <span data-ttu-id="7f587-115">Aşağıdaki örnek, türünde olduğu <xref:System.Linq.Enumerable.ToList%2A> gibi bir diziyi öğesine hemen değerlendirmek için yöntemini kullanır <xref:System.Collections.Generic.List%601> `T` <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="7f587-115">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="7f587-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f587-116">See also</span></span>

- [<span data-ttu-id="7f587-117">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="7f587-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
