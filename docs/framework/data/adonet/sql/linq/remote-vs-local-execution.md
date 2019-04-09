---
title: Uzak ve Yerel Yürütme Karşılaştırması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 02d0417bc05f8585dc469d365089c8123d395f64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164521"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="3cb7e-102">Uzak ve Yerel Yürütme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="3cb7e-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="3cb7e-103">Sorgularınızın ya da uzaktan yürütün karar verebilirsiniz (diğer bir deyişle, veritabanı altyapısı veritabanı sorgusu çalıştırır) veya yerel olarak ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel önbelleğe karşı sorgu yürütülür).</span><span class="sxs-lookup"><span data-stu-id="3cb7e-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="3cb7e-104">Uzaktan Yürütme</span><span class="sxs-lookup"><span data-stu-id="3cb7e-104">Remote Execution</span></span>  
 <span data-ttu-id="3cb7e-105">Şu sorguyu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="3cb7e-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="3cb7e-106">Veritabanınızı gösteren binlerce satır siparişler varsa, bunların tüm küçük bir alt işleme alınması istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="3cb7e-107">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> sınıfının Implements <xref:System.Linq.IQueryable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="3cb7e-108">Bu yaklaşım sorgularını uzaktan yürütüldüğünden emin olur.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="3cb7e-109">Bu teknik akıştan iki önemli avantajları:</span><span class="sxs-lookup"><span data-stu-id="3cb7e-109">Two major benefits flow from this technique:</span></span>  
  
-   <span data-ttu-id="3cb7e-110">Gereksiz verileri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-110">Unnecessary data is not retrieved.</span></span>  
  
-   <span data-ttu-id="3cb7e-111">Veritabanı altyapısı tarafından çalıştırılan bir sorgu genellikle büyük verimli veritabanı dizinleri nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="3cb7e-112">Yerel Yürütme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="3cb7e-112">Local Execution</span></span>  
 <span data-ttu-id="3cb7e-113">Diğer durumlarda, ilişkili varlık kümesinin tamamını yerel önbellek üzerinde olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="3cb7e-114">Bu amaçla <xref:System.Data.Linq.EntitySet%601> sağlar <xref:System.Data.Linq.EntitySet%601.Load%2A> tüm üyelerini açıkça yüklemek için gereken yöntemini <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="3cb7e-115">Varsa bir <xref:System.Data.Linq.EntitySet%601> zaten yüklendiğinde sonraki sorgular yerel olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="3cb7e-116">Bu yaklaşım, iki şekilde yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="3cb7e-116">This approach helps in two ways:</span></span>  
  
-   <span data-ttu-id="3cb7e-117">Tam bir set yerel olarak kullanılması gerekir ya da birden çok kez uzak sorguları ve ilişkili gecikme süreleri önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
-   <span data-ttu-id="3cb7e-118">Varlık eksiksiz bir varlık seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="3cb7e-119">Aşağıdaki kod parçası yerel yürütme gösterilmektedir elde edilebilir:</span><span class="sxs-lookup"><span data-stu-id="3cb7e-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="3cb7e-120">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="3cb7e-120">Comparison</span></span>  
 <span data-ttu-id="3cb7e-121">Bu iki özellik güçlü bir birleşim seçenekleri sağlar: büyük ve küçük koleksiyonlar için veya tam koleksiyon gerekmesi halinde yerel yürütme için uzaktan yürütme.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="3cb7e-122">Uzaktan yürütme aracılığıyla uygulama <xref:System.Linq.IQueryable>ve bellek içi karşı yerel yürütme <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="3cb7e-123">Yerel yürütme zorlamak için (diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601>), bkz: [türü genel IEnumerable öğesine dönüştürme](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="3cb7e-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="3cb7e-124">Sırasız kümeleri sorguları</span><span class="sxs-lookup"><span data-stu-id="3cb7e-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="3cb7e-125">Uygulayan bir yerel koleksiyonu arasındaki önemli fark Not <xref:System.Collections.Generic.List%601> ve uzak sorguları karşı yürütülen sağlayan koleksiyonu *kümeleri sıralanmamış* ilişkisel bir veritabanındaki.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <xref:System.Collections.Generic.List%601> <span data-ttu-id="3cb7e-126">Dizin değerlerinin kullananlar gibi yöntemler, genellikle bir sıralanmamış karşı uzak sorgu alınamıyor listesi semantiğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-126">methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="3cb7e-127">Bu nedenle, bu tür yöntemler dolaylı olarak yük <xref:System.Data.Linq.EntitySet%601> yerel yürütmeye olanak tanımak için.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb7e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cb7e-128">See also</span></span>

- [<span data-ttu-id="3cb7e-129">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="3cb7e-129">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
