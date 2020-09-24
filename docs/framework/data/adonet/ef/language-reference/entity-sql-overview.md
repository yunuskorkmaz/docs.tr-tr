---
title: Entity SQL’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: e9a5117984380938e48e0cd1113107c74389480f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148133"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="f9881-102">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f9881-102">Entity SQL Overview</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="f9881-103">, Entity Framework kavramsal modelleri sorgulamanızı sağlayan bir SQL benzeri dildir.</span><span class="sxs-lookup"><span data-stu-id="f9881-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="f9881-104">Kavramsal modeller verileri varlıklar ve ilişkiler olarak temsil eder ve [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bu varlıkları ve ılışkılerı SQL kullanan kullanıcılara tanıdık bir biçimde sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9881-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="f9881-105">Entity Framework, genel olarak depolamaya özgü sorgulara çevirmek için depolama 'ya özgü veri sağlayıcılarıyla birlikte kullanılabilir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f9881-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="f9881-106">EntityClient sağlayıcısı bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] varlık modeline karşı bir komut yürütmek ve skaler sonuçlar, sonuç kümeleri ve nesne grafikleri dahil zengin veri türlerini döndürmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9881-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="f9881-107"><xref:System.Data.EntityClient.EntityCommand>Nesneleri oluştururken, özelliğine bir sorgu dizesi atayarak bir saklı yordam adı veya bir sorgu metni belirtebilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f9881-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f9881-108">, <xref:System.Data.EntityClient.EntityDataReader> BIR EDM için yürütme sonuçlarını sunar <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="f9881-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="f9881-109">Öğesini döndüren komutunu yürütmek için <xref:System.Data.EntityClient.EntityDataReader> çağrısı yapın <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> .</span><span class="sxs-lookup"><span data-stu-id="f9881-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="f9881-110">EntityClient sağlayıcısına ek olarak Entity Framework, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları kavramsal bir modele karşı yürütmek ve verileri varlık türlerinin örnekleri olan kesin türü BELIRTILMIŞ clr nesneleri olarak döndürmek için kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9881-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="f9881-111">Daha fazla bilgi için bkz. [nesneleriyle çalışma](../working-with-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f9881-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="f9881-112">Bu bölüm hakkında kavramsal bilgiler sağlar [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f9881-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9881-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f9881-113">In This Section</span></span>  

 [<span data-ttu-id="f9881-114">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="f9881-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="f9881-115">Entity SQL Hızlı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9881-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="f9881-116">Tür sistemi</span><span class="sxs-lookup"><span data-stu-id="f9881-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="f9881-117">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="f9881-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="f9881-118">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="f9881-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="f9881-119">Sorgu Planını Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="f9881-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="f9881-120">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="f9881-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="f9881-121">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="f9881-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="f9881-122">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9881-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="f9881-123">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="f9881-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="f9881-124">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="f9881-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="f9881-125">Değişmez Değerler</span><span class="sxs-lookup"><span data-stu-id="f9881-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="f9881-126">Null Değişmez Değerler ve Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="f9881-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="f9881-127">Giriş Karakter Kümesi</span><span class="sxs-lookup"><span data-stu-id="f9881-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="f9881-128">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f9881-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="f9881-129">İşlevler</span><span class="sxs-lookup"><span data-stu-id="f9881-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="f9881-130">İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="f9881-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="f9881-131">Sayfalama</span><span class="sxs-lookup"><span data-stu-id="f9881-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="f9881-132">Karşılaştırma Semantiği</span><span class="sxs-lookup"><span data-stu-id="f9881-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="f9881-133">İç İçe Geçmiş Entity SQL Sorguları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9881-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="f9881-134">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="f9881-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="f9881-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9881-135">See also</span></span>

- [<span data-ttu-id="f9881-136">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9881-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f9881-137">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="f9881-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="f9881-138">CSDL, SSDL ve MSL Belirtimleri</span><span class="sxs-lookup"><span data-stu-id="f9881-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
