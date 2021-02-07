---
description: 'Hakkında daha fazla bilgi edinin: uzak ve yerel yürütme'
title: Uzak ve Yerel Yürütme Karşılaştırması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: ea4d85faedd4a299da292029e64d77132e1a65a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695222"
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="fcdb3-103">Uzak ve Yerel Yürütme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="fcdb3-103">Remote vs. Local Execution</span></span>

<span data-ttu-id="fcdb3-104">Sorgularınızı uzaktan yürütmeye karar verebilirsiniz (yani, veritabanı altyapısı sorguyu veritabanına karşı yürütür) veya yerel olarak ( [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguyu yerel bir önbellekte yürütür).</span><span class="sxs-lookup"><span data-stu-id="fcdb3-104">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="fcdb3-105">Uzaktan Yürütme</span><span class="sxs-lookup"><span data-stu-id="fcdb3-105">Remote Execution</span></span>  

 <span data-ttu-id="fcdb3-106">Şu sorguyu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="fcdb3-106">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="fcdb3-107">Veritabanınızda binlerce sipariş satırı varsa, küçük bir alt kümeyi işlemeye kadar tümünü almak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-107">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="fcdb3-108">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, <xref:System.Data.Linq.EntitySet%601> sınıfı arabirimini uygular <xref:System.Linq.IQueryable> .</span><span class="sxs-lookup"><span data-stu-id="fcdb3-108">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="fcdb3-109">Bu yaklaşım, bu tür sorguların uzaktan yürütülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-109">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="fcdb3-110">Bu teknikten iki önemli avantaj akışı:</span><span class="sxs-lookup"><span data-stu-id="fcdb3-110">Two major benefits flow from this technique:</span></span>  
  
- <span data-ttu-id="fcdb3-111">Gereksiz veriler alınmadı.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-111">Unnecessary data is not retrieved.</span></span>  
  
- <span data-ttu-id="fcdb3-112">Veritabanı altyapısı tarafından yürütülen bir sorgu, veritabanı dizinleri nedeniyle genellikle daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-112">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="fcdb3-113">Yerel Yürütme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="fcdb3-113">Local Execution</span></span>  

 <span data-ttu-id="fcdb3-114">Diğer durumlarda, yerel önbellekte ilgili varlıkların tamamen kümesine sahip olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-114">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="fcdb3-115">Bu amaçla, <xref:System.Data.Linq.EntitySet%601> <xref:System.Data.Linq.EntitySet%601.Load%2A> tüm üyelerini açıkça yüklemek için yöntemini sağlar <xref:System.Data.Linq.EntitySet%601> .</span><span class="sxs-lookup"><span data-stu-id="fcdb3-115">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="fcdb3-116">Zaten yüklüyse <xref:System.Data.Linq.EntitySet%601> , sonraki sorgular yerel olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-116">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="fcdb3-117">Bu yaklaşım iki şekilde yardımcı olur:</span><span class="sxs-lookup"><span data-stu-id="fcdb3-117">This approach helps in two ways:</span></span>  
  
- <span data-ttu-id="fcdb3-118">Tamamlanma kümesinin yerel olarak veya birden çok kez kullanılması gerekiyorsa, uzak sorgulardan ve ilişkili gecikmelerin önüne kurtulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-118">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
- <span data-ttu-id="fcdb3-119">Varlık, bir bütün varlık olarak seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-119">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="fcdb3-120">Aşağıdaki kod parçası, yerel yürütmenin nasıl elde edilebilir olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="fcdb3-120">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="fcdb3-121">Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fcdb3-121">Comparison</span></span>  

 <span data-ttu-id="fcdb3-122">Bu iki özellik, seçeneklerin güçlü bir birleşimini sağlar: büyük koleksiyonlar için uzaktan yürütme ve küçük koleksiyonlar için yerel yürütme ve tüm koleksiyonun gerekli olduğu durumlar.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-122">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="fcdb3-123">Uzaktan yürütmeyi <xref:System.Linq.IQueryable> , bellek içi bir koleksiyon ile ve yerel yürütme aracılığıyla uyguırın <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="fcdb3-123">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="fcdb3-124">Yerel yürütmeyi zorlamak için (yani, <xref:System.Collections.Generic.IEnumerable%601> ) bkz. [bir türü genel IEnumerable 'a dönüştürme](convert-a-type-to-a-generic-ienumerable.md).</span><span class="sxs-lookup"><span data-stu-id="fcdb3-124">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="fcdb3-125">Sırasız kümeler için sorgular</span><span class="sxs-lookup"><span data-stu-id="fcdb3-125">Queries Against Unordered Sets</span></span>  

 <span data-ttu-id="fcdb3-126">' İ uygulayan bir yerel koleksiyon <xref:System.Collections.Generic.List%601> ve ilişkisel bir veritabanındaki *sırasız kümeler* için yürütülen uzak sorgular sağlayan bir koleksiyon arasındaki önemli farkı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-126">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="fcdb3-127"><xref:System.Collections.Generic.List%601> Dizin değerlerini kullanan Yöntemler, genellikle sıralanmamış bir küme için uzak bir sorgu üzerinden elde edilemez liste semantiğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-127"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="fcdb3-128">Bu nedenle, bu tür yöntemler yerel yürütmeye izin vermek için öğesini örtülü olarak yükler <xref:System.Data.Linq.EntitySet%601> .</span><span class="sxs-lookup"><span data-stu-id="fcdb3-128">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdb3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcdb3-129">See also</span></span>

- [<span data-ttu-id="fcdb3-130">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="fcdb3-130">Query Concepts</span></span>](query-concepts.md)
