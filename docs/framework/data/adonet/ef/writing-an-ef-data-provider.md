---
title: "Bir Entity Framework veri sağlayıcısı yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 80f425f6e2a9d583ec221b91ae9bb2cd2604ff54
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="6f1de-102">Bir Entity Framework veri sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="6f1de-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="6f1de-103">Bu bölümde nasıl yazılacağından bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dışında bir veri kaynağı desteklemek için sağlayıcı [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f1de-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6f1de-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Destekleyen bir sağlayıcı içerir [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f1de-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="6f1de-105">Entity Framework sağlayıcı modeline giriş</span><span class="sxs-lookup"><span data-stu-id="6f1de-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="6f1de-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veritabanı bağımsızdır ve farklı veri kaynakları kümesine bağlanmak için ADO.NET sağlayıcısı modeli kullanarak bir sağlayıcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f1de-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="6f1de-107">Entity Framework veri sağlayıcısı (ADO.NET veri sağlayıcı modeli kullanılarak oluşturulan) aşağıdaki işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="6f1de-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="6f1de-108">Varlık veri modeli (EDM) ilkel türler sağlayıcısı türleri ile eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f1de-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="6f1de-109">Sağlayıcıya özgü işlevleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="6f1de-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="6f1de-110">Sağlayıcıya özgü komutlar desteklemek belirli bir DbQueryCommandTree için oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="6f1de-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="6f1de-111">Sağlayıcıya özgü güncelleştirme komutları aracılığıyla güncelleştirmeleri desteklemek belirli bir DbModificationCommandTree için oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f1de-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="6f1de-112">Bir veritabanını temel alan bir model oluşturulmasını desteklemek için depolama şema tanımı için dosyaları eşleme açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6f1de-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="6f1de-113">Meta verileri (tablolar ve görünümler, örneğin) yoluyla kavramsal model kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="6f1de-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="6f1de-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="6f1de-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="6f1de-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f1de-115">Sample</span></span>  
 <span data-ttu-id="6f1de-116">Bkz: [Entity Framework örnek sağlayıcısı](http://go.microsoft.com/fwlink/?LinkId=180616) örneği için bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dışında bir veri kaynağı destekleyen sağlayıcı [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f1de-116">See the [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f1de-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6f1de-117">In This Section</span></span>  
 [<span data-ttu-id="6f1de-118">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="6f1de-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="6f1de-119">Değişiklik SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f1de-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="6f1de-120">Sağlayıcı Bildirimi Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6f1de-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f1de-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f1de-121">See Also</span></span>  
 [<span data-ttu-id="6f1de-122">Veri Sağlayıcılarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="6f1de-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
