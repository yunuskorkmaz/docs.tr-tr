---
description: Entity Framework için SqlClient hakkında daha fazla bilgi edinin
title: Entity Framework için SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: eba5602c13f66d1ee4404bbc27035304e34c1cd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673134"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="cfd9b-103">Entity Framework için SqlClient</span><span class="sxs-lookup"><span data-stu-id="cfd9b-103">SqlClient for the Entity Framework</span></span>

<span data-ttu-id="cfd9b-104">Bu bölümde, Entity Framework Microsoft SQL Server üzerinde çalışmasını sağlayan SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-104">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="cfd9b-105">Sağlayıcı şeması özniteliği</span><span class="sxs-lookup"><span data-stu-id="cfd9b-105">Provider Schema Attribute</span></span>  

 <span data-ttu-id="cfd9b-106">`Provider` , `Schema` depo şeması tanım dili (ssdl) içindeki bir öğenin özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-106">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="cfd9b-107">SqlClient kullanmak için, "System. Data. SqlClient" dizesini `Provider` öğesinin özniteliğine atayın `Schema` .</span><span class="sxs-lookup"><span data-stu-id="cfd9b-107">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="cfd9b-108">ProviderManifestToken şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="cfd9b-108">ProviderManifestToken Schema Attribute</span></span>  

 <span data-ttu-id="cfd9b-109">`ProviderManifestToken` , `Schema` SSDL içindeki öğesinin gerekli bir özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-109">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="cfd9b-110">Bu belirteç, çevrimdışı senaryolar için sağlayıcı bildirimini yüklemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-110">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="cfd9b-111">Özniteliği hakkında daha fazla bilgi için `ProviderManifestToken` bkz. [şema Öğesı (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="cfd9b-111">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="cfd9b-112">SqlClient, farklı SQL Server sürümleri için veri sağlayıcısı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-112">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="cfd9b-113">Bu sürümlerin farklı özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-113">These versions have different capabilities.</span></span> <span data-ttu-id="cfd9b-114">Örneğin, SQL Server 2000 desteklemez `varchar(max)` ve `nvarchar(max)` SQL Server 2005 ile tanıtılan türler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-114">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="cfd9b-115">SqlClient farklı SQL Server sürümleri için aşağıdaki sağlayıcı bildirim belirteçlerini üretir ve kabul eder.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-115">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="cfd9b-116">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="cfd9b-116">SQL Server 2000</span></span>|<span data-ttu-id="cfd9b-117">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="cfd9b-117">SQL Server 2005</span></span>|<span data-ttu-id="cfd9b-118">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="cfd9b-118">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="cfd9b-119">2000</span><span class="sxs-lookup"><span data-stu-id="cfd9b-119">2000</span></span>|<span data-ttu-id="cfd9b-120">2005</span><span class="sxs-lookup"><span data-stu-id="cfd9b-120">2005</span></span>|<span data-ttu-id="cfd9b-121">2008</span><span class="sxs-lookup"><span data-stu-id="cfd9b-121">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="cfd9b-122">Visual Studio 2010 ' den itibaren, [ADO.NET varlık veri modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) SQL Server 2000 ' yi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-122">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="cfd9b-123">Sağlayıcı ad alanı adı</span><span class="sxs-lookup"><span data-stu-id="cfd9b-123">Provider Namespace Name</span></span>  

 <span data-ttu-id="cfd9b-124">Tüm sağlayıcıların bir ad alanı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-124">All providers must specify a namespace.</span></span> <span data-ttu-id="cfd9b-125">Bu özellik, sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan önek Entity Framework söyler.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-125">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="cfd9b-126">SqlClient sağlayıcı bildirimleri için ad alanı `SqlServer` .</span><span class="sxs-lookup"><span data-stu-id="cfd9b-126">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="cfd9b-127">Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları](./language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cfd9b-127">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="cfd9b-128">Türler</span><span class="sxs-lookup"><span data-stu-id="cfd9b-128">Types</span></span>  

 <span data-ttu-id="cfd9b-129">Entity Framework için SqlClient sağlayıcısı, kavramsal model türleri ve SQL Server türleri arasında eşleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-129">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="cfd9b-130">Daha fazla bilgi için bkz. [Entity FrameworkTypes Için SqlClient](sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="cfd9b-130">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="cfd9b-131">İşlevler</span><span class="sxs-lookup"><span data-stu-id="cfd9b-131">Functions</span></span>  

 <span data-ttu-id="cfd9b-132">Entity Framework için SqlClient sağlayıcısı, sağlayıcı tarafından desteklenen işlevlerin listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-132">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="cfd9b-133">Desteklenen işlevlerin listesi için bkz. [Entity Framework işlevleri Için SqlClient](sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="cfd9b-133">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cfd9b-134">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cfd9b-134">In This Section</span></span>  

 [<span data-ttu-id="cfd9b-135">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cfd9b-135">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="cfd9b-136">Entity FrameworkTypes için SqlClient</span><span class="sxs-lookup"><span data-stu-id="cfd9b-136">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="cfd9b-137">Entity Framework için SqlClient’ta Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="cfd9b-137">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="cfd9b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfd9b-138">See also</span></span>

- [<span data-ttu-id="cfd9b-139">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="cfd9b-139">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="cfd9b-140">Dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="cfd9b-140">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="cfd9b-141">Entity Framework için SqlClient sağlayıcısında bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="cfd9b-141">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
