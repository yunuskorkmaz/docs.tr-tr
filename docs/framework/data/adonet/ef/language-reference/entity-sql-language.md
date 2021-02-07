---
description: 'Hakkında daha fazla bilgi edinin: Entity SQL dil'
title: Entity SQL Dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: c05e561e5da3f9ee8788a25f8ca97b22444e109f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724576"
---
# <a name="entity-sql-language"></a><span data-ttu-id="2087c-103">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="2087c-103">Entity SQL Language</span></span>

<span data-ttu-id="2087c-104">Entity SQL, SQL 'e benzer bir depolama bağımsız sorgu dilidir.</span><span class="sxs-lookup"><span data-stu-id="2087c-104">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="2087c-105">Entity SQL, varlık verilerini nesneler olarak ya da tablolu bir biçimde sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2087c-105">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="2087c-106">Aşağıdaki durumlarda Entity SQL kullanmayı göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2087c-106">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="2087c-107">Bir sorgu, çalışma zamanında dinamik olarak oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2087c-107">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="2087c-108">Bu durumda, <xref:System.Data.Objects.ObjectQuery%601> çalışma zamanında Entity SQL bir sorgu dizesi oluşturmak yerine ' ın Sorgu Oluşturucu yöntemlerini kullanmayı da göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2087c-108">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="2087c-109">Model tanımının bir parçası olarak bir sorgu tanımlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="2087c-109">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="2087c-110">Bir veri modelinde yalnızca Entity SQL desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2087c-110">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="2087c-111">Daha fazla bilgi için bkz. [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="2087c-111">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="2087c-112">' İ kullanarak salt okuma varlık verilerini satır kümesi olarak döndürmek için EntityClient kullanılırken <xref:System.Data.EntityClient.EntityDataReader> .</span><span class="sxs-lookup"><span data-stu-id="2087c-112">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="2087c-113">Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](../entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="2087c-113">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="2087c-114">SQL tabanlı sorgu dillerinde zaten bir uzman varsa Entity SQL en doğal olarak görünebilir.</span><span class="sxs-lookup"><span data-stu-id="2087c-114">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="2087c-115">EntityClient sağlayıcı ile Entity SQL kullanma</span><span class="sxs-lookup"><span data-stu-id="2087c-115">Using Entity SQL with the EntityClient provider</span></span>  

 <span data-ttu-id="2087c-116">EntityClient sağlayıcı ile Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="2087c-116">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="2087c-117">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2087c-117">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="2087c-118">Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2087c-118">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="2087c-119">Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="2087c-119">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="2087c-120">Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="2087c-120">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="2087c-121">Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="2087c-121">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="2087c-122">Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="2087c-122">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="2087c-123">Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="2087c-123">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="2087c-124">Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme</span><span class="sxs-lookup"><span data-stu-id="2087c-124">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="2087c-125">Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme</span><span class="sxs-lookup"><span data-stu-id="2087c-125">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="2087c-126">Nasıl yapılır: Çok Biçimli Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="2087c-126">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="2087c-127">Nasıl yapılır: Nasıl yapılır: Navigate İşleci ile İlişkilerde Gezinme</span><span class="sxs-lookup"><span data-stu-id="2087c-127">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="2087c-128">Nesne sorgularıyla Entity SQL kullanma</span><span class="sxs-lookup"><span data-stu-id="2087c-128">Using Entity SQL with object queries</span></span>  

 <span data-ttu-id="2087c-129">Nesne sorgularıyla Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="2087c-129">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="2087c-130">[Nasıl yapılır: varlık türü nesneleri döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-130">[How to: Execute a Query that Returns Entity Type Objects](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-131">[Nasıl yapılır: Parametreli sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-131">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-132">[Nasıl yapılır: gezinme özelliklerini kullanarak Ilişkilerde gezinme](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-132">[How to: Navigate Relationships Using Navigation Properties](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-133">[Nasıl yapılır: User-Defined Işlevi çağırma](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-133">[How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-134">[Nasıl yapılır: verileri filtreleme](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-134">[How to: Filter Data](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-135">[Nasıl yapılır: verileri sıralama](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-135">[How to: Sort Data](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-136">[Nasıl yapılır: verileri gruplandırma](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-136">[How to: Group Data](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-137">[Nasıl yapılır: verileri toplama](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-137">[How to: Aggregate Data](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-138">[Nasıl yapılır: anonim tür nesneleri döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-138">[How to: Execute a Query that Returns Anonymous Type Objects](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-139">[Nasıl yapılır: temel türlerin bir koleksiyonunu döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-139">[How to: Execute a Query that Returns a Collection of Primitive Types](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-140">[Nasıl yapılır: bir EntityCollection 'da Ilgili nesneleri sorgulama](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-140">[How to: Query Related Objects in an EntityCollection](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-141">[Nasıl yapılır: Iki sorgunun birleşimini sıralama](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-141">[How to: Order the Union of Two Queries](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="2087c-142">[Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2087c-142">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2087c-143">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2087c-143">In This Section</span></span>  

 [<span data-ttu-id="2087c-144">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2087c-144">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="2087c-145">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2087c-145">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="2087c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2087c-146">See also</span></span>

- [<span data-ttu-id="2087c-147">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2087c-147">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="2087c-148">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2087c-148">Language Reference</span></span>](index.md)
