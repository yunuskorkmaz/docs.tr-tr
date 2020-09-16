---
title: Entity SQL Dili
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 2600b7626ebc5196c702f2d1e3159fd9549227f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553388"
---
# <a name="entity-sql-language"></a><span data-ttu-id="17ac3-102">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="17ac3-102">Entity SQL Language</span></span>
<span data-ttu-id="17ac3-103">Entity SQL, SQL 'e benzer bir depolama bağımsız sorgu dilidir.</span><span class="sxs-lookup"><span data-stu-id="17ac3-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="17ac3-104">Entity SQL, varlık verilerini nesneler olarak ya da tablolu bir biçimde sorgulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="17ac3-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="17ac3-105">Aşağıdaki durumlarda Entity SQL kullanmayı göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="17ac3-105">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="17ac3-106">Bir sorgu, çalışma zamanında dinamik olarak oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17ac3-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="17ac3-107">Bu durumda, <xref:System.Data.Objects.ObjectQuery%601> çalışma zamanında Entity SQL bir sorgu dizesi oluşturmak yerine ' ın Sorgu Oluşturucu yöntemlerini kullanmayı da göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="17ac3-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="17ac3-108">Model tanımının bir parçası olarak bir sorgu tanımlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="17ac3-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="17ac3-109">Bir veri modelinde yalnızca Entity SQL desteklenir.</span><span class="sxs-lookup"><span data-stu-id="17ac3-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="17ac3-110">Daha fazla bilgi için bkz. [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="17ac3-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="17ac3-111">' İ kullanarak salt okuma varlık verilerini satır kümesi olarak döndürmek için EntityClient kullanılırken <xref:System.Data.EntityClient.EntityDataReader> .</span><span class="sxs-lookup"><span data-stu-id="17ac3-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="17ac3-112">Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](../entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="17ac3-112">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="17ac3-113">SQL tabanlı sorgu dillerinde zaten bir uzman varsa Entity SQL en doğal olarak görünebilir.</span><span class="sxs-lookup"><span data-stu-id="17ac3-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="17ac3-114">EntityClient sağlayıcı ile Entity SQL kullanma</span><span class="sxs-lookup"><span data-stu-id="17ac3-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="17ac3-115">EntityClient sağlayıcı ile Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="17ac3-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="17ac3-116">Entity Framework için EntityClient Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="17ac3-116">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="17ac3-117">Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="17ac3-117">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="17ac3-118">Nasıl yapılır: PrimitiveType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="17ac3-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="17ac3-119">Nasıl yapılır: StructuralType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="17ac3-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="17ac3-120">Nasıl yapılır: RefType Sonuçları Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="17ac3-120">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="17ac3-121">Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="17ac3-121">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="17ac3-122">Nasıl yapılır: İç İçe Geçmiş Koleksiyonlar Döndüren Bir Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="17ac3-122">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="17ac3-123">Nasıl yapılır: EntityCommand Kullanarak Parametreli Entity SQL Sorgusu Yürütme</span><span class="sxs-lookup"><span data-stu-id="17ac3-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="17ac3-124">Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme</span><span class="sxs-lookup"><span data-stu-id="17ac3-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="17ac3-125">Nasıl yapılır: Çok Biçimli Sorgu Yürütme</span><span class="sxs-lookup"><span data-stu-id="17ac3-125">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="17ac3-126">Nasıl yapılır: Nasıl yapılır: Navigate İşleci ile İlişkilerde Gezinme</span><span class="sxs-lookup"><span data-stu-id="17ac3-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="17ac3-127">Nesne sorgularıyla Entity SQL kullanma</span><span class="sxs-lookup"><span data-stu-id="17ac3-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="17ac3-128">Nesne sorgularıyla Entity SQL kullanmak istiyorsanız, daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="17ac3-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="17ac3-129">[Nasıl yapılır: varlık türü nesneleri döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-129">[How to: Execute a Query that Returns Entity Type Objects](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-130">[Nasıl yapılır: Parametreli sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-130">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-131">[Nasıl yapılır: gezinme özelliklerini kullanarak Ilişkilerde gezinme](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-131">[How to: Navigate Relationships Using Navigation Properties](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-132">[Nasıl yapılır: Kullanıcı tanımlı bir Işlevi çağırma](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-132">[How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-133">[Nasıl yapılır: verileri filtreleme](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-133">[How to: Filter Data](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-134">[Nasıl yapılır: verileri sıralama](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-134">[How to: Sort Data](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-135">[Nasıl yapılır: verileri gruplandırma](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-135">[How to: Group Data](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-136">[Nasıl yapılır: verileri toplama](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-136">[How to: Aggregate Data](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-137">[Nasıl yapılır: anonim tür nesneleri döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-137">[How to: Execute a Query that Returns Anonymous Type Objects](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-138">[Nasıl yapılır: temel türlerin bir koleksiyonunu döndüren bir sorgu yürütme](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-138">[How to: Execute a Query that Returns a Collection of Primitive Types](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-139">[Nasıl yapılır: bir EntityCollection 'da Ilgili nesneleri sorgulama](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-139">[How to: Query Related Objects in an EntityCollection](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-140">[Nasıl yapılır: Iki sorgunun birleşimini sıralama](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-140">[How to: Order the Union of Two Queries](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="17ac3-141">[Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17ac3-141">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17ac3-142">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="17ac3-142">In This Section</span></span>  
 [<span data-ttu-id="17ac3-143">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="17ac3-143">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="17ac3-144">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="17ac3-144">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="17ac3-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17ac3-145">See also</span></span>

- [<span data-ttu-id="17ac3-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="17ac3-146">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="17ac3-147">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="17ac3-147">Language Reference</span></span>](index.md)
