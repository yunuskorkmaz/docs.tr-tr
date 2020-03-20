---
title: Entity SQL’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
ms.openlocfilehash: 880b81f2b6d4c4b893d28c919490f88dfb2a42e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150382"
---
# <a name="entity-sql-overview"></a><span data-ttu-id="a885d-102">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a885d-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a885d-103">Varlık Çerçevesi'ndeki kavramsal modelleri sorgulamanızı sağlayan SQL benzeri bir dildir.</span><span class="sxs-lookup"><span data-stu-id="a885d-103">is a SQL-like language that enables you to query conceptual models in the Entity Framework.</span></span> <span data-ttu-id="a885d-104">Kavramsal modeller verileri varlıklar ve ilişkiler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak temsil ediyor ve bu varlıkları ve ilişkileri SQL kullananlara tanıdık bir biçimde sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a885d-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  

 <span data-ttu-id="a885d-105">Varlık Çerçevesi, genel [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olarak depolamaya özgü sorgulara çevirmek için depolamaya özgü veri sağlayıcılarıyla birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="a885d-105">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="a885d-106">EntityClient sağlayıcısı, bir varlık [!INCLUDE[esql](../../../../../../includes/esql-md.md)] modeline karşı bir komut yürütmek ve skaler sonuçlar, sonuç kümeleri ve nesne grafikleri de dahil olmak üzere zengin veri türlerini döndürmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a885d-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="a885d-107">Nesneleri oluşturduğunuzda, <xref:System.Data.EntityClient.EntityCommand> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> bir sorgu dizesi atayarak depolanmış yordam adı veya sorgu metnini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a885d-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a885d-108">Bir <xref:System.Data.EntityClient.EntityDataReader> EDM'ye karşı <xref:System.Data.EntityClient.EntityCommand> bir uygulamanın sonuçlarını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a885d-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="a885d-109">Döndüren komutu <xref:System.Data.EntityClient.EntityDataReader>yürütmek <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>için , çağrı .</span><span class="sxs-lookup"><span data-stu-id="a885d-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="a885d-110">EntityClient sağlayıcısına ek olarak, Entity Framework, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguları kavramsal bir modele karşı yürütmek ve verileri varlık türlerinin örnekleri olan güçlü bir şekilde yazılan CLR nesneleri olarak döndürmek için kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a885d-110">In addition to the EntityClient provider, the Entity Framework enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="a885d-111">Daha fazla bilgi için [bkz.](../working-with-objects.md)</span><span class="sxs-lookup"><span data-stu-id="a885d-111">For more information, see [Working with Objects](../working-with-objects.md).</span></span>  
  
 <span data-ttu-id="a885d-112">Bu bölümde. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a885d-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a885d-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a885d-113">In This Section</span></span>  
 [<span data-ttu-id="a885d-114">Entity SQL ile Transact-SQL Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="a885d-114">How Entity SQL Differs from Transact-SQL</span></span>](how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="a885d-115">Entity SQL Hızlı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a885d-115">Entity SQL Quick Reference</span></span>](entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="a885d-116">Tür Sistemi</span><span class="sxs-lookup"><span data-stu-id="a885d-116">Type System</span></span>](type-system-entity-sql.md)  
  
 [<span data-ttu-id="a885d-117">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="a885d-117">Type Definitions</span></span>](type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="a885d-118">Oluşturma Türleri</span><span class="sxs-lookup"><span data-stu-id="a885d-118">Constructing Types</span></span>](constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="a885d-119">Sorgu Planını Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="a885d-119">Query Plan Caching</span></span>](query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="a885d-120">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="a885d-120">Namespaces</span></span>](namespaces-entity-sql.md)  
  
 [<span data-ttu-id="a885d-121">Tanımlayıcılar</span><span class="sxs-lookup"><span data-stu-id="a885d-121">Identifiers</span></span>](identifiers-entity-sql.md)  
  
 [<span data-ttu-id="a885d-122">Parametre</span><span class="sxs-lookup"><span data-stu-id="a885d-122">Parameters</span></span>](parameters-entity-sql.md)  
  
 [<span data-ttu-id="a885d-123">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="a885d-123">Variables</span></span>](variables-entity-sql.md)  
  
 [<span data-ttu-id="a885d-124">Desteklenmeyen İfadeler</span><span class="sxs-lookup"><span data-stu-id="a885d-124">Unsupported Expressions</span></span>](unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="a885d-125">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="a885d-125">Literals</span></span>](literals-entity-sql.md)  
  
 [<span data-ttu-id="a885d-126">Null Değişmez Değerler ve Tür Çıkarımı</span><span class="sxs-lookup"><span data-stu-id="a885d-126">Null Literals and Type Inference</span></span>](null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="a885d-127">Giriş Karakter Kümesi</span><span class="sxs-lookup"><span data-stu-id="a885d-127">Input Character Set</span></span>](input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="a885d-128">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="a885d-128">Query Expressions</span></span>](query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="a885d-129">Işlev</span><span class="sxs-lookup"><span data-stu-id="a885d-129">Functions</span></span>](functions-entity-sql.md)  
  
 [<span data-ttu-id="a885d-130">İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="a885d-130">Operator Precedence</span></span>](operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="a885d-131">Sayfalama</span><span class="sxs-lookup"><span data-stu-id="a885d-131">Paging</span></span>](paging-entity-sql.md)  
  
 [<span data-ttu-id="a885d-132">Karşılaştırma Semantiği</span><span class="sxs-lookup"><span data-stu-id="a885d-132">Comparison Semantics</span></span>](comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="a885d-133">İç İçe Geçmiş Entity SQL Sorguları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a885d-133">Composing Nested Entity SQL Queries</span></span>](composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="a885d-134">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="a885d-134">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="a885d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a885d-135">See also</span></span>

- [<span data-ttu-id="a885d-136">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a885d-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="a885d-137">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="a885d-137">Entity SQL Language</span></span>](entity-sql-language.md)
- [<span data-ttu-id="a885d-138">CSDL, SSDL ve MSL Belirtimleri</span><span class="sxs-lookup"><span data-stu-id="a885d-138">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
