---
title: 'Sorgu ifadesi söz dizimi örnekleri: Bölümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: 24063d71326c432fcf16ba6924ed6d0963814d88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651155"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="80f52-102">Sorgu ifadesi söz dizimi örnekleri: Bölümleme</span><span class="sxs-lookup"><span data-stu-id="80f52-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="80f52-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="80f52-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="80f52-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="80f52-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="80f52-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="80f52-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="80f52-106">Atla</span><span class="sxs-lookup"><span data-stu-id="80f52-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="80f52-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="80f52-107">Example</span></span>  
 <span data-ttu-id="80f52-108">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Skip%2A> , ancak ilk iki adres Seattle tüm almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80f52-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="80f52-109">Take</span><span class="sxs-lookup"><span data-stu-id="80f52-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="80f52-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="80f52-110">Example</span></span>  
 <span data-ttu-id="80f52-111">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Take%2A> Seattle ilk üç adresini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80f52-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="80f52-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80f52-112">See also</span></span>
- [<span data-ttu-id="80f52-113">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="80f52-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
