---
title: Entity Framework için SqlClient
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: d81499961e7e47bba3b2594ddddd192c87a4a936
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195468"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="6ee84-102">Entity Framework için SqlClient</span><span class="sxs-lookup"><span data-stu-id="6ee84-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="6ee84-103">Bu bölümde, .NET Framework veri sağlayıcısı için Entity Framework, Microsoft SQL Server üzerinde çalışacak şekilde etkinleştirir SQL Server'nin (SqlClient) açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6ee84-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="6ee84-104">Sağlayıcı şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="6ee84-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="6ee84-105">`Provider` bir özniteliğidir `Schema` depo şeması tanım dili (SSDL) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6ee84-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="6ee84-106">SqlClient kullanmak için "System.Data.SqlClient" dize atamak `Provider` özniteliği `Schema` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6ee84-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="6ee84-107">ProviderManifestToken şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="6ee84-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="6ee84-108">`ProviderManifestToken` gerekli bir özniteliktir `Schema` SSDL öğesinde.</span><span class="sxs-lookup"><span data-stu-id="6ee84-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="6ee84-109">Bu belirteç sağlayıcı bildirimi çevrimdışı senaryolar için yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6ee84-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="6ee84-110">Hakkında daha fazla bilgi için `ProviderManifestToken` özniteliği için bkz: [şema öğesi (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="6ee84-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="6ee84-111">SqlClient farklı SQL Server sürümleri için veri sağlayıcısı olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ee84-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="6ee84-112">Bu sürümleri, farklı özelliklere sahip.</span><span class="sxs-lookup"><span data-stu-id="6ee84-112">These versions have different capabilities.</span></span> <span data-ttu-id="6ee84-113">Örneğin, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] desteklemediği `varchar(max)` ve `nvarchar(max)` ile sunulan türleri [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6ee84-113">For example, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] does not support `varchar(max)` and `nvarchar(max)` types that were introduced with [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="6ee84-114">SqlClient oluşturur ve SQL Server'ın farklı sürümlerinin aşağıdaki sağlayıcısı bildirimi belirteçleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6ee84-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="6ee84-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="6ee84-115">SQL Server 2000</span></span>|<span data-ttu-id="6ee84-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="6ee84-116">SQL Server 2005</span></span>|<span data-ttu-id="6ee84-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="6ee84-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="6ee84-118">2000</span><span class="sxs-lookup"><span data-stu-id="6ee84-118">2000</span></span>|<span data-ttu-id="6ee84-119">2005</span><span class="sxs-lookup"><span data-stu-id="6ee84-119">2005</span></span>|<span data-ttu-id="6ee84-120">2008</span><span class="sxs-lookup"><span data-stu-id="6ee84-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6ee84-121">Visual Studio 2010 ile başlayarak [ADO.NET varlık veri modeli Araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) SQL Server 2000 desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6ee84-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="6ee84-122">Sağlayıcı Namespace adı</span><span class="sxs-lookup"><span data-stu-id="6ee84-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="6ee84-123">Tüm sağlayıcılar, bir ad belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ee84-123">All providers must specify a namespace.</span></span> <span data-ttu-id="6ee84-124">Bu özellik, hangi önekin türleri ve işlevleri gibi belirli yapılar için sağlayıcı tarafından kullanılan Entity Framework söyler.</span><span class="sxs-lookup"><span data-stu-id="6ee84-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="6ee84-125">Ad alanı için SqlClient sağlayıcısı bildirimleri `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="6ee84-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="6ee84-126">Ad alanları hakkında daha fazla bilgi için bkz. [ad alanları](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6ee84-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="6ee84-127">Türler</span><span class="sxs-lookup"><span data-stu-id="6ee84-127">Types</span></span>  
 <span data-ttu-id="6ee84-128">Entity Framework için SqlClient sağlayıcısı kavramsal model türleri ve SQL Server türleri arasında eşleme bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ee84-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="6ee84-129">Daha fazla bilgi için [Entity FrameworkTypes için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="6ee84-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="6ee84-130">İşlevler</span><span class="sxs-lookup"><span data-stu-id="6ee84-130">Functions</span></span>  
 <span data-ttu-id="6ee84-131">Entity Framework için SqlClient sağlayıcısı sağlayıcı tarafından desteklenen işlevlerin listesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ee84-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="6ee84-132">Desteklenen işlevlerin bir listesi için bkz. [Entity Framework işlevleri için SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6ee84-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ee84-133">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6ee84-133">In This Section</span></span>  
 [<span data-ttu-id="6ee84-134">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6ee84-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="6ee84-135">Entity FrameworkTypes için SqlClient</span><span class="sxs-lookup"><span data-stu-id="6ee84-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="6ee84-136">Entity Framework için SqlClient’ta Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="6ee84-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="6ee84-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ee84-137">See also</span></span>

- [<span data-ttu-id="6ee84-138">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="6ee84-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="6ee84-139">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6ee84-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [<span data-ttu-id="6ee84-140">Entity Framework için SqlClient sağlayıcısı bilinen</span><span class="sxs-lookup"><span data-stu-id="6ee84-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
