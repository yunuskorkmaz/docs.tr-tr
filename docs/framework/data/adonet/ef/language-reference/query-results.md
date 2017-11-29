---
title: "Sorgu Sonuçları"
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
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32133d1b6fce619fb9990ab89820b7f19b6a5926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="query-results"></a><span data-ttu-id="edc73-102">Sorgu Sonuçları</span><span class="sxs-lookup"><span data-stu-id="edc73-102">Query Results</span></span>
<span data-ttu-id="edc73-103">Sonra bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgu komut ağaçlarını dönüştürülür ve yürütülen, sorgu sonuçları genellikle aşağıdakilerden biri olarak döndürülür:</span><span class="sxs-lookup"><span data-stu-id="edc73-103">After a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is converted to command trees and executed, the query results are usually returned as one of the following:</span></span>  
  
-   <span data-ttu-id="edc73-104">Sıfır veya daha fazla belirtilmiş varlık nesnesi ya da projeksiyon, kavramsal modelde karmaşık türler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="edc73-104">A collection of zero or more typed entity objects or a projection of complex types in the conceptual model.</span></span>  
  
-   <span data-ttu-id="edc73-105">Kavramsal model tarafından desteklenen CLR türleri.</span><span class="sxs-lookup"><span data-stu-id="edc73-105">CLR types supported by the conceptual model.</span></span>  
  
-   <span data-ttu-id="edc73-106">Satır içi koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="edc73-106">Inline collections.</span></span>  
  
-   <span data-ttu-id="edc73-107">Anonim türler.</span><span class="sxs-lookup"><span data-stu-id="edc73-107">Anonymous types.</span></span>  
  
 <span data-ttu-id="edc73-108">Veri kaynağına karşı sorgu yürütüldü, sonuçları CLR türlerine gerçekleştirilip ve istemciye döndürülen.</span><span class="sxs-lookup"><span data-stu-id="edc73-108">When the query has executed against the data source, the results are materialized into CLR types and returned to the client.</span></span> <span data-ttu-id="edc73-109">Tüm nesne materialization tarafından gerçekleştirilen [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edc73-109">All object materialization is performed by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="edc73-110">Eşleştirilemez arasında kaynaklanan hataları [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ve CLR nesnesi materialization sırasında durum için özel durumlar neden olur.</span><span class="sxs-lookup"><span data-stu-id="edc73-110">Any errors that result from an inability to map between the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] and the CLR will cause exceptions to be thrown during object materialization.</span></span>  
  
 <span data-ttu-id="edc73-111">Sorgu yürütme ilkel kavramsal model türü döndürürse, tek başına ve kesilir CLR Türleri sonuçları oluşur [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edc73-111">If the query execution returns primitive conceptual model types, the results consist of CLR types that are stand-alone and disconnected from the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="edc73-112">Sorgu yazılan varlığın nesneler koleksiyonunu döndürürse, ancak tarafından temsil edilen <xref:System.Data.Objects.ObjectQuery%601>, bu türlerde nesne bağlamı tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="edc73-112">However, if the query returns a collection of typed entity objects, represented by <xref:System.Data.Objects.ObjectQuery%601>, those types are tracked by the object context.</span></span> <span data-ttu-id="edc73-113">Tüm nesne davranışı (örneğin, alt/üst koleksiyonları, değişiklik izleme, çok biçimlilik ve benzeri) olan tanımlandığı şekilde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edc73-113">All object behavior (such as child/parent collections, change tracking, polymorphism, and so on) are as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="edc73-114">Bu işlevsellik, kapasite tanımlandığı gibi kullanılabilir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="edc73-114">This functionality can be used in its capacity, as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="edc73-115">Daha fazla bilgi için bkz: [nesneleriyle çalışma](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="edc73-115">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="edc73-116">Struct türleri (örneğin, anonim türler ve null olabilir karmaşık türler) sorgularından döndürülen kullanılabilir `null` değeri.</span><span class="sxs-lookup"><span data-stu-id="edc73-116">Struct types returned from queries (such as anonymous types and nullable complex types) can be of `null` value.</span></span> <span data-ttu-id="edc73-117">Bir <xref:System.Data.Objects.DataClasses.EntityCollection%601> döndürülen varlığı özelliği de kullanılabilir `null` değeri.</span><span class="sxs-lookup"><span data-stu-id="edc73-117">An <xref:System.Data.Objects.DataClasses.EntityCollection%601> property of a returned entity can also be of `null` value.</span></span> <span data-ttu-id="edc73-118">Bu koleksiyon özelliği değil bir varlığın yansıtma sonuçlanabilir `null` arama gibi değeri <xref:System.Linq.Queryable.FirstOrDefault%2A> üzerinde bir <xref:System.Data.Objects.ObjectQuery%601> öğe sahip.</span><span class="sxs-lookup"><span data-stu-id="edc73-118">This can result from projecting the collection property of an entity that is of `null` value, such as calling <xref:System.Linq.Queryable.FirstOrDefault%2A> on an <xref:System.Data.Objects.ObjectQuery%601> that has no elements.</span></span>  
  
 <span data-ttu-id="edc73-119">Bazı durumlarda, bir sorgu yürütmesi sırasında gerçekleştirilmiş sonucu oluşturmak için görünebilir ancak sorgu sunucuda yürütülür ve varlık nesnesi hiçbir zaman CLR gerçekleştirilip.</span><span class="sxs-lookup"><span data-stu-id="edc73-119">In certain situations, a query might appear to generate a materialized result during its execution, but the query will be executed on the server and the entity object will never be materialized in the CLR.</span></span> <span data-ttu-id="edc73-120">Nesne materialization üzerinde yan etkileri bağlı olarak, bu sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="edc73-120">This can cause problems if you are depending on side effects of object materialization.</span></span>  
  
 <span data-ttu-id="edc73-121">Aşağıdaki örnek, özel bir sınıf içerir `MyContact`, ile bir `LastName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="edc73-121">The following example contains a custom class, `MyContact`, with a `LastName` property.</span></span> <span data-ttu-id="edc73-122">Zaman `LastName` özelliği ayarlanmış bir `count` değişkeni artar.</span><span class="sxs-lookup"><span data-stu-id="edc73-122">When the `LastName` property is set, a `count` variable is incremented.</span></span> <span data-ttu-id="edc73-123">İki aşağıdaki sorguları yürütün, ilk sorguyu artırır `count` ikinci sorguyu almayacak sırada.</span><span class="sxs-lookup"><span data-stu-id="edc73-123">If you execute the two following queries, the first query will increment `count` while the second query will not.</span></span> <span data-ttu-id="edc73-124">Bunun nedeni, ikinci sorgusunda `LastName` özelliği sonuçlarından öngörülen ve `MyContact` sınıfı hiçbir zaman oluşturulur, mağaza'sorguyu yürütmek için gerekli olmadığından.</span><span class="sxs-lookup"><span data-stu-id="edc73-124">This is because in the second query the `LastName` property is projected from the results and the `MyContact` class is never created, because it is not required to execute the query on the store.</span></span>  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
