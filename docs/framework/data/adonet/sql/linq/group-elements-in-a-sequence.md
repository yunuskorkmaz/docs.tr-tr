---
title: "Bir sırada Grup öğeleri"
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
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a398bb7b951fcf2dd2449b6468a19d39a134a4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="a2fa0-102">Bir sırada Grup öğeleri</span><span class="sxs-lookup"><span data-stu-id="a2fa0-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="a2fa0-103"><xref:System.Linq.Enumerable.GroupBy%2A> İşleci bir sıradaki gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="a2fa0-104">Aşağıdaki örnekler, Northwind veritabanı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2fa0-105">Sütun değerleri null <xref:System.Linq.Enumerable.GroupBy%2A> sorgular bazen throw bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="a2fa0-106">Daha fazla bilgi için "GroupBy InvalidOperationException" bölümüne bakın [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="a2fa0-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2fa0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-107">Example</span></span>  
 <span data-ttu-id="a2fa0-108">Aşağıdaki örnek bölümleri `Products` tarafından `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="a2fa0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-109">Example</span></span>  
 <span data-ttu-id="a2fa0-110">Aşağıdaki örnek kullanır <xref:System.Linq.Enumerable.Max%2A> her biri için en fazla birim fiyat bulmak için `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="a2fa0-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-111">Example</span></span>  
 <span data-ttu-id="a2fa0-112">Aşağıdaki örnek, ortalama bulmak için ortalama kullanır `UnitPrice` her `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="a2fa0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-113">Example</span></span>  
 <span data-ttu-id="a2fa0-114">Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.Sum%2A> toplam bulmak için `UnitPrice` her `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="a2fa0-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-115">Example</span></span>  
 <span data-ttu-id="a2fa0-116">Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.Count%2A> sayısını bulmak için dönüştürülmesine `Products` her `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="a2fa0-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-117">Example</span></span>  
 <span data-ttu-id="a2fa0-118">Aşağıdaki örnek, bir aşağıdaki kullanır `where` en az 10 ürünleri yüklü tüm kategorileri bulmak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="a2fa0-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-119">Example</span></span>  
 <span data-ttu-id="a2fa0-120">Aşağıdaki örnek göre ürünler grupları `CategoryID` ve `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="a2fa0-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-121">Example</span></span>  
 <span data-ttu-id="a2fa0-122">Aşağıdaki örnek, ürünler ve iki dizilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="a2fa0-123">Birim Fiyat daha az veya bu değere eşit 10 ürünleriyle ilk dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="a2fa0-124">Birim Fiyat 10'dan büyük ürünleriyle ikinci dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="a2fa0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2fa0-125">Example</span></span>  
 <span data-ttu-id="a2fa0-126"><xref:System.Linq.Queryable.GroupBy%2A> İşleci yalnızca tek bir anahtar bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="a2fa0-127">Birden çok anahtara göre gruplandırmak gerekiyorsa, aşağıdaki örnekte olduğu gibi anonim bir tür oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a2fa0-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="a2fa0-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-128">See Also</span></span>  
 [<span data-ttu-id="a2fa0-129">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="a2fa0-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="a2fa0-130">Örnek veritabanları yükleme</span><span class="sxs-lookup"><span data-stu-id="a2fa0-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
