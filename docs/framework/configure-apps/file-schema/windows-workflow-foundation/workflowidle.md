---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: af8a2568eb13bb3007065c4b4a3564aae27de7ac
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280936"
---
# <a name="workflowidle"></a><span data-ttu-id="d87a6-101">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="d87a6-101">\<workflowIdle></span></span>
<span data-ttu-id="d87a6-102">Boş iş akışı örnekleri zaman kaldırıldı ve kalıcı denetleyen bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="d87a6-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="d87a6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d87a6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d87a6-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d87a6-104">\<behaviors></span></span>  
<span data-ttu-id="d87a6-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d87a6-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="d87a6-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d87a6-106">\<behavior></span></span>  
<span data-ttu-id="d87a6-107">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="d87a6-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d87a6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d87a6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d87a6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d87a6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d87a6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d87a6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d87a6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d87a6-111">Attributes</span></span>  
  
|<span data-ttu-id="d87a6-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d87a6-112">Attribute</span></span>|<span data-ttu-id="d87a6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d87a6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d87a6-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="d87a6-114">timeToPersist</span></span>|<span data-ttu-id="d87a6-115">İş akışı boş olur ve kalıcı saat arasındaki süre belirten bir Timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="d87a6-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="d87a6-116">TimeSpan.MaxValue varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d87a6-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="d87a6-117">İş akışı örneği boşta kaldığında geçmesini süresi başlar.</span><span class="sxs-lookup"><span data-stu-id="d87a6-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="d87a6-118">Bu öznitelik, en çok bellekte hala örnek koruyarak bir iş akışı örneği daha agresif bir biçimde sürdürülmesi istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d87a6-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="d87a6-119">Bu öznitelik, yalnızca öğenin değeri ise geçerlidir'den az **timeToUnload** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d87a6-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="d87a6-120">Büyükse, göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="d87a6-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="d87a6-121">Bu öznitelik ile belirtilen değer önce aşılırsa **timeToUnload** özniteliği Kalıcılık iş akışı kaldırıldı önce tamamlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d87a6-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="d87a6-122">Bu iş akışı kalıcı kadar kaldırma işlemi gecikebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d87a6-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="d87a6-123">Kalıcılık katman geçici hatalar için herhangi bir yeniden deneme işlenmesinden sorumludur ve yalnızca kurtarılabilir olmayan hataları üzerinde özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d87a6-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="d87a6-124">Bu nedenle, Kalıcılık sırasında oluşturulan özel durumlar olarak kabul edilir ve iş akışı örneği durduruldu.</span><span class="sxs-lookup"><span data-stu-id="d87a6-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="d87a6-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="d87a6-125">timeToUnload</span></span>|<span data-ttu-id="d87a6-126">Saat arasındaki süre belirten bir Timespan değeri iş akışı boş olur ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="d87a6-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="d87a6-127">Varsayılan değer 1 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="d87a6-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="d87a6-128">Bir iş akışı kaldırılırken ayrıca kalıcı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d87a6-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="d87a6-129">Bu öznitelik iş akışı örneği kalıcı ve hemen sonra kaldırıldığında sıfır olarak ayarlanırsa, iş akışı boş olur.</span><span class="sxs-lookup"><span data-stu-id="d87a6-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="d87a6-130">Bu öznitelik için TimeSpan.MaxValue etkili bir şekilde ayarlanması kaldırma işlemi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d87a6-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="d87a6-131">Boş iş akışı örnekleri hiçbir zaman kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d87a6-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d87a6-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d87a6-132">Child Elements</span></span>  
 <span data-ttu-id="d87a6-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="d87a6-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d87a6-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d87a6-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d87a6-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="d87a6-135">Element</span></span>|<span data-ttu-id="d87a6-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d87a6-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d87a6-137">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d87a6-137">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d87a6-138">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d87a6-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d87a6-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d87a6-139">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
