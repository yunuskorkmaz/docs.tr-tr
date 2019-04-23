---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: bf6c889fff2635cd50597e72151c46fbb4d9b97d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150624"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="82861-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="82861-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="82861-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="82861-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="82861-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82861-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="82861-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="82861-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="82861-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="82861-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="82861-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="82861-107">Example</span></span>  
 <span data-ttu-id="82861-108">Aşağıdaki örnekte <xref:System.Linq.Enumerable.ToArray%2A> hemen bir sıralı bir dizi içine değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="82861-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="82861-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="82861-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="82861-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="82861-110">Example</span></span>  
 <span data-ttu-id="82861-111">Aşağıdaki örnekte <xref:System.Linq.Enumerable.ToDictionary%2A> hemen bir dizisi ve ilişkili bir anahtar ifadesi bir sözlükte değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="82861-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="82861-112">ToList</span><span class="sxs-lookup"><span data-stu-id="82861-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="82861-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="82861-113">Example</span></span>  
 <span data-ttu-id="82861-114">Aşağıdaki örnekte <xref:System.Linq.Enumerable.ToList%2A> hemen bir dizisi olarak değerlendirmek için bir yöntem bir <xref:System.Collections.Generic.List%601>burada `T` türünde <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="82861-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="82861-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82861-115">See also</span></span>

- [<span data-ttu-id="82861-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="82861-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
