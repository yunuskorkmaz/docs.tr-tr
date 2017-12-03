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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bed850baca2d06dc0de173ab798da29fb3ec7cc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="support-for-queries"></a><span data-ttu-id="ca64b-102">Sorgular için destek</span><span class="sxs-lookup"><span data-stu-id="ca64b-102">Support for Queries</span></span>
<span data-ttu-id="ca64b-103">SQL iş akışı örneği deposuna iyi bilinen bir özellik kümesi depolama alanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ca64b-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="ca64b-104">Kullanıcılar için Sorgulayabileceğiniz çıkarak bu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ca64b-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="ca64b-105">Aşağıdaki listede bu iyi bilinen özelliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="ca64b-105">The following list contains some of these well-known properties:</span></span>  
  
-   <span data-ttu-id="ca64b-106">**Site adı.**</span><span class="sxs-lookup"><span data-stu-id="ca64b-106">**Site Name.**</span></span> <span data-ttu-id="ca64b-107">Hizmet içeren Web sitesi adı.</span><span class="sxs-lookup"><span data-stu-id="ca64b-107">Name of the Web site that contains the service.</span></span>  
  
-   <span data-ttu-id="ca64b-108">**Göreli uygulama yolu.**</span><span class="sxs-lookup"><span data-stu-id="ca64b-108">**Relative Application Path.**</span></span> <span data-ttu-id="ca64b-109">Web sitesi göre uygulamanın yolu.</span><span class="sxs-lookup"><span data-stu-id="ca64b-109">Path of the application relative to the Web site.</span></span>  
  
-   <span data-ttu-id="ca64b-110">**Göreli hizmet yolu.**</span><span class="sxs-lookup"><span data-stu-id="ca64b-110">**Relative Service Path.**</span></span> <span data-ttu-id="ca64b-111">Hizmet uygulaması göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="ca64b-111">Path of the service relative to the application.</span></span>  
  
-   <span data-ttu-id="ca64b-112">**Hizmet adı.**</span><span class="sxs-lookup"><span data-stu-id="ca64b-112">**Service Name.**</span></span> <span data-ttu-id="ca64b-113">Hizmetin adı.</span><span class="sxs-lookup"><span data-stu-id="ca64b-113">Name of the service.</span></span>  
  
-   <span data-ttu-id="ca64b-114">**Hizmet Namespace.**</span><span class="sxs-lookup"><span data-stu-id="ca64b-114">**Service Namespace.**</span></span> <span data-ttu-id="ca64b-115">Hizmetin kullandığı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="ca64b-115">Name of the namespace that the service uses.</span></span>  
  
-   <span data-ttu-id="ca64b-116">**Geçerli makineye.**</span><span class="sxs-lookup"><span data-stu-id="ca64b-116">**Current Machine.**</span></span>  
  
-   <span data-ttu-id="ca64b-117">**Son makine**.</span><span class="sxs-lookup"><span data-stu-id="ca64b-117">**Last Machine**.</span></span> <span data-ttu-id="ca64b-118">İş akışı hizmeti örneği en son ne zaman çalıştırıldığı bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="ca64b-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca64b-119">İş akışı hizmeti ana bilgisayarı kullanarak kendini barındıran senaryolar için yalnızca son dört özellikleri doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ca64b-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="ca64b-120">İş akışı uygulama senaryoları için yalnızca en son özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ca64b-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="ca64b-121">İş akışı çalışma zamanı ilk üç özellikleri için değer sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="ca64b-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="ca64b-122">İş akışı hizmeti ana bilgisayarı için değer sağlıyor **askıya neden** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca64b-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="ca64b-123">SQL iş akışı örneği deposuna kendisi için değer sağlıyor **son güncelleştirilen makine** özelliği.</span><span class="sxs-lookup"><span data-stu-id="ca64b-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="ca64b-124">SQL iş akışı örneği depolama özelliğini de Kalıcılık veritabanı ve belirttiğiniz değerleri depolamak istediğiniz özel özellikler sorgularda kullanmak istediğiniz belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca64b-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="ca64b-125">Özel promosyonlar hakkında daha fazla bilgi için bkz: [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="ca64b-125">For more information about custom promotions, see [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="ca64b-126">Görünümler</span><span class="sxs-lookup"><span data-stu-id="ca64b-126">Views</span></span>  
 <span data-ttu-id="ca64b-127">Örnek deposuna aşağıdaki görünümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ca64b-127">The instance store contains the following views.</span></span> <span data-ttu-id="ca64b-128">Bkz: [Kalıcılık veritabanı şeması](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) daha ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="ca64b-128">See [Persistence Database Schema](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="ca64b-129">Örnek görünümü</span><span class="sxs-lookup"><span data-stu-id="ca64b-129">The Instances View</span></span>  
 <span data-ttu-id="ca64b-130">Örnekleri görünüm aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="ca64b-130">The Instances view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="ca64b-131">**Kimliği**</span><span class="sxs-lookup"><span data-stu-id="ca64b-131">**Id**</span></span>  
  
2.  <span data-ttu-id="ca64b-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="ca64b-132">**PendingTimer**</span></span>  
  
3.  <span data-ttu-id="ca64b-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="ca64b-133">**CreationTime**</span></span>  
  
4.  <span data-ttu-id="ca64b-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="ca64b-134">**LastUpdatedTime**</span></span>  
  
5.  <span data-ttu-id="ca64b-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="ca64b-135">**ServiceDeploymentId**</span></span>  
  
6.  <span data-ttu-id="ca64b-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="ca64b-136">**SuspensionExceptionName**</span></span>  
  
7.  <span data-ttu-id="ca64b-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="ca64b-137">**SuspensionReason**</span></span>  
  
8.  <span data-ttu-id="ca64b-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="ca64b-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="ca64b-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="ca64b-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="ca64b-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="ca64b-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="ca64b-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="ca64b-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="ca64b-142">**Isınitialized**</span><span class="sxs-lookup"><span data-stu-id="ca64b-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="ca64b-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="ca64b-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="ca64b-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="ca64b-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="ca64b-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="ca64b-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="ca64b-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="ca64b-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="ca64b-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="ca64b-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="ca64b-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="ca64b-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="ca64b-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="ca64b-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="ca64b-150">ServiceDeployments görünümü</span><span class="sxs-lookup"><span data-stu-id="ca64b-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="ca64b-151">ServiceDeployments görünüm aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="ca64b-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="ca64b-152">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="ca64b-152">**SiteName**</span></span>  
  
2.  <span data-ttu-id="ca64b-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="ca64b-153">**RelativeServicePath**</span></span>  
  
3.  <span data-ttu-id="ca64b-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="ca64b-154">**RelativeApplicationPath**</span></span>  
  
4.  <span data-ttu-id="ca64b-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="ca64b-155">**ServiceName**</span></span>  
  
5.  <span data-ttu-id="ca64b-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="ca64b-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="ca64b-157">InstancePromotedProperties görünümü</span><span class="sxs-lookup"><span data-stu-id="ca64b-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="ca64b-158">InstancePromotedProperties görünüm aşağıdaki alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="ca64b-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="ca64b-159">Yükseltilen özellikleri hakkında daha fazla bilgi için bkz: [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ca64b-159">For details on promoted properties, see the [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) topic.</span></span>  
  
1.  <span data-ttu-id="ca64b-160">**Örnek kimliği**</span><span class="sxs-lookup"><span data-stu-id="ca64b-160">**InstanceId**</span></span>  
  
2.  <span data-ttu-id="ca64b-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="ca64b-161">**EncodingOption**</span></span>  
  
3.  <span data-ttu-id="ca64b-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="ca64b-162">**PromotionName**</span></span>  
  
4.  <span data-ttu-id="ca64b-163">**Değer #** (alanlardan çeşitli **Value1** için **Value64**).</span><span class="sxs-lookup"><span data-stu-id="ca64b-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
