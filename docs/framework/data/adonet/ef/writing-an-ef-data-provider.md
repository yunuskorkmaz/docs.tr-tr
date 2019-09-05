---
title: Entity Framework Veri Sağlayıcısı Yazma
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248183"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="9b672-102">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="9b672-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="9b672-103">Bu bölümde, SQL Server dışında bir veri [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] kaynağını destekleyecek bir sağlayıcının nasıl yazılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b672-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="9b672-104">, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server destekleyen bir sağlayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="9b672-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="9b672-105">Entity Framework sağlayıcı modeline giriş</span><span class="sxs-lookup"><span data-stu-id="9b672-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="9b672-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , Veritabanına bağımsızdır ve çeşitli veri kaynaklarına bağlanmak için ADO.NET sağlayıcı modelini kullanarak bir sağlayıcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b672-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="9b672-107">Entity Framework veri sağlayıcısı (ADO.NET Veri Sağlayıcısı modeli kullanılarak oluşturulan) aşağıdaki işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="9b672-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="9b672-108">Varlık Veri Modeli (EDM) temel türlerini sağlayıcı türlerine eşler.</span><span class="sxs-lookup"><span data-stu-id="9b672-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="9b672-109">Sağlayıcıya özgü işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b672-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="9b672-110">Sorguları desteklemek [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] için belirli bir DbQueryCommandTree için sağlayıcıya özel komutlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9b672-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
- <span data-ttu-id="9b672-111">İçindeki güncelleştirmeleri desteklemek için belirli bir DbModificationCommandTree için sağlayıcıya özgü güncelleştirme komutları oluşturur [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b672-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="9b672-112">Bir veritabanını temel alan bir modelin oluşturulmasını desteklemek için mağaza şeması tanımı için eşleme dosyalarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b672-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="9b672-113">Kavramsal model aracılığıyla meta verileri (örneğin, tablolar ve görünümler) kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="9b672-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="9b672-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86,&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="9b672-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="9b672-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="9b672-115">Sample</span></span>  
 <span data-ttu-id="9b672-116">SQL Server dışında bir veri kaynağını destekleyen bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] sağlayıcının örneği için [Entity Framework örnek sağlayıcısına](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) bakın.</span><span class="sxs-lookup"><span data-stu-id="9b672-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b672-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9b672-117">In This Section</span></span>  
 [<span data-ttu-id="9b672-118">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="9b672-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="9b672-119">Değişiklik SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b672-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="9b672-120">Sağlayıcı Bildirimi Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9b672-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="9b672-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b672-121">See also</span></span>

- [<span data-ttu-id="9b672-122">Veri Sağlayıcılarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="9b672-122">Working with Data Providers</span></span>](working-with-data-providers.md)
