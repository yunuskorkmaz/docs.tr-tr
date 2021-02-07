---
description: 'Hakkında daha fazla bilgi edinin: <workflowIdle>'
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: c1707ab5c633a358846a8ddf529bbfab90d3012d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697965"
---
# \<workflowIdle>

<span data-ttu-id="c7bdc-102">Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="c7bdc-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7bdc-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7bdc-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7bdc-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c7bdc-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7bdc-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7bdc-106">Attributes</span></span>  
  
|<span data-ttu-id="c7bdc-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c7bdc-107">Attribute</span></span>|<span data-ttu-id="c7bdc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7bdc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c7bdc-109">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="c7bdc-109">timeToPersist</span></span>|<span data-ttu-id="c7bdc-110">İş akışının boşta olduğu ve kalıcı olduğu zaman arasındaki süreyi belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-110">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="c7bdc-111">Varsayılan değer TimeSpan. MaxValue ' dır.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-111">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="c7bdc-112">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-112">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="c7bdc-113">Bu öznitelik, bir iş akışı örneğini daha fazla kararlılık halinde kalıcı hale getirmek istiyorsanız yararlıdır, ancak örneğin, örneği mümkün olduğunca uzun süre tutarken</span><span class="sxs-lookup"><span data-stu-id="c7bdc-113">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="c7bdc-114">Bu öznitelik yalnızca değeri **TimeToUnload** özniteliğinden daha küçükse geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-114">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="c7bdc-115">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-115">If it is greater, it is ignored.</span></span> <span data-ttu-id="c7bdc-116">Bu öznitelik **TimeToUnload** özniteliği tarafından belirtilen değerden önce geçtiğinde, iş akışı kaldırılmadan önce Kalıcılık tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-116">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="c7bdc-117">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-117">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="c7bdc-118">Kalıcılık katmanı, geçici hatalara yönelik yeniden denemeleri işlemekten sorumludur ve yalnızca kurtarılamaz hatalarda özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-118">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="c7bdc-119">Bu nedenle, kalıcılık sırasında oluşan tüm özel durumlar önemli olarak değerlendirilir ve iş akışı örneği iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-119">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c7bdc-120">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="c7bdc-120">timeToUnload</span></span>|<span data-ttu-id="c7bdc-121">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-121">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="c7bdc-122">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-122">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="c7bdc-123">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-123">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="c7bdc-124">Bu öznitelik sıfır olarak ayarlandıysa iş akışı örneği kalıcıdır ve iş akışı boşta olduktan hemen sonra kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-124">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="c7bdc-125">Bu özniteliğin TimeSpan. MaxValue olarak ayarlanması, kaldırma işlemini etkin bir şekilde devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-125">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="c7bdc-126">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-126">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c7bdc-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7bdc-127">Child Elements</span></span>  

 <span data-ttu-id="c7bdc-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c7bdc-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7bdc-129">Parent Elements</span></span>  
  
|<span data-ttu-id="c7bdc-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7bdc-130">Element</span></span>|<span data-ttu-id="c7bdc-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7bdc-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7bdc-132">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c7bdc-132">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c7bdc-133">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-133">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7bdc-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7bdc-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
