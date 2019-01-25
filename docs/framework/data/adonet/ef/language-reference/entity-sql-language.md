---
title: Entity SQL dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 0c698f04c3b95ffb204a20d41e91ef3f6210c5d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494106"
---
# <a name="entity-sql-language"></a><span data-ttu-id="27f46-102">Entity SQL dili</span><span class="sxs-lookup"><span data-stu-id="27f46-102">Entity SQL Language</span></span>
<span data-ttu-id="27f46-103">Entity SQL SQL'e benzeyen bir depolamadan bağımsız sorgu dilidir.</span><span class="sxs-lookup"><span data-stu-id="27f46-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="27f46-104">Entity SQL sorgu bir varlığın verilerinin nesneleri ya da tablo biçiminde sağlar.</span><span class="sxs-lookup"><span data-stu-id="27f46-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="27f46-105">Aşağıdaki durumlarda varlık SQL kullanmayı düşünmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="27f46-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="27f46-106">Ne zaman bir sorgunun çalışma zamanında dinamik olarak oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27f46-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="27f46-107">Bu durumda, aynı zamanda sorgu oluşturucu yöntemleri kullanılarak dikkate almanız gereken <xref:System.Data.Objects.ObjectQuery%601> varlık SQL oluşturmak yerine sorgu zamanında dizesi.</span><span class="sxs-lookup"><span data-stu-id="27f46-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="27f46-108">Model tanımının bir parçası bir sorgu tanımlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="27f46-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="27f46-109">Yalnızca varlık SQL veri modelinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="27f46-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="27f46-110">Daha fazla bilgi için [QueryView öğesi (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="27f46-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
-   <span data-ttu-id="27f46-111">Satır kümeleri kullanarak olarak salt okunur varlık verilerini döndürmek için EntityClient kullanırken bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="27f46-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="27f46-112">Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="27f46-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="27f46-113">SQL tabanlı sorgu dillerde Uzman zaten varsa, size en doğal varlık SQL gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="27f46-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="27f46-114">Entity SQL EntityClient sağlayıcısı ile kullanma</span><span class="sxs-lookup"><span data-stu-id="27f46-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="27f46-115">Entity SQL EntityClient sağlayıcısı ile kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="27f46-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="27f46-116">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="27f46-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="27f46-117">Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="27f46-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="27f46-118">Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="27f46-119">Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="27f46-120">Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="27f46-121">Nasıl yapılır: Karmaşık türler döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="27f46-122">Nasıl yapılır: İç içe geçmiş koleksiyonlar döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="27f46-123">Nasıl yapılır: EntityCommand kullanarak parametreli varlık SQL sorgusu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="27f46-124">Nasıl yapılır: EntityCommand kullanarak parametreli saklı yordam yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="27f46-125">Nasıl yapılır: Çok biçimli sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="27f46-126">Nasıl yapılır: İle ilişkilerde gezinme işleci gidin</span><span class="sxs-lookup"><span data-stu-id="27f46-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="27f46-127">Entity SQL nesnesi sorgularıyla kullanma</span><span class="sxs-lookup"><span data-stu-id="27f46-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="27f46-128">Entity SQL ile nesne sorguları kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="27f46-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="27f46-129">Nasıl yapılır: Varlık türü nesnesi döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](https://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="27f46-130">Nasıl yapılır: Parametreli bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-130">How to: Execute a Parameterized Query</span></span>](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="27f46-131">Nasıl yapılır: Gezinti özellikleri kullanarak ilişkilerde gezinme</span><span class="sxs-lookup"><span data-stu-id="27f46-131">How to: Navigate Relationships Using Navigation Properties</span></span>](https://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="27f46-132">Nasıl yapılır: Bir kullanıcı tanımlı işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="27f46-132">How to: Call a User-Defined Function</span></span>](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="27f46-133">Nasıl yapılır: Verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="27f46-133">How to: Filter Data</span></span>](https://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="27f46-134">Nasıl yapılır: Verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="27f46-134">How to: Sort Data</span></span>](https://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="27f46-135">Nasıl yapılır: Verileri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="27f46-135">How to: Group Data</span></span>](https://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="27f46-136">Nasıl yapılır: Veri toplama</span><span class="sxs-lookup"><span data-stu-id="27f46-136">How to: Aggregate Data</span></span>](https://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="27f46-137">Nasıl yapılır: Anonim türdeki nesneleri döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="27f46-138">Nasıl yapılır: Temel türlerin koleksiyonunu döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="27f46-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](https://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="27f46-139">Nasıl yapılır: Bir entitycollection'ın ilgili nesneleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="27f46-139">How to: Query Related Objects in an EntityCollection</span></span>](https://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="27f46-140">Nasıl yapılır: Sırada iki sorgu birleşimi</span><span class="sxs-lookup"><span data-stu-id="27f46-140">How to: Order the Union of Two Queries</span></span>](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="27f46-141">Nasıl yapılır: Sorgu sonuçları sayfasından</span><span class="sxs-lookup"><span data-stu-id="27f46-141">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="27f46-142">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="27f46-142">In This Section</span></span>  
 [<span data-ttu-id="27f46-143">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="27f46-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="27f46-144">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="27f46-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="27f46-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27f46-145">See also</span></span>
- [<span data-ttu-id="27f46-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="27f46-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
- [<span data-ttu-id="27f46-147">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="27f46-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
