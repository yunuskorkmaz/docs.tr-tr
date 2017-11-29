---
title: "Varlık SQL genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 301a934cad59b14d1a65a1e98247490d578e6866
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-overview"></a><span data-ttu-id="f7046-102">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="f7046-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f7046-103">kavramsal modellerde sorgu olanak tanıyan bir SQL benzeri bir dildir [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7046-103"> is a SQL-like language that enables you to query conceptual models in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="f7046-104">Kavramsal modeller varlıkları ve ilişkileri, verilerini temsil eden ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu varlıkları ve ilişkileri SQL kullanmış olan olanlar için tanıdık bir biçimde sorgu olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f7046-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
  
 <span data-ttu-id="f7046-105">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Çalışır genel çevirmek için depolama özgü veri sağlayıcılarıyla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] içine depolama özgü sorgular.</span><span class="sxs-lookup"><span data-stu-id="f7046-105">The [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="f7046-106">EntityClient sağlayıcısı yürütmek için bir yol sağlayan bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] komutu karşı bir varlık modeli ve zengin skaler sonuçları, sonuç kümeleri ve nesne grafiklerinin dahil olmak üzere veri türlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7046-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="f7046-107">Oluşturduğunuzda <xref:System.Data.EntityClient.EntityCommand> nesneleri belirtebilirsiniz bir saklı yordam adı veya bir sorgu metnini atayarak bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu dizesi için kendi <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f7046-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f7046-108"><xref:System.Data.EntityClient.EntityDataReader> Yürütme sonuçlarını gösterir bir <xref:System.Data.EntityClient.EntityCommand> EDM karşı.</span><span class="sxs-lookup"><span data-stu-id="f7046-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="f7046-109">Döndürür komutu çalıştırmak için <xref:System.Data.EntityClient.EntityDataReader>, çağrı <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7046-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="f7046-110">EntityClient sağlayıcısı yanı sıra [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] kullanmanıza olanak tanır [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal model sorgu yürütebilir ve varlık türleri örneklerini kesin türü belirtilmiş CLR nesneler veri döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="f7046-110">In addition to the EntityClient provider, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="f7046-111">Daha fazla bilgi için bkz: [nesneleriyle çalışma](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f7046-111">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="f7046-112">Bu bölümde hakkında kavramsal bilgiler verilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7046-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7046-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f7046-113">In This Section</span></span>  
 [<span data-ttu-id="f7046-114">Varlık SQL Transact-SQL nasıl farklıdır</span><span class="sxs-lookup"><span data-stu-id="f7046-114">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="f7046-115">Varlık SQL hızlı başvuru</span><span class="sxs-lookup"><span data-stu-id="f7046-115">Entity SQL Quick Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="f7046-116">Tür sistemi</span><span class="sxs-lookup"><span data-stu-id="f7046-116">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [<span data-ttu-id="f7046-117">Tür tanımları</span><span class="sxs-lookup"><span data-stu-id="f7046-117">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="f7046-118">Türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7046-118">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="f7046-119">Sorgu planı önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="f7046-119">Query Plan Caching</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="f7046-120">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="f7046-120">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [<span data-ttu-id="f7046-121">Tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="f7046-121">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [<span data-ttu-id="f7046-122">Parametreleri</span><span class="sxs-lookup"><span data-stu-id="f7046-122">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [<span data-ttu-id="f7046-123">Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f7046-123">Variables</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [<span data-ttu-id="f7046-124">Desteklenmeyen ifadeler</span><span class="sxs-lookup"><span data-stu-id="f7046-124">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="f7046-125">Değişmez değerler</span><span class="sxs-lookup"><span data-stu-id="f7046-125">Literals</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [<span data-ttu-id="f7046-126">Null değişmez değerler ve tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="f7046-126">Null Literals and Type Inference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="f7046-127">Giriş karakter kümesi</span><span class="sxs-lookup"><span data-stu-id="f7046-127">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="f7046-128">Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f7046-128">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="f7046-129">İşlevler</span><span class="sxs-lookup"><span data-stu-id="f7046-129">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [<span data-ttu-id="f7046-130">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="f7046-130">Operator Precedence</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="f7046-131">Disk belleği</span><span class="sxs-lookup"><span data-stu-id="f7046-131">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [<span data-ttu-id="f7046-132">Karşılaştırma semantiği</span><span class="sxs-lookup"><span data-stu-id="f7046-132">Comparison Semantics</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="f7046-133">İç içe geçmiş varlık SQL sorguları oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7046-133">Composing Nested Entity SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="f7046-134">Yapılandırılmış boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="f7046-134">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="f7046-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7046-135">See Also</span></span>  
 [<span data-ttu-id="f7046-136">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f7046-136">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f7046-137">Varlık SQL dili</span><span class="sxs-lookup"><span data-stu-id="f7046-137">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [<span data-ttu-id="f7046-138">CSDL, SSDL ve MSL belirtimleri</span><span class="sxs-lookup"><span data-stu-id="f7046-138">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
