---
description: 'Daha fazla bilgi edinin: öğeleri sırayla gruplandırma'
title: Dizideki Öğeleri Gruplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: bc9a4d042ed0edb090f0530ebb24d99a5390c882
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786075"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="fe753-103">Dizideki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="fe753-103">Group Elements in a Sequence</span></span>

<span data-ttu-id="fe753-104"><xref:System.Linq.Enumerable.GroupBy%2A>İşleci bir sıranın öğelerini gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="fe753-104">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="fe753-105">Aşağıdaki örnekler Northwind veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe753-105">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe753-106">Sorgularda null sütun değerleri <xref:System.Linq.Enumerable.GroupBy%2A> bazen bir oluşturabilir <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="fe753-106">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="fe753-107">Daha fazla bilgi için [sorun giderme](troubleshooting.md)konusunun "GroupBy InvalidOperationException" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fe753-107">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe753-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-108">Example</span></span>  

 <span data-ttu-id="fe753-109">Aşağıdaki örnek, bölümlerine `Products` göre `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="fe753-109">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="fe753-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-110">Example</span></span>  

 <span data-ttu-id="fe753-111">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Max%2A> her biri için en fazla birim fiyatını bulmak için kullanır `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="fe753-111">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="fe753-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-112">Example</span></span>  

 <span data-ttu-id="fe753-113">Aşağıdaki örnek ortalamasını, her birinin ortalamasını bulmak için kullanır `UnitPrice` `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="fe753-113">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="fe753-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-114">Example</span></span>  

 <span data-ttu-id="fe753-115">Aşağıdaki örnek, <xref:System.Linq.Queryable.Sum%2A> her birinin toplamını bulmak için kullanır `UnitPrice` `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="fe753-115">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="fe753-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-116">Example</span></span>  

 <span data-ttu-id="fe753-117">Aşağıdaki örnek, <xref:System.Linq.Queryable.Count%2A> her birinin içindeki Discontinued sayısını bulmak için kullanır `Products` `CategoryID` .</span><span class="sxs-lookup"><span data-stu-id="fe753-117">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="fe753-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-118">Example</span></span>  

 <span data-ttu-id="fe753-119">Aşağıdaki örnek, `where` en az 10 ürüne sahip tüm kategorileri bulmak için aşağıdaki yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe753-119">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="fe753-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-120">Example</span></span>  

 <span data-ttu-id="fe753-121">Aşağıdaki örnek ürünlerini ve ile gruplandırır `CategoryID` `SupplierID` .</span><span class="sxs-lookup"><span data-stu-id="fe753-121">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="fe753-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-122">Example</span></span>  

 <span data-ttu-id="fe753-123">Aşağıdaki örnek iki ürün dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe753-123">The following example returns two sequences of products.</span></span> <span data-ttu-id="fe753-124">İlk sıra, birim fiyatı 10 ' dan küçük veya buna eşit olan ürünleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe753-124">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="fe753-125">İkinci sıra, birim fiyatı 10 ' dan büyük olan ürünleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe753-125">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="fe753-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe753-126">Example</span></span>  

 <span data-ttu-id="fe753-127"><xref:System.Linq.Queryable.GroupBy%2A>İşleci yalnızca tek bir anahtar bağımsız değişkeni alabilir.</span><span class="sxs-lookup"><span data-stu-id="fe753-127">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="fe753-128">Birden fazla anahtarla gruplandırmalısınız, aşağıdaki örnekte olduğu gibi anonim bir tür oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="fe753-128">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="fe753-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe753-129">See also</span></span>

- [<span data-ttu-id="fe753-130">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="fe753-130">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="fe753-131">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="fe753-131">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
