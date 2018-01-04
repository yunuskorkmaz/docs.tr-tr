---
title: '&lt;hizmetlerin&gt; &lt;eklenmesi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a859676adf48fda05040633fb8909d161e9ce8e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="2ef24-102">&lt;hizmetlerin&gt; &lt;eklenmesi&gt;</span><span class="sxs-lookup"><span data-stu-id="2ef24-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="2ef24-103">Öğesinin bir örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı barındırmak için [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="2ef24-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="2ef24-104">Bu öğe türünde <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2ef24-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="2ef24-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2ef24-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2ef24-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="2ef24-106">\<behaviors></span></span>  
<span data-ttu-id="2ef24-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2ef24-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="2ef24-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2ef24-108">\<behavior></span></span>  
<span data-ttu-id="2ef24-109">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="2ef24-109">\<services></span></span>  
<span data-ttu-id="2ef24-110">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="2ef24-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ef24-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ef24-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ef24-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ef24-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2ef24-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ef24-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ef24-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2ef24-114">Attributes</span></span>  
  
|<span data-ttu-id="2ef24-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2ef24-115">Attribute</span></span>|<span data-ttu-id="2ef24-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ef24-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ef24-117">türü</span><span class="sxs-lookup"><span data-stu-id="2ef24-117">type</span></span>|<span data-ttu-id="2ef24-118">Hizmetin başlatılması için derleme nitelenmiş tür adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="2ef24-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="2ef24-119">Belirtilen hizmet kendi oluşturucular imzalarını hakkında belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ef24-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="2ef24-120">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2ef24-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ef24-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ef24-121">Child Elements</span></span>  
 <span data-ttu-id="2ef24-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="2ef24-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ef24-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ef24-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2ef24-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="2ef24-124">Element</span></span>|<span data-ttu-id="2ef24-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ef24-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ef24-126">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="2ef24-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="2ef24-127">Eklenecek hizmetler koleksiyonu <xref:System.Workflow.Runtime.WorkflowRuntime> altyapısı.</span><span class="sxs-lookup"><span data-stu-id="2ef24-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="2ef24-128">Tür öğeleridir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2ef24-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="2ef24-129">Koleksiyonda belirtilen hizmetler iş akışı çalışma zamanı altyapısı tarafından başlatılan ve hizmetlerinin için eklenen zaman uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2ef24-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="2ef24-130">Bu nedenle, koleksiyonda belirtilen hizmetlerden kendi oluşturucular imzalarını hakkında belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ef24-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="2ef24-131">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2ef24-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ef24-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ef24-132">Remarks</span></span>  
 <span data-ttu-id="2ef24-133">Bu öğe belirtilen hizmeti iş akışı çalışma zamanı altyapısı tarafından başlatılan ve hizmetlerinin için eklenen zaman uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2ef24-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="2ef24-134">Bu nedenle, belirtilen hizmet kendi oluşturucular imzalarını hakkında belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ef24-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="2ef24-135">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2ef24-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ef24-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ef24-136">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ef24-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ef24-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="2ef24-138">İş akışı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="2ef24-138">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
