---
title: "Sorgular için destek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4f338f9ae5cc6967885d0518eb573d9f9535fc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="support-for-queries"></a><span data-ttu-id="d2be2-102">Sorgular için destek</span><span class="sxs-lookup"><span data-stu-id="d2be2-102">Support for Queries</span></span>
<span data-ttu-id="d2be2-103">SQL iş akışı örneği deposuna iyi bilinen bir özellik kümesi depolama alanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d2be2-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="d2be2-104">Kullanıcılar için Sorgulayabileceğiniz çıkarak bu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="d2be2-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="d2be2-105">Aşağıdaki listede bu iyi bilinen özelliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="d2be2-105">The following list contains some of these well-known properties:</span></span>  
  
-   <span data-ttu-id="d2be2-106">**Site adı.**</span><span class="sxs-lookup"><span data-stu-id="d2be2-106">**Site Name.**</span></span> <span data-ttu-id="d2be2-107">Hizmet içeren Web sitesi adı.</span><span class="sxs-lookup"><span data-stu-id="d2be2-107">Name of the Web site that contains the service.</span></span>  
  
-   <span data-ttu-id="d2be2-108">**Göreli uygulama yolu.**</span><span class="sxs-lookup"><span data-stu-id="d2be2-108">**Relative Application Path.**</span></span> <span data-ttu-id="d2be2-109">Web sitesi göre uygulamanın yolu.</span><span class="sxs-lookup"><span data-stu-id="d2be2-109">Path of the application relative to the Web site.</span></span>  
  
-   <span data-ttu-id="d2be2-110">**Göreli hizmet yolu.**</span><span class="sxs-lookup"><span data-stu-id="d2be2-110">**Relative Service Path.**</span></span> <span data-ttu-id="d2be2-111">Hizmet uygulaması göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="d2be2-111">Path of the service relative to the application.</span></span>  
  
-   <span data-ttu-id="d2be2-112">**Hizmet adı.**</span><span class="sxs-lookup"><span data-stu-id="d2be2-112">**Service Name.**</span></span> <span data-ttu-id="d2be2-113">Hizmetin adı.</span><span class="sxs-lookup"><span data-stu-id="d2be2-113">Name of the service.</span></span>  
  
-   <span data-ttu-id="d2be2-114">**Hizmet Namespace.**</span><span class="sxs-lookup"><span data-stu-id="d2be2-114">**Service Namespace.**</span></span> <span data-ttu-id="d2be2-115">Hizmetin kullandığı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="d2be2-115">Name of the namespace that the service uses.</span></span>  
  
-   <span data-ttu-id="d2be2-116">**Geçerli makineye.**</span><span class="sxs-lookup"><span data-stu-id="d2be2-116">**Current Machine.**</span></span>  
  
-   <span data-ttu-id="d2be2-117">**Son makine**.</span><span class="sxs-lookup"><span data-stu-id="d2be2-117">**Last Machine**.</span></span> <span data-ttu-id="d2be2-118">İş akışı hizmeti örneği en son ne zaman çalıştırıldığı bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="d2be2-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2be2-119">İş akışı hizmeti ana bilgisayarı kullanarak kendini barındıran senaryolar için yalnızca son dört özellikleri doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d2be2-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="d2be2-120">İş akışı uygulama senaryoları için yalnızca en son özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="d2be2-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="d2be2-121">İş akışı çalışma zamanı ilk üç özellikleri için değer sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="d2be2-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="d2be2-122">İş akışı hizmeti ana bilgisayarı için değer sağlıyor **askıya neden** özelliği.</span><span class="sxs-lookup"><span data-stu-id="d2be2-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="d2be2-123">SQL iş akışı örneği deposuna kendisi için değer sağlıyor **son güncelleştirilen makine** özelliği.</span><span class="sxs-lookup"><span data-stu-id="d2be2-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="d2be2-124">SQL iş akışı örneği depolama özelliğini de Kalıcılık veritabanı ve belirttiğiniz değerleri depolamak istediğiniz özel özellikler sorgularda kullanmak istediğiniz belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2be2-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="d2be2-125">Özel promosyonlar hakkında daha fazla bilgi için bkz: [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="d2be2-125">For more information about custom promotions, see [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="d2be2-126">Görünümler</span><span class="sxs-lookup"><span data-stu-id="d2be2-126">Views</span></span>  
 <span data-ttu-id="d2be2-127">Örnek deposuna aşağıdaki görünümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d2be2-127">The instance store contains the following views.</span></span> <span data-ttu-id="d2be2-128">Bkz: [Kalıcılık veritabanı şeması](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) daha ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d2be2-128">See [Persistence Database Schema](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="d2be2-129">Örnek görünümü</span><span class="sxs-lookup"><span data-stu-id="d2be2-129">The Instances View</span></span>  
 <span data-ttu-id="d2be2-130">Örnekleri görünüm aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="d2be2-130">The Instances view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="d2be2-131">**Kimliği**</span><span class="sxs-lookup"><span data-stu-id="d2be2-131">**Id**</span></span>  
  
2.  <span data-ttu-id="d2be2-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="d2be2-132">**PendingTimer**</span></span>  
  
3.  <span data-ttu-id="d2be2-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="d2be2-133">**CreationTime**</span></span>  
  
4.  <span data-ttu-id="d2be2-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="d2be2-134">**LastUpdatedTime**</span></span>  
  
5.  <span data-ttu-id="d2be2-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="d2be2-135">**ServiceDeploymentId**</span></span>  
  
6.  <span data-ttu-id="d2be2-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="d2be2-136">**SuspensionExceptionName**</span></span>  
  
7.  <span data-ttu-id="d2be2-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="d2be2-137">**SuspensionReason**</span></span>  
  
8.  <span data-ttu-id="d2be2-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="d2be2-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="d2be2-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="d2be2-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="d2be2-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="d2be2-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="d2be2-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="d2be2-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="d2be2-142">**Isınitialized**</span><span class="sxs-lookup"><span data-stu-id="d2be2-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="d2be2-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="d2be2-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="d2be2-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="d2be2-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="d2be2-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="d2be2-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="d2be2-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d2be2-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="d2be2-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d2be2-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="d2be2-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d2be2-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="d2be2-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="d2be2-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="d2be2-150">ServiceDeployments görünümü</span><span class="sxs-lookup"><span data-stu-id="d2be2-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="d2be2-151">ServiceDeployments görünüm aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="d2be2-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="d2be2-152">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="d2be2-152">**SiteName**</span></span>  
  
2.  <span data-ttu-id="d2be2-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="d2be2-153">**RelativeServicePath**</span></span>  
  
3.  <span data-ttu-id="d2be2-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="d2be2-154">**RelativeApplicationPath**</span></span>  
  
4.  <span data-ttu-id="d2be2-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="d2be2-155">**ServiceName**</span></span>  
  
5.  <span data-ttu-id="d2be2-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="d2be2-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="d2be2-157">InstancePromotedProperties görünümü</span><span class="sxs-lookup"><span data-stu-id="d2be2-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="d2be2-158">InstancePromotedProperties görünüm aşağıdaki alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="d2be2-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="d2be2-159">Yükseltilen özellikleri hakkında daha fazla bilgi için bkz: [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d2be2-159">For details on promoted properties, see the [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) topic.</span></span>  
  
1.  <span data-ttu-id="d2be2-160">**Örnek kimliği**</span><span class="sxs-lookup"><span data-stu-id="d2be2-160">**InstanceId**</span></span>  
  
2.  <span data-ttu-id="d2be2-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="d2be2-161">**EncodingOption**</span></span>  
  
3.  <span data-ttu-id="d2be2-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="d2be2-162">**PromotionName**</span></span>  
  
4.  <span data-ttu-id="d2be2-163">**Değer #** (alanlardan çeşitli **Value1** için **Value64**).</span><span class="sxs-lookup"><span data-stu-id="d2be2-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
