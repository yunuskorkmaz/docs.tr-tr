---
title: Entity Framework için SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: 7f3a1d4bbd18977bbb1dc9ce65140428ea6fe2f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156543"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="2e68a-102">Entity Framework için SqlClient</span><span class="sxs-lookup"><span data-stu-id="2e68a-102">SqlClient for the Entity Framework</span></span>

<span data-ttu-id="2e68a-103">Bu bölümde, Entity Framework Microsoft SQL Server üzerinde çalışmasını sağlayan SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e68a-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="2e68a-104">Sağlayıcı şeması özniteliği</span><span class="sxs-lookup"><span data-stu-id="2e68a-104">Provider Schema Attribute</span></span>  

 <span data-ttu-id="2e68a-105">`Provider` , `Schema` depo şeması tanım dili (ssdl) içindeki bir öğenin özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="2e68a-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="2e68a-106">SqlClient kullanmak için, "System. Data. SqlClient" dizesini `Provider` öğesinin özniteliğine atayın `Schema` .</span><span class="sxs-lookup"><span data-stu-id="2e68a-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="2e68a-107">ProviderManifestToken şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="2e68a-107">ProviderManifestToken Schema Attribute</span></span>  

 <span data-ttu-id="2e68a-108">`ProviderManifestToken` , `Schema` SSDL içindeki öğesinin gerekli bir özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="2e68a-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="2e68a-109">Bu belirteç, çevrimdışı senaryolar için sağlayıcı bildirimini yüklemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e68a-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="2e68a-110">Özniteliği hakkında daha fazla bilgi için `ProviderManifestToken` bkz. [şema Öğesı (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="2e68a-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="2e68a-111">SqlClient, farklı SQL Server sürümleri için veri sağlayıcısı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e68a-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="2e68a-112">Bu sürümlerin farklı özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2e68a-112">These versions have different capabilities.</span></span> <span data-ttu-id="2e68a-113">Örneğin, SQL Server 2000 desteklemez `varchar(max)` ve `nvarchar(max)` SQL Server 2005 ile tanıtılan türler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2e68a-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="2e68a-114">SqlClient farklı SQL Server sürümleri için aşağıdaki sağlayıcı bildirim belirteçlerini üretir ve kabul eder.</span><span class="sxs-lookup"><span data-stu-id="2e68a-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="2e68a-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="2e68a-115">SQL Server 2000</span></span>|<span data-ttu-id="2e68a-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="2e68a-116">SQL Server 2005</span></span>|<span data-ttu-id="2e68a-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="2e68a-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="2e68a-118">2000</span><span class="sxs-lookup"><span data-stu-id="2e68a-118">2000</span></span>|<span data-ttu-id="2e68a-119">2005</span><span class="sxs-lookup"><span data-stu-id="2e68a-119">2005</span></span>|<span data-ttu-id="2e68a-120">2008</span><span class="sxs-lookup"><span data-stu-id="2e68a-120">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="2e68a-121">Visual Studio 2010 ' den itibaren, [ADO.NET varlık veri modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) SQL Server 2000 ' yi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2e68a-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="2e68a-122">Sağlayıcı ad alanı adı</span><span class="sxs-lookup"><span data-stu-id="2e68a-122">Provider Namespace Name</span></span>  

 <span data-ttu-id="2e68a-123">Tüm sağlayıcıların bir ad alanı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e68a-123">All providers must specify a namespace.</span></span> <span data-ttu-id="2e68a-124">Bu özellik, sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan önek Entity Framework söyler.</span><span class="sxs-lookup"><span data-stu-id="2e68a-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="2e68a-125">SqlClient sağlayıcı bildirimleri için ad alanı `SqlServer` .</span><span class="sxs-lookup"><span data-stu-id="2e68a-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="2e68a-126">Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları](./language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2e68a-126">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="2e68a-127">Türler</span><span class="sxs-lookup"><span data-stu-id="2e68a-127">Types</span></span>  

 <span data-ttu-id="2e68a-128">Entity Framework için SqlClient sağlayıcısı, kavramsal model türleri ve SQL Server türleri arasında eşleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2e68a-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="2e68a-129">Daha fazla bilgi için bkz. [Entity FrameworkTypes Için SqlClient](sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="2e68a-129">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="2e68a-130">İşlevler</span><span class="sxs-lookup"><span data-stu-id="2e68a-130">Functions</span></span>  

 <span data-ttu-id="2e68a-131">Entity Framework için SqlClient sağlayıcısı, sağlayıcı tarafından desteklenen işlevlerin listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2e68a-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="2e68a-132">Desteklenen işlevlerin listesi için bkz. [Entity Framework işlevleri Için SqlClient](sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="2e68a-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2e68a-133">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2e68a-133">In This Section</span></span>  

 [<span data-ttu-id="2e68a-134">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2e68a-134">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="2e68a-135">Entity FrameworkTypes için SqlClient</span><span class="sxs-lookup"><span data-stu-id="2e68a-135">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="2e68a-136">Entity Framework için SqlClient’ta Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="2e68a-136">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="2e68a-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e68a-137">See also</span></span>

- [<span data-ttu-id="2e68a-138">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="2e68a-138">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="2e68a-139">Dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="2e68a-139">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="2e68a-140">Entity Framework için SqlClient sağlayıcısında bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="2e68a-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
