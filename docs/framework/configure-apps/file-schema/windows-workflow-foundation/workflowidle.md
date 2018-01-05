---
title: '&lt;workflowIdle&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2440f322ea7dbd3a6d6f9d56878273c49b26bfa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="505d8-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="505d8-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="505d8-103">Boşta iş akışı örnekleri zaman kaldırıldı ve kalıcı denetimleri hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="505d8-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="505d8-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="505d8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="505d8-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="505d8-105">\<behaviors></span></span>  
<span data-ttu-id="505d8-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="505d8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="505d8-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="505d8-107">\<behavior></span></span>  
<span data-ttu-id="505d8-108">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="505d8-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="505d8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="505d8-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="505d8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="505d8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="505d8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="505d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="505d8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="505d8-112">Attributes</span></span>  
  
|<span data-ttu-id="505d8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="505d8-113">Attribute</span></span>|<span data-ttu-id="505d8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="505d8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="505d8-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="505d8-115">timeToPersist</span></span>|<span data-ttu-id="505d8-116">Zaman yayılımı değeri iş akışı boş olur ve kalıcı saat arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="505d8-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="505d8-117">TimeSpan.MaxValue varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="505d8-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="505d8-118">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="505d8-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="505d8-119">Bu öznitelik, bir iş akışı örneği daha agresif mümkün olduğunca uzun bir süre bellekte hala örneği tutarken kalıcı hale getirmek istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="505d8-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="505d8-120">Bu öznitelik yalnızca değerini ise geçerlidir küçük **timeToUnload** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="505d8-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="505d8-121">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="505d8-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="505d8-122">Bu öznitelik ile belirtilen değer önce aşılırsa, **timeToUnload** özniteliği Kalıcılık iş akışı kaldırılmadan önce tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="505d8-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="505d8-123">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="505d8-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="505d8-124">Saklama katmanını geçici hatalar için herhangi bir yeniden deneme işlemekten sorumludur ve kurtarılabilir olmayan hataları üzerinde yalnızca özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="505d8-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="505d8-125">Bu nedenle, Kalıcılık sırasında karşılaşılan özel durumlar olarak kabul edilir ve iş akışı örneği durduruldu.</span><span class="sxs-lookup"><span data-stu-id="505d8-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="505d8-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="505d8-126">timeToUnload</span></span>|<span data-ttu-id="505d8-127">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="505d8-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="505d8-128">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="505d8-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="505d8-129">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="505d8-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="505d8-130">İş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır bu öznitelik ayarlanırsa iş akışı boş olur.</span><span class="sxs-lookup"><span data-stu-id="505d8-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="505d8-131">Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="505d8-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="505d8-132">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="505d8-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="505d8-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="505d8-133">Child Elements</span></span>  
 <span data-ttu-id="505d8-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="505d8-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="505d8-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="505d8-135">Parent Elements</span></span>  
  
|<span data-ttu-id="505d8-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="505d8-136">Element</span></span>|<span data-ttu-id="505d8-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="505d8-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="505d8-138">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="505d8-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="505d8-139">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="505d8-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="505d8-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="505d8-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
