---
title: "Yöntem temelli sorgu sözdizimi örnekleri: dönüştürme"
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
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8c61d84d4ef03f7c62cc055ec125514df6fe9d53
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="80ca0-102">Yöntem temelli sorgu sözdizimi örnekleri: dönüştürme</span><span class="sxs-lookup"><span data-stu-id="80ca0-102">Method-Based Query Syntax Examples: Conversion</span></span>
<span data-ttu-id="80ca0-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> ve <xref:System.Linq.Enumerable.ToList%2A> sorgulamak için yöntemleri [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) yöntemi tabanlı sorgu sözdizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="80ca0-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="80ca0-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="80ca0-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="80ca0-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="80ca0-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="80ca0-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="80ca0-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="80ca0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="80ca0-107">Example</span></span>  
 <span data-ttu-id="80ca0-108">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.ToArray%2A> hemen bir dizi bir dizi içine değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="80ca0-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="80ca0-109">Todictionary öğesini</span><span class="sxs-lookup"><span data-stu-id="80ca0-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="80ca0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="80ca0-110">Example</span></span>  
 <span data-ttu-id="80ca0-111">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.ToDictionary%2A> hemen bir sıra ve bir sözlük ilgili bir anahtar ifadesine değerlendirmek için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="80ca0-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="80ca0-112">ToList</span><span class="sxs-lookup"><span data-stu-id="80ca0-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="80ca0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="80ca0-113">Example</span></span>  
 <span data-ttu-id="80ca0-114">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.ToList%2A> hemen dizisi içine değerlendirmek için bir yöntem bir <xref:System.Collections.Generic.List%601>, burada `T` türü <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="80ca0-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="80ca0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80ca0-115">See Also</span></span>  
 [<span data-ttu-id="80ca0-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="80ca0-116">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
