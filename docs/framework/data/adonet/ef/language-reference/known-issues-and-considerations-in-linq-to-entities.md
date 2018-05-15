---
title: Bilinen sorunlar ve dikkat edilmesi gerekenler LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 6b54f75afd52b5179693c5a92ebce2e8aa02f122
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="00c0b-102">Bilinen sorunlar ve dikkat edilmesi gerekenler LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="00c0b-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="00c0b-103">Bu bölüm ile ilgili bilinen sorunlar hakkında bilgi sağlar [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="00c0b-103">This section provides information about known issues with [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
-   [<span data-ttu-id="00c0b-104">LINQ sorguları, önbelleğe alınamıyor</span><span class="sxs-lookup"><span data-stu-id="00c0b-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
-   [<span data-ttu-id="00c0b-105">Kayıp bilgi sıralama</span><span class="sxs-lookup"><span data-stu-id="00c0b-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
-   [<span data-ttu-id="00c0b-106">İmzasız tamsayılar desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="00c0b-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
-   [<span data-ttu-id="00c0b-107">Tür dönüştürme hataları</span><span class="sxs-lookup"><span data-stu-id="00c0b-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
-   [<span data-ttu-id="00c0b-108">Skaler olmayan değişkenleri desteklenmiyor başvurma</span><span class="sxs-lookup"><span data-stu-id="00c0b-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
-   [<span data-ttu-id="00c0b-109">İç içe geçmiş sorgular SQL Server 2000 ile başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="00c0b-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
-   [<span data-ttu-id="00c0b-110">Anonim bir tür yansıtma</span><span class="sxs-lookup"><span data-stu-id="00c0b-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="00c0b-111">LINQ sorguları, önbelleğe alınamıyor</span><span class="sxs-lookup"><span data-stu-id="00c0b-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="00c0b-112">.NET Framework 4. 5'ile başlayarak, LINQ to Entities sorgularında otomatik olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="00c0b-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="00c0b-113">Ancak, LINQ to Entities sorgularında geçerli `Enumerable.Contains` bellek içi koleksiyonlara işleci otomatik olarak önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="00c0b-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="00c0b-114">Ayrıca derlenmiş LINQ sorgularını bellek içi koleksiyonlarda kümesini parametreleştirme izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="00c0b-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="00c0b-115">Kayıp bilgi sıralama</span><span class="sxs-lookup"><span data-stu-id="00c0b-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="00c0b-116">Anonim bir tür sütunları yansıtma karşı yürütülen bazı sorgular kaybolur sipariş bilgilerini neden olacak bir [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] veritabanı "80" için bir uyumluluk düzeyi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="00c0b-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] database set to a compatibility level of "80".</span></span>  <span data-ttu-id="00c0b-117">Order by listesinde bir sütun adı Seçici içinde bir sütun adı eşleştiğinde aşağıdaki örnekte gösterildiği gibi oluşur:</span><span class="sxs-lookup"><span data-stu-id="00c0b-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="00c0b-118">İmzasız tamsayılar desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="00c0b-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="00c0b-119">Bir işaretsiz tamsayı türünde belirten bir [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] çünkü sorgu desteklenmiyor [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] imzasız tamsayılar desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="00c0b-119">Specifying an unsigned integer type in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="00c0b-120">İşaretsiz tamsayıya belirtirseniz bir <xref:System.ArgumentException> özel durum sorgu ifade çevirisi sırasında aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="00c0b-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="00c0b-121">Bir sıra kimliği 48000 ile bu örnek sorgular.</span><span class="sxs-lookup"><span data-stu-id="00c0b-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="00c0b-122">Tür dönüştürme hataları</span><span class="sxs-lookup"><span data-stu-id="00c0b-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="00c0b-123">Visual Basic'te bir özellik SQL Server bit türünde bir sütun 1 kullanmanın bir değerle eşlendiğinde, `CByte` işlevi, bir <xref:System.Data.SqlClient.SqlException> bir "Aritmetik Taşma Hatası" iletisiyle atılır.</span><span class="sxs-lookup"><span data-stu-id="00c0b-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="00c0b-124">Aşağıdaki örnek sorgularda `Product.MakeFlag` AdventureWorks örnek veritabanını ve özel bir Durum sütununda üzerinden sorgu sonuçlarını yinelendiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="00c0b-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="00c0b-125">Skaler olmayan değişkenleri desteklenmiyor başvurma</span><span class="sxs-lookup"><span data-stu-id="00c0b-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="00c0b-126">Sorguda bir varlık gibi bir skaler olmayan değişkenleri başvuran desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="00c0b-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="00c0b-127">Böyle bir sorguyu yürütüldüğünde, bir <xref:System.NotSupportedException> bildiren bir ileti ile özel durum "türünde sabit değer oluşturulamıyor `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="00c0b-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="00c0b-128">Yalnızca ilkel türler ('Örneğin Int32, String ve GUID') bu bağlamda desteklenir."</span><span class="sxs-lookup"><span data-stu-id="00c0b-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00c0b-129">Skaler değişkenleri koleksiyonu başvuran desteklenir.</span><span class="sxs-lookup"><span data-stu-id="00c0b-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="00c0b-130">İç içe geçmiş sorgular SQL Server 2000 ile başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="00c0b-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="00c0b-131">Üç veya daha çok düzey derinliğinde iç içe geçmiş Transact-SQL sorguları oluşturdukları ile SQL Server 2000, LINQ to Entities sorgularında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="00c0b-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="00c0b-132">Anonim bir tür yansıtma</span><span class="sxs-lookup"><span data-stu-id="00c0b-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="00c0b-133">İlk sorguyu yolunuzu kullanarak ilgili nesneleri içerecek şekilde tanımlarsanız <xref:System.Data.Objects.ObjectQuery%601.Include%2A> yöntemi <xref:System.Data.Objects.ObjectQuery%601> ve anonim bir tür için döndürülen nesnelerin projeye LINQ kullanın, INCLUDE yönteminde belirtilen nesnelerin sorguda dahil edilmez sonuçları.</span><span class="sxs-lookup"><span data-stu-id="00c0b-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="00c0b-134">İlişkili nesneleri almak için döndürülen türleri anonim bir tür için proje yok.</span><span class="sxs-lookup"><span data-stu-id="00c0b-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="00c0b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00c0b-135">See Also</span></span>  
 [<span data-ttu-id="00c0b-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="00c0b-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
