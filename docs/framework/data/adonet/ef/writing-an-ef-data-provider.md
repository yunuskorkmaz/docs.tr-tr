---
title: Bir Entity Framework veri sağlayıcısı yazma
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 578de94aa191d7302b762f1cdc87d4a6810037e3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762640"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="113d6-102">Bir Entity Framework veri sağlayıcısı yazma</span><span class="sxs-lookup"><span data-stu-id="113d6-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="113d6-103">Bu bölümde nasıl yazılacağından bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL sunucusu dışında bir veri kaynağı desteklemek için sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="113d6-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="113d6-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server'ı destekleyen bir sağlayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="113d6-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="113d6-105">Entity Framework sağlayıcı modeline giriş</span><span class="sxs-lookup"><span data-stu-id="113d6-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="113d6-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Veritabanı bağımsızdır ve farklı veri kaynakları kümesine bağlanmak için ADO.NET sağlayıcısı modeli kullanarak bir sağlayıcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="113d6-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="113d6-107">Entity Framework veri sağlayıcısı (ADO.NET veri sağlayıcı modeli kullanılarak oluşturulan) aşağıdaki işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="113d6-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="113d6-108">Varlık veri modeli (EDM) ilkel türler sağlayıcısı türleri ile eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="113d6-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="113d6-109">Sağlayıcıya özgü işlevleri kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="113d6-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="113d6-110">Sağlayıcıya özgü komutlar desteklemek belirli bir DbQueryCommandTree için oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="113d6-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="113d6-111">Sağlayıcıya özgü güncelleştirme komutları aracılığıyla güncelleştirmeleri desteklemek belirli bir DbModificationCommandTree için oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="113d6-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="113d6-112">Bir veritabanını temel alan bir model oluşturulmasını desteklemek için depolama şema tanımı için dosyaları eşleme açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="113d6-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="113d6-113">Meta verileri (tablolar ve görünümler, örneğin) yoluyla kavramsal model kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="113d6-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="113d6-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="113d6-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="113d6-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="113d6-115">Sample</span></span>  
 <span data-ttu-id="113d6-116">Bkz: [Entity Framework örnek sağlayıcısı](http://go.microsoft.com/fwlink/?LinkId=180616) örneği için bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] destekleyen SQL sunucusu dışında bir veri kaynağı sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="113d6-116">See the [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="113d6-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="113d6-117">In This Section</span></span>  
 [<span data-ttu-id="113d6-118">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="113d6-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="113d6-119">Değişiklik SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="113d6-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="113d6-120">Sağlayıcı Bildirimi Belirtimi</span><span class="sxs-lookup"><span data-stu-id="113d6-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="113d6-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="113d6-121">See Also</span></span>  
 [<span data-ttu-id="113d6-122">Veri Sağlayıcılarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="113d6-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
