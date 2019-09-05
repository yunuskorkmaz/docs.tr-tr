---
title: Entity SQL Dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251011"
---
# <a name="entity-sql-language"></a><span data-ttu-id="a36dc-102">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="a36dc-102">Entity SQL Language</span></span>
<span data-ttu-id="a36dc-103">Entity SQL, SQL 'e benzer bir depolama bağımsız sorgu dilidir.</span><span class="sxs-lookup"><span data-stu-id="a36dc-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="a36dc-104">Entity SQL, varlık verilerini nesneler olarak ya da tablolu bir biçimde sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a36dc-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="a36dc-105">Aşağıdaki durumlarda Entity SQL kullanmayı göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a36dc-105">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="a36dc-106">Bir sorgu, çalışma zamanında dinamik olarak oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a36dc-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="a36dc-107">Bu durumda, çalışma zamanında Entity SQL bir sorgu dizesi oluşturmak yerine ' ın <xref:System.Data.Objects.ObjectQuery%601> Sorgu Oluşturucu yöntemlerini kullanmayı da göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a36dc-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="a36dc-108">Model tanımının bir parçası olarak bir sorgu tanımlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="a36dc-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="a36dc-109">Bir veri modelinde yalnızca Entity SQL desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a36dc-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="a36dc-110">Daha fazla bilgi için bkz. [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="a36dc-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="a36dc-111">' İ kullanarak <xref:System.Data.EntityClient.EntityDataReader>salt okuma varlık verilerini satır kümesi olarak döndürmek için EntityClient kullanılırken.</span><span class="sxs-lookup"><span data-stu-id="a36dc-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="a36dc-112">Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](../entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="a36dc-112">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="a36dc-113">SQL tabanlı sorgu dillerinde zaten bir uzman varsa Entity SQL en doğal olarak görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a36dc-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="a36dc-114">EntityClient sağlayıcı ile Entity SQL kullanma</span><span class="sxs-lookup"><span data-stu-id="a36dc-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="a36dc-115">EntityClient sağlayıcı ile Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="a36dc-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="a36dc-116">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="a36dc-116">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="a36dc-117">Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a36dc-117">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="a36dc-118">Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="a36dc-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="a36dc-119">Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="a36dc-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="a36dc-120">Nasıl yapılır: RefType sonuçları döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="a36dc-120">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="a36dc-121">Nasıl yapılır: Karmaşık türler döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="a36dc-121">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="a36dc-122">Nasıl yapılır: Iç Içe geçmiş Koleksiyonlar döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="a36dc-122">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="a36dc-123">Nasıl yapılır: EntityCommand kullanarak parametreli Entity SQL sorgusu yürütme</span><span class="sxs-lookup"><span data-stu-id="a36dc-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="a36dc-124">Nasıl yapılır: EntityCommand kullanarak parametreli saklı yordam yürütme</span><span class="sxs-lookup"><span data-stu-id="a36dc-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="a36dc-125">Nasıl yapılır: Polimorfik sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="a36dc-125">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="a36dc-126">Nasıl yapılır: Gezinme Işleciyle Ilişkilerde gezinme</span><span class="sxs-lookup"><span data-stu-id="a36dc-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="a36dc-127">Nesne sorgularıyla Entity SQL kullanma</span><span class="sxs-lookup"><span data-stu-id="a36dc-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="a36dc-128">Nesne sorgularıyla Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="a36dc-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="a36dc-129">[Nasıl yapılır: Varlık türü nesneleri döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-129">[How to: Execute a Query that Returns Entity Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-130">[Nasıl yapılır: Parametreli sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-130">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-131">[Nasıl yapılır: Gezinti özelliklerini kullanarak Ilişkilerde gezin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-131">[How to: Navigate Relationships Using Navigation Properties](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-132">[Nasıl yapılır: Kullanıcı tanımlı bir Işlev çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-132">[How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-133">[Nasıl yapılır: Verileri Filtrele](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-133">[How to: Filter Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-134">[Nasıl yapılır: Verileri sıralama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-134">[How to: Sort Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-135">[Nasıl yapılır: Verileri gruplandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-135">[How to: Group Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-136">[Nasıl yapılır: Verileri topla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-136">[How to: Aggregate Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-137">[Nasıl yapılır: Anonim tür nesneleri döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-137">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-138">[Nasıl yapılır: Temel türlerin bir koleksiyonunu döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-138">[How to: Execute a Query that Returns a Collection of Primitive Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-139">[Nasıl yapılır: Bir EntityCollection 'da Ilişkili nesneleri sorgulama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-139">[How to: Query Related Objects in an EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-140">[Nasıl yapılır: Iki sorgunun birleşimini sıralama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-140">[How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="a36dc-141">[Nasıl yapılır: Sorgu sonuçları aracılığıyla sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a36dc-141">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a36dc-142">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a36dc-142">In This Section</span></span>  
 [<span data-ttu-id="a36dc-143">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a36dc-143">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="a36dc-144">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a36dc-144">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="a36dc-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a36dc-145">See also</span></span>

- [<span data-ttu-id="a36dc-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a36dc-146">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="a36dc-147">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a36dc-147">Language Reference</span></span>](index.md)
