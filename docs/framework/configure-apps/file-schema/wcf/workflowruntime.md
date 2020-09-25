---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 4a450fb6f02bbf0f1681f7b2fabea9da7b65cbea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183604"
---
# \<workflowRuntime>

<span data-ttu-id="0b89c-101"><xref:System.Workflow.Runtime.WorkflowRuntime>İş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b89c-101">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="0b89c-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b89c-102">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b89c-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b89c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0b89c-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b89c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b89c-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b89c-105">Attributes</span></span>  
  
|<span data-ttu-id="0b89c-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0b89c-106">Attribute</span></span>|<span data-ttu-id="0b89c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b89c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b89c-108">CachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="0b89c-108">cachedInstanceExpiration</span></span>|<span data-ttu-id="0b89c-109"><xref:System.TimeSpan>Bir iş akışı örneğinin, zorla kaldırılmadan veya durdurulmadan önce boşta durumunda kalabileceği en uzun süreyi belirten isteğe bağlı bir değer.</span><span class="sxs-lookup"><span data-stu-id="0b89c-109">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="0b89c-110">WorkflowRuntime, `PersistenceService` UnloadOnIdle işlemini gerçekleştirirse, bu öznitelik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="0b89c-110">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="0b89c-111">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="0b89c-111">enablePerformanceCounters</span></span>|<span data-ttu-id="0b89c-112">Performans sayaçlarının etkin olup olmadığını belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="0b89c-112">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="0b89c-113">Performans sayaçları, iş akışı ile ilgili çeşitli istatistikler hakkında bilgi sağlar, ancak iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalışırken performans cezasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0b89c-113">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="0b89c-114">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="0b89c-114">The default value is `true`.</span></span>|  
|<span data-ttu-id="0b89c-115">name</span><span class="sxs-lookup"><span data-stu-id="0b89c-115">name</span></span>|<span data-ttu-id="0b89c-116">İş akışı çalışma zamanı altyapısının adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="0b89c-116">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="0b89c-117">Bu ad, bu çalışma zamanını sistemde çalışmakta olabilecek diğer çalışma zamanları (örneğin, performans sayaçları) ayırt etmek için çıktıda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b89c-117">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="0b89c-118">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="0b89c-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="0b89c-119">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="0b89c-119">validateOnCreate</span></span>|<span data-ttu-id="0b89c-120">WorkflowServiceHost açıldığında iş akışı tanımı doğrulamasının gerçekleşmeyeceğini belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="0b89c-120">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="0b89c-121">Bu öznitelik olarak ayarlandığında `true` , iş akışı doğrulama her `WorkflowServiceHost.Open` çağrıldığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0b89c-121">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="0b89c-122">Doğrulama hataları bulunursa bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="0b89c-122">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="0b89c-123">Bu özellik olarak ayarlandığında `false` , Iş akışı tanımı doğrulaması gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="0b89c-123">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="0b89c-124">Bu özellik için varsayılan değer `true` .</span><span class="sxs-lookup"><span data-stu-id="0b89c-124">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b89c-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b89c-125">Child Elements</span></span>  
  
|<span data-ttu-id="0b89c-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b89c-126">Element</span></span>|<span data-ttu-id="0b89c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b89c-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b89c-128">commonParameters</span><span class="sxs-lookup"><span data-stu-id="0b89c-128">commonParameters</span></span>|<span data-ttu-id="0b89c-129">Hizmetler tarafından kullanılan ortak parametrelerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="0b89c-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="0b89c-130">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0b89c-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="0b89c-131">services</span><span class="sxs-lookup"><span data-stu-id="0b89c-131">services</span></span>|<span data-ttu-id="0b89c-132">Altyapıya eklenecek hizmetlerden oluşan bir koleksiyon <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="0b89c-132">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="0b89c-133">Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="0b89c-133">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="0b89c-134">Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="0b89c-134">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="0b89c-135">Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b89c-135">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="0b89c-136">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="0b89c-136">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0b89c-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0b89c-137">Parent Elements</span></span>  
  
|<span data-ttu-id="0b89c-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="0b89c-138">Element</span></span>|<span data-ttu-id="0b89c-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b89c-139">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0b89c-140">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0b89c-140">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b89c-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b89c-141">Remarks</span></span>  

 <span data-ttu-id="0b89c-142">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için <xref:System.Workflow.Runtime.WorkflowRuntime> bkz. [Iş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0b89c-142">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b89c-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b89c-143">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="0b89c-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b89c-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="0b89c-145">[İş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0b89c-145">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
