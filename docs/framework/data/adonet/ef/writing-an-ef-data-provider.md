---
title: Entity Framework Veri Sağlayıcısı Yazma
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854166"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="e011d-102">Entity Framework Veri Sağlayıcısı Yazma</span><span class="sxs-lookup"><span data-stu-id="e011d-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="e011d-103">Bu bölümde, SQL Server dışında bir veri kaynağını desteklemek için Entity Framework sağlayıcısı yazma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e011d-103">This section discusses how to write an Entity Framework provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="e011d-104">Entity Framework, SQL Server destekleyen bir sağlayıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="e011d-104">The Entity Framework includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="e011d-105">Entity Framework sağlayıcı modeline giriş</span><span class="sxs-lookup"><span data-stu-id="e011d-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="e011d-106">Entity Framework, veritabanına bağımsızdır ve çeşitli veri kaynaklarına bağlanmak için ADO.NET sağlayıcı modelini kullanarak bir sağlayıcı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e011d-106">The Entity Framework is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="e011d-107">Entity Framework veri sağlayıcısı (ADO.NET Veri Sağlayıcısı modeli kullanılarak oluşturulan) aşağıdaki işlevleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e011d-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="e011d-108">Varlık Veri Modeli (EDM) temel türlerini sağlayıcı türlerine eşler.</span><span class="sxs-lookup"><span data-stu-id="e011d-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="e011d-109">Sağlayıcıya özgü işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="e011d-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="e011d-110">Entity Framework sorgularını desteklemek için belirli bir DbQueryCommandTree için sağlayıcıya özel komutlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e011d-110">Generates provider-specific commands for a given DbQueryCommandTree to support Entity Framework queries.</span></span>  
  
- <span data-ttu-id="e011d-111">Entity Framework aracılığıyla güncelleştirmeleri desteklemek için belirli bir DbModificationCommandTree için sağlayıcıya özgü güncelleştirme komutları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e011d-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the Entity Framework.</span></span>  
  
- <span data-ttu-id="e011d-112">Bir veritabanını temel alan bir modelin oluşturulmasını desteklemek için mağaza şeması tanımı için eşleme dosyalarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e011d-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="e011d-113">Kavramsal model aracılığıyla meta verileri (örneğin, tablolar ve görünümler) kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="e011d-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="e011d-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86,&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="e011d-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="e011d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="e011d-115">Sample</span></span>  
 <span data-ttu-id="e011d-116">SQL Server dışında bir veri kaynağını destekleyen bir Entity Framework sağlayıcısı örneği için [Entity Framework örnek sağlayıcısına](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) bakın.</span><span class="sxs-lookup"><span data-stu-id="e011d-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an Entity Framework provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e011d-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e011d-117">In This Section</span></span>  
 [<span data-ttu-id="e011d-118">SQL Üretimi</span><span class="sxs-lookup"><span data-stu-id="e011d-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="e011d-119">Değişiklik SQL Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e011d-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="e011d-120">Sağlayıcı Bildirimi Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e011d-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="e011d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e011d-121">See also</span></span>

- [<span data-ttu-id="e011d-122">Veri Sağlayıcılarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="e011d-122">Working with Data Providers</span></span>](working-with-data-providers.md)
