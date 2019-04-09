---
title: Entity SQL Dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 09ec1a5518ec0847b54394449f32b3068c811577
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140939"
---
# <a name="entity-sql-language"></a><span data-ttu-id="61a56-102">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="61a56-102">Entity SQL Language</span></span>
<span data-ttu-id="61a56-103">Entity SQL SQL'e benzeyen bir depolamadan bağımsız sorgu dilidir.</span><span class="sxs-lookup"><span data-stu-id="61a56-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="61a56-104">Entity SQL sorgu bir varlığın verilerinin nesneleri ya da tablo biçiminde sağlar.</span><span class="sxs-lookup"><span data-stu-id="61a56-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="61a56-105">Aşağıdaki durumlarda varlık SQL kullanmayı düşünmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="61a56-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="61a56-106">Ne zaman bir sorgunun çalışma zamanında dinamik olarak oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="61a56-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="61a56-107">Bu durumda, aynı zamanda sorgu oluşturucu yöntemleri kullanılarak dikkate almanız gereken <xref:System.Data.Objects.ObjectQuery%601> varlık SQL oluşturmak yerine sorgu zamanında dizesi.</span><span class="sxs-lookup"><span data-stu-id="61a56-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="61a56-108">Model tanımının bir parçası bir sorgu tanımlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="61a56-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="61a56-109">Yalnızca varlık SQL veri modelinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="61a56-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="61a56-110">Daha fazla bilgi için [QueryView öğesi (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="61a56-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
-   <span data-ttu-id="61a56-111">Satır kümeleri kullanarak olarak salt okunur varlık verilerini döndürmek için EntityClient kullanırken bir <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="61a56-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="61a56-112">Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="61a56-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="61a56-113">SQL tabanlı sorgu dillerde Uzman zaten varsa, size en doğal varlık SQL gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="61a56-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="61a56-114">Entity SQL EntityClient sağlayıcısı ile kullanma</span><span class="sxs-lookup"><span data-stu-id="61a56-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="61a56-115">Entity SQL EntityClient sağlayıcısı ile kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="61a56-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="61a56-116">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="61a56-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="61a56-117">Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="61a56-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="61a56-118">Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="61a56-119">Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="61a56-120">Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="61a56-121">Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="61a56-122">Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="61a56-123">Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="61a56-124">Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="61a56-125">Nasıl yapılır: Çok Biçimli Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="61a56-126">Nasıl yapılır: Nasıl yapılır: Navigate İşleci ile İlişkilerde Gezinme</span><span class="sxs-lookup"><span data-stu-id="61a56-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="61a56-127">Entity SQL nesnesi sorgularıyla kullanma</span><span class="sxs-lookup"><span data-stu-id="61a56-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="61a56-128">Entity SQL ile nesne sorguları kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="61a56-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="61a56-129">Nasıl yapılır: Varlık türü nesnesi döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [<span data-ttu-id="61a56-130">Nasıl yapılır: Parametreli bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-130">How to: Execute a Parameterized Query</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [<span data-ttu-id="61a56-131">Nasıl yapılır: Gezinti özellikleri kullanarak ilişkilerde gezinme</span><span class="sxs-lookup"><span data-stu-id="61a56-131">How to: Navigate Relationships Using Navigation Properties</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [<span data-ttu-id="61a56-132">Nasıl yapılır: Bir kullanıcı tanımlı işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="61a56-132">How to: Call a User-Defined Function</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [<span data-ttu-id="61a56-133">Nasıl yapılır: Verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="61a56-133">How to: Filter Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [<span data-ttu-id="61a56-134">Nasıl yapılır: Verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="61a56-134">How to: Sort Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [<span data-ttu-id="61a56-135">Nasıl yapılır: Verileri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="61a56-135">How to: Group Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [<span data-ttu-id="61a56-136">Nasıl yapılır: Veri toplama</span><span class="sxs-lookup"><span data-stu-id="61a56-136">How to: Aggregate Data</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [<span data-ttu-id="61a56-137">Nasıl yapılır: Anonim türdeki nesneleri döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [<span data-ttu-id="61a56-138">Nasıl yapılır: Temel türlerin koleksiyonunu döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="61a56-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [<span data-ttu-id="61a56-139">Nasıl yapılır: Bir entitycollection'ın ilgili nesneleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="61a56-139">How to: Query Related Objects in an EntityCollection</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [<span data-ttu-id="61a56-140">Nasıl yapılır: Sırada iki sorgu birleşimi</span><span class="sxs-lookup"><span data-stu-id="61a56-140">How to: Order the Union of Two Queries</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [<span data-ttu-id="61a56-141">Nasıl yapılır: Sorgu sonuçları sayfasından</span><span class="sxs-lookup"><span data-stu-id="61a56-141">How to: Page Through Query Results</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a><span data-ttu-id="61a56-142">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="61a56-142">In This Section</span></span>  
 [<span data-ttu-id="61a56-143">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="61a56-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="61a56-144">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="61a56-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="61a56-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61a56-145">See also</span></span>

- [<span data-ttu-id="61a56-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="61a56-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
- [<span data-ttu-id="61a56-147">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="61a56-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
