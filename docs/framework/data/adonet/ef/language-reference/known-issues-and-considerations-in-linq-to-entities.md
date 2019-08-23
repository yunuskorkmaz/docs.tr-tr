---
title: LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 66af3395d7ba7271323ad6461e8e1fb8c823a1c6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913910"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="b90f7-102">LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="b90f7-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="b90f7-103">Bu bölüm LINQ to Entities sorgularıyla ilgili bilinen sorunlar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b90f7-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="b90f7-104">Önbelleğe alınabilecek LINQ sorguları</span><span class="sxs-lookup"><span data-stu-id="b90f7-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="b90f7-105">Sipariş bilgileri kayıp</span><span class="sxs-lookup"><span data-stu-id="b90f7-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="b90f7-106">İşaretsiz tamsayılar desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b90f7-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="b90f7-107">Tür dönüştürme hataları</span><span class="sxs-lookup"><span data-stu-id="b90f7-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="b90f7-108">Skalar olmayan değişkenlere başvurma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b90f7-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="b90f7-109">İç içe geçmiş sorgular SQL Server 2000 ile başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="b90f7-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="b90f7-110">Anonim bir türe yansıtma</span><span class="sxs-lookup"><span data-stu-id="b90f7-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="b90f7-111">Önbelleğe alınabilecek LINQ sorguları</span><span class="sxs-lookup"><span data-stu-id="b90f7-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="b90f7-112">.NET Framework 4,5 ' den başlayarak LINQ to Entities sorguları otomatik olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="b90f7-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="b90f7-113">Ancak, bu işleci, `Enumerable.Contains` bellek içi koleksiyonlara uygulayan LINQ to Entities sorguları otomatik olarak önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="b90f7-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="b90f7-114">Ayrıca, derlenen LINQ sorgularında bellek içi koleksiyonlara parametreleştirmeye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="b90f7-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="b90f7-115">Sipariş bilgileri kayıp</span><span class="sxs-lookup"><span data-stu-id="b90f7-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="b90f7-116">Sütunları anonim bir türde yansıtma, bir SQL Server 2005 veritabanına karşı yürütülen bazı sorgularda sıralama bilgilerinin "80" uyumluluk düzeyine ayarlanmış olarak kaybolmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b90f7-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="b90f7-117">Bu durum, aşağıdaki örnekte gösterildiği gibi, order by listesindeki bir sütun adı seçicideki bir sütun adıyla eşleştiğinde meydana gelir:</span><span class="sxs-lookup"><span data-stu-id="b90f7-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="b90f7-118">İşaretsiz tamsayılar desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b90f7-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="b90f7-119">İşaretsiz tamsayılar desteklemediğinden LINQ to Entities sorgusunda işaretsiz bir tamsayı türü belirtilmesi desteklenmez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b90f7-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="b90f7-120">İşaretsiz bir tamsayı belirtirseniz, aşağıdaki örnekte gösterildiği <xref:System.ArgumentException> gibi sorgu ifadesi çevirisi sırasında bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="b90f7-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="b90f7-121">Bu örnek 48000 KIMLIKLI bir sipariş için sorgular.</span><span class="sxs-lookup"><span data-stu-id="b90f7-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="b90f7-122">Tür dönüştürme hataları</span><span class="sxs-lookup"><span data-stu-id="b90f7-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="b90f7-123">Visual Basic, bir özellik `CByte` işlevi kullanılarak 1 değeri olan SQL Server bit türünde bir sütunla eşlendiğinde, bir <xref:System.Data.SqlClient.SqlException> "aritmetik taşma hatası" iletisiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b90f7-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="b90f7-124">Aşağıdaki örnek, AdventureWorks örnek `Product.MakeFlag` veritabanındaki sütununu sorgular ve sorgu sonuçları üzerinden yineedildiğinde bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b90f7-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="b90f7-125">Skalar olmayan değişkenlere başvurma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b90f7-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="b90f7-126">Bir sorgu içindeki bir varlık gibi skaler olmayan değişkenlere başvurma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b90f7-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="b90f7-127">Böyle bir sorgu yürütüldüğünde, <xref:System.NotSupportedException> "türün `EntityType`sabit değeri oluşturulamıyor" iletisini içeren bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b90f7-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="b90f7-128">Bu bağlamda yalnızca ilkel türler (Int32, String ve Guid gibi) destekleniyor. "</span><span class="sxs-lookup"><span data-stu-id="b90f7-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b90f7-129">Skaler değişkenler koleksiyonuna başvurmak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b90f7-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="b90f7-130">İç içe geçmiş sorgular SQL Server 2000 ile başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="b90f7-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="b90f7-131">SQL Server 2000 ile, üç veya daha fazla düzey derinlikli iç içe Transact-SQL sorguları oluşturduklarında LINQ to Entities sorguları başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="b90f7-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="b90f7-132">Anonim bir türe yansıtma</span><span class="sxs-lookup"><span data-stu-id="b90f7-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="b90f7-133">Üzerinde yöntemi<xref:System.Data.Objects.ObjectQuery%601.Include%2A> kullanarak ilgili nesneleri dahil etmek için ilk sorgu yolunu tanımlayabilir veardındandöndürülennesnelerianonimbirtüreeklemekiçinLINQkullanıyorsanız,Includeyöntemindebelirtilennesnelersorguyaeklenmez<xref:System.Data.Objects.ObjectQuery%601> sonucunun.</span><span class="sxs-lookup"><span data-stu-id="b90f7-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="b90f7-134">İlgili nesneleri almak için, döndürülen türleri bir anonim türe proje olarak değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="b90f7-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="b90f7-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b90f7-135">See also</span></span>

- [<span data-ttu-id="b90f7-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b90f7-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
