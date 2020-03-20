---
title: LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150148"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="f527e-102">LINQ to Entities Hakkında Bilinen Sorunlar ve Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="f527e-102">Known Issues and Considerations in LINQ to Entities</span></span>
<span data-ttu-id="f527e-103">Bu bölümde, LINQ ile Varlıklar sorguları için bilinen sorunlar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f527e-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="f527e-104">Önbelleğe Alınamayan LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="f527e-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="f527e-105">Kayıp Bilgileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="f527e-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="f527e-106">İmzasız Tümsatörler Desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="f527e-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="f527e-107">Dönüşüm Hatalarını Yazın</span><span class="sxs-lookup"><span data-stu-id="f527e-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="f527e-108">Skaler Olmayan Değişkenlere Başvurma Desteklenmez</span><span class="sxs-lookup"><span data-stu-id="f527e-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="f527e-109">SQL Server 2000 ile İç Içe Sorgular Başarısız Olabilir</span><span class="sxs-lookup"><span data-stu-id="f527e-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="f527e-110">Anonim Türe Yansıtma</span><span class="sxs-lookup"><span data-stu-id="f527e-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="f527e-111">Önbelleğe Alınamayan LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="f527e-111">LINQ Queries That cannot be Cached</span></span>  
 <span data-ttu-id="f527e-112">.NET Framework 4.5 ile başlayarak, LinQ to Ntities sorguları otomatik olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="f527e-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="f527e-113">Ancak, `Enumerable.Contains` işleci bellek içi koleksiyonlara uygulayan Varlıklara LINQ sorguları otomatik olarak önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="f527e-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="f527e-114">Ayrıca derlenmiş LINQ sorgularında bellek içi koleksiyonları parametrelendirmeye izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="f527e-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a><span data-ttu-id="f527e-115">Kayıp Bilgileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="f527e-115">Ordering Information Lost</span></span>  
 <span data-ttu-id="f527e-116">Sütunları anonim bir türe yansıtmak, SQL Server 2005 veritabanına karşı "80" uyumluluk düzeyine ayarlanan bazı sorgularda sipariş bilgilerinin kaybolmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f527e-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="f527e-117">Bu, sipariş eki listesindeki bir sütun adı, aşağıdaki örnekte gösterildiği gibi seçicideki bir sütun adıyla eşleştiğinde oluşur:</span><span class="sxs-lookup"><span data-stu-id="f527e-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="f527e-118">İmzasız Tümsatörler Desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="f527e-118">Unsigned Integers Not Supported</span></span>  
 <span data-ttu-id="f527e-119">Varlık Çerçevesi imzasız tamsayıları desteklemediği için, LINQ'dan Varlıklara sorgusunda imzasız bir tamsayı türü belirtilmesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f527e-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the Entity Framework does not support unsigned integers.</span></span> <span data-ttu-id="f527e-120">İmzasız bir karşıcı belirtirseniz, <xref:System.ArgumentException> aşağıdaki örnekte gösterildiği gibi sorgu ifadesi çevirisi sırasında bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="f527e-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="f527e-121">Bu örnek, ID 48000 olan bir siparişi sorgular.</span><span class="sxs-lookup"><span data-stu-id="f527e-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a><span data-ttu-id="f527e-122">Dönüşüm Hatalarını Yazın</span><span class="sxs-lookup"><span data-stu-id="f527e-122">Type Conversion Errors</span></span>  
 <span data-ttu-id="f527e-123">Visual Basic'te, bir özellik işlevi kullanarak 1 değeri olan SQL Server bit `CByte` türündeki <xref:System.Data.SqlClient.SqlException> bir sütuna eşlendiğinde, "Aritmetik taşaşma hatası" iletisi ile bir a atılır.</span><span class="sxs-lookup"><span data-stu-id="f527e-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="f527e-124">Aşağıdaki örnek, AdventureWorks örnek veritabanındaki `Product.MakeFlag` sütunu sorgular ve sorgu sonuçları üzerinde tekrarlandığında bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="f527e-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="f527e-125">Skaler Olmayan Değişkenlere Başvurma Desteklenmez</span><span class="sxs-lookup"><span data-stu-id="f527e-125">Referencing Non-Scalar Variables Not Supported</span></span>  
 <span data-ttu-id="f527e-126">Bir sorguda varlık gibi skaler olmayan değişkenlere başvuru önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f527e-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="f527e-127">Böyle bir sorgu yürütüldüğünde, <xref:System.NotSupportedException> "Türünün `EntityType`sabit bir değeri oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="f527e-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="f527e-128">Bu bağlamda yalnızca ilkel türler ('Int32, String ve Guid' gibi) desteklenir."</span><span class="sxs-lookup"><span data-stu-id="f527e-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f527e-129">Skaler değişkenler koleksiyonuna başvuru desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f527e-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="f527e-130">SQL Server 2000 ile İç Içe Sorgular Başarısız Olabilir</span><span class="sxs-lookup"><span data-stu-id="f527e-130">Nested Queries May Fail with SQL Server 2000</span></span>  
 <span data-ttu-id="f527e-131">SQL Server 2000 ile LINQ to Ntities sorguları, üç veya daha fazla düzey derinliğinde iç içe geçirilmiş Transact-SQL sorguları üretirlerse başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="f527e-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="f527e-132">Anonim Türe Yansıtma</span><span class="sxs-lookup"><span data-stu-id="f527e-132">Projecting to an Anonymous Type</span></span>  
 <span data-ttu-id="f527e-133">İlk sorgu yolunuzu, yöntemüzerinde yöntem kullanarak <xref:System.Data.Objects.ObjectQuery%601.Include%2A> ilgili nesneleri <xref:System.Data.Objects.ObjectQuery%601> içerecek şekilde tanımlar ve döndürülen nesneleri anonim bir türe yansıtmak için LINQ'yu kullanırsanız, dahil etme yönteminde belirtilen nesneler sorgu sonuçlarına dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="f527e-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="f527e-134">İlgili nesneleri almak için döndürülen türleri anonim bir türe yansıtmayın.</span><span class="sxs-lookup"><span data-stu-id="f527e-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="f527e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f527e-135">See also</span></span>

- [<span data-ttu-id="f527e-136">LINQ - Varlıklar</span><span class="sxs-lookup"><span data-stu-id="f527e-136">LINQ to Entities</span></span>](linq-to-entities.md)
