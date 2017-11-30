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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5f9b4989de57204d9ec97d69475121c30ae82644
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="5c658-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="5c658-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="5c658-103">Boşta iş akışı örnekleri zaman kaldırıldı ve kalıcı denetimleri hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="5c658-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="5c658-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5c658-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5c658-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="5c658-105">\<behaviors></span></span>  
<span data-ttu-id="5c658-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5c658-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5c658-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5c658-107">\<behavior></span></span>  
<span data-ttu-id="5c658-108">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="5c658-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c658-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c658-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c658-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c658-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5c658-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c658-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c658-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c658-112">Attributes</span></span>  
  
|<span data-ttu-id="5c658-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5c658-113">Attribute</span></span>|<span data-ttu-id="5c658-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c658-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c658-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="5c658-115">timeToPersist</span></span>|<span data-ttu-id="5c658-116">Zaman yayılımı değeri iş akışı boş olur ve kalıcı saat arasındaki süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c658-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="5c658-117">TimeSpan.MaxValue varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="5c658-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="5c658-118">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="5c658-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="5c658-119">Bu öznitelik, bir iş akışı örneği daha agresif mümkün olduğunca uzun bir süre bellekte hala örneği tutarken kalıcı hale getirmek istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5c658-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="5c658-120">Bu öznitelik yalnızca değerini ise geçerlidir küçük **timeToUnload** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5c658-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="5c658-121">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="5c658-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="5c658-122">Bu öznitelik ile belirtilen değer önce aşılırsa, **timeToUnload** özniteliği Kalıcılık iş akışı kaldırılmadan önce tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c658-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="5c658-123">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5c658-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="5c658-124">Saklama katmanını geçici hatalar için herhangi bir yeniden deneme işlemekten sorumludur ve kurtarılabilir olmayan hataları üzerinde yalnızca özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5c658-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="5c658-125">Bu nedenle, Kalıcılık sırasında karşılaşılan özel durumlar olarak kabul edilir ve iş akışı örneği durduruldu.</span><span class="sxs-lookup"><span data-stu-id="5c658-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="5c658-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="5c658-126">timeToUnload</span></span>|<span data-ttu-id="5c658-127">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="5c658-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="5c658-128">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="5c658-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="5c658-129">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5c658-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="5c658-130">İş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır bu öznitelik ayarlanırsa iş akışı boş olur.</span><span class="sxs-lookup"><span data-stu-id="5c658-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="5c658-131">Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5c658-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="5c658-132">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="5c658-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c658-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c658-133">Child Elements</span></span>  
 <span data-ttu-id="5c658-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c658-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c658-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c658-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5c658-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c658-136">Element</span></span>|<span data-ttu-id="5c658-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c658-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c658-138">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5c658-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="5c658-139">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c658-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c658-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c658-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
