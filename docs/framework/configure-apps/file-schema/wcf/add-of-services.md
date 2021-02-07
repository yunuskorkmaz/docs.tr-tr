---
description: 'Hakkında daha fazla bilgi <add> edinin: <services>'
title: <add> / <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 868a4ef9fafcc42ca4620880b2c6f1cb499cab4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750032"
---
# <a name="add-of-services"></a><span data-ttu-id="d67dd-103">\<add> / \<services></span><span class="sxs-lookup"><span data-stu-id="d67dd-103">\<add> of \<services></span></span>

<span data-ttu-id="d67dd-104"><xref:System.Workflow.Runtime.WorkflowRuntime>İş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d67dd-104">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="d67dd-105">Bu öğe türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="d67dd-105">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d67dd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d67dd-106">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d67dd-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d67dd-107">Attributes and Elements</span></span>  

 <span data-ttu-id="d67dd-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d67dd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d67dd-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d67dd-109">Attributes</span></span>  
  
|<span data-ttu-id="d67dd-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d67dd-110">Attribute</span></span>|<span data-ttu-id="d67dd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d67dd-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d67dd-112">tür</span><span class="sxs-lookup"><span data-stu-id="d67dd-112">type</span></span>|<span data-ttu-id="d67dd-113">Başlatılacak hizmetin derleme nitelikli tür adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d67dd-113">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="d67dd-114">Belirtilen hizmet, oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="d67dd-114">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d67dd-115">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d67dd-115">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d67dd-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d67dd-116">Child Elements</span></span>  

 <span data-ttu-id="d67dd-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="d67dd-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d67dd-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d67dd-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d67dd-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="d67dd-119">Element</span></span>|<span data-ttu-id="d67dd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d67dd-120">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="d67dd-121">Altyapıya eklenecek hizmetlerden oluşan bir koleksiyon <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="d67dd-121">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="d67dd-122">Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="d67dd-122">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="d67dd-123">Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="d67dd-123">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="d67dd-124">Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="d67dd-124">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d67dd-125">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d67dd-125">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d67dd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d67dd-126">Remarks</span></span>  

 <span data-ttu-id="d67dd-127">Bu öğede belirtilen hizmet, iş akışı çalışma zamanı altyapısı tarafından başlatılacak ve uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrıldığında hizmetlerine eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="d67dd-127">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="d67dd-128">Bu nedenle, belirtilen hizmet oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="d67dd-128">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d67dd-129">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d67dd-129">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d67dd-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d67dd-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d67dd-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d67dd-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="d67dd-132">[İş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d67dd-132">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
