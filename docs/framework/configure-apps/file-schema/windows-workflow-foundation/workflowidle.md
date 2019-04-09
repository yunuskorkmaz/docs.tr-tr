---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1dc186f5899935dab43c0d33894e659c4b19748c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201123"
---
# <a name="workflowidle"></a><span data-ttu-id="5b34c-101">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="5b34c-101">\<workflowIdle></span></span>
<span data-ttu-id="5b34c-102">Boş iş akışı örnekleri zaman kaldırıldı ve kalıcı denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="5b34c-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="5b34c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5b34c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5b34c-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="5b34c-104">\<behaviors></span></span>  
<span data-ttu-id="5b34c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5b34c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="5b34c-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5b34c-106">\<behavior></span></span>  
<span data-ttu-id="5b34c-107">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="5b34c-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b34c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b34c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b34c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b34c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5b34c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b34c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b34c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b34c-111">Attributes</span></span>  
  
|<span data-ttu-id="5b34c-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5b34c-112">Attribute</span></span>|<span data-ttu-id="5b34c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b34c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b34c-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="5b34c-114">timeToPersist</span></span>|<span data-ttu-id="5b34c-115">İş akışı boş olur ve kalıcı saat arasındaki süre belirten bir Timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="5b34c-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="5b34c-116">TimeSpan.MaxValue varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="5b34c-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="5b34c-117">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="5b34c-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="5b34c-118">Bu öznitelik, en çok bellekte hala örnek koruyarak bir iş akışı örneği daha agresif bir biçimde sürdürülmesi istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5b34c-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="5b34c-119">Bu öznitelik, yalnızca öğenin değeri ise geçerlidir'den az **timeToUnload** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5b34c-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="5b34c-120">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="5b34c-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="5b34c-121">Bu öznitelik ile belirtilen değer önce aşılırsa **timeToUnload** özniteliği Kalıcılık iş akışı kaldırıldı önce tamamlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="5b34c-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="5b34c-122">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b34c-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="5b34c-123">Kalıcılık katman geçici hatalar için herhangi bir yeniden deneme işlenmesinden sorumludur ve yalnızca kurtarılabilir olmayan hataları üzerinde özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b34c-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="5b34c-124">Bu nedenle, Kalıcılık sırasında oluşturulan özel durumlar olarak kabul edilir ve iş akışı örneği durduruldu.</span><span class="sxs-lookup"><span data-stu-id="5b34c-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="5b34c-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="5b34c-125">timeToUnload</span></span>|<span data-ttu-id="5b34c-126">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="5b34c-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="5b34c-127">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="5b34c-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="5b34c-128">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5b34c-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="5b34c-129">Bu öznitelik iş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır olarak ayarlanırsa, iş akışı boş olur.</span><span class="sxs-lookup"><span data-stu-id="5b34c-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="5b34c-130">Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5b34c-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="5b34c-131">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="5b34c-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b34c-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b34c-132">Child Elements</span></span>  
 <span data-ttu-id="5b34c-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="5b34c-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b34c-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b34c-134">Parent Elements</span></span>  
  
|<span data-ttu-id="5b34c-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b34c-135">Element</span></span>|<span data-ttu-id="5b34c-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b34c-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b34c-137">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5b34c-137">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="5b34c-138">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b34c-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b34c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b34c-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
