---
title: Sorgu Desteği
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: e281b5ae7a41bd282f8e7c7eb9db6f99ef5487f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948934"
---
# <a name="support-for-queries"></a><span data-ttu-id="d0b8d-102">Sorgu Desteği</span><span class="sxs-lookup"><span data-stu-id="d0b8d-102">Support for Queries</span></span>
<span data-ttu-id="d0b8d-103">SQL Iş akışı örneği deposu depodaki bir dizi iyi bilinen özelliği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="d0b8d-104">Kullanıcılar, bu özelliklere göre örnekleri sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="d0b8d-105">Aşağıdaki listede, bu iyi bilinen özelliklerden bazıları yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="d0b8d-105">The following list contains some of these well-known properties:</span></span>  
  
- <span data-ttu-id="d0b8d-106">**Site adı.**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-106">**Site Name.**</span></span> <span data-ttu-id="d0b8d-107">Hizmeti içeren Web sitesinin adı.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-107">Name of the Web site that contains the service.</span></span>  
  
- <span data-ttu-id="d0b8d-108">**Göreli uygulama yolu.**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-108">**Relative Application Path.**</span></span> <span data-ttu-id="d0b8d-109">Web sitesine göre uygulamanın yolu.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-109">Path of the application relative to the Web site.</span></span>  
  
- <span data-ttu-id="d0b8d-110">**Göreli hizmet yolu.**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-110">**Relative Service Path.**</span></span> <span data-ttu-id="d0b8d-111">Uygulamaya göre hizmetin yolu.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-111">Path of the service relative to the application.</span></span>  
  
- <span data-ttu-id="d0b8d-112">**Hizmet adı.**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-112">**Service Name.**</span></span> <span data-ttu-id="d0b8d-113">Hizmetin adı.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-113">Name of the service.</span></span>  
  
- <span data-ttu-id="d0b8d-114">**Hizmet ad alanı.**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-114">**Service Namespace.**</span></span> <span data-ttu-id="d0b8d-115">Hizmetin kullandığı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-115">Name of the namespace that the service uses.</span></span>  
  
- <span data-ttu-id="d0b8d-116">**Geçerli makine.**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-116">**Current Machine.**</span></span>  
  
- <span data-ttu-id="d0b8d-117">**Son makine**.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-117">**Last Machine**.</span></span> <span data-ttu-id="d0b8d-118">İş akışı hizmeti örneğinin son çalıştırıldığı bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0b8d-119">Iş akışı hizmeti ana bilgisayarı kullanan şirket içinde barındırılan senaryolar için yalnızca son dört Özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="d0b8d-120">Iş akışı uygulama senaryolarında yalnızca son özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="d0b8d-121">İş akışı çalışma zamanı, ilk üç özellik için değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="d0b8d-122">İş akışı hizmeti Konağı, **askıya alma nedeni** özelliğinin değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="d0b8d-123">SQL Iş akışı örneği deposunun kendisi, **son güncelleştirilmiş makine** özelliği için değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="d0b8d-124">SQL Iş akışı örneği deposu özelliği ayrıca, değerlerini Kalıcılık veritabanında depolamak istediğiniz ve sorgularda kullanmak istediğiniz özel özellikleri belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="d0b8d-125">Özel promosyonlar hakkında daha fazla bilgi için bkz. [depolama genişletilebilirliği](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="d0b8d-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="d0b8d-126">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d0b8d-126">Views</span></span>  
 <span data-ttu-id="d0b8d-127">Örnek deposu aşağıdaki görünümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-127">The instance store contains the following views.</span></span> <span data-ttu-id="d0b8d-128">Daha fazla ayrıntı için bkz. [Kalıcılık veritabanı şeması](persistence-database-schema.md) .</span><span class="sxs-lookup"><span data-stu-id="d0b8d-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="d0b8d-129">Örnekler görünümü</span><span class="sxs-lookup"><span data-stu-id="d0b8d-129">The Instances View</span></span>  
 <span data-ttu-id="d0b8d-130">Örnekler görünümü aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="d0b8d-130">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="d0b8d-131">**Kimlik**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-131">**Id**</span></span>  
  
2. <span data-ttu-id="d0b8d-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-132">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="d0b8d-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-133">**CreationTime**</span></span>  
  
4. <span data-ttu-id="d0b8d-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-134">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="d0b8d-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-135">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="d0b8d-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-136">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="d0b8d-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-137">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="d0b8d-138">**Activeyer Işaretleri**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="d0b8d-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="d0b8d-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="d0b8d-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="d0b8d-142">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="d0b8d-143">**Isaskıya alındı**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="d0b8d-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="d0b8d-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="d0b8d-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="d0b8d-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="d0b8d-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="d0b8d-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="d0b8d-150">Servicedağıtımlar görünümü</span><span class="sxs-lookup"><span data-stu-id="d0b8d-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="d0b8d-151">Servicedağıtımlar görünümü aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="d0b8d-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="d0b8d-152">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-152">**SiteName**</span></span>  
  
2. <span data-ttu-id="d0b8d-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-153">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="d0b8d-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-154">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="d0b8d-155">**HizmetAdı**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-155">**ServiceName**</span></span>  
  
5. <span data-ttu-id="d0b8d-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="d0b8d-157">InstancePromotedProperties görünümü</span><span class="sxs-lookup"><span data-stu-id="d0b8d-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="d0b8d-158">InstancePromotedProperties görünümü aşağıdaki alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="d0b8d-159">Yükseltilen özelliklerle ilgili ayrıntılar için bkz. [depolama genişletilebilirliği](store-extensibility.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="d0b8d-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="d0b8d-160">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-160">**InstanceId**</span></span>  
  
2. <span data-ttu-id="d0b8d-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-161">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="d0b8d-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="d0b8d-162">**PromotionName**</span></span>  
  
4. <span data-ttu-id="d0b8d-163">**Değer #** ( **değer1** ile **Value64**arasında bir alan aralığı).</span><span class="sxs-lookup"><span data-stu-id="d0b8d-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
