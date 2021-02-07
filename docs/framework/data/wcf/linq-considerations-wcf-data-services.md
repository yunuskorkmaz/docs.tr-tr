---
description: 'Daha fazla bilgi edinin: LINQ konuları (WCF Veri Hizmetleri)'
title: LINQ hususları (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 4205fc5c67c5939377e2a964d5a82d8855b03fce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764971"
---
# <a name="linq-considerations-wcf-data-services"></a><span data-ttu-id="d0392-103">LINQ hususları (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="d0392-103">LINQ Considerations (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="d0392-104">Bu konu, LINQ sorgularının nasıl oluşturulduğu ve WCF Veri Hizmetleri yürütüldüğü ve açık veri Protokolü 'Nü (OData) uygulayan bir veri hizmetini sorgulamak için LINQ kullanma sınırlamalarını kullanırken oluşan yol hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0392-104">This topic provides information about the way in which LINQ queries are composed and executed when you are using the WCF Data Services client and limitations of using LINQ to query a data service that implements the Open Data Protocol (OData).</span></span> <span data-ttu-id="d0392-105">OData tabanlı bir veri hizmetine yönelik sorgu oluşturma ve yürütme hakkında daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d0392-105">For more information about composing and executing queries against an OData-based data service, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="composing-linq-queries"></a><span data-ttu-id="d0392-106">LINQ sorguları oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="d0392-106">Composing LINQ Queries</span></span>  

 <span data-ttu-id="d0392-107">LINQ, uygulayan bir nesne koleksiyonuna karşı sorgu oluşturma imkanı sağlar <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="d0392-107">LINQ enables you to compose queries against a collection of objects that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d0392-108">Visual Studio 'daki **hizmet başvurusu Ekle** iletişim kutusu ve DataSvcUtil.exe Aracı, bir OData hizmetinin ' den devralan varlık kapsayıcı sınıfı olarak bir temsilini <xref:System.Data.Services.Client.DataServiceContext> , ayrıca akışlarda döndürülen varlıkları temsil eden nesneleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0392-108">Both the **Add Service Reference** dialog box in Visual Studio and the DataSvcUtil.exe tool are used to generate a representation of an OData service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>, as well as objects that represent the entities returned in feeds.</span></span> <span data-ttu-id="d0392-109">Bu araçlar, hizmet tarafından akış olarak gösterilen koleksiyonlar için varlık kapsayıcı sınıfında özellikler de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0392-109">These tools also generate properties on the entity container class for the collections that are exposed as feeds by the service.</span></span> <span data-ttu-id="d0392-110">Veri hizmetini kapsülleyen sınıfın bu özelliklerinin her biri, döndürür <xref:System.Data.Services.Client.DataServiceQuery%601> .</span><span class="sxs-lookup"><span data-stu-id="d0392-110">Each of these properties of the class that encapsulates the data service return a <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span> <span data-ttu-id="d0392-111"><xref:System.Data.Services.Client.DataServiceQuery%601>Sınıfı <xref:System.Linq.IQueryable%601> LINQ tarafından tanımlanan arabirimi uyguladığından, istemci kitaplığı tarafından, yürütme sırasında veri hizmetine gönderilen bir sorgu isteği URI 'sine çevrilen veri hizmeti tarafından kullanıma sunulan akışlara YÖNELIK bir LINQ sorgusu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0392-111">Because the <xref:System.Data.Services.Client.DataServiceQuery%601> class implements the <xref:System.Linq.IQueryable%601> interface defined by LINQ, you can compose a LINQ query against feeds exposed by the data service, which are translated by the client library into a query request URI that is sent to the data service on execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d0392-112">LINQ sözdiziminde ifade edilen sorgu kümesi, OData veri Hizmetleri tarafından kullanılan URI sözdiziminde etkinleştirilenlerden daha yavaştır.</span><span class="sxs-lookup"><span data-stu-id="d0392-112">The set of queries expressible in the LINQ syntax is broader than those enabled in the URI syntax that is used by OData data services.</span></span> <span data-ttu-id="d0392-113"><xref:System.NotSupportedException>Sorgu, hedef veri hizmetindeki BIR URI ile eşleştirilemez olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="d0392-113">A <xref:System.NotSupportedException> is raised when the query cannot be mapped to a URI in the target data service.</span></span> <span data-ttu-id="d0392-114">Daha fazla bilgi için bu konudaki [Desteklenmeyen LINQ yöntemlerine](linq-considerations-wcf-data-services.md#unsupportedMethods) bakın.</span><span class="sxs-lookup"><span data-stu-id="d0392-114">For more information, see the [Unsupported LINQ Methods](linq-considerations-wcf-data-services.md#unsupportedMethods) in this topic.</span></span>  
  
 <span data-ttu-id="d0392-115">Aşağıdaki örnek, `Orders` $30 'den daha fazla nakliye maliyeti olan BIR LINQ sorgusudur ve en son teslim tarihinden itibaren sevkiyat tarihine göre sonuçları sıralar:</span><span class="sxs-lookup"><span data-stu-id="d0392-115">The following example is a LINQ query that returns `Orders` that have a freight cost of more than $30 and sorts the results by the shipping date, starting with the latest ship date:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]
  
 <span data-ttu-id="d0392-116">Bu LINQ sorgusu, Northwind tabanlı [hızlı başlangıç](quickstart-wcf-data-services.md) veri hizmeti 'ne karşı yürütülen AŞAĞıDAKI sorgu URI 'sine çevrilir:</span><span class="sxs-lookup"><span data-stu-id="d0392-116">This LINQ query is translated into the following query URI that is executed against the Northwind-based [quickstart](quickstart-wcf-data-services.md) data service:</span></span>  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 <span data-ttu-id="d0392-117">LINQ hakkında daha fazla genel bilgi için bkz. [dil Ile tümleşik sorgu (LINQ)-C#](../../../csharp/programming-guide/concepts/linq/index.md) veya [dil ile TÜMLEŞIK sorgu (lınq)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0392-117">For more general information about LINQ, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
 <span data-ttu-id="d0392-118">LINQ, önceki örnekte gösterilen dile özgü bildirim temelli sorgu söz dizimini ve standart sorgu işleçleri olarak bilinen bir sorgu yöntemleri kümesini kullanarak sorgu oluşturma imkanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0392-118">LINQ enables you to compose queries by using both the language-specific declarative query syntax, shown in the previous example, as well as a set of query methods known as standard query operators.</span></span> <span data-ttu-id="d0392-119">Önceki örneğe eşdeğer bir sorgu, aşağıdaki örnekte gösterildiği gibi yalnızca Yöntem tabanlı sözdizimi kullanılarak oluşturulabilir:</span><span class="sxs-lookup"><span data-stu-id="d0392-119">An equivalent query to the previous example can be composed by using only the method-based syntax, as shown the following example:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]
  
 <span data-ttu-id="d0392-120">WCF Veri Hizmetleri istemcisi, her iki türdeki sorguyu bir sorgu URI 'sine çevirebilir ve sorgu yöntemlerini sorgu ifadesine ekleyerek bir LINQ sorgusunu genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0392-120">The WCF Data Services client is able to translate both kinds of composed queries into a query URI, and you can extend a LINQ query by appending query methods to a query expression.</span></span> <span data-ttu-id="d0392-121">Bir sorgu ifadesine ya da öğesine Yöntem sözdizimini ekleyerek LINQ sorguları oluşturduğunuzda <xref:System.Data.Services.Client.DataServiceQuery%601> , işlemler sorgu URI 'sine yöntemlerin çağrıldığı sırada eklenir.</span><span class="sxs-lookup"><span data-stu-id="d0392-121">When you compose LINQ queries by appending method syntax to a query expression or a <xref:System.Data.Services.Client.DataServiceQuery%601>, the operations are added to the query URI in the order in which methods are called.</span></span> <span data-ttu-id="d0392-122">Bu, <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> her sorgu seçeneğini sorgu URI 'sine eklemek için yöntemini çağırmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="d0392-122">This is equivalent to calling the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method to add each query option to the query URI.</span></span>  
  
## <a name="executing-linq-queries"></a><span data-ttu-id="d0392-123">LINQ sorguları yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="d0392-123">Executing LINQ Queries</span></span>  

 <span data-ttu-id="d0392-124">Sorgunun eklendiği gibi bazı LINQ sorgu yöntemleri, sorgunun <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d0392-124">Certain LINQ query methods, such as <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> or <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, when appended to the query, cause the query to be executed.</span></span> <span data-ttu-id="d0392-125">Bir sorgu, `foreach` döngü sırasında veya sorgu bir koleksiyona atandığında olduğu gibi, sonuçlar örtük olarak numaralandırıldıktan sonra da yürütülür `List` .</span><span class="sxs-lookup"><span data-stu-id="d0392-125">A query is also executed when results are enumerated implicitly, such as during a `foreach` loop or when the query is assigned to a `List` collection.</span></span> <span data-ttu-id="d0392-126">Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d0392-126">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d0392-127">İstemci iki bölümde bir LINQ sorgusu yürütür.</span><span class="sxs-lookup"><span data-stu-id="d0392-127">The client executes a LINQ query in two parts.</span></span> <span data-ttu-id="d0392-128">Mümkün olduğunda, bir sorgudaki LINQ ifadeleri ilk olarak istemcide değerlendirilir ve ardından bir URI tabanlı sorgu oluşturulup hizmette verilere göre değerlendirme için veri hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d0392-128">Whenever possible, LINQ expressions in a query are first evaluated on the client, and then a URI-based query is generated and sent to the data service for evaluation against data in the service.</span></span> <span data-ttu-id="d0392-129">Daha fazla bilgi için, [veri hizmetini sorgularken](querying-the-data-service-wcf-data-services.md) [Istemci ile sunucu yürütme karşılaştırması](querying-the-data-service-wcf-data-services.md#executingQueries) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d0392-129">For more information, see the section [Client versus Server Execution](querying-the-data-service-wcf-data-services.md#executingQueries) in [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d0392-130">Bir LINQ sorgusu, OData ile uyumlu bir sorgu URI 'sine çevrilemez, yürütme denendiğinde bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d0392-130">When a LINQ query cannot be translated in an OData-compliant query URI, an exception is raised when execution is attempted.</span></span> <span data-ttu-id="d0392-131">Daha fazla bilgi için bkz. [veri hizmetini sorgulama](querying-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d0392-131">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="linq-query-examples"></a><span data-ttu-id="d0392-132">LINQ sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="d0392-132">LINQ Query Examples</span></span>  

 <span data-ttu-id="d0392-133">Aşağıdaki bölümlerde yer alan örneklerde, bir OData hizmetine karşı yürütülebilecek LINQ sorgularının türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d0392-133">The examples in the following sections demonstrate the kinds of LINQ queries that can be executed against an OData service.</span></span>  
  
<a name="filtering"></a>

### <a name="filtering"></a><span data-ttu-id="d0392-134">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="d0392-134">Filtering</span></span>  

 <span data-ttu-id="d0392-135">Bu bölümdeki LINQ sorgu örnekleri, hizmet tarafından döndürülen akıştaki verileri filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="d0392-135">The LINQ query examples in this section filter data in the feed returned by the service.</span></span>  
  
 <span data-ttu-id="d0392-136">Aşağıdaki örnekler, döndürülen `Orders` varlıkların yalnızca $30 'den büyük bir nakliye maliyeti olan siparişlerin döndürüldüğünden filtre uygulayan eşdeğer sorgulardır:</span><span class="sxs-lookup"><span data-stu-id="d0392-136">The following examples are equivalent queries that filter the returned `Orders` entities so that only orders with a freight cost greater than $30 are returned:</span></span>  
  
- <span data-ttu-id="d0392-137">LINQ sorgu söz dizimini kullanma:</span><span class="sxs-lookup"><span data-stu-id="d0392-137">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]
  
- <span data-ttu-id="d0392-138">LINQ sorgu yöntemlerini kullanma:</span><span class="sxs-lookup"><span data-stu-id="d0392-138">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]
  
- <span data-ttu-id="d0392-139">URI sorgu dizesi `$filter` seçeneği:</span><span class="sxs-lookup"><span data-stu-id="d0392-139">The URI query string `$filter` option:</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]
  
 <span data-ttu-id="d0392-140">Önceki örneklerin hepsi sorgu URI 'sine çevrilir: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M` .</span><span class="sxs-lookup"><span data-stu-id="d0392-140">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.</span></span>  
  
<a name="sorting"></a>

### <a name="sorting"></a><span data-ttu-id="d0392-141">Sıralama</span><span class="sxs-lookup"><span data-stu-id="d0392-141">Sorting</span></span>  

 <span data-ttu-id="d0392-142">Aşağıdaki örneklerde, döndürülen verileri hem şirket adına hem de posta koduna göre sıralayan, azalan olan eşdeğer sorgular gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d0392-142">The following examples show equivalent queries that sort returned data both by the company name and by postal code, descending:</span></span>  
  
- <span data-ttu-id="d0392-143">LINQ sorgu söz dizimini kullanma:</span><span class="sxs-lookup"><span data-stu-id="d0392-143">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]
  
- <span data-ttu-id="d0392-144">LINQ sorgu yöntemlerini kullanma:</span><span class="sxs-lookup"><span data-stu-id="d0392-144">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]
  
- <span data-ttu-id="d0392-145">URI sorgu dizesi `$orderby` seçeneği):</span><span class="sxs-lookup"><span data-stu-id="d0392-145">URI query string `$orderby` option):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]
  
 <span data-ttu-id="d0392-146">Önceki örneklerin hepsi sorgu URI 'sine çevrilir: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc` .</span><span class="sxs-lookup"><span data-stu-id="d0392-146">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.</span></span>  
  
<a name="projection"></a>

### <a name="projection"></a><span data-ttu-id="d0392-147">Projeksiyon</span><span class="sxs-lookup"><span data-stu-id="d0392-147">Projection</span></span>  

 <span data-ttu-id="d0392-148">Aşağıdaki örneklerde, projenin verileri daha dar bir türe döndürdüğü eşdeğer sorgular gösterilmektedir `CustomerAddress` :</span><span class="sxs-lookup"><span data-stu-id="d0392-148">The following examples show equivalent queries that project returned data into the narrower `CustomerAddress` type:</span></span>  
  
- <span data-ttu-id="d0392-149">LINQ sorgu söz dizimini kullanma:</span><span class="sxs-lookup"><span data-stu-id="d0392-149">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]
  
- <span data-ttu-id="d0392-150">LINQ sorgu yöntemlerini kullanma:</span><span class="sxs-lookup"><span data-stu-id="d0392-150">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]

> [!NOTE]
> <span data-ttu-id="d0392-151">`$select`Sorgu seçeneği, yöntemi kullanılarak sorgu URI 'sine eklenemez <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> .</span><span class="sxs-lookup"><span data-stu-id="d0392-151">The `$select` query option cannot be added to a query URI by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="d0392-152"><xref:System.Linq.Enumerable.Select%2A>İstemcinin `$select` istek URI 'sinde sorgu seçeneğini OLUŞTURMASı için LINQ metodunu kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="d0392-152">We recommend that you use the LINQ <xref:System.Linq.Enumerable.Select%2A> method to have the client generate the `$select` query option in the request URI.</span></span>  
  
 <span data-ttu-id="d0392-153">Önceki örneklerin her ikisi de sorgu URI 'sine çevrilir: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"` .</span><span class="sxs-lookup"><span data-stu-id="d0392-153">Both of the previous examples are translated to the query URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.</span></span>  
  
<a name="paging"></a>

### <a name="client-paging"></a><span data-ttu-id="d0392-154">İstemci disk belleği</span><span class="sxs-lookup"><span data-stu-id="d0392-154">Client Paging</span></span>  

 <span data-ttu-id="d0392-155">Aşağıdaki örneklerde, 25 siparişi içeren sıralanmış sıra varlıklarının bir sayfasını isteyen ve ilk 50 siparişi atlayarak eşdeğer sorgular gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d0392-155">The following examples show equivalent queries that request a page of sorted order entities that includes 25 orders, skipping the first 50 orders:</span></span>  
  
- <span data-ttu-id="d0392-156">Sorgu yöntemleri bir LINQ sorgusuna uygulanıyor:</span><span class="sxs-lookup"><span data-stu-id="d0392-156">Applying query methods to a LINQ query:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]
  
- <span data-ttu-id="d0392-157">URI sorgu dizesi `$skip` ve `$top` seçenekleri):</span><span class="sxs-lookup"><span data-stu-id="d0392-157">URI query string `$skip` and `$top` options):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]
  
 <span data-ttu-id="d0392-158">Önceki örneklerin her ikisi de sorgu URI 'sine çevrilir: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25` .</span><span class="sxs-lookup"><span data-stu-id="d0392-158">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.</span></span>  
  
<a name="expand"></a>

### <a name="expand"></a><span data-ttu-id="d0392-159">Genişlet</span><span class="sxs-lookup"><span data-stu-id="d0392-159">Expand</span></span>  

 <span data-ttu-id="d0392-160">Bir OData veri hizmetini sorguladığınızda, sorgunun hedeflediği varlıkla ilgili varlıkların döndürülen akışı dahil edilmesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0392-160">When you query an OData data service, you can request that entities related to the entity targeted by the query be included the returned feed.</span></span> <span data-ttu-id="d0392-161"><xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>Yöntemi, <xref:System.Data.Services.Client.DataServiceQuery%601> LINQ sorgusunun hedeflediği varlık kümesi için, parametresi olarak sağlanan ilgili varlık kümesi adı ile çağrılır `path` .</span><span class="sxs-lookup"><span data-stu-id="d0392-161">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is called on the <xref:System.Data.Services.Client.DataServiceQuery%601> for the entity set targeted by the LINQ query, with the related entity set name supplied as the `path` parameter.</span></span> <span data-ttu-id="d0392-162">Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d0392-162">For more information, see [Loading Deferred Content](loading-deferred-content-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d0392-163">Aşağıdaki örneklerde, yöntemi bir sorguda kullanmanın eşdeğer yolları gösterilmektedir <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> :</span><span class="sxs-lookup"><span data-stu-id="d0392-163">The following examples show equivalent ways to use the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method in a query:</span></span>  
  
- <span data-ttu-id="d0392-164">LINQ sorgu sözdiziminde:</span><span class="sxs-lookup"><span data-stu-id="d0392-164">In LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- <span data-ttu-id="d0392-165">LINQ sorgu yöntemleriyle:</span><span class="sxs-lookup"><span data-stu-id="d0392-165">With LINQ query methods:</span></span>  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]

 <span data-ttu-id="d0392-166">Önceki örneklerin her ikisi de sorgu URI 'sine çevrilir: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details` .</span><span class="sxs-lookup"><span data-stu-id="d0392-166">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.</span></span>  
  
<a name="unsupportedMethods"></a>

## <a name="unsupported-linq-methods"></a><span data-ttu-id="d0392-167">Desteklenmeyen LINQ yöntemleri</span><span class="sxs-lookup"><span data-stu-id="d0392-167">Unsupported LINQ Methods</span></span>  

 <span data-ttu-id="d0392-168">Aşağıdaki tablo, LINQ yöntemlerinin sınıflarını içerir ve bir OData hizmetine karşı yürütülen bir sorguya eklenemez:</span><span class="sxs-lookup"><span data-stu-id="d0392-168">The following table contains the classes of LINQ methods are not supported and cannot be included in a query executed against an OData service:</span></span>  
  
|<span data-ttu-id="d0392-169">İşlem Türü</span><span class="sxs-lookup"><span data-stu-id="d0392-169">Operation Type</span></span>|<span data-ttu-id="d0392-170">Desteklenmeyen Yöntem</span><span class="sxs-lookup"><span data-stu-id="d0392-170">Unsupported Method</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="d0392-171">İşleç ayarla</span><span class="sxs-lookup"><span data-stu-id="d0392-171">Set operators</span></span>|<span data-ttu-id="d0392-172">Tüm küme işleçleri, aşağıdakileri içeren bir öğesine karşı desteklenmez <xref:System.Data.Services.Client.DataServiceQuery%601> :</span><span class="sxs-lookup"><span data-stu-id="d0392-172">All set operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, which included the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|<span data-ttu-id="d0392-173">Sıralama işleçleri</span><span class="sxs-lookup"><span data-stu-id="d0392-173">Ordering operators</span></span>|<span data-ttu-id="d0392-174">Gerektiren aşağıdaki sıralama işleçleri bir için <xref:System.Collections.Generic.IComparer%601> desteklenmez <xref:System.Data.Services.Client.DataServiceQuery%601> :</span><span class="sxs-lookup"><span data-stu-id="d0392-174">The following ordering operators that require <xref:System.Collections.Generic.IComparer%601> are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|<span data-ttu-id="d0392-175">Projeksiyon ve filtreleme işleçleri</span><span class="sxs-lookup"><span data-stu-id="d0392-175">Projection and filtering operators</span></span>|<span data-ttu-id="d0392-176">Konumsal bağımsız değişkeni kabul eden aşağıdaki projeksiyon ve filtreleme işleçleri bir için desteklenmez <xref:System.Data.Services.Client.DataServiceQuery%601> :</span><span class="sxs-lookup"><span data-stu-id="d0392-176">The following projection and filtering operators that accept a positional argument are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|<span data-ttu-id="d0392-177">Gruplandırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="d0392-177">Grouping operators</span></span>|<span data-ttu-id="d0392-178"><xref:System.Data.Services.Client.DataServiceQuery%601>Aşağıdakiler de dahil olmak üzere tüm gruplandırma işleçleri bir için desteklenmez:</span><span class="sxs-lookup"><span data-stu-id="d0392-178">All grouping operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> <span data-ttu-id="d0392-179">Gruplandırma işlemlerinin istemcide gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0392-179">Grouping operations must be performed on the client.</span></span>|  
|<span data-ttu-id="d0392-180">Toplama işleçleri</span><span class="sxs-lookup"><span data-stu-id="d0392-180">Aggregate operators</span></span>|<span data-ttu-id="d0392-181">Aşağıdakiler dahil olmak üzere tüm toplama işlemleri bir öğesine karşı desteklenmez <xref:System.Data.Services.Client.DataServiceQuery%601> :</span><span class="sxs-lookup"><span data-stu-id="d0392-181">All aggregate operations are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> <span data-ttu-id="d0392-182">Toplama işlemleri istemci üzerinde gerçekleştirilmelidir veya bir hizmet işlemi tarafından kapsüllenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d0392-182">Aggregate operations must either be performed on the client or be encapsulated by a service operation.</span></span>|  
|<span data-ttu-id="d0392-183">Sayfalama işleçleri</span><span class="sxs-lookup"><span data-stu-id="d0392-183">Paging operators</span></span>|<span data-ttu-id="d0392-184">Aşağıdaki sayfalama işleçleri bir için desteklenmez <xref:System.Data.Services.Client.DataServiceQuery%601> :</span><span class="sxs-lookup"><span data-stu-id="d0392-184">The following paging operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A><br/><br/><span data-ttu-id="d0392-185">**Note:**  Boş bir dizide yürütülen sayfalama işleçleri null döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0392-185">**Note:**  Paging operators that are executed on an empty sequence return null.</span></span>|  
|<span data-ttu-id="d0392-186">Diğer işleçler</span><span class="sxs-lookup"><span data-stu-id="d0392-186">Other operators</span></span>|<span data-ttu-id="d0392-187">Aşağıdaki işleçler bir için de desteklenmez <xref:System.Data.Services.Client.DataServiceQuery%601> :</span><span class="sxs-lookup"><span data-stu-id="d0392-187">The following operators are also not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> - <xref:System.Linq.Enumerable.Empty%2A><br />- <xref:System.Linq.Enumerable.Range%2A><br />- <xref:System.Linq.Enumerable.Repeat%2A><br />- <xref:System.Linq.Enumerable.ToDictionary%2A><br />- <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>

## <a name="supported-expression-functions"></a><span data-ttu-id="d0392-188">Desteklenen Ifade Işlevleri</span><span class="sxs-lookup"><span data-stu-id="d0392-188">Supported Expression Functions</span></span>  

 <span data-ttu-id="d0392-189">Aşağıdaki ortak dil çalışma zamanı (CLR) yöntemleri ve özellikleri, bir OData hizmetine istek URI 'sine eklenmek üzere bir sorgu ifadesinde çevrilebilmesi için desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d0392-189">The following common-language runtime (CLR) methods and properties are supported because they can be translated in a query expression for inclusion in the request URI to an OData service:</span></span>  
  
|<span data-ttu-id="d0392-190"><xref:System.String> Üyesidir</span><span class="sxs-lookup"><span data-stu-id="d0392-190"><xref:System.String> Member</span></span>|<span data-ttu-id="d0392-191">Desteklenen OData Işlevi</span><span class="sxs-lookup"><span data-stu-id="d0392-191">Supported OData Function</span></span>|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<span data-ttu-id="d0392-192"><xref:System.DateTime> Üye<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d0392-192"><xref:System.DateTime> Member<sup>1</sup></span></span>|<span data-ttu-id="d0392-193">Desteklenen OData Işlevi</span><span class="sxs-lookup"><span data-stu-id="d0392-193">Supported OData Function</span></span>|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <span data-ttu-id="d0392-194"><sup>1</sup> ' In ve Visual Basic içindeki yöntemin eşdeğer tarih ve saat özellikleri <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d0392-194"><sup>1</sup>The equivalent date and time properties of <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> and the <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> method in Visual Basic are also supported.</span></span>  
  
|<span data-ttu-id="d0392-195"><xref:System.Math> Üyesidir</span><span class="sxs-lookup"><span data-stu-id="d0392-195"><xref:System.Math> Member</span></span>|<span data-ttu-id="d0392-196">Desteklenen OData Işlevi</span><span class="sxs-lookup"><span data-stu-id="d0392-196">Supported OData Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<span data-ttu-id="d0392-197"><xref:System.Linq.Expressions.Expression> Üyesidir</span><span class="sxs-lookup"><span data-stu-id="d0392-197"><xref:System.Linq.Expressions.Expression> Member</span></span>|<span data-ttu-id="d0392-198">Desteklenen OData Işlevi</span><span class="sxs-lookup"><span data-stu-id="d0392-198">Supported OData Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 <span data-ttu-id="d0392-199">İstemci Ayrıca istemcideki ek CLR işlevlerini değerlendirebiliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0392-199">The client may also be able to evaluate additional CLR functions on the client.</span></span> <span data-ttu-id="d0392-200">, <xref:System.NotSupportedException> İstemcide değerlendirilemeyen herhangi bir ifade için oluşturulur ve sunucuda değerlendirme için geçerli bir Istek URI 'sine çevrilemez.</span><span class="sxs-lookup"><span data-stu-id="d0392-200">A <xref:System.NotSupportedException> is raised for any expression that cannot be evaluated on the client and cannot be translated into a valid request URI for evaluation on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0392-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0392-201">See also</span></span>

- [<span data-ttu-id="d0392-202">Veri Hizmetini Sorgulama</span><span class="sxs-lookup"><span data-stu-id="d0392-202">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)
- [<span data-ttu-id="d0392-203">Sorgu Projeksiyonları</span><span class="sxs-lookup"><span data-stu-id="d0392-203">Query Projections</span></span>](query-projections-wcf-data-services.md)
- [<span data-ttu-id="d0392-204">Nesne Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="d0392-204">Object Materialization</span></span>](object-materialization-wcf-data-services.md)
- [<span data-ttu-id="d0392-205">OData: URI kuralları</span><span class="sxs-lookup"><span data-stu-id="d0392-205">OData: URI Conventions</span></span>](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)
