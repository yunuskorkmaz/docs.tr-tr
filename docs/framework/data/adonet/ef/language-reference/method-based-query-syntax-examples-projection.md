---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Projeksiyon'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 3a9203a51bbb61b32300919656084d7d95ddfa79
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397316"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="1ef71-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="1ef71-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="1ef71-103">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ef71-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="1ef71-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="1ef71-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1ef71-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="1ef71-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="1ef71-106">Seçim</span><span class="sxs-lookup"><span data-stu-id="1ef71-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="1ef71-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef71-107">Example</span></span>  
 <span data-ttu-id="1ef71-108">Aşağıdaki örnek, <xref:System.Linq.Queryable.Select%2A> `Product.Name` ve `Product.ProductID` özelliklerini bir anonim türler dizisi halinde proje yapmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef71-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="1ef71-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef71-109">Example</span></span>  
 <span data-ttu-id="1ef71-110">Aşağıdaki örnek, yalnızca ürün <xref:System.Linq.Enumerable.Select%2A> adlarından oluşan bir dizi döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef71-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="1ef71-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="1ef71-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="1ef71-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef71-112">Example</span></span>  
 <span data-ttu-id="1ef71-113">Aşağıdaki örnek, 500,00 ' <xref:System.Linq.Enumerable.SelectMany%2A> den küçük `TotalDue` olan tüm siparişleri seçmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef71-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="1ef71-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ef71-114">Example</span></span>  
 <span data-ttu-id="1ef71-115">Aşağıdaki örnek, 1 Ekim <xref:System.Linq.Enumerable.SelectMany%2A> 2002 veya sonraki sürümlerde siparişin yapıldığı tüm siparişleri seçmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ef71-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1ef71-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ef71-116">See also</span></span>

- [<span data-ttu-id="1ef71-117">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="1ef71-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
