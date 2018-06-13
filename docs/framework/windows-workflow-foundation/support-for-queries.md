---
title: Sorgular için destek
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 5c46ed5ae2fc2cc2275bfa7251fe5f8fa346c1f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517997"
---
# <a name="support-for-queries"></a><span data-ttu-id="6be66-102">Sorgular için destek</span><span class="sxs-lookup"><span data-stu-id="6be66-102">Support for Queries</span></span>
<span data-ttu-id="6be66-103">SQL iş akışı örneği deposuna iyi bilinen bir özellik kümesi depolama alanına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6be66-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="6be66-104">Kullanıcılar için Sorgulayabileceğiniz çıkarak bu özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6be66-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="6be66-105">Aşağıdaki listede bu iyi bilinen özelliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="6be66-105">The following list contains some of these well-known properties:</span></span>  
  
-   <span data-ttu-id="6be66-106">**Site adı.**</span><span class="sxs-lookup"><span data-stu-id="6be66-106">**Site Name.**</span></span> <span data-ttu-id="6be66-107">Hizmet içeren Web sitesi adı.</span><span class="sxs-lookup"><span data-stu-id="6be66-107">Name of the Web site that contains the service.</span></span>  
  
-   <span data-ttu-id="6be66-108">**Göreli uygulama yolu.**</span><span class="sxs-lookup"><span data-stu-id="6be66-108">**Relative Application Path.**</span></span> <span data-ttu-id="6be66-109">Web sitesi göre uygulamanın yolu.</span><span class="sxs-lookup"><span data-stu-id="6be66-109">Path of the application relative to the Web site.</span></span>  
  
-   <span data-ttu-id="6be66-110">**Göreli hizmet yolu.**</span><span class="sxs-lookup"><span data-stu-id="6be66-110">**Relative Service Path.**</span></span> <span data-ttu-id="6be66-111">Hizmet uygulaması göreli yolu.</span><span class="sxs-lookup"><span data-stu-id="6be66-111">Path of the service relative to the application.</span></span>  
  
-   <span data-ttu-id="6be66-112">**Hizmet adı.**</span><span class="sxs-lookup"><span data-stu-id="6be66-112">**Service Name.**</span></span> <span data-ttu-id="6be66-113">Hizmetin adı.</span><span class="sxs-lookup"><span data-stu-id="6be66-113">Name of the service.</span></span>  
  
-   <span data-ttu-id="6be66-114">**Hizmet Namespace.**</span><span class="sxs-lookup"><span data-stu-id="6be66-114">**Service Namespace.**</span></span> <span data-ttu-id="6be66-115">Hizmetin kullandığı ad alanının adı.</span><span class="sxs-lookup"><span data-stu-id="6be66-115">Name of the namespace that the service uses.</span></span>  
  
-   <span data-ttu-id="6be66-116">**Geçerli makineye.**</span><span class="sxs-lookup"><span data-stu-id="6be66-116">**Current Machine.**</span></span>  
  
-   <span data-ttu-id="6be66-117">**Son makine**.</span><span class="sxs-lookup"><span data-stu-id="6be66-117">**Last Machine**.</span></span> <span data-ttu-id="6be66-118">İş akışı hizmeti örneği en son ne zaman çalıştırıldığı bilgisayar.</span><span class="sxs-lookup"><span data-stu-id="6be66-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6be66-119">İş akışı hizmeti ana bilgisayarı kullanarak kendini barındıran senaryolar için yalnızca son dört özellikleri doldurulur.</span><span class="sxs-lookup"><span data-stu-id="6be66-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="6be66-120">İş akışı uygulama senaryoları için yalnızca en son özellik doldurulur.</span><span class="sxs-lookup"><span data-stu-id="6be66-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="6be66-121">İş akışı çalışma zamanı ilk üç özellikleri için değer sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="6be66-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="6be66-122">İş akışı hizmeti ana bilgisayarı için değer sağlıyor **askıya neden** özelliği.</span><span class="sxs-lookup"><span data-stu-id="6be66-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="6be66-123">SQL iş akışı örneği deposuna kendisi için değer sağlıyor **son güncelleştirilen makine** özelliği.</span><span class="sxs-lookup"><span data-stu-id="6be66-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="6be66-124">SQL iş akışı örneği depolama özelliğini de Kalıcılık veritabanı ve belirttiğiniz değerleri depolamak istediğiniz özel özellikler sorgularda kullanmak istediğiniz belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6be66-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="6be66-125">Özel promosyonlar hakkında daha fazla bilgi için bkz: [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="6be66-125">For more information about custom promotions, see [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="6be66-126">Görünümler</span><span class="sxs-lookup"><span data-stu-id="6be66-126">Views</span></span>  
 <span data-ttu-id="6be66-127">Örnek deposuna aşağıdaki görünümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6be66-127">The instance store contains the following views.</span></span> <span data-ttu-id="6be66-128">Bkz: [Kalıcılık veritabanı şeması](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) daha ayrıntılı bilgi için.</span><span class="sxs-lookup"><span data-stu-id="6be66-128">See [Persistence Database Schema](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="6be66-129">Örnek görünümü</span><span class="sxs-lookup"><span data-stu-id="6be66-129">The Instances View</span></span>  
 <span data-ttu-id="6be66-130">Örnekleri görünüm aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="6be66-130">The Instances view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="6be66-131">**Kimliği**</span><span class="sxs-lookup"><span data-stu-id="6be66-131">**Id**</span></span>  
  
2.  <span data-ttu-id="6be66-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="6be66-132">**PendingTimer**</span></span>  
  
3.  <span data-ttu-id="6be66-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="6be66-133">**CreationTime**</span></span>  
  
4.  <span data-ttu-id="6be66-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="6be66-134">**LastUpdatedTime**</span></span>  
  
5.  <span data-ttu-id="6be66-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="6be66-135">**ServiceDeploymentId**</span></span>  
  
6.  <span data-ttu-id="6be66-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="6be66-136">**SuspensionExceptionName**</span></span>  
  
7.  <span data-ttu-id="6be66-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="6be66-137">**SuspensionReason**</span></span>  
  
8.  <span data-ttu-id="6be66-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="6be66-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="6be66-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="6be66-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="6be66-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="6be66-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="6be66-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="6be66-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="6be66-142">**Isınitialized**</span><span class="sxs-lookup"><span data-stu-id="6be66-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="6be66-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="6be66-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="6be66-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="6be66-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="6be66-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="6be66-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="6be66-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="6be66-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="6be66-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="6be66-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="6be66-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="6be66-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="6be66-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="6be66-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="6be66-150">ServiceDeployments görünümü</span><span class="sxs-lookup"><span data-stu-id="6be66-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="6be66-151">ServiceDeployments görünüm aşağıdaki alanları içerir:</span><span class="sxs-lookup"><span data-stu-id="6be66-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1.  <span data-ttu-id="6be66-152">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="6be66-152">**SiteName**</span></span>  
  
2.  <span data-ttu-id="6be66-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="6be66-153">**RelativeServicePath**</span></span>  
  
3.  <span data-ttu-id="6be66-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="6be66-154">**RelativeApplicationPath**</span></span>  
  
4.  <span data-ttu-id="6be66-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="6be66-155">**ServiceName**</span></span>  
  
5.  <span data-ttu-id="6be66-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="6be66-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="6be66-157">InstancePromotedProperties görünümü</span><span class="sxs-lookup"><span data-stu-id="6be66-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="6be66-158">InstancePromotedProperties görünüm aşağıdaki alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="6be66-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="6be66-159">Yükseltilen özellikleri hakkında daha fazla bilgi için bkz: [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) konu.</span><span class="sxs-lookup"><span data-stu-id="6be66-159">For details on promoted properties, see the [Store Extensibility](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) topic.</span></span>  
  
1.  <span data-ttu-id="6be66-160">**örnek kimliği**</span><span class="sxs-lookup"><span data-stu-id="6be66-160">**InstanceId**</span></span>  
  
2.  <span data-ttu-id="6be66-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="6be66-161">**EncodingOption**</span></span>  
  
3.  <span data-ttu-id="6be66-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="6be66-162">**PromotionName**</span></span>  
  
4.  <span data-ttu-id="6be66-163">**Değer #** (alanlardan çeşitli **Value1** için **Value64**).</span><span class="sxs-lookup"><span data-stu-id="6be66-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
