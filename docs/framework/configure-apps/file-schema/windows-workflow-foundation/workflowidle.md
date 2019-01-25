---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 9d9eb45090367fb2cc18fc357c219e74d63fb667
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628108"
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="9dcb2-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="9dcb2-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="9dcb2-103">Boş iş akışı örnekleri zaman kaldırıldı ve kalıcı denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="9dcb2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9dcb2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9dcb2-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="9dcb2-105">\<behaviors></span></span>  
<span data-ttu-id="9dcb2-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9dcb2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9dcb2-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="9dcb2-107">\<behavior></span></span>  
<span data-ttu-id="9dcb2-108">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="9dcb2-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dcb2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dcb2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9dcb2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dcb2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9dcb2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9dcb2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9dcb2-112">Attributes</span></span>  
  
|<span data-ttu-id="9dcb2-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9dcb2-113">Attribute</span></span>|<span data-ttu-id="9dcb2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dcb2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9dcb2-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="9dcb2-115">timeToPersist</span></span>|<span data-ttu-id="9dcb2-116">İş akışı boş olur ve kalıcı saat arasındaki süre belirten bir Timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="9dcb2-117">TimeSpan.MaxValue varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="9dcb2-118">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="9dcb2-119">Bu öznitelik, en çok bellekte hala örnek koruyarak bir iş akışı örneği daha agresif bir biçimde sürdürülmesi istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="9dcb2-120">Bu öznitelik, yalnızca öğenin değeri ise geçerlidir'den az **timeToUnload** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="9dcb2-121">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="9dcb2-122">Bu öznitelik ile belirtilen değer önce aşılırsa **timeToUnload** özniteliği Kalıcılık iş akışı kaldırıldı önce tamamlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="9dcb2-123">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="9dcb2-124">Kalıcılık katman geçici hatalar için herhangi bir yeniden deneme işlenmesinden sorumludur ve yalnızca kurtarılabilir olmayan hataları üzerinde özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="9dcb2-125">Bu nedenle, Kalıcılık sırasında oluşturulan özel durumlar olarak kabul edilir ve iş akışı örneği durduruldu.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="9dcb2-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="9dcb2-126">timeToUnload</span></span>|<span data-ttu-id="9dcb2-127">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="9dcb2-128">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="9dcb2-129">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="9dcb2-130">Bu öznitelik iş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır olarak ayarlanırsa, iş akışı boş olur.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="9dcb2-131">Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="9dcb2-132">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9dcb2-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dcb2-133">Child Elements</span></span>  
 <span data-ttu-id="9dcb2-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9dcb2-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dcb2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="9dcb2-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="9dcb2-136">Element</span></span>|<span data-ttu-id="9dcb2-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dcb2-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9dcb2-138">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9dcb2-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="9dcb2-139">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9dcb2-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dcb2-140">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
