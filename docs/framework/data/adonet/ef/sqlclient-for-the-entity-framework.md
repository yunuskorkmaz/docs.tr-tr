---
title: Entity Framework SqlClient
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 5949ee1931b9ab9adf1f14b921432cae531cebd5
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="678b7-102">Entity Framework SqlClient</span><span class="sxs-lookup"><span data-stu-id="678b7-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="678b7-103">Bu bölümde, .NET Framework veri sağlayıcısı için SQL Microsoft SQL Server üzerinde çalışmak Entity Framework sağlayan Server (SqlClient) açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="678b7-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="678b7-104">Sağlayıcı şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="678b7-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="678b7-105">`Provider` bir özniteliği olan `Schema` depo şeması tanım dili (SSDL) öğe.</span><span class="sxs-lookup"><span data-stu-id="678b7-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="678b7-106">SqlClient kullanmak için "System.Data.SqlClient" dizesi atamak `Provider` özniteliği `Schema` öğesi.</span><span class="sxs-lookup"><span data-stu-id="678b7-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="678b7-107">ProviderManifestToken şema özniteliği</span><span class="sxs-lookup"><span data-stu-id="678b7-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="678b7-108">`ProviderManifestToken` gerekli bir özniteliği olan `Schema` SSDL öğesinde.</span><span class="sxs-lookup"><span data-stu-id="678b7-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="678b7-109">Bu belirteç sağlayıcısı bildirimi çevrimdışı senaryolar için yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="678b7-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="678b7-110">Hakkında daha fazla bilgi için `ProviderManifestToken` özniteliği için bkz: [şema öğesi (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).</span><span class="sxs-lookup"><span data-stu-id="678b7-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](http://msdn.microsoft.com/library/fec75ae4-7f16-4421-9265-9dac61509222).</span></span>  
  
 <span data-ttu-id="678b7-111">SqlClient veri sağlayıcısı olarak SQL Server'ın farklı sürümleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="678b7-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="678b7-112">Bu sürümleri farklı özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="678b7-112">These versions have different capabilities.</span></span> <span data-ttu-id="678b7-113">Örneğin, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] desteklemediği `varchar(max)` ve `nvarchar(max)` ile sunulan türleri [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="678b7-113">For example, [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] does not support `varchar(max)` and `nvarchar(max)` types that were introduced with [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="678b7-114">SqlClient üretir ve SQL Server'ın farklı sürümleri için aşağıdaki sağlayıcı bildirim belirteci kabul eder.</span><span class="sxs-lookup"><span data-stu-id="678b7-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="678b7-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="678b7-115">SQL Server 2000</span></span>|<span data-ttu-id="678b7-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="678b7-116">SQL Server 2005</span></span>|<span data-ttu-id="678b7-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="678b7-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="678b7-118">2000</span><span class="sxs-lookup"><span data-stu-id="678b7-118">2000</span></span>|<span data-ttu-id="678b7-119">2005</span><span class="sxs-lookup"><span data-stu-id="678b7-119">2005</span></span>|<span data-ttu-id="678b7-120">2008</span><span class="sxs-lookup"><span data-stu-id="678b7-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="678b7-121">Visual Studio 2010 ile başlayan [ADO.NET varlık veri modeli Araçları](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) SQL Server 2000 desteklemez.</span><span class="sxs-lookup"><span data-stu-id="678b7-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="678b7-122">Sağlayıcı Namespace adı</span><span class="sxs-lookup"><span data-stu-id="678b7-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="678b7-123">Tüm sağlayıcılar bir ad belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="678b7-123">All providers must specify a namespace.</span></span> <span data-ttu-id="678b7-124">Bu özellik, hangi önekin türler ve işlevler gibi belirli yapıları için sağlayıcı tarafından kullanılan Entity Framework söyler.</span><span class="sxs-lookup"><span data-stu-id="678b7-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="678b7-125">Ad alanı SqlClient sağlayıcısı bildirimleri için `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="678b7-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="678b7-126">Ad alanları hakkında daha fazla bilgi için bkz: [ad alanları](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="678b7-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="678b7-127">Türler</span><span class="sxs-lookup"><span data-stu-id="678b7-127">Types</span></span>  
 <span data-ttu-id="678b7-128">SqlClient sağlayıcısı Entity Framework için kavramsal model türleri ve SQL Server türleri arasında eşleme bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="678b7-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="678b7-129">Daha fazla bilgi için bkz: [varlık FrameworkTypes SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="678b7-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="678b7-130">İşlevler</span><span class="sxs-lookup"><span data-stu-id="678b7-130">Functions</span></span>  
 <span data-ttu-id="678b7-131">SqlClient sağlayıcısı için Entity Framework sağlayıcı tarafından desteklenen işlevleri listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="678b7-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="678b7-132">Desteklenen işlevlerin bir listesi için bkz: [SqlClient Entity Framework işlevleri için](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="678b7-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="678b7-133">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="678b7-133">In This Section</span></span>  
 [<span data-ttu-id="678b7-134">Entity Framework için SqlClient İşlevleri</span><span class="sxs-lookup"><span data-stu-id="678b7-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="678b7-135">Entity FrameworkTypes için SqlClient</span><span class="sxs-lookup"><span data-stu-id="678b7-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="678b7-136">Entity Framework için SqlClient’ta Bilinen Sorunlar</span><span class="sxs-lookup"><span data-stu-id="678b7-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="678b7-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="678b7-137">See Also</span></span>  
 [<span data-ttu-id="678b7-138">Entity SQL Dili</span><span class="sxs-lookup"><span data-stu-id="678b7-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [<span data-ttu-id="678b7-139">Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="678b7-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [<span data-ttu-id="678b7-140">Bilinen sorunlar Entity Framework SqlClient Sağlayıcısı'nda</span><span class="sxs-lookup"><span data-stu-id="678b7-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
