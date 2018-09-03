---
title: 'Metot tabanlı sorgu söz dizimi örnekleri: projeksiyon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 81484f729b2282678b3fa1a92b5050cf7a502db5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469901"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="0ad0b-102">Metot tabanlı sorgu söz dizimi örnekleri: projeksiyon</span><span class="sxs-lookup"><span data-stu-id="0ad0b-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="0ad0b-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> methodsto sorgu [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) metot tabanlı sorgu söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0ad0b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methodsto query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="0ad0b-104">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0ad0b-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0ad0b-105">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="0ad0b-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="0ad0b-106">Seçim</span><span class="sxs-lookup"><span data-stu-id="0ad0b-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ad0b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ad0b-107">Example</span></span>  
 <span data-ttu-id="0ad0b-108">Aşağıdaki örnekte <xref:System.Linq.Queryable.Select%2A> projesine yöntemi `Product.Name` ve `Product.ProductID` anonim türler dizisini özellikleri.</span><span class="sxs-lookup"><span data-stu-id="0ad0b-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="0ad0b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ad0b-109">Example</span></span>  
 <span data-ttu-id="0ad0b-110">Aşağıdaki örnekte <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adlarını bir dizisini döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ad0b-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="0ad0b-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="0ad0b-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="0ad0b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ad0b-112">Example</span></span>  
 <span data-ttu-id="0ad0b-113">Aşağıdaki örnekte <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi tümünü seçmek için siparişleri nerede `TotalDue` kısa da 500,00 olduğu.</span><span class="sxs-lookup"><span data-stu-id="0ad0b-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="0ad0b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ad0b-114">Example</span></span>  
 <span data-ttu-id="0ad0b-115">Aşağıdaki örnekte <xref:System.Linq.Enumerable.SelectMany%2A> burada sırasını yapıldı 1 Ekim 2002 veya daha sonra tüm siparişleri seçmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ad0b-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="0ad0b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ad0b-116">See Also</span></span>  
 [<span data-ttu-id="0ad0b-117">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="0ad0b-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
