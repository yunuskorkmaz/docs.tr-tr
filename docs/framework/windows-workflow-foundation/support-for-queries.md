---
description: 'Hakkında daha fazla bilgi edinin: sorgular için destek'
title: Sorgu Desteği
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 418e511e8b845653b9f3ec86d90c6cbfb25d5671
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755219"
---
# <a name="support-for-queries"></a><span data-ttu-id="05af0-103">Sorgu Desteği</span><span class="sxs-lookup"><span data-stu-id="05af0-103">Support for Queries</span></span>

<span data-ttu-id="05af0-104">SQL Iş akışı örneği deposu depodaki bir dizi iyi bilinen özelliği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="05af0-104">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="05af0-105">Kullanıcılar, bu özelliklere göre örnekleri sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="05af0-105">Users can query for instances based on these properties.</span></span> <span data-ttu-id="05af0-106">Aşağıdaki listede, bu iyi bilinen özelliklerden bazıları yer almaktadır:</span><span class="sxs-lookup"><span data-stu-id="05af0-106">The following list contains some of these well-known properties:</span></span>  
  
- <span data-ttu-id="05af0-107">**Site adı.**</span><span class="sxs-lookup"><span data-stu-id="05af0-107">**Site Name.**</span></span> <span data-ttu-id="05af0-108">Hizmeti içeren Web sitesinin adı.</span><span class="sxs-lookup"><span data-stu-id="05af0-108">Name of the Web site that contains the service.</span></span>  
  
- <span data-ttu-id="05af0-109">**Göreli uygulama yolu.**</span><span class="sxs-lookup"><span data-stu-id="05af0-109">**Relative Application Path.**</span></span> <span data-ttu-id="05af0-110">Web sitesine göre uygulamanın yolu.</span><span class="sxs-lookup"><span data-stu-id="05af0-110">Path of the application relative to the Web site.</span></span>  
  
- <span data-ttu-id="05af0-111">**Göreli hizmet yolu.**</span><span class="sxs-lookup"><span data-stu-id="05af0-111">**Relative Service Path.**</span></span> <span data-ttu-id="05af0-112">Uygulamaya göre hizmetin yolu.</span><span class="sxs-lookup"><span data-stu-id="05af0-112">Path of the service relative to the application.</span></span>  
  
- <span data-ttu-id="05af0-113">**Hizmet adı.**</span><span class="sxs-lookup"><span data-stu-id="05af0-113">**Service Name.**</span></span> <span data-ttu-id="05af0-114">Hizmetin adı.</span><span class="sxs-lookup"><span data-stu-id="05af0-114">Name of the service.</span></span>  
  
- <span data-ttu-id="05af0-115">**Hizmet ad alanı.**</span><span class="sxs-lookup"><span data-stu-id="05af0-115">**Service Namespace.**</span></span> <span data-ttu-id="05af0-116">Hizmetin kullandığı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="05af0-116">Name of the namespace that the service uses.</span></span>  
  
- <span data-ttu-id="05af0-117">**Geçerli makine.**</span><span class="sxs-lookup"><span data-stu-id="05af0-117">**Current Machine.**</span></span>  
  
- <span data-ttu-id="05af0-118">**Son makine**.</span><span class="sxs-lookup"><span data-stu-id="05af0-118">**Last Machine**.</span></span> <span data-ttu-id="05af0-119">İş akışı hizmeti örneğinin son çalıştırıldığı bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="05af0-119">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05af0-120">Iş akışı hizmeti ana bilgisayarı kullanan şirket içinde barındırılan senaryolar için yalnızca son dört Özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="05af0-120">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="05af0-121">Iş akışı uygulama senaryolarında yalnızca son özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="05af0-121">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="05af0-122">İş akışı çalışma zamanı, ilk üç özellik için değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="05af0-122">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="05af0-123">İş akışı hizmeti Konağı, **askıya alma nedeni** özelliğinin değerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="05af0-123">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="05af0-124">SQL Iş akışı örneği deposunun kendisi, **son güncelleştirilmiş makine** özelliği için değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="05af0-124">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="05af0-125">SQL Iş akışı örneği deposu özelliği ayrıca, değerlerini Kalıcılık veritabanında depolamak istediğiniz ve sorgularda kullanmak istediğiniz özel özellikleri belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="05af0-125">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="05af0-126">Özel promosyonlar hakkında daha fazla bilgi için bkz. [depolama genişletilebilirliği](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="05af0-126">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="05af0-127">Görünümler</span><span class="sxs-lookup"><span data-stu-id="05af0-127">Views</span></span>  

 <span data-ttu-id="05af0-128">Örnek deposu aşağıdaki görünümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="05af0-128">The instance store contains the following views.</span></span> <span data-ttu-id="05af0-129">Daha fazla ayrıntı için bkz. [Kalıcılık veritabanı şeması](persistence-database-schema.md) .</span><span class="sxs-lookup"><span data-stu-id="05af0-129">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="05af0-130">Örnekler görünümü</span><span class="sxs-lookup"><span data-stu-id="05af0-130">The Instances View</span></span>  

 <span data-ttu-id="05af0-131">Örnekler görünümü aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="05af0-131">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="05af0-132">**Numarasını**</span><span class="sxs-lookup"><span data-stu-id="05af0-132">**Id**</span></span>  
  
2. <span data-ttu-id="05af0-133">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="05af0-133">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="05af0-134">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="05af0-134">**CreationTime**</span></span>  
  
4. <span data-ttu-id="05af0-135">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="05af0-135">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="05af0-136">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="05af0-136">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="05af0-137">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="05af0-137">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="05af0-138">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="05af0-138">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="05af0-139">**Activeyer Işaretleri**</span><span class="sxs-lookup"><span data-stu-id="05af0-139">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="05af0-140">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="05af0-140">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="05af0-141">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="05af0-141">**LastMachine**</span></span>  
  
11. <span data-ttu-id="05af0-142">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="05af0-142">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="05af0-143">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="05af0-143">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="05af0-144">**Isaskıya alındı**</span><span class="sxs-lookup"><span data-stu-id="05af0-144">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="05af0-145">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="05af0-145">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="05af0-146">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="05af0-146">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="05af0-147">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="05af0-147">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="05af0-148">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="05af0-148">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="05af0-149">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="05af0-149">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="05af0-150">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="05af0-150">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="05af0-151">Servicedağıtımlar görünümü</span><span class="sxs-lookup"><span data-stu-id="05af0-151">The ServiceDeployments view</span></span>  

 <span data-ttu-id="05af0-152">Servicedağıtımlar görünümü aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="05af0-152">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="05af0-153">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="05af0-153">**SiteName**</span></span>  
  
2. <span data-ttu-id="05af0-154">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="05af0-154">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="05af0-155">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="05af0-155">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="05af0-156">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="05af0-156">**ServiceName**</span></span>  
  
5. <span data-ttu-id="05af0-157">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="05af0-157">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="05af0-158">InstancePromotedProperties görünümü</span><span class="sxs-lookup"><span data-stu-id="05af0-158">The InstancePromotedProperties view</span></span>  

 <span data-ttu-id="05af0-159">InstancePromotedProperties görünümü aşağıdaki alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="05af0-159">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="05af0-160">Yükseltilen özelliklerle ilgili ayrıntılar için bkz. [depolama genişletilebilirliği](store-extensibility.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="05af0-160">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="05af0-161">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="05af0-161">**InstanceId**</span></span>  
  
2. <span data-ttu-id="05af0-162">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="05af0-162">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="05af0-163">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="05af0-163">**PromotionName**</span></span>  
  
4. <span data-ttu-id="05af0-164">**Değer #** ( **değer1** ile **Value64** arasında bir alan aralığı).</span><span class="sxs-lookup"><span data-stu-id="05af0-164">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
