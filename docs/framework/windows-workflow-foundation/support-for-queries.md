---
title: Sorgu Desteği
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307957"
---
# <a name="support-for-queries"></a><span data-ttu-id="d22d4-102">Sorgu Desteği</span><span class="sxs-lookup"><span data-stu-id="d22d4-102">Support for Queries</span></span>
<span data-ttu-id="d22d4-103">SQL iş akışı örneği Store iyi bilinen özellikler kümesi deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d22d4-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="d22d4-104">Kullanıcılar için sorgulayabilir örnekleri, bu özellikleri bağlı.</span><span class="sxs-lookup"><span data-stu-id="d22d4-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="d22d4-105">Aşağıdaki liste, bazı iyi bilinen bu özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d22d4-105">The following list contains some of these well-known properties:</span></span>  
  
-   <span data-ttu-id="d22d4-106">**Site adı.**</span><span class="sxs-lookup"><span data-stu-id="d22d4-106">**Site Name.**</span></span> <span data-ttu-id="d22d4-107">Hizmeti içeren Web sitesinin adı.</span><span class="sxs-lookup"><span data-stu-id="d22d4-107">Name of the Web site that contains the service.</span></span>  
  
-   <span data-ttu-id="d22d4-108">**Uygulama göreli yolu.**</span><span class="sxs-lookup"><span data-stu-id="d22d4-108">**Relative Application Path.**</span></span> <span data-ttu-id="d22d4-109">Uygulamanın Web sitesini göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="d22d4-109">Path of the application relative to the Web site.</span></span>  
  
-   <span data-ttu-id="d22d4-110">**Hizmet göreli yolu.**</span><span class="sxs-lookup"><span data-stu-id="d22d4-110">**Relative Service Path.**</span></span> <span data-ttu-id="d22d4-111">Hizmet uygulaması göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="d22d4-111">Path of the service relative to the application.</span></span>  
  
-   <span data-ttu-id="d22d4-112">**Hizmet adı.**</span><span class="sxs-lookup"><span data-stu-id="d22d4-112">**Service Name.**</span></span> <span data-ttu-id="d22d4-113">Hizmetin adı.</span><span class="sxs-lookup"><span data-stu-id="d22d4-113">Name of the service.</span></span>  
  
-   <span data-ttu-id="d22d4-114">**Hizmet Namespace.**</span><span class="sxs-lookup"><span data-stu-id="d22d4-114">**Service Namespace.**</span></span> <span data-ttu-id="d22d4-115">Hizmetin kullandığı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="d22d4-115">Name of the namespace that the service uses.</span></span>  
  
-   <span data-ttu-id="d22d4-116">**Geçerli makine.**</span><span class="sxs-lookup"><span data-stu-id="d22d4-116">**Current Machine.**</span></span>  
  
-   <span data-ttu-id="d22d4-117">**Son makine**.</span><span class="sxs-lookup"><span data-stu-id="d22d4-117">**Last Machine**.</span></span> <span data-ttu-id="d22d4-118">İş akışı hizmet örneği son kez çalıştırıldığı bir bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="d22d4-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d22d4-119">İş akışı hizmeti konağı kullanarak şirket içinde barındırılan senaryoları için yalnızca son dört özellikleri doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d22d4-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="d22d4-120">İş akışı uygulama senaryoları için yalnızca en son özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d22d4-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="d22d4-121">İş akışı çalışma zamanı ilk üç özellikleri için değer sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="d22d4-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="d22d4-122">İş akışı hizmeti konağı için değer sağlayan **askıya alma nedeni** özelliği.</span><span class="sxs-lookup"><span data-stu-id="d22d4-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="d22d4-123">SQL iş akışı örneği Store kendisi için değer sağlıyor **son güncelleştirilen makine** özelliği.</span><span class="sxs-lookup"><span data-stu-id="d22d4-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="d22d4-124">SQL iş akışı örneği Store özellik de Kalıcılık veritabanı ve belirttiğiniz değerleri depolamak kullanmak istediğiniz özel özellikler sorgularda kullanmak istediğinizi belirtmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d22d4-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="d22d4-125">Özel promosyonlar hakkında daha fazla bilgi için bkz: [Store genişletilebilirlik](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="d22d4-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="d22d4-126">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d22d4-126">Views</span></span>  
 <span data-ttu-id="d22d4-127">Örnek depo, aşağıdaki görünümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d22d4-127">The instance store contains the following views.</span></span> <span data-ttu-id="d22d4-128">Bkz: [Kalıcılık veritabanı şeması](persistence-database-schema.md) daha ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d22d4-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="d22d4-129">Örnekleri görüntüle</span><span class="sxs-lookup"><span data-stu-id="d22d4-129">The Instances View</span></span>  
 <span data-ttu-id="d22d4-130">Örnekler görünümü, aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="d22d4-130">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="d22d4-131">**Kimlik**</span><span class="sxs-lookup"><span data-stu-id="d22d4-131">**Id**</span></span>  
  
2. <span data-ttu-id="d22d4-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="d22d4-132">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="d22d4-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="d22d4-133">**CreationTime**</span></span>  
  
4. <span data-ttu-id="d22d4-134">**lastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="d22d4-134">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="d22d4-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="d22d4-135">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="d22d4-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="d22d4-136">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="d22d4-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="d22d4-137">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="d22d4-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="d22d4-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="d22d4-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="d22d4-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="d22d4-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="d22d4-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="d22d4-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="d22d4-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="d22d4-142">**Isınitialized**</span><span class="sxs-lookup"><span data-stu-id="d22d4-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="d22d4-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="d22d4-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="d22d4-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="d22d4-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="d22d4-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="d22d4-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="d22d4-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d22d4-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="d22d4-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d22d4-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="d22d4-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d22d4-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="d22d4-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d22d4-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="d22d4-150">ServiceDeployments görüntüle</span><span class="sxs-lookup"><span data-stu-id="d22d4-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="d22d4-151">ServiceDeployments görünümü, aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="d22d4-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="d22d4-152">**Site adı**</span><span class="sxs-lookup"><span data-stu-id="d22d4-152">**SiteName**</span></span>  
  
2. <span data-ttu-id="d22d4-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="d22d4-153">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="d22d4-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="d22d4-154">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="d22d4-155">**serviceName**</span><span class="sxs-lookup"><span data-stu-id="d22d4-155">**ServiceName**</span></span>  
  
5. <span data-ttu-id="d22d4-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="d22d4-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="d22d4-157">InstancePromotedProperties görüntüle</span><span class="sxs-lookup"><span data-stu-id="d22d4-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="d22d4-158">InstancePromotedProperties görünümü, aşağıdaki alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="d22d4-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="d22d4-159">Yükseltilen özellikleri hakkında ayrıntılı bilgi için bkz. [Store genişletilebilirlik](store-extensibility.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d22d4-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="d22d4-160">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="d22d4-160">**InstanceId**</span></span>  
  
2. <span data-ttu-id="d22d4-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="d22d4-161">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="d22d4-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="d22d4-162">**PromotionName**</span></span>  
  
4. <span data-ttu-id="d22d4-163">**Değer #** (alanlardan bir dizi **Value1** için **Value64**).</span><span class="sxs-lookup"><span data-stu-id="d22d4-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
