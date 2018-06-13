---
title: 'Yöntem temelli sorgu sözdizimi örnekleri: dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: 6ca770f067a3086f021cd87e226f66716b39e595
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763260"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="559f3-102">Yöntem temelli sorgu sözdizimi örnekleri: dönüştürme</span><span class="sxs-lookup"><span data-stu-id="559f3-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="559f3-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> sorgulamak için yöntemleri [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) yöntemi tabanlı sorgu sözdizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="559f3-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="559f3-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="559f3-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="559f3-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="559f3-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="559f3-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="559f3-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="559f3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="559f3-107">Example</span></span>  
 <span data-ttu-id="559f3-108">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.ToArray%2A> hemen bir dizi bir dizi içine değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="559f3-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="559f3-109">Todictionary öğesini</span><span class="sxs-lookup"><span data-stu-id="559f3-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="559f3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="559f3-110">Example</span></span>  
 <span data-ttu-id="559f3-111">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.ToDictionary%2A> hemen bir sıra ve bir sözlük ilgili bir anahtar ifadesine değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="559f3-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="559f3-112">ToList</span><span class="sxs-lookup"><span data-stu-id="559f3-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="559f3-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="559f3-113">Example</span></span>  
 <span data-ttu-id="559f3-114">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.ToList%2A> hemen dizisi içine değerlendirmek için bir yöntem bir <xref:System.Collections.Generic.List%601>, burada `T` türü <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="559f3-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="559f3-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="559f3-115">See Also</span></span>  
 [<span data-ttu-id="559f3-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="559f3-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
