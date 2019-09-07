---
title: <add> / <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: dc769097a3aede2522c1fa7a4cf8e36c2d8fdfe8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398287"
---
# <a name="add-of-services"></a><span data-ttu-id="9d1c2-102">\<\<hizmet > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="9d1c2-102">\<add> of \<services></span></span>
<span data-ttu-id="9d1c2-103">İş akışı tabanlı Windows Communication Foundation (WCF <xref:System.Workflow.Runtime.WorkflowRuntime> ) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="9d1c2-104">Bu öğe türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
<span data-ttu-id="9d1c2-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d1c2-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9d1c2-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9d1c2-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9d1c2-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9d1c2-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9d1c2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9d1c2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="9d1c2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9d1c2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="9d1c2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowRuntime >** ](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="9d1c2-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="9d1c2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Hizmetler >** ](services-of-workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="9d1c2-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)</span></span>\
<span data-ttu-id="9d1c2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="9d1c2-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d1c2-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d1c2-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d1c2-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d1c2-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9d1c2-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d1c2-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9d1c2-116">Attributes</span></span>  
  
|<span data-ttu-id="9d1c2-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9d1c2-117">Attribute</span></span>|<span data-ttu-id="9d1c2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d1c2-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d1c2-119">türü</span><span class="sxs-lookup"><span data-stu-id="9d1c2-119">type</span></span>|<span data-ttu-id="9d1c2-120">Başlatılacak hizmetin derleme nitelikli tür adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-120">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="9d1c2-121">Belirtilen hizmet, oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-121">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9d1c2-122">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-122">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d1c2-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d1c2-123">Child Elements</span></span>  
 <span data-ttu-id="9d1c2-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d1c2-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d1c2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9d1c2-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="9d1c2-126">Element</span></span>|<span data-ttu-id="9d1c2-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d1c2-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d1c2-128">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="9d1c2-128">\<services></span></span>](services-of-workflowruntime.md)|<span data-ttu-id="9d1c2-129"><xref:System.Workflow.Runtime.WorkflowRuntime> Altyapıya eklenecek hizmetlerden oluşan bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-129">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="9d1c2-130">Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-130">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="9d1c2-131">Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-131">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="9d1c2-132">Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-132">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9d1c2-133">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-133">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d1c2-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d1c2-134">Remarks</span></span>  
 <span data-ttu-id="9d1c2-135">Bu öğede belirtilen hizmet, iş akışı çalışma zamanı altyapısı tarafından başlatılacak ve uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrıldığında hizmetlerine eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-135">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="9d1c2-136">Bu nedenle, belirtilen hizmet oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-136">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9d1c2-137">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-137">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d1c2-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d1c2-138">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="9d1c2-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d1c2-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="9d1c2-140">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9d1c2-140">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
