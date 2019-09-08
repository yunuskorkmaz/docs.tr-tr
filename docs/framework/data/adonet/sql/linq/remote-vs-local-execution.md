---
title: Uzak ve Yerel Yürütme Karşılaştırması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: a21d5bbffdb1a78d3062929a1ca384a750af59a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781161"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="a6b89-102">Uzak ve Yerel Yürütme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="a6b89-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="a6b89-103">Sorgularınızı uzaktan yürütmeye karar verebilirsiniz (yani, veritabanı altyapısı sorguyu veritabanına karşı yürütür) veya yerel olarak ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguyu yerel bir önbellekte yürütür).</span><span class="sxs-lookup"><span data-stu-id="a6b89-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="a6b89-104">Uzaktan Yürütme</span><span class="sxs-lookup"><span data-stu-id="a6b89-104">Remote Execution</span></span>  
 <span data-ttu-id="a6b89-105">Aşağıdaki sorguyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a6b89-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="a6b89-106">Veritabanınızda binlerce sipariş satırı varsa, küçük bir alt kümeyi işlemeye kadar tümünü almak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6b89-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="a6b89-107">' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.IQueryable> sınıfı arabirimini uygular. <xref:System.Data.Linq.EntitySet%601></span><span class="sxs-lookup"><span data-stu-id="a6b89-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="a6b89-108">Bu yaklaşım, bu tür sorguların uzaktan yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6b89-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="a6b89-109">Bu teknikten iki önemli avantaj akışı:</span><span class="sxs-lookup"><span data-stu-id="a6b89-109">Two major benefits flow from this technique:</span></span>  
  
- <span data-ttu-id="a6b89-110">Gereksiz veriler alınmadı.</span><span class="sxs-lookup"><span data-stu-id="a6b89-110">Unnecessary data is not retrieved.</span></span>  
  
- <span data-ttu-id="a6b89-111">Veritabanı altyapısı tarafından yürütülen bir sorgu, veritabanı dizinleri nedeniyle genellikle daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="a6b89-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="a6b89-112">Yerel Yürütme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="a6b89-112">Local Execution</span></span>  
 <span data-ttu-id="a6b89-113">Diğer durumlarda, yerel önbellekte ilgili varlıkların tamamen kümesine sahip olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6b89-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="a6b89-114">Bu amaçla <xref:System.Data.Linq.EntitySet%601> , tümüyelerini<xref:System.Data.Linq.EntitySet%601.Load%2A> açıkça yüklemek için yöntemini sağlar. <xref:System.Data.Linq.EntitySet%601></span><span class="sxs-lookup"><span data-stu-id="a6b89-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="a6b89-115"><xref:System.Data.Linq.EntitySet%601> Zaten yüklüyse, sonraki sorgular yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a6b89-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="a6b89-116">Bu yaklaşım iki şekilde yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="a6b89-116">This approach helps in two ways:</span></span>  
  
- <span data-ttu-id="a6b89-117">Tamamlanma kümesinin yerel olarak veya birden çok kez kullanılması gerekiyorsa, uzak sorgulardan ve ilişkili gecikmelerin önüne kurtulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6b89-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
- <span data-ttu-id="a6b89-118">Varlık, bir bütün varlık olarak seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a6b89-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="a6b89-119">Aşağıdaki kod parçası, yerel yürütmenin nasıl elde edilebilir olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="a6b89-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="a6b89-120">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="a6b89-120">Comparison</span></span>  
 <span data-ttu-id="a6b89-121">Bu iki özellik, seçeneklerin güçlü bir birleşimini sağlar: büyük koleksiyonlar için uzaktan yürütme ve küçük koleksiyonlar için yerel yürütme ve tüm koleksiyonun gerekli olduğu durumlar.</span><span class="sxs-lookup"><span data-stu-id="a6b89-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="a6b89-122">Uzaktan yürütmeyi, bellek <xref:System.Linq.IQueryable> <xref:System.Collections.Generic.IEnumerable%601> içi bir koleksiyon ile ve yerel yürütme aracılığıyla uyguırın.</span><span class="sxs-lookup"><span data-stu-id="a6b89-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="a6b89-123">Yerel yürütmeyi zorlamak için (yani, <xref:System.Collections.Generic.IEnumerable%601>) bkz. [bir türü genel IEnumerable 'a dönüştürme](convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="a6b89-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="a6b89-124">Sırasız kümeler için sorgular</span><span class="sxs-lookup"><span data-stu-id="a6b89-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="a6b89-125">' İ uygulayan <xref:System.Collections.Generic.List%601> bir yerel koleksiyon ve ilişkisel bir veritabanındaki *sırasız kümeler* için yürütülen uzak sorgular sağlayan bir koleksiyon arasındaki önemli farkı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a6b89-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="a6b89-126"><xref:System.Collections.Generic.List%601>Dizin değerlerini kullanan Yöntemler, genellikle sıralanmamış bir küme için uzak bir sorgu üzerinden elde edilemez liste semantiğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a6b89-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="a6b89-127">Bu nedenle, bu tür yöntemler yerel yürütmeye izin <xref:System.Data.Linq.EntitySet%601> vermek için öğesini örtülü olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="a6b89-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b89-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6b89-128">See also</span></span>

- [<span data-ttu-id="a6b89-129">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="a6b89-129">Query Concepts</span></span>](query-concepts.md)
