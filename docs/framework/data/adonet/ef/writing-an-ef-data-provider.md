---
title: Bir Entity Framework veri sağlayıcısı yazma
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 254207b9c3f5edd55fff867b784d71359f6c94c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627960"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="541dd-102">Bir Entity Framework veri sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="541dd-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="541dd-103">Bu bölümde nasıl yazılacağını açıklar bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server dışındaki bir veri kaynağını desteklemek için sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="541dd-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="541dd-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server'ı destekleyen bir sağlayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="541dd-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="541dd-105">Entity Framework sağlayıcısı modeli ile tanışın</span><span class="sxs-lookup"><span data-stu-id="541dd-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="541dd-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veritabanı bağımsızdır ve farklı bir veri kaynağı kümesine bağlanmak için ADO.NET sağlayıcısı modeli kullanarak bir sağlayıcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="541dd-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="541dd-107">Entity Framework veri sağlayıcısı (ADO.NET veri sağlayıcı modeli kullanılarak oluşturulan), aşağıdaki işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="541dd-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="541dd-108">Varlık veri modeli (EDM) ilkel tür sağlayıcısı türleri ile eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="541dd-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="541dd-109">Sağlayıcıya özgü işlevleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="541dd-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="541dd-110">Sağlayıcıya özgü komutlar için desteklemek belirli bir DbQueryCommandTree oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="541dd-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="541dd-111">Sağlayıcıya özgü güncelleştirme komutları aracılığıyla güncelleştirmeleri desteklemek belirli bir DbModificationCommandTree oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="541dd-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="541dd-112">Kullanıma sunan bir veritabanını temel alan bir model oluşturulmasını desteklemek için depolama şema tanımı dosyaları eşleme.</span><span class="sxs-lookup"><span data-stu-id="541dd-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="541dd-113">Metadata (tablolar ve görünümler, örneğin) bir kavramsal model üzerinden kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="541dd-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="541dd-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="541dd-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="541dd-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="541dd-115">Sample</span></span>  
 <span data-ttu-id="541dd-116">Bkz: [Entity Framework örnek sağlayıcısı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) gösteren bir örnek bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] destekleyen SQL Server dışındaki bir veri kaynağı sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="541dd-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="541dd-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="541dd-117">In This Section</span></span>  
 [<span data-ttu-id="541dd-118">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="541dd-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="541dd-119">Değişiklik SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="541dd-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="541dd-120">Sağlayıcı Bildirimi Belirtimi</span><span class="sxs-lookup"><span data-stu-id="541dd-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="541dd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="541dd-121">See also</span></span>
- [<span data-ttu-id="541dd-122">Veri Sağlayıcılarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="541dd-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
