---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 16a485b6d0ba2584cccd08a36506582fd3930f71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947173"
---
# <a name="workflowidle"></a><span data-ttu-id="c59a4-101">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="c59a4-101">\<workflowIdle></span></span>
<span data-ttu-id="c59a4-102">Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="c59a4-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="c59a4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c59a4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c59a4-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c59a4-104">\<behaviors></span></span>  
<span data-ttu-id="c59a4-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c59a4-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c59a4-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c59a4-106">\<behavior></span></span>  
<span data-ttu-id="c59a4-107">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="c59a4-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c59a4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c59a4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c59a4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c59a4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c59a4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c59a4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c59a4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c59a4-111">Attributes</span></span>  
  
|<span data-ttu-id="c59a4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c59a4-112">Attribute</span></span>|<span data-ttu-id="c59a4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c59a4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c59a4-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="c59a4-114">timeToPersist</span></span>|<span data-ttu-id="c59a4-115">İş akışının boşta olduğu ve kalıcı olduğu zaman arasındaki süreyi belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="c59a4-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="c59a4-116">Varsayılan değer TimeSpan. MaxValue ' dır.</span><span class="sxs-lookup"><span data-stu-id="c59a4-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="c59a4-117">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="c59a4-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="c59a4-118">Bu öznitelik, bir iş akışı örneğini daha fazla kararlılık halinde kalıcı hale getirmek istiyorsanız yararlıdır, ancak örneğin, örneği mümkün olduğunca uzun süre tutarken</span><span class="sxs-lookup"><span data-stu-id="c59a4-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="c59a4-119">Bu öznitelik yalnızca değeri **TimeToUnload** özniteliğinden daha küçükse geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c59a4-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="c59a4-120">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c59a4-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="c59a4-121">Bu öznitelik **TimeToUnload** özniteliği tarafından belirtilen değerden önce geçtiğinde, iş akışı kaldırılmadan önce Kalıcılık tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c59a4-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="c59a4-122">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c59a4-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="c59a4-123">Kalıcılık katmanı, geçici hatalara yönelik yeniden denemeleri işlemekten sorumludur ve yalnızca kurtarılamaz hatalarda özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c59a4-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="c59a4-124">Bu nedenle, kalıcılık sırasında oluşan tüm özel durumlar önemli olarak değerlendirilir ve iş akışı örneği iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="c59a4-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c59a4-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="c59a4-125">timeToUnload</span></span>|<span data-ttu-id="c59a4-126">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="c59a4-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="c59a4-127">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="c59a4-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="c59a4-128">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c59a4-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="c59a4-129">Bu öznitelik sıfır olarak ayarlandıysa iş akışı örneği kalıcıdır ve iş akışı boşta olduktan hemen sonra kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c59a4-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="c59a4-130">Bu özniteliğin TimeSpan. MaxValue olarak ayarlanması, kaldırma işlemini etkin bir şekilde devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c59a4-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="c59a4-131">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c59a4-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c59a4-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c59a4-132">Child Elements</span></span>  
 <span data-ttu-id="c59a4-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="c59a4-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c59a4-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c59a4-134">Parent Elements</span></span>  
  
|<span data-ttu-id="c59a4-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="c59a4-135">Element</span></span>|<span data-ttu-id="c59a4-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c59a4-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c59a4-137">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="c59a4-137">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c59a4-138">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c59a4-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c59a4-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c59a4-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
