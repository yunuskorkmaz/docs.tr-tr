---
title: '&lt;hizmetlerin&gt; &lt;eklenmesi&gt;'
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 6aa903d4188d108940c76ac50eb0a706fbea8f8b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530256"
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="833a9-102">&lt;hizmetlerin&gt; &lt;eklenmesi&gt;</span><span class="sxs-lookup"><span data-stu-id="833a9-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="833a9-103">Örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındıran için.</span><span class="sxs-lookup"><span data-stu-id="833a9-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="833a9-104">Bu öğe türünde <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="833a9-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="833a9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="833a9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="833a9-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="833a9-106">\<behaviors></span></span>  
<span data-ttu-id="833a9-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="833a9-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="833a9-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="833a9-108">\<behavior></span></span>  
<span data-ttu-id="833a9-109">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="833a9-109">\<services></span></span>  
<span data-ttu-id="833a9-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="833a9-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="833a9-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="833a9-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="833a9-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="833a9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="833a9-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="833a9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="833a9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="833a9-114">Attributes</span></span>  
  
|<span data-ttu-id="833a9-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="833a9-115">Attribute</span></span>|<span data-ttu-id="833a9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="833a9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="833a9-117">türü</span><span class="sxs-lookup"><span data-stu-id="833a9-117">type</span></span>|<span data-ttu-id="833a9-118">Hizmetin başlatılması için derleme nitelikli tür adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="833a9-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="833a9-119">Belirtilen hizmet oluşturucuları imzalarını hakkında belirli kurallara uymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="833a9-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="833a9-120">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="833a9-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="833a9-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="833a9-121">Child Elements</span></span>  
 <span data-ttu-id="833a9-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="833a9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="833a9-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="833a9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="833a9-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="833a9-124">Element</span></span>|<span data-ttu-id="833a9-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="833a9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="833a9-126">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="833a9-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="833a9-127">Eklenecek hizmetler koleksiyonu <xref:System.Workflow.Runtime.WorkflowRuntime> altyapısı.</span><span class="sxs-lookup"><span data-stu-id="833a9-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="833a9-128">Öğeleri türlerinin <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="833a9-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="833a9-129">Koleksiyonda belirtilen Hizmetleri iş akışı çalışma zamanı altyapısı tarafından başlatılan ve hizmetlerinin için eklenen zaman uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="833a9-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="833a9-130">Bu nedenle, koleksiyonda belirtilen hizmetlerden, oluşturucuları imzalarını hakkında belirli kurallara uymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="833a9-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="833a9-131">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="833a9-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="833a9-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="833a9-132">Remarks</span></span>  
 <span data-ttu-id="833a9-133">Bu öğede belirtilen hizmeti iş akışı çalışma zamanı altyapısı tarafından başlatılan ve hizmetlerinin için eklenen zaman uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="833a9-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="833a9-134">Bu nedenle, belirtilen hizmet, oluşturucuları imzalarını hakkında belirli kurallara uymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="833a9-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="833a9-135">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="833a9-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="833a9-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="833a9-136">Example</span></span>  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="833a9-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="833a9-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <span data-ttu-id="833a9-138">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="833a9-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
