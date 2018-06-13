---
title: 'Yöntem temelli sorgu sözdizimi örnekleri: projeksiyonu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: b938e32ae0e10498203e141c34d35a18a3515257
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761551"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="33ea2-102">Yöntem temelli sorgu sözdizimi örnekleri: projeksiyonu</span><span class="sxs-lookup"><span data-stu-id="33ea2-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="33ea2-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> methodsto sorgu [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) yöntemi tabanlı sorgu sözdizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="33ea2-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methodsto query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="33ea2-104">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="33ea2-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="33ea2-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="33ea2-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="33ea2-106">Seçim</span><span class="sxs-lookup"><span data-stu-id="33ea2-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="33ea2-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="33ea2-107">Example</span></span>  
 <span data-ttu-id="33ea2-108">Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.Select%2A> yöntemi projesine `Product.Name` ve `Product.ProductID` anonim türleri dizisi özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="33ea2-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="33ea2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="33ea2-109">Example</span></span>  
 <span data-ttu-id="33ea2-110">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Select%2A> yöntemi yalnızca ürün adlarının dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33ea2-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="33ea2-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="33ea2-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="33ea2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="33ea2-112">Example</span></span>  
 <span data-ttu-id="33ea2-113">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.SelectMany%2A> tümünü seçmek için yöntemi siparişleri where `TotalDue` değerinden 500,00 değil.</span><span class="sxs-lookup"><span data-stu-id="33ea2-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="33ea2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="33ea2-114">Example</span></span>  
 <span data-ttu-id="33ea2-115">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.SelectMany%2A> burada sırasını yapıldı 1 Ekim 2002 veya sonraki sürümlerde tüm siparişleri seçmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="33ea2-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="33ea2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33ea2-116">See Also</span></span>  
 [<span data-ttu-id="33ea2-117">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="33ea2-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
