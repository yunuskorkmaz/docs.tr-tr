---
description: 'Daha fazla bilgi edinin: birleştirme ve çapraz ürün sorguları'
title: Birleşimler ve Çapraz Ürün Sorguları Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 1adee3576d7b30d6ec9a9c4e920befcd21dd9e85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739124"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="72672-103">Birleşimler ve Çapraz Ürün Sorguları Düzenleme</span><span class="sxs-lookup"><span data-stu-id="72672-103">Formulate Joins and Cross-Product Queries</span></span>

<span data-ttu-id="72672-104">Aşağıdaki örneklerde, birden çok tablodan sonuçların nasıl birleştirileceğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="72672-104">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72672-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-105">Example</span></span>  

 <span data-ttu-id="72672-106">Aşağıdaki örnek, `From` `from` Londra 'daki müşterilerin tüm siparişlerini seçmek için Visual Basic (C# ' deki yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="72672-106">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="72672-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-107">Example</span></span>  

 <span data-ttu-id="72672-108">Aşağıdaki örnek, `Where` Birleşik Devletler içindeki yan yana `where` filtrelemek için Visual Basic (C# ' deki yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır `Products` `Supplier` .</span><span class="sxs-lookup"><span data-stu-id="72672-108">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="72672-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-109">Example</span></span>  

 <span data-ttu-id="72672-110">Aşağıdaki örnek, `From` `from` Seattle 'daki çalışanları filtrelemek ve bölgelerini listelemek için Visual Basic (C# ' deki yan tümce) yan tümcesinde yabancı anahtar gezintisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="72672-110">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="72672-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-111">Example</span></span>  

 <span data-ttu-id="72672-112">Aşağıdaki örnek, `Select` `select` bir çalışanın birbirlerine ve her iki çalışanın de aynı olduğu yere rapor ettiği çalışan çiftlerini filtrelemek için Visual Basic (C# ' deki yan tümce) yan tümcesinde yabancı anahtar gezintisini kullanır `City` .</span><span class="sxs-lookup"><span data-stu-id="72672-112">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="72672-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-113">Example</span></span>  

 <span data-ttu-id="72672-114">Aşağıdaki Visual Basic örnek tüm müşteriler ve siparişler için, siparişlerin müşterilerle eşleştiğinden emin olur ve bu listedeki her müşteri için bir kişi adı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="72672-114">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="72672-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-115">Example</span></span>  

 <span data-ttu-id="72672-116">Aşağıdaki örnek iki tablo ve proje sonucunu açık bir şekilde iki tablo olarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="72672-116">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="72672-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-117">Example</span></span>  

 <span data-ttu-id="72672-118">Aşağıdaki örnek, her birinin üç tablo ve proje sonucunu açıkça birleştirir.</span><span class="sxs-lookup"><span data-stu-id="72672-118">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="72672-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-119">Example</span></span>  

 <span data-ttu-id="72672-120">Aşağıdaki örnek kullanılarak nasıl elde edilecek gösterilmektedir `LEFT OUTER JOIN` `DefaultIfEmpty()` .</span><span class="sxs-lookup"><span data-stu-id="72672-120">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="72672-121">`DefaultIfEmpty()`Yöntemi, için olmadığında null değerini döndürür `Order` `Employee` .</span><span class="sxs-lookup"><span data-stu-id="72672-121">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="72672-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-122">Example</span></span>  

 <span data-ttu-id="72672-123">Aşağıdaki örnek, bir `let` birleşimden kaynaklanan bir ifadeyi projeler.</span><span class="sxs-lookup"><span data-stu-id="72672-123">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="72672-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-124">Example</span></span>  

 <span data-ttu-id="72672-125">Aşağıdaki örnek bir `join` bileşik anahtarla bir gösterir.</span><span class="sxs-lookup"><span data-stu-id="72672-125">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="72672-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="72672-126">Example</span></span>  

 <span data-ttu-id="72672-127">Aşağıdaki örnek, bir `join` tarafın null yapılabilir olduğunu ve diğerinin ne şekilde olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="72672-127">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="72672-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72672-128">See also</span></span>

- [<span data-ttu-id="72672-129">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="72672-129">Query Examples</span></span>](query-examples.md)
