---
title: "Birleştirmeler ve çapraz ürün sorgularını düzenleme"
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
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f652f25d04480afb3df1f623347eee23d3ed258
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="aab37-102">Birleştirmeler ve çapraz ürün sorgularını düzenleme</span><span class="sxs-lookup"><span data-stu-id="aab37-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="aab37-103">Aşağıdaki örnekler, birleştirme birden çok tablodan sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aab37-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aab37-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-104">Example</span></span>  
 <span data-ttu-id="aab37-105">Aşağıdaki örnek, yabancı anahtar Gezinti bölmesinde kullanır `From` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` yan tümcesinde C#) Londra'da müşteriler için tüm siparişleri seçin.</span><span class="sxs-lookup"><span data-stu-id="aab37-105">The following example uses foreign key navigation in the `From` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="aab37-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-106">Example</span></span>  
 <span data-ttu-id="aab37-107">Aşağıdaki örnek, yabancı anahtar Gezinti bölmesinde kullanır `Where` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` yan tümcesinde C#) çıkış, stok için filtre uygulamak için `Products` , `Supplier` ABD'de değil.</span><span class="sxs-lookup"><span data-stu-id="aab37-107">The following example uses foreign key navigation in the `Where` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="aab37-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-108">Example</span></span>  
 <span data-ttu-id="aab37-109">Aşağıdaki örnek, yabancı anahtar Gezinti bölmesinde kullanır `From` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` yan tümcesinde C#) Ankara çalışanları için filtre ve bunların bölgeleri listesi.</span><span class="sxs-lookup"><span data-stu-id="aab37-109">The following example uses foreign key navigation in the `From` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="aab37-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-110">Example</span></span>  
 <span data-ttu-id="aab37-111">Aşağıdaki örnek, yabancı anahtar Gezinti bölmesinde kullanır `Select` yan tümcesinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` yan tümcesinde C#) çalışanlar çiftleri için iki çalışanlar aynı olduğu ve burada bir çalışan diğer raporlar filtrelemek için `City`.</span><span class="sxs-lookup"><span data-stu-id="aab37-111">The following example uses foreign key navigation in the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="aab37-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-112">Example</span></span>  
 <span data-ttu-id="aab37-113">Aşağıdaki [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] örnek tüm müşteriler ve siparişler görünüyor, siparişler müşterilere eşleştirilir emin olur ve bu listedeki her müşteri için bir ilgili kişi adı sağlanır güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="aab37-113">The following [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="aab37-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-114">Example</span></span>  
 <span data-ttu-id="aab37-115">Aşağıdaki örnekte, her iki tabloyu iki tablolar ve projeleri sonuçlarını açıkça birleştirir.</span><span class="sxs-lookup"><span data-stu-id="aab37-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="aab37-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-116">Example</span></span>  
 <span data-ttu-id="aab37-117">Aşağıdaki örnekte, üç tablolar ve projeleri sonuçlarından bunların her birini açıkça birleştirir.</span><span class="sxs-lookup"><span data-stu-id="aab37-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="aab37-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-118">Example</span></span>  
 <span data-ttu-id="aab37-119">Aşağıdaki örnek, elde etmek gösterilmiştir bir `LEFT OUTER JOIN` kullanarak `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="aab37-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="aab37-120">`DefaultIfEmpty()` Yöntemi null değerini döndürür olduğunda hiçbir `Order` için `Employee`.</span><span class="sxs-lookup"><span data-stu-id="aab37-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="aab37-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-121">Example</span></span>  
 <span data-ttu-id="aab37-122">Aşağıdaki örnek projeler bir `let` birleştirme sonucu oluşan ifade.</span><span class="sxs-lookup"><span data-stu-id="aab37-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="aab37-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-123">Example</span></span>  
 <span data-ttu-id="aab37-124">Aşağıdaki örnekte gösterildiği bir `join` bileşik bir anahtar ile.</span><span class="sxs-lookup"><span data-stu-id="aab37-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="aab37-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="aab37-125">Example</span></span>  
 <span data-ttu-id="aab37-126">Aşağıdaki örnekte nasıl oluşturulacağını gösteren bir `join` burada sütunlardan boş değer atanabilir ve diğer değil.</span><span class="sxs-lookup"><span data-stu-id="aab37-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="aab37-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aab37-127">See Also</span></span>  
 [<span data-ttu-id="aab37-128">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="aab37-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
