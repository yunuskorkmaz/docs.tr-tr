---
title: "Sorgu ifade sözdizimi örnekleri: projeksiyonu"
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
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 83d4f1e68938d4aa7330fbcacb40c44b3c06e400
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="3c095-102">Sorgu ifade sözdizimi örnekleri: projeksiyonu</span><span class="sxs-lookup"><span data-stu-id="3c095-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="3c095-103">Bu konudaki örnekler nasıl kullanılacağını gösteren `Select` yöntemi ve `From … From …` sorgulamak için anahtar sözcükler [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3c095-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="3c095-104">`From … From …`eşdeğerdir sorgu tabanlı, `SelectMany` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3c095-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="3c095-105">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3c095-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="3c095-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="3c095-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="3c095-107">Seçim</span><span class="sxs-lookup"><span data-stu-id="3c095-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="3c095-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c095-108">Example</span></span>  
 <span data-ttu-id="3c095-109">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek yöntemi `Product` tablo ve ürün adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3c095-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="3c095-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c095-110">Example</span></span>  
 <span data-ttu-id="3c095-111">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adlarını bir dizi dönün.</span><span class="sxs-lookup"><span data-stu-id="3c095-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="3c095-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c095-112">Example</span></span>  
 <span data-ttu-id="3c095-113">Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.Select%2A> yöntemi projesine `Product.Name` ve `Product.ProductID` anonim türleri dizisi özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="3c095-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="3c095-114">Kaynak...</span><span class="sxs-lookup"><span data-stu-id="3c095-114">From …</span></span> <span data-ttu-id="3c095-115">Kaynak...</span><span class="sxs-lookup"><span data-stu-id="3c095-115">From …</span></span> <span data-ttu-id="3c095-116">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="3c095-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="3c095-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c095-117">Example</span></span>  
 <span data-ttu-id="3c095-118">Aşağıdaki örnek kullanır `From … From …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) tümünü seçmek için nereye siparişleri `TotalDue` değerinden 500,00 değil.</span><span class="sxs-lookup"><span data-stu-id="3c095-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="3c095-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c095-119">Example</span></span>  
 <span data-ttu-id="3c095-120">Aşağıdaki örnek kullanır `From … From …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) burada sırasını yapıldı 1 Ekim 2002 veya sonraki sürümlerde tüm siparişleri seçmek için.</span><span class="sxs-lookup"><span data-stu-id="3c095-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="3c095-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c095-121">Example</span></span>  
 <span data-ttu-id="3c095-122">Aşağıdaki örnek kullanan bir `From … From …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) sipariş toplam olduğu 10000.00 kullandığı'dan büyük ve tüm siparişleri seçmek için `From` toplam iki kez isteyen önlemek için atama.</span><span class="sxs-lookup"><span data-stu-id="3c095-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="3c095-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c095-123">See Also</span></span>  
 [<span data-ttu-id="3c095-124">LINQ to Entities sorguları</span><span class="sxs-lookup"><span data-stu-id="3c095-124">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
