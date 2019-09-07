---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397535"
---
# <a name="workflowidle"></a><span data-ttu-id="b25c9-101">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="b25c9-101">\<workflowIdle></span></span>
<span data-ttu-id="b25c9-102">Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b25c9-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="b25c9-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b25c9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b25c9-104">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b25c9-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b25c9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b25c9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b25c9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b25c9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b25c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b25c9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b25c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowIdle >**</span><span class="sxs-lookup"><span data-stu-id="b25c9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25c9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b25c9-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b25c9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b25c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b25c9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b25c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b25c9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b25c9-112">Attributes</span></span>  
  
|<span data-ttu-id="b25c9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b25c9-113">Attribute</span></span>|<span data-ttu-id="b25c9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b25c9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b25c9-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="b25c9-115">timeToPersist</span></span>|<span data-ttu-id="b25c9-116">İş akışının boşta olduğu ve kalıcı olduğu zaman arasındaki süreyi belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="b25c9-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="b25c9-117">Varsayılan değer TimeSpan. MaxValue ' dır.</span><span class="sxs-lookup"><span data-stu-id="b25c9-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="b25c9-118">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="b25c9-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="b25c9-119">Bu öznitelik, bir iş akışı örneğini daha fazla kararlılık halinde kalıcı hale getirmek istiyorsanız yararlıdır, ancak örneğin, örneği mümkün olduğunca uzun süre tutarken</span><span class="sxs-lookup"><span data-stu-id="b25c9-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="b25c9-120">Bu öznitelik yalnızca değeri **TimeToUnload** özniteliğinden daha küçükse geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b25c9-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="b25c9-121">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="b25c9-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="b25c9-122">Bu öznitelik **TimeToUnload** özniteliği tarafından belirtilen değerden önce geçtiğinde, iş akışı kaldırılmadan önce Kalıcılık tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b25c9-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="b25c9-123">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b25c9-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="b25c9-124">Kalıcılık katmanı, geçici hatalara yönelik yeniden denemeleri işlemekten sorumludur ve yalnızca kurtarılamaz hatalarda özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b25c9-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="b25c9-125">Bu nedenle, kalıcılık sırasında oluşan tüm özel durumlar önemli olarak değerlendirilir ve iş akışı örneği iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="b25c9-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="b25c9-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="b25c9-126">timeToUnload</span></span>|<span data-ttu-id="b25c9-127">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="b25c9-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="b25c9-128">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="b25c9-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="b25c9-129">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b25c9-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="b25c9-130">Bu öznitelik sıfır olarak ayarlandıysa iş akışı örneği kalıcıdır ve iş akışı boşta olduktan hemen sonra kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b25c9-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="b25c9-131">Bu özniteliğin TimeSpan. MaxValue olarak ayarlanması, kaldırma işlemini etkin bir şekilde devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b25c9-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="b25c9-132">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b25c9-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b25c9-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b25c9-133">Child Elements</span></span>  
 <span data-ttu-id="b25c9-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="b25c9-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b25c9-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b25c9-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b25c9-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="b25c9-136">Element</span></span>|<span data-ttu-id="b25c9-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b25c9-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b25c9-138">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="b25c9-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b25c9-139">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b25c9-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b25c9-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b25c9-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
