---
title: Dizideki Öğeleri Gruplama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: 50887acefdd5d0feaf9d0885e9ee842f44f0ef65
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915046"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="0cfd0-102">Dizideki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="0cfd0-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="0cfd0-103"><xref:System.Linq.Enumerable.GroupBy%2A> İşleci bir sıranın öğelerini gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="0cfd0-104">Aşağıdaki örnekler Northwind veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cfd0-105"><xref:System.Linq.Enumerable.GroupBy%2A> Sorgularda null sütun değerleri bazen bir <xref:System.InvalidOperationException>oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="0cfd0-106">Daha fazla bilgi için [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)konusunun "GroupBy InvalidOperationException" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cfd0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-107">Example</span></span>  
 <span data-ttu-id="0cfd0-108">Aşağıdaki örnek, bölümlerine `Products` göre `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="0cfd0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-109">Example</span></span>  
 <span data-ttu-id="0cfd0-110">Aşağıdaki örnek, her <xref:System.Linq.Enumerable.Max%2A> biri `CategoryID`için en fazla birim fiyatını bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="0cfd0-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-111">Example</span></span>  
 <span data-ttu-id="0cfd0-112">Aşağıdaki örnek ortalamasını, her birinin `UnitPrice` `CategoryID`ortalamasını bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="0cfd0-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-113">Example</span></span>  
 <span data-ttu-id="0cfd0-114">Aşağıdaki örnek, her <xref:System.Linq.Queryable.Sum%2A> birinin `CategoryID`toplamını `UnitPrice` bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="0cfd0-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-115">Example</span></span>  
 <span data-ttu-id="0cfd0-116">Aşağıdaki örnek, her <xref:System.Linq.Queryable.Count%2A> birinin `CategoryID`içindeki Discontinued `Products` sayısını bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="0cfd0-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-117">Example</span></span>  
 <span data-ttu-id="0cfd0-118">Aşağıdaki örnek, en az 10 `where` ürüne sahip tüm kategorileri bulmak için aşağıdaki yan tümceyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="0cfd0-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-119">Example</span></span>  
 <span data-ttu-id="0cfd0-120">Aşağıdaki örnek ürünlerini ve `CategoryID` `SupplierID`ile gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="0cfd0-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-121">Example</span></span>  
 <span data-ttu-id="0cfd0-122">Aşağıdaki örnek iki ürün dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="0cfd0-123">İlk sıra, birim fiyatı 10 ' dan küçük veya buna eşit olan ürünleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="0cfd0-124">İkinci sıra, birim fiyatı 10 ' dan büyük olan ürünleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="0cfd0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfd0-125">Example</span></span>  
 <span data-ttu-id="0cfd0-126"><xref:System.Linq.Queryable.GroupBy%2A> İşleci yalnızca tek bir anahtar bağımsız değişkeni alabilir.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="0cfd0-127">Birden fazla anahtarla gruplandırmalısınız, aşağıdaki örnekte olduğu gibi anonim bir tür oluşturmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="0cfd0-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="0cfd0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cfd0-128">See also</span></span>

- [<span data-ttu-id="0cfd0-129">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="0cfd0-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="0cfd0-130">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="0cfd0-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
