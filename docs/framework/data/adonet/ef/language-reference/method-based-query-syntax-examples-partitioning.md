---
title: "Yöntem temelli sorgu sözdizimi örnekleri: bölümlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b7b64874-c3c8-4bdb-862c-89a168d07827
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8c88e8c853c43c40950089b538ebf44b6d5a67aa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-partitioning"></a><span data-ttu-id="337f7-102">Yöntem temelli sorgu sözdizimi örnekleri: bölümlendirme</span><span class="sxs-lookup"><span data-stu-id="337f7-102">Method-Based Query Syntax Examples: Partitioning</span></span>
<span data-ttu-id="337f7-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Take%2A> sorgulamak için yöntemleri [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="337f7-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="337f7-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="337f7-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="337f7-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="337f7-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="337f7-106">Atla</span><span class="sxs-lookup"><span data-stu-id="337f7-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="337f7-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="337f7-107">Example</span></span>  
 <span data-ttu-id="337f7-108">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Skip%2A> tüm almak için yöntemi ancak ilk beş kişiler ilgili kişi tablosu.</span><span class="sxs-lookup"><span data-stu-id="337f7-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP L2E Examples#SkipSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="337f7-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="337f7-109">Example</span></span>  
 <span data-ttu-id="337f7-110">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Skip%2A> tüm almak için yöntemi ancak ilk iki adres Seattle'da.</span><span class="sxs-lookup"><span data-stu-id="337f7-110">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="337f7-111">Take</span><span class="sxs-lookup"><span data-stu-id="337f7-111">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="337f7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="337f7-112">Example</span></span>  
 <span data-ttu-id="337f7-113">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Take%2A> ilgili kişi tablosundan yalnızca ilk beş kişileri almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="337f7-113">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the Contact table.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP L2E Examples#TakeSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="337f7-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="337f7-114">Example</span></span>  
 <span data-ttu-id="337f7-115">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Take%2A> ilk üç adres Seattle almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="337f7-115">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="337f7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="337f7-116">See Also</span></span>  
 [<span data-ttu-id="337f7-117">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="337f7-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
