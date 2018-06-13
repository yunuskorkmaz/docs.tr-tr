---
title: Uzak vs. Yerel çalıştırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 9488cb4c15c2e0646d91bdba36e7d4e2be2efbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360053"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="52901-102">Uzak vs. Yerel çalıştırma</span><span class="sxs-lookup"><span data-stu-id="52901-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="52901-103">Sorgularınızın ya da uzaktan yürütme karar verebilirsiniz (diğer bir deyişle, veritabanı altyapısı veritabanında sorgu yürütür) veya yerel olarak ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yerel önbelleğe karşı sorgu yürütülür).</span><span class="sxs-lookup"><span data-stu-id="52901-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="52901-104">Uzaktan yürütme</span><span class="sxs-lookup"><span data-stu-id="52901-104">Remote Execution</span></span>  
 <span data-ttu-id="52901-105">Aşağıdaki sorgu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="52901-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="52901-106">Veritabanınızı binlerce siparişleri satır varsa, bunları tüm küçük bir alt işlem almak istiyor musunuz.</span><span class="sxs-lookup"><span data-stu-id="52901-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="52901-107">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.EntitySet%601> uygulayan sınıf <xref:System.Linq.IQueryable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="52901-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="52901-108">Bu yaklaşım sorgularını uzaktan çalıştırılabilir emin olur.</span><span class="sxs-lookup"><span data-stu-id="52901-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="52901-109">Bu teknik akışından iki önemli faydası:</span><span class="sxs-lookup"><span data-stu-id="52901-109">Two major benefits flow from this technique:</span></span>  
  
-   <span data-ttu-id="52901-110">Gereksiz verileri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="52901-110">Unnecessary data is not retrieved.</span></span>  
  
-   <span data-ttu-id="52901-111">Veritabanı altyapısı tarafından çalıştırılan bir sorguyu genellikle daha büyük veritabanı dizinlerini nedeniyle verimli.</span><span class="sxs-lookup"><span data-stu-id="52901-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="52901-112">Yerel çalıştırma</span><span class="sxs-lookup"><span data-stu-id="52901-112">Local Execution</span></span>  
 <span data-ttu-id="52901-113">Diğer durumlarda, yerel önbellekte eksiksiz ilgili varlıklar olarak sahip olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52901-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="52901-114">Bu amaçla <xref:System.Data.Linq.EntitySet%601> sağlar <xref:System.Data.Linq.EntitySet%601.Load%2A> tüm üyelerini açıkça yüklemek için yöntem <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="52901-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="52901-115">Varsa bir <xref:System.Data.Linq.EntitySet%601> yüklenen, zaten sonraki sorguları yerel olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="52901-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="52901-116">Bu yaklaşımın iki yolla yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="52901-116">This approach helps in two ways:</span></span>  
  
-   <span data-ttu-id="52901-117">Yerel olarak tamamını kullanılan veya birden çok kez, uzak sorgular ve ilişkili gecikmeleri önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52901-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
-   <span data-ttu-id="52901-118">Varlık eksiksiz bir varlık olarak serileştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="52901-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="52901-119">Aşağıdaki kod parçası nasıl yerel yürütme gösterilmektedir elde edilebilir:</span><span class="sxs-lookup"><span data-stu-id="52901-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="52901-120">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="52901-120">Comparison</span></span>  
 <span data-ttu-id="52901-121">Güçlü bir seçenekleri birleşimini bu iki özellikleri sağlar: uzaktan yürütme büyük koleksiyonları ve yerel yürütme küçük koleksiyonlar için veya tam koleksiyon burada gereklidir.</span><span class="sxs-lookup"><span data-stu-id="52901-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="52901-122">Uzaktan yürütme aracılığıyla uygulama <xref:System.Linq.IQueryable>ve bir bellek içi karşı yerel yürütme <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="52901-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="52901-123">Yerel yürütme zorlamak için (diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601>), bkz: [bir tür için genel bir IEnumerable Dönüştür](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="52901-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="52901-124">Sırasız kümeleri sorguları</span><span class="sxs-lookup"><span data-stu-id="52901-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="52901-125">Arabirimini uygulayan bir yerel koleksiyonu arasında önemli fark Not <xref:System.Collections.Generic.List%601> ve yürütülen uzak sorgularını sağlayan koleksiyonu *kümeleri sıralanmamış* ilişkisel bir veritabanındaki.</span><span class="sxs-lookup"><span data-stu-id="52901-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="52901-126"><xref:System.Collections.Generic.List%601> Dizin değerlerini kullananlar gibi yöntemleri genellikle sırasız ayarlanmış bir uzak bir sorgu üzerinden alınamıyor listesi semantiği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="52901-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="52901-127">Bu nedenle, bu tür yöntemleri dolaylı olarak yük <xref:System.Data.Linq.EntitySet%601> yerel yürütülmesine izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="52901-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52901-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52901-128">See Also</span></span>  
 [<span data-ttu-id="52901-129">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="52901-129">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
