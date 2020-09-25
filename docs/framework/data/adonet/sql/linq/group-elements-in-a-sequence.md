---
title: Dizideki Öğeleri Gruplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: d11d6f6231c1871cd54f0b0e3f6f862dc10b328b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194355"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="56fa3-102">Dizideki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="56fa3-102">Group Elements in a Sequence</span></span>

<span data-ttu-id="56fa3-103"><xref:System.Linq.Enumerable.GroupBy%2A>İşleci bir sıranın öğelerini gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="56fa3-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="56fa3-104">Aşağıdaki örnekler Northwind veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="56fa3-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56fa3-105">Sorgularda null sütun değerleri <xref:System.Linq.Enumerable.GroupBy%2A> bazen bir oluşturabilir <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="56fa3-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="56fa3-106">Daha fazla bilgi için [sorun giderme](troubleshooting.md)konusunun "GroupBy InvalidOperationException" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="56fa3-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56fa3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-107">Example</span></span>  

 <span data-ttu-id="56fa3-108">Aşağıdaki örnek, bölümlerine `Products` göre `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="56fa3-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="56fa3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-109">Example</span></span>  

 <span data-ttu-id="56fa3-110">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Max%2A> her biri için en fazla birim fiyatını bulmak için kullanır `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="56fa3-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="56fa3-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-111">Example</span></span>  

 <span data-ttu-id="56fa3-112">Aşağıdaki örnek ortalamasını, her birinin ortalamasını bulmak için kullanır `UnitPrice` `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="56fa3-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="56fa3-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-113">Example</span></span>  

 <span data-ttu-id="56fa3-114">Aşağıdaki örnek, <xref:System.Linq.Queryable.Sum%2A> her birinin toplamını bulmak için kullanır `UnitPrice` `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="56fa3-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="56fa3-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-115">Example</span></span>  

 <span data-ttu-id="56fa3-116">Aşağıdaki örnek, <xref:System.Linq.Queryable.Count%2A> her birinin içindeki Discontinued sayısını bulmak için kullanır `Products` `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="56fa3-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="56fa3-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-117">Example</span></span>  

 <span data-ttu-id="56fa3-118">Aşağıdaki örnek, `where` en az 10 ürüne sahip tüm kategorileri bulmak için aşağıdaki yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="56fa3-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="56fa3-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-119">Example</span></span>  

 <span data-ttu-id="56fa3-120">Aşağıdaki örnek ürünlerini ve ile gruplandırır `CategoryID` `SupplierID` .</span><span class="sxs-lookup"><span data-stu-id="56fa3-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="56fa3-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-121">Example</span></span>  

 <span data-ttu-id="56fa3-122">Aşağıdaki örnek iki ürün dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="56fa3-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="56fa3-123">İlk sıra, birim fiyatı 10 ' dan küçük veya buna eşit olan ürünleri içerir.</span><span class="sxs-lookup"><span data-stu-id="56fa3-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="56fa3-124">İkinci sıra, birim fiyatı 10 ' dan büyük olan ürünleri içerir.</span><span class="sxs-lookup"><span data-stu-id="56fa3-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="56fa3-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="56fa3-125">Example</span></span>  

 <span data-ttu-id="56fa3-126"><xref:System.Linq.Queryable.GroupBy%2A>İşleci yalnızca tek bir anahtar bağımsız değişkeni alabilir.</span><span class="sxs-lookup"><span data-stu-id="56fa3-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="56fa3-127">Birden fazla anahtarla gruplandırmalısınız, aşağıdaki örnekte olduğu gibi anonim bir tür oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="56fa3-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="56fa3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56fa3-128">See also</span></span>

- [<span data-ttu-id="56fa3-129">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="56fa3-129">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="56fa3-130">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="56fa3-130">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
