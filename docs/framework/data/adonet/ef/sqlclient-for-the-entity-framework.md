---
title: Entity Framework için SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: ec67637c416f2560c1f5d0a9fd0e856703820a84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954963"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="6dc8b-102">Entity Framework için SqlClient</span><span class="sxs-lookup"><span data-stu-id="6dc8b-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="6dc8b-103">Bu bölümde, Entity Framework Microsoft SQL Server üzerinde çalışmasını sağlayan SQL Server (SqlClient) için .NET Framework Veri Sağlayıcısı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="6dc8b-104">Sağlayıcı şeması özniteliği</span><span class="sxs-lookup"><span data-stu-id="6dc8b-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="6dc8b-105">`Provider`, depo şeması tanım dili `Schema` (ssdl) içindeki bir öğenin özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="6dc8b-106">SqlClient kullanmak için, "System. Data. SqlClient" `Provider` dizesini `Schema` öğesinin özniteliğine atayın.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="6dc8b-107">ProviderManifestToken şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="6dc8b-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="6dc8b-108">`ProviderManifestToken`, SSDL içindeki `Schema` öğesinin gerekli bir özniteliğidir.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="6dc8b-109">Bu belirteç, çevrimdışı senaryolar için sağlayıcı bildirimini yüklemek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="6dc8b-110">Özniteliği hakkında `ProviderManifestToken` daha fazla bilgi için bkz. [şema öğesi (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="6dc8b-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="6dc8b-111">SqlClient, farklı SQL Server sürümleri için veri sağlayıcısı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="6dc8b-112">Bu sürümlerin farklı özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-112">These versions have different capabilities.</span></span> <span data-ttu-id="6dc8b-113">Örneğin, SQL Server 2000 desteklemez `varchar(max)` ve `nvarchar(max)` SQL Server 2005 ile tanıtılan türler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="6dc8b-114">SqlClient farklı SQL Server sürümleri için aşağıdaki sağlayıcı bildirim belirteçlerini üretir ve kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="6dc8b-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="6dc8b-115">SQL Server 2000</span></span>|<span data-ttu-id="6dc8b-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="6dc8b-116">SQL Server 2005</span></span>|<span data-ttu-id="6dc8b-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="6dc8b-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="6dc8b-118">2000</span><span class="sxs-lookup"><span data-stu-id="6dc8b-118">2000</span></span>|<span data-ttu-id="6dc8b-119">2005</span><span class="sxs-lookup"><span data-stu-id="6dc8b-119">2005</span></span>|<span data-ttu-id="6dc8b-120">2008</span><span class="sxs-lookup"><span data-stu-id="6dc8b-120">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6dc8b-121">Visual Studio 2010 ' den itibaren, [ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) SQL Server 2000 ' yi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="6dc8b-122">Sağlayıcı ad alanı adı</span><span class="sxs-lookup"><span data-stu-id="6dc8b-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="6dc8b-123">Tüm sağlayıcıların bir ad alanı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-123">All providers must specify a namespace.</span></span> <span data-ttu-id="6dc8b-124">Bu özellik, sağlayıcı tarafından türler ve işlevler gibi belirli yapılar için kullanılan önek Entity Framework söyler.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="6dc8b-125">SqlClient sağlayıcı bildirimleri `SqlServer`için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="6dc8b-126">Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6dc8b-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="6dc8b-127">Türler</span><span class="sxs-lookup"><span data-stu-id="6dc8b-127">Types</span></span>  
 <span data-ttu-id="6dc8b-128">Entity Framework için SqlClient sağlayıcısı, kavramsal model türleri ve SQL Server türleri arasında eşleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="6dc8b-129">Daha fazla bilgi için bkz. [Entity FrameworkTypes Için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="6dc8b-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="6dc8b-130">İşlevler</span><span class="sxs-lookup"><span data-stu-id="6dc8b-130">Functions</span></span>  
 <span data-ttu-id="6dc8b-131">Entity Framework için SqlClient sağlayıcısı, sağlayıcı tarafından desteklenen işlevlerin listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="6dc8b-132">Desteklenen işlevlerin listesi için bkz. [Entity Framework işlevleri Için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6dc8b-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6dc8b-133">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6dc8b-133">In This Section</span></span>  
 [<span data-ttu-id="6dc8b-134">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6dc8b-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="6dc8b-135">Entity FrameworkTypes için SqlClient</span><span class="sxs-lookup"><span data-stu-id="6dc8b-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="6dc8b-136">Entity Framework için SqlClient’ta Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="6dc8b-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="6dc8b-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dc8b-137">See also</span></span>

- [<span data-ttu-id="6dc8b-138">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="6dc8b-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="6dc8b-139">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6dc8b-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [<span data-ttu-id="6dc8b-140">Entity Framework için SqlClient sağlayıcısında bilinen sorunlar</span><span class="sxs-lookup"><span data-stu-id="6dc8b-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
