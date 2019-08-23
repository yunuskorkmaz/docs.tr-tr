---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 0cd04f66cc4b73eb5f1c43bd6c8dc9189dfceff1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915210"
---
# <a name="workflowruntime"></a><span data-ttu-id="ddae0-101">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="ddae0-101">\<workflowRuntime></span></span>
<span data-ttu-id="ddae0-102">İş akışı tabanlı Windows Communication Foundation (WCF <xref:System.Workflow.Runtime.WorkflowRuntime> ) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="ddae0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ddae0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ddae0-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="ddae0-104">\<behaviors></span></span>  
<span data-ttu-id="ddae0-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ddae0-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ddae0-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="ddae0-106">\<behavior></span></span>  
<span data-ttu-id="ddae0-107">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="ddae0-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddae0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddae0-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddae0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddae0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ddae0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ddae0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddae0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ddae0-111">Attributes</span></span>  
  
|<span data-ttu-id="ddae0-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ddae0-112">Attribute</span></span>|<span data-ttu-id="ddae0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddae0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ddae0-114">CachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="ddae0-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="ddae0-115">Bir iş <xref:System.TimeSpan> akışı örneğinin, zorla kaldırılmadan veya durdurulmadan önce boşta durumunda kalabileceği en uzun süreyi belirten isteğe bağlı bir değer.</span><span class="sxs-lookup"><span data-stu-id="ddae0-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="ddae0-116">WorkflowRuntime `PersistenceService` , UnloadOnIdle işlemini gerçekleştirirse, bu öznitelik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="ddae0-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="ddae0-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="ddae0-117">enablePerformanceCounters</span></span>|<span data-ttu-id="ddae0-118">Performans sayaçlarının etkin olup olmadığını belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="ddae0-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="ddae0-119">Performans sayaçları, iş akışı ile ilgili çeşitli istatistikler hakkında bilgi sağlar, ancak iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalışırken performans cezasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ddae0-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="ddae0-120">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="ddae0-121">name</span><span class="sxs-lookup"><span data-stu-id="ddae0-121">name</span></span>|<span data-ttu-id="ddae0-122">İş akışı çalışma zamanı altyapısının adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ddae0-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="ddae0-123">Bu ad, bu çalışma zamanını sistemde çalışmakta olabilecek diğer çalışma zamanları (örneğin, performans sayaçları) ayırt etmek için çıktıda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ddae0-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="ddae0-124">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="ddae0-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="ddae0-125">validateOnCreate</span></span>|<span data-ttu-id="ddae0-126">WorkflowServiceHost açıldığında iş akışı tanımı doğrulamasının gerçekleşmeyeceğini belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="ddae0-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="ddae0-127">Bu öznitelik olarak `true`ayarlandığında, iş akışı doğrulama `WorkflowServiceHost.Open` her çağrıldığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ddae0-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="ddae0-128">Doğrulama hataları bulunursa bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="ddae0-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="ddae0-129">Bu özellik olarak `false`ayarlandığında, iş akışı tanımı doğrulaması gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="ddae0-130">Bu özellik `true`için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="ddae0-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddae0-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddae0-131">Child Elements</span></span>  
  
|<span data-ttu-id="ddae0-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="ddae0-132">Element</span></span>|<span data-ttu-id="ddae0-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddae0-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ddae0-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="ddae0-134">commonParameters</span></span>|<span data-ttu-id="ddae0-135">Hizmetler tarafından kullanılan ortak parametrelerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ddae0-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="ddae0-136">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="ddae0-137">hizmetler</span><span class="sxs-lookup"><span data-stu-id="ddae0-137">services</span></span>|<span data-ttu-id="ddae0-138"><xref:System.Workflow.Runtime.WorkflowRuntime> Altyapıya eklenecek hizmetlerden oluşan bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="ddae0-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="ddae0-139">Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ddae0-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="ddae0-140">Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="ddae0-141">Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="ddae0-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="ddae0-142">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ddae0-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddae0-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ddae0-143">Parent Elements</span></span>  
  
|<span data-ttu-id="ddae0-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="ddae0-144">Element</span></span>|<span data-ttu-id="ddae0-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddae0-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddae0-146">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="ddae0-146">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ddae0-147">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddae0-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ddae0-148">Remarks</span></span>  
 <span data-ttu-id="ddae0-149">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için bkz. [iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ddae0-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddae0-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddae0-150">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ddae0-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddae0-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="ddae0-152">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ddae0-152">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
