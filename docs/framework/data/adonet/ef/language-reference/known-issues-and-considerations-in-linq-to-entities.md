---
title: LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: d7d87a3e95cf66efb91b71f6ff3c7c9bb1fbb311
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662143"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="be17c-102">LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="be17c-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="be17c-103">Bu bölümde, LINQ to Entities sorgularında bilinen sorunlar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="be17c-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="be17c-104">LINQ sorguları, önbelleğe alınamaz</span><span class="sxs-lookup"><span data-stu-id="be17c-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="be17c-105">Kayıp bilgileri sıralama</span><span class="sxs-lookup"><span data-stu-id="be17c-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="be17c-106">İşaretsiz tamsayılar desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="be17c-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="be17c-107">Tür dönüştürme hataları</span><span class="sxs-lookup"><span data-stu-id="be17c-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="be17c-108">Desteklenmeyen skaler olmayan değişkenleri başvurma</span><span class="sxs-lookup"><span data-stu-id="be17c-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="be17c-109">SQL Server 2000 ile iç içe geçmiş sorgular başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="be17c-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="be17c-110">Anonim bir tür için yansıtma</span><span class="sxs-lookup"><span data-stu-id="be17c-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="be17c-111">LINQ sorguları, önbelleğe alınamaz</span><span class="sxs-lookup"><span data-stu-id="be17c-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="be17c-112">.NET Framework 4.5 ile başlayarak, LINQ to Entities sorgularında otomatik olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="be17c-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="be17c-113">Ancak LINQ to Entities sorgularında, geçerli `Enumerable.Contains` işleci bellek içi koleksiyonlara otomatik olarak önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="be17c-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="be17c-114">Bellek içi koleksiyonları derlenmiş LINQ sorgularında ayrıca kümesini parametreleştirme izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="be17c-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a><span data-ttu-id="be17c-115">Kayıp bilgileri sıralama</span><span class="sxs-lookup"><span data-stu-id="be17c-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="be17c-116">Sütunlar anonim bir tür yansıtma sıralama "80" bir uyumluluk düzeyine ayarlanmış bir SQL Server 2005 veritabanı karşı yürütülen sorgular kaybolur bilgilere neden olur.</span><span class="sxs-lookup"><span data-stu-id="be17c-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="be17c-117">Order by listesi bir sütun adı bir sütun adı Seçici içinde eşleştiğinde aşağıdaki örnekte gösterildiği gibi oluşur:</span><span class="sxs-lookup"><span data-stu-id="be17c-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="be17c-118">İşaretsiz tamsayılar desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="be17c-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="be17c-119">Bir işaretsiz tamsayı türü bir LINQ to Entities sorgusunda belirtilmesi desteklenmez çünkü [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] işaretsiz tamsayılar desteklemez.</span><span class="sxs-lookup"><span data-stu-id="be17c-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not support unsigned integers.</span></span> <span data-ttu-id="be17c-120">İşaretsiz bir tamsayı belirtmeniz durumunda bir <xref:System.ArgumentException> özel durumu aşağıdaki örnekte gösterildiği gibi sorgu ifade çevirisi sırasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="be17c-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="be17c-121">Bu örnek sorguları bir sipariş kimliği 48000 için.</span><span class="sxs-lookup"><span data-stu-id="be17c-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a><span data-ttu-id="be17c-122">Tür dönüştürme hataları</span><span class="sxs-lookup"><span data-stu-id="be17c-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="be17c-123">Visual Basic'te, bir özellik SQL Server bit türünde bir sütun 1'i kullanarak bir değer ile eşlendiğinde `CByte` işlevi, bir <xref:System.Data.SqlClient.SqlException> "aritmetik taşma hata" iletisi ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="be17c-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="be17c-124">Aşağıdaki örnek sorgularda `Product.MakeFlag` üzerinden sorgu sonuçları yinelendiğinde sütununda AdventureWorks örnek veritabanı ve bir özel durum harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="be17c-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="be17c-125">Desteklenmeyen skaler olmayan değişkenleri başvurma</span><span class="sxs-lookup"><span data-stu-id="be17c-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="be17c-126">Bir varlıkta bir sorgu gibi bir skaler olmayan değişkenleri başvuran desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="be17c-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="be17c-127">Bu tür bir sorgu yürütüldüğünde, bir <xref:System.NotSupportedException> bildiren bir ileti ile özel durum oluştu "türünde bir sabit değer oluşturulamıyor `EntityType`.</span><span class="sxs-lookup"><span data-stu-id="be17c-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="be17c-128">Yalnızca ilkel türler ('Örneğin Int32, String ve Guid') bu bağlamda desteklenir."</span><span class="sxs-lookup"><span data-stu-id="be17c-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be17c-129">Skalar değişkenler koleksiyonunu başvuran desteklenir.</span><span class="sxs-lookup"><span data-stu-id="be17c-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="be17c-130">SQL Server 2000 ile iç içe geçmiş sorgular başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="be17c-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="be17c-131">Üç veya daha fazla düzeyleri derin iç içe geçmiş Transact-SQL sorguları ürettikleri ile SQL Server 2000, LINQ to Entities sorgularında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="be17c-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="be17c-132">Anonim bir tür için yansıtma</span><span class="sxs-lookup"><span data-stu-id="be17c-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="be17c-133">İlgili nesneler kullanarak eklemek için ilk sorgu yolunuzu tanımlarsanız, <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metodunda <xref:System.Data.Objects.ObjectQuery%601> ve ardından döndürülen nesneleri anonim bir tür projeye LINQ kullanmak için dahil etme yöntemi belirtilen nesnelerin sorguda yer almaz Sonuç.</span><span class="sxs-lookup"><span data-stu-id="be17c-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="be17c-134">İlgili nesneler almak için döndürülen türleri anonim bir tür için proje değil.</span><span class="sxs-lookup"><span data-stu-id="be17c-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="be17c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be17c-135">See also</span></span>

- [<span data-ttu-id="be17c-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="be17c-136">LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
