---
title: <add> / <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 26d43460f225cb57946aca80e3d1e3fde2ea1100
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557716"
---
# <a name="add-of-services"></a><span data-ttu-id="c47e4-102">\<add> / \<services></span><span class="sxs-lookup"><span data-stu-id="c47e4-102">\<add> of \<services></span></span>
<span data-ttu-id="c47e4-103"><xref:System.Workflow.Runtime.WorkflowRuntime>İş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c47e4-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="c47e4-104">Bu öğe türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="c47e4-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c47e4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c47e4-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c47e4-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c47e4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c47e4-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c47e4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c47e4-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c47e4-108">Attributes</span></span>  
  
|<span data-ttu-id="c47e4-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c47e4-109">Attribute</span></span>|<span data-ttu-id="c47e4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c47e4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c47e4-111">tür</span><span class="sxs-lookup"><span data-stu-id="c47e4-111">type</span></span>|<span data-ttu-id="c47e4-112">Başlatılacak hizmetin derleme nitelikli tür adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c47e4-112">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="c47e4-113">Belirtilen hizmet, oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="c47e4-113">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="c47e4-114">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c47e4-114">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c47e4-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c47e4-115">Child Elements</span></span>  
 <span data-ttu-id="c47e4-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c47e4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c47e4-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c47e4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c47e4-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c47e4-118">Element</span></span>|<span data-ttu-id="c47e4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c47e4-119">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="c47e4-120">Altyapıya eklenecek hizmetlerden oluşan bir koleksiyon <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="c47e4-120">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="c47e4-121">Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="c47e4-121">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="c47e4-122">Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="c47e4-122">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="c47e4-123">Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="c47e4-123">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="c47e4-124">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c47e4-124">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c47e4-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c47e4-125">Remarks</span></span>  
 <span data-ttu-id="c47e4-126">Bu öğede belirtilen hizmet, iş akışı çalışma zamanı altyapısı tarafından başlatılacak ve uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrıldığında hizmetlerine eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="c47e4-126">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="c47e4-127">Bu nedenle, belirtilen hizmet oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="c47e4-127">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="c47e4-128">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c47e4-128">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c47e4-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="c47e4-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c47e4-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c47e4-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="c47e4-131">[İş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c47e4-131">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
