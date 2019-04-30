---
title: Sorgu Desteği
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641521"
---
# <a name="support-for-queries"></a><span data-ttu-id="fc7cc-102">Sorgu Desteği</span><span class="sxs-lookup"><span data-stu-id="fc7cc-102">Support for Queries</span></span>
<span data-ttu-id="fc7cc-103">SQL iş akışı örneği Store iyi bilinen özellikler kümesi deposuna kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="fc7cc-104">Kullanıcılar için sorgulayabilir örnekleri, bu özellikleri bağlı.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="fc7cc-105">Aşağıdaki liste, bazı iyi bilinen bu özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="fc7cc-105">The following list contains some of these well-known properties:</span></span>  
  
- <span data-ttu-id="fc7cc-106">**Site adı.**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-106">**Site Name.**</span></span> <span data-ttu-id="fc7cc-107">Hizmeti içeren Web sitesinin adı.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-107">Name of the Web site that contains the service.</span></span>  
  
- <span data-ttu-id="fc7cc-108">**Uygulama göreli yolu.**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-108">**Relative Application Path.**</span></span> <span data-ttu-id="fc7cc-109">Uygulamanın Web sitesini göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-109">Path of the application relative to the Web site.</span></span>  
  
- <span data-ttu-id="fc7cc-110">**Hizmet göreli yolu.**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-110">**Relative Service Path.**</span></span> <span data-ttu-id="fc7cc-111">Hizmet uygulaması göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-111">Path of the service relative to the application.</span></span>  
  
- <span data-ttu-id="fc7cc-112">**Hizmet adı.**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-112">**Service Name.**</span></span> <span data-ttu-id="fc7cc-113">Hizmetin adı.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-113">Name of the service.</span></span>  
  
- <span data-ttu-id="fc7cc-114">**Hizmet Namespace.**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-114">**Service Namespace.**</span></span> <span data-ttu-id="fc7cc-115">Hizmetin kullandığı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-115">Name of the namespace that the service uses.</span></span>  
  
- <span data-ttu-id="fc7cc-116">**Geçerli makine.**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-116">**Current Machine.**</span></span>  
  
- <span data-ttu-id="fc7cc-117">**Son makine**.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-117">**Last Machine**.</span></span> <span data-ttu-id="fc7cc-118">İş akışı hizmet örneği son kez çalıştırıldığı bir bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc7cc-119">İş akışı hizmeti konağı kullanarak şirket içinde barındırılan senaryoları için yalnızca son dört özellikleri doldurulur.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="fc7cc-120">İş akışı uygulama senaryoları için yalnızca en son özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="fc7cc-121">İş akışı çalışma zamanı ilk üç özellikleri için değer sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="fc7cc-122">İş akışı hizmeti konağı için değer sağlayan **askıya alma nedeni** özelliği.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="fc7cc-123">SQL iş akışı örneği Store kendisi için değer sağlıyor **son güncelleştirilen makine** özelliği.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="fc7cc-124">SQL iş akışı örneği Store özellik de Kalıcılık veritabanı ve belirttiğiniz değerleri depolamak kullanmak istediğiniz özel özellikler sorgularda kullanmak istediğinizi belirtmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="fc7cc-125">Özel promosyonlar hakkında daha fazla bilgi için bkz: [Store genişletilebilirlik](store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="fc7cc-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="fc7cc-126">Görünümler</span><span class="sxs-lookup"><span data-stu-id="fc7cc-126">Views</span></span>  
 <span data-ttu-id="fc7cc-127">Örnek depo, aşağıdaki görünümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-127">The instance store contains the following views.</span></span> <span data-ttu-id="fc7cc-128">Bkz: [Kalıcılık veritabanı şeması](persistence-database-schema.md) daha ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="fc7cc-129">Örnekleri görüntüle</span><span class="sxs-lookup"><span data-stu-id="fc7cc-129">The Instances View</span></span>  
 <span data-ttu-id="fc7cc-130">Örnekler görünümü, aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="fc7cc-130">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="fc7cc-131">**Kimlik**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-131">**Id**</span></span>  
  
2. <span data-ttu-id="fc7cc-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-132">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="fc7cc-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-133">**CreationTime**</span></span>  
  
4. <span data-ttu-id="fc7cc-134">**lastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-134">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="fc7cc-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-135">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="fc7cc-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-136">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="fc7cc-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-137">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="fc7cc-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="fc7cc-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="fc7cc-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="fc7cc-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="fc7cc-142">**Isınitialized**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="fc7cc-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="fc7cc-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="fc7cc-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="fc7cc-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="fc7cc-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="fc7cc-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="fc7cc-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="fc7cc-150">ServiceDeployments görüntüle</span><span class="sxs-lookup"><span data-stu-id="fc7cc-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="fc7cc-151">ServiceDeployments görünümü, aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="fc7cc-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="fc7cc-152">**Site adı**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-152">**SiteName**</span></span>  
  
2. <span data-ttu-id="fc7cc-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-153">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="fc7cc-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-154">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="fc7cc-155">**serviceName**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-155">**ServiceName**</span></span>  
  
5. <span data-ttu-id="fc7cc-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="fc7cc-157">InstancePromotedProperties görüntüle</span><span class="sxs-lookup"><span data-stu-id="fc7cc-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="fc7cc-158">InstancePromotedProperties görünümü, aşağıdaki alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="fc7cc-159">Yükseltilen özellikleri hakkında ayrıntılı bilgi için bkz. [Store genişletilebilirlik](store-extensibility.md) konu.</span><span class="sxs-lookup"><span data-stu-id="fc7cc-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="fc7cc-160">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-160">**InstanceId**</span></span>  
  
2. <span data-ttu-id="fc7cc-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-161">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="fc7cc-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="fc7cc-162">**PromotionName**</span></span>  
  
4. <span data-ttu-id="fc7cc-163">**Değer #** (alanlardan bir dizi **Value1** için **Value64**).</span><span class="sxs-lookup"><span data-stu-id="fc7cc-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
