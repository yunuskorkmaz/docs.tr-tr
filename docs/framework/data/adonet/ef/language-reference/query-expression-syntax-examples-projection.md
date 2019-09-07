---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: b5139cc310689eb05833ead8d35c03d02eb2fc58
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398426"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="36ade-102">Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="36ade-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="36ade-103">Bu konudaki örneklerde, sorgu ifadesi söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak `From … From …` için `Select` yönteminin ve anahtar sözcüklerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="36ade-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="36ade-104">`From … From …`, `SelectMany` yönteminin sorgu tabanlı eşdeğeri olur.</span><span class="sxs-lookup"><span data-stu-id="36ade-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="36ade-105">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="36ade-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="36ade-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="36ade-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="36ade-107">Seçim</span><span class="sxs-lookup"><span data-stu-id="36ade-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="36ade-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ade-108">Example</span></span>  
 <span data-ttu-id="36ade-109">Aşağıdaki örnek, `Product` tablodaki tüm <xref:System.Linq.Enumerable.Select%2A> satırları döndürmek ve ürün adlarını göstermek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="36ade-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="36ade-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ade-110">Example</span></span>  
 <span data-ttu-id="36ade-111">Aşağıdaki örnek, yalnızca <xref:System.Linq.Enumerable.Select%2A> ürün adlarından oluşan bir dizi döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="36ade-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="36ade-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ade-112">Example</span></span>  
 <span data-ttu-id="36ade-113">Aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> `Product.Name` ve `Product.ProductID` özelliklerini bir anonim türler dizisi halinde proje yapmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="36ade-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="36ade-114">Kaynak...</span><span class="sxs-lookup"><span data-stu-id="36ade-114">From …</span></span> <span data-ttu-id="36ade-115">Kaynak...</span><span class="sxs-lookup"><span data-stu-id="36ade-115">From …</span></span> <span data-ttu-id="36ade-116">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="36ade-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="36ade-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ade-117">Example</span></span>  
 <span data-ttu-id="36ade-118">Aşağıdaki örnek, 500,00 `From … From …` ' den küçük `TotalDue` olan tüm <xref:System.Linq.Enumerable.SelectMany%2A> siparişleri seçmek için (yönteminin eşdeğeri) kullanır.</span><span class="sxs-lookup"><span data-stu-id="36ade-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="36ade-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ade-119">Example</span></span>  
 <span data-ttu-id="36ade-120">Aşağıdaki örnek, 1 `From … From …` Ekim 2002 veya sonraki bir <xref:System.Linq.Enumerable.SelectMany%2A> sürümde siparişin yapıldığı tüm siparişleri seçmek için (yönteminin eşdeğeri) kullanır.</span><span class="sxs-lookup"><span data-stu-id="36ade-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="36ade-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ade-121">Example</span></span>  
 <span data-ttu-id="36ade-122">Aşağıdaki örnek, siparişin toplamının `From … From …` 10000,00 ' den büyük olduğu <xref:System.Linq.Enumerable.SelectMany%2A> tüm siparişleri seçmek ve toplamı iki kez istememek için atamayı kullanması `From` için bir (yönteminin eşdeğeri) kullanır.</span><span class="sxs-lookup"><span data-stu-id="36ade-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="36ade-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36ade-123">See also</span></span>

- [<span data-ttu-id="36ade-124">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="36ade-124">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
