---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 790e852eb515e19afc324f6e1c25db81ed22999c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148678"
---
# \<workflowIdle>

<span data-ttu-id="95725-101">Boştaki iş akışı örneklerinin ne zaman kaldırılabileceğini ve kalıcı olduğunu denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="95725-101">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="95725-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="95725-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95725-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="95725-103">Attributes and Elements</span></span>  

 <span data-ttu-id="95725-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95725-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95725-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="95725-105">Attributes</span></span>  
  
|<span data-ttu-id="95725-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="95725-106">Attribute</span></span>|<span data-ttu-id="95725-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95725-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95725-108">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="95725-108">timeToPersist</span></span>|<span data-ttu-id="95725-109">İş akışının boşta olduğu ve kalıcı olduğu zaman arasındaki süreyi belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="95725-109">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="95725-110">Varsayılan değer TimeSpan. MaxValue ' dır.</span><span class="sxs-lookup"><span data-stu-id="95725-110">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="95725-111">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="95725-111">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="95725-112">Bu öznitelik, bir iş akışı örneğini daha fazla kararlılık halinde kalıcı hale getirmek istiyorsanız yararlıdır, ancak örneğin, örneği mümkün olduğunca uzun süre tutarken</span><span class="sxs-lookup"><span data-stu-id="95725-112">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="95725-113">Bu öznitelik yalnızca değeri **TimeToUnload** özniteliğinden daha küçükse geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="95725-113">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="95725-114">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="95725-114">If it is greater, it is ignored.</span></span> <span data-ttu-id="95725-115">Bu öznitelik **TimeToUnload** özniteliği tarafından belirtilen değerden önce geçtiğinde, iş akışı kaldırılmadan önce Kalıcılık tamamlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95725-115">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="95725-116">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="95725-116">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="95725-117">Kalıcılık katmanı, geçici hatalara yönelik yeniden denemeleri işlemekten sorumludur ve yalnızca kurtarılamaz hatalarda özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95725-117">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="95725-118">Bu nedenle, kalıcılık sırasında oluşan tüm özel durumlar önemli olarak değerlendirilir ve iş akışı örneği iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="95725-118">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="95725-119">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="95725-119">timeToUnload</span></span>|<span data-ttu-id="95725-120">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="95725-120">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="95725-121">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="95725-121">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="95725-122">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="95725-122">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="95725-123">Bu öznitelik sıfır olarak ayarlandıysa iş akışı örneği kalıcıdır ve iş akışı boşta olduktan hemen sonra kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="95725-123">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="95725-124">Bu özniteliğin TimeSpan. MaxValue olarak ayarlanması, kaldırma işlemini etkin bir şekilde devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="95725-124">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="95725-125">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="95725-125">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95725-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="95725-126">Child Elements</span></span>  

 <span data-ttu-id="95725-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="95725-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95725-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="95725-128">Parent Elements</span></span>  
  
|<span data-ttu-id="95725-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="95725-129">Element</span></span>|<span data-ttu-id="95725-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95725-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95725-131">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="95725-131">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="95725-132">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="95725-132">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95725-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95725-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
