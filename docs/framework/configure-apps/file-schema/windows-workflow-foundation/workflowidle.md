---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151851"
---
# <a name="workflowidle"></a><span data-ttu-id="c2677-101">\<iş akışıBoş></span><span class="sxs-lookup"><span data-stu-id="c2677-101">\<workflowIdle></span></span>
<span data-ttu-id="c2677-102">Boşta kalan iş akışı örnekleri boşaldığında ve kalıcı olduğunda denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="c2677-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="c2677-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2677-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2677-104">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c2677-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="c2677-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c2677-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="c2677-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c2677-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="c2677-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranış>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c2677-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="c2677-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<iş akışıBoş>**</span><span class="sxs-lookup"><span data-stu-id="c2677-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2677-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2677-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2677-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2677-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c2677-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c2677-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2677-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c2677-112">Attributes</span></span>  
  
|<span data-ttu-id="c2677-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c2677-113">Attribute</span></span>|<span data-ttu-id="c2677-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2677-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2677-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="c2677-115">timeToPersist</span></span>|<span data-ttu-id="c2677-116">İş akışının boşta kalıp kalıcı olduğu süreyi belirten bir Zaman Dilimi değeri.</span><span class="sxs-lookup"><span data-stu-id="c2677-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="c2677-117">Varsayılan değer TimeSpan.MaxValue'dir.</span><span class="sxs-lookup"><span data-stu-id="c2677-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="c2677-118">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="c2677-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="c2677-119">Bu öznitelik, bir iş akışı örneğini mümkün olduğunca uzun süre bellekte tutarken daha agresif bir şekilde sürdürmek istiyorsanız yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c2677-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="c2677-120">Bu öznitelik yalnızca değeri **timeToUnload** özniteliğinden daha azsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2677-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="c2677-121">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c2677-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="c2677-122">Bu **öznitelik, zaman ToUnload** özniteliği tarafından belirtilen değerden önce atılırsa, iş akışı kaldırılmadan önce kalıcılığın tamamlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2677-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="c2677-123">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c2677-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="c2677-124">Kalıcılık katmanı geçici hatalar için herhangi bir yeniden deneme işlemek için sorumludur ve yalnızca kurtarılamaz hatalar üzerinde özel durumlar atar.</span><span class="sxs-lookup"><span data-stu-id="c2677-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="c2677-125">Bu nedenle, kalıcılık sırasında atılan tüm özel durumlar ölümcül olarak kabul edilir ve iş akışı örneği iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="c2677-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c2677-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="c2677-126">timeToUnload</span></span>|<span data-ttu-id="c2677-127">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="c2677-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="c2677-128">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="c2677-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="c2677-129">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c2677-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="c2677-130">Bu öznitelik sıfırolarak ayarlanırsa, iş akışı örneği kalıcı dır ve iş akışı boşta kaldıktan hemen sonra boşaltılır.</span><span class="sxs-lookup"><span data-stu-id="c2677-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="c2677-131">Bu özniteliği TimeSpan.MaxValue olarak ayarlamak, boşaltma işlemini etkin bir şekilde devre dışı eder.</span><span class="sxs-lookup"><span data-stu-id="c2677-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="c2677-132">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c2677-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2677-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2677-133">Child Elements</span></span>  
 <span data-ttu-id="c2677-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="c2677-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2677-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c2677-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c2677-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="c2677-136">Element</span></span>|<span data-ttu-id="c2677-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2677-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2677-138">\<hizmet davranış \<>Davranışlar></span><span class="sxs-lookup"><span data-stu-id="c2677-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c2677-139">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2677-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2677-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2677-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
