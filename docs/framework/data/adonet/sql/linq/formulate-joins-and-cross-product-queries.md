---
title: Birleşimler ve Çapraz Ürün Sorguları Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 002a644ff5d48b25351228dcd74330707491d6c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782087"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="31659-102">Birleşimler ve Çapraz Ürün Sorguları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="31659-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="31659-103">Aşağıdaki örneklerde, birden çok tablodan sonuçların nasıl birleştirileceğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31659-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31659-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-104">Example</span></span>  
 <span data-ttu-id="31659-105">Aşağıdaki örnek, Londra 'daki müşterilere ait tüm siparişleri `From` seçmek için Visual Basic (`from` içindeki C#yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="31659-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="31659-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-106">Example</span></span>  
 <span data-ttu-id="31659-107">Aşağıdaki örnek, Birleşik Devletler içinde olan stok `Where` C# `Products` `Supplier` dışı için filtrelemek üzere Visual Basic (`where` içindeki yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="31659-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="31659-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-108">Example</span></span>  
 <span data-ttu-id="31659-109">Aşağıdaki örnek, Seattle 'daki çalışanları filtrelemek ve bölgelerini `From` listelemek için Visual Basic (`from` içindeki C#yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="31659-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="31659-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-110">Example</span></span>  
 <span data-ttu-id="31659-111">Aşağıdaki örnek, bir çalışanın birbirlerine ve her iki `Select` çalışanın de aynı `City`olduğu`select` yere rapor C#ettiği çalışan çiftlerini filtrelemek için Visual Basic (içindeki yan tümce) yan tümcesinde yabancı anahtar gezintisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="31659-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="31659-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-112">Example</span></span>  
 <span data-ttu-id="31659-113">Aşağıdaki Visual Basic örnek tüm müşteriler ve siparişler için, siparişlerin müşterilerle eşleştiğinden emin olur ve bu listedeki her müşteri için bir kişi adı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="31659-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="31659-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-114">Example</span></span>  
 <span data-ttu-id="31659-115">Aşağıdaki örnek iki tablo ve proje sonucunu açık bir şekilde iki tablo olarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="31659-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="31659-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-116">Example</span></span>  
 <span data-ttu-id="31659-117">Aşağıdaki örnek, her birinin üç tablo ve proje sonucunu açıkça birleştirir.</span><span class="sxs-lookup"><span data-stu-id="31659-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="31659-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-118">Example</span></span>  
 <span data-ttu-id="31659-119">Aşağıdaki örnek kullanılarak `LEFT OUTER JOIN` `DefaultIfEmpty()`nasıl elde edilecek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="31659-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="31659-120">`DefaultIfEmpty()` Yöntemi `Order` , için`Employee`olmadığında null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="31659-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="31659-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-121">Example</span></span>  
 <span data-ttu-id="31659-122">Aşağıdaki örnek, bir birleşimden kaynaklanan bir `let` ifadeyi projeler.</span><span class="sxs-lookup"><span data-stu-id="31659-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="31659-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-123">Example</span></span>  
 <span data-ttu-id="31659-124">Aşağıdaki örnek bir bileşik anahtarla `join` bir gösterir.</span><span class="sxs-lookup"><span data-stu-id="31659-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="31659-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="31659-125">Example</span></span>  
 <span data-ttu-id="31659-126">Aşağıdaki örnek, bir tarafın null yapılabilir olduğunu `join` ve diğerinin ne şekilde olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31659-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="31659-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31659-127">See also</span></span>

- [<span data-ttu-id="31659-128">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="31659-128">Query Examples</span></span>](query-examples.md)
