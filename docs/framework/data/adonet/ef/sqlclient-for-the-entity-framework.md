---
title: Entity Framework için SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: e8933a975c075407066bff97672f1b82f125bb47
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662106"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="9f49a-102">Entity Framework için SqlClient</span><span class="sxs-lookup"><span data-stu-id="9f49a-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="9f49a-103">Bu bölümde, .NET Framework veri sağlayıcısı için Entity Framework, Microsoft SQL Server üzerinde çalışacak şekilde etkinleştirir SQL Server'nin (SqlClient) açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f49a-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="9f49a-104">Sağlayıcı şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="9f49a-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="9f49a-105">`Provider` bir özniteliğidir `Schema` depo şeması tanım dili (SSDL) öğesi.</span><span class="sxs-lookup"><span data-stu-id="9f49a-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="9f49a-106">SqlClient kullanmak için "System.Data.SqlClient" dize atamak `Provider` özniteliği `Schema` öğesi.</span><span class="sxs-lookup"><span data-stu-id="9f49a-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="9f49a-107">ProviderManifestToken şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="9f49a-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="9f49a-108">`ProviderManifestToken` gerekli bir özniteliktir `Schema` SSDL öğesinde.</span><span class="sxs-lookup"><span data-stu-id="9f49a-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="9f49a-109">Bu belirteç sağlayıcı bildirimi çevrimdışı senaryolar için yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f49a-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="9f49a-110">Hakkında daha fazla bilgi için `ProviderManifestToken` özniteliği için bkz: [şema öğesi (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="9f49a-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="9f49a-111">SqlClient farklı SQL Server sürümleri için veri sağlayıcısı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f49a-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="9f49a-112">Bu sürümleri, farklı özelliklere sahip.</span><span class="sxs-lookup"><span data-stu-id="9f49a-112">These versions have different capabilities.</span></span> <span data-ttu-id="9f49a-113">Örneğin, SQL Server 2000 desteklemediği `varchar(max)` ve `nvarchar(max)` SQL Server 2005'te tanıtılan türleri.</span><span class="sxs-lookup"><span data-stu-id="9f49a-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="9f49a-114">SqlClient oluşturur ve SQL Server'ın farklı sürümlerinin aşağıdaki sağlayıcısı bildirimi belirteçleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9f49a-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="9f49a-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="9f49a-115">SQL Server 2000</span></span>|<span data-ttu-id="9f49a-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="9f49a-116">SQL Server 2005</span></span>|<span data-ttu-id="9f49a-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="9f49a-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="9f49a-118">2000</span><span class="sxs-lookup"><span data-stu-id="9f49a-118">2000</span></span>|<span data-ttu-id="9f49a-119">2005</span><span class="sxs-lookup"><span data-stu-id="9f49a-119">2005</span></span>|<span data-ttu-id="9f49a-120">2008</span><span class="sxs-lookup"><span data-stu-id="9f49a-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9f49a-121">Visual Studio 2010 ile başlayarak [ADO.NET varlık veri modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) SQL Server 2000 desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9f49a-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="9f49a-122">Sağlayıcı Namespace adı</span><span class="sxs-lookup"><span data-stu-id="9f49a-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="9f49a-123">Tüm sağlayıcılar, bir ad belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f49a-123">All providers must specify a namespace.</span></span> <span data-ttu-id="9f49a-124">Bu özellik, hangi önekin türleri ve işlevleri gibi belirli yapılar için sağlayıcı tarafından kullanılan Entity Framework söyler.</span><span class="sxs-lookup"><span data-stu-id="9f49a-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="9f49a-125">Ad alanı için SqlClient sağlayıcısı bildirimleri `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="9f49a-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="9f49a-126">Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9f49a-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="9f49a-127">Türler</span><span class="sxs-lookup"><span data-stu-id="9f49a-127">Types</span></span>  
 <span data-ttu-id="9f49a-128">Entity Framework için SqlClient sağlayıcısı kavramsal model türleri ve SQL Server türleri arasında eşleme bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f49a-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="9f49a-129">Daha fazla bilgi için [Entity FrameworkTypes için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="9f49a-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="9f49a-130">İşlevler</span><span class="sxs-lookup"><span data-stu-id="9f49a-130">Functions</span></span>  
 <span data-ttu-id="9f49a-131">Entity Framework için SqlClient sağlayıcısı sağlayıcı tarafından desteklenen işlevlerin listesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f49a-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="9f49a-132">Desteklenen işlevlerin bir listesi için bkz. [Entity Framework işlevleri için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="9f49a-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f49a-133">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9f49a-133">In This Section</span></span>  
 [<span data-ttu-id="9f49a-134">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9f49a-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="9f49a-135">Entity FrameworkTypes için SqlClient</span><span class="sxs-lookup"><span data-stu-id="9f49a-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="9f49a-136">Entity Framework için SqlClient’ta Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="9f49a-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="9f49a-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f49a-137">See also</span></span>

- [<span data-ttu-id="9f49a-138">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="9f49a-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="9f49a-139">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9f49a-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [<span data-ttu-id="9f49a-140">Entity Framework için SqlClient sağlayıcısı bilinen</span><span class="sxs-lookup"><span data-stu-id="9f49a-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
