---
title: Entity SQL’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 100d616462cd76e1dde8fc855787ec3118842fc8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073476"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="c4e43-102">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c4e43-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c4e43-103">kavramsal modellerde sorgu olanak tanıyan SQL benzeri bir dil olan [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4e43-103">is a SQL-like language that enables you to query conceptual models in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="c4e43-104">Kavramsal modeller varlıklar ve ilişkiler, verilerini temsil eden ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu varlıklar ve ilişkiler SQL kullanmış olan bu tanıdık bir biçimde sorgulamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4e43-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
  
 <span data-ttu-id="c4e43-105">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] Çalışır genel çevirmek için depolama özgü veri sağlayıcılarıyla [!INCLUDE[esql](../../../../../../includes/esql-md.md)] depolama özgü sorgulara.</span><span class="sxs-lookup"><span data-stu-id="c4e43-105">The [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="c4e43-106">EntityClient sağlayıcı yürütmek için bir yol sağlayan bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] komut karşı bir varlık modeli ve zengin skaler sonuçları, sonuç kümesi ve nesne grafiklerini de dahil olmak üzere veri türlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4e43-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="c4e43-107">Oluşturduğunuzda <xref:System.Data.EntityClient.EntityCommand> nesnelerini belirtebileceğiniz bir saklı yordam adı veya bir sorgu metnini atayarak bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu dizesi için kendi <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c4e43-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c4e43-108"><xref:System.Data.EntityClient.EntityDataReader> Çalıştırma sonuçlarını gösteren bir <xref:System.Data.EntityClient.EntityCommand> EDM karşı.</span><span class="sxs-lookup"><span data-stu-id="c4e43-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="c4e43-109">Döndüren komutu yürütmek için <xref:System.Data.EntityClient.EntityDataReader>, çağrı <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4e43-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="c4e43-110">EntityClient sağlayıcısı yanı sıra [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] kullanmanızı sağlayan [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modeline karşı sorgular yürütün ve varlık türleri örnekleri olan türü kesin belirlenmiş CLR nesnesi verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4e43-110">In addition to the EntityClient provider, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="c4e43-111">Daha fazla bilgi için [nesneleriyle çalışma](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="c4e43-111">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="c4e43-112">Bu bölümde, hakkında kavramsal bilgiler verilmektedir. [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4e43-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4e43-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c4e43-113">In This Section</span></span>  
 [<span data-ttu-id="c4e43-114">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="c4e43-114">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="c4e43-115">Entity SQL Hızlı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4e43-115">Entity SQL Quick Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="c4e43-116">Tür Sistemi</span><span class="sxs-lookup"><span data-stu-id="c4e43-116">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-117">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="c4e43-117">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-118">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="c4e43-118">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-119">Sorgu Planını Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="c4e43-119">Query Plan Caching</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-120">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="c4e43-120">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-121">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="c4e43-121">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-122">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4e43-122">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-123">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c4e43-123">Variables</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-124">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="c4e43-124">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-125">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="c4e43-125">Literals</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-126">Null Değişmez Değerler ve Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="c4e43-126">Null Literals and Type Inference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-127">Giriş Karakter Kümesi</span><span class="sxs-lookup"><span data-stu-id="c4e43-127">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-128">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="c4e43-128">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-129">İşlevler</span><span class="sxs-lookup"><span data-stu-id="c4e43-129">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-130">İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="c4e43-130">Operator Precedence</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-131">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="c4e43-131">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-132">Karşılaştırma Semantiği</span><span class="sxs-lookup"><span data-stu-id="c4e43-132">Comparison Semantics</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="c4e43-133">İç İçe Geçmiş Entity SQL Sorguları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4e43-133">Composing Nested Entity SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="c4e43-134">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="c4e43-134">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="c4e43-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4e43-135">See also</span></span>

- [<span data-ttu-id="c4e43-136">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4e43-136">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="c4e43-137">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="c4e43-137">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="c4e43-138">CSDL, SSDL ve MSL belirtimleri</span><span class="sxs-lookup"><span data-stu-id="c4e43-138">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
