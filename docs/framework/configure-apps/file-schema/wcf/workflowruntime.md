---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: db5e1083c07d4e204eb19eaae9257ed44439132e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206570"
---
# <a name="workflowruntime"></a><span data-ttu-id="e55af-101">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="e55af-101">\<workflowRuntime></span></span>
<span data-ttu-id="e55af-102">Örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındıran için.</span><span class="sxs-lookup"><span data-stu-id="e55af-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="e55af-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e55af-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e55af-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="e55af-104">\<behaviors></span></span>  
<span data-ttu-id="e55af-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e55af-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="e55af-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e55af-106">\<behavior></span></span>  
<span data-ttu-id="e55af-107">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="e55af-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55af-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e55af-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e55af-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e55af-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e55af-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e55af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e55af-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e55af-111">Attributes</span></span>  
  
|<span data-ttu-id="e55af-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e55af-112">Attribute</span></span>|<span data-ttu-id="e55af-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e55af-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e55af-114">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="e55af-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="e55af-115">İsteğe bağlı <xref:System.TimeSpan> bir iş akışı örneği bellek içi kalarak en uzun süreyi belirten bir değer zorla kaldırıldı veya sona erdirildi önce boşta durumda.</span><span class="sxs-lookup"><span data-stu-id="e55af-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="e55af-116">İş akışı workflowruntime varsa `PersistenceService` unloadOnIdle gerçekleştirir, bu öznitelik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e55af-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="e55af-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="e55af-117">enablePerformanceCounters</span></span>|<span data-ttu-id="e55af-118">Performans sayaçlarının etkin olup olmadığını belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="e55af-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="e55af-119">Performans sayaçları, çeşitli iş akışı ile ilgili istatistikleri bilgi sağlar, ancak bunlar iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalıştırırken bir performans sorununa neden.</span><span class="sxs-lookup"><span data-stu-id="e55af-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="e55af-120">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e55af-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="e55af-121">name</span><span class="sxs-lookup"><span data-stu-id="e55af-121">name</span></span>|<span data-ttu-id="e55af-122">İş akışı çalışma zamanı altyapısı adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="e55af-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="e55af-123">Çıktıda çalışma zamanı bu sistem, örneğin, performans sayaçları çalışan diğer çalışma zamanları ayırmak için kullanılan adı.</span><span class="sxs-lookup"><span data-stu-id="e55af-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="e55af-124">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e55af-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="e55af-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="e55af-125">validateOnCreate</span></span>|<span data-ttu-id="e55af-126">WorkflowServiceHost açıldığında iş akışı tanımı doğrulamasını gerçekleşip gerçekleşmeyeceğini belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="e55af-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="e55af-127">Bu öznitelik ayarlandığında `true`, iş akışı doğrulama her zaman yürütülür `WorkflowServiceHost.Open` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e55af-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="e55af-128">Doğrulama hatası bulunursa, bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="e55af-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="e55af-129">Bu özelliği ayarlandığında `false`, herhangi bir iş akışı tanımı doğrulaması gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="e55af-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="e55af-130">Bu özellik için varsayılan değer `true`.</span><span class="sxs-lookup"><span data-stu-id="e55af-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e55af-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e55af-131">Child Elements</span></span>  
  
|<span data-ttu-id="e55af-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="e55af-132">Element</span></span>|<span data-ttu-id="e55af-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e55af-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e55af-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="e55af-134">commonParameters</span></span>|<span data-ttu-id="e55af-135">Hizmetler tarafından kullanılan ortak parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e55af-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="e55af-136">Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="e55af-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="e55af-137">hizmetler</span><span class="sxs-lookup"><span data-stu-id="e55af-137">services</span></span>|<span data-ttu-id="e55af-138">Eklenecek hizmetler koleksiyonu <xref:System.Workflow.Runtime.WorkflowRuntime> altyapısı.</span><span class="sxs-lookup"><span data-stu-id="e55af-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="e55af-139">Öğeleri türlerinin <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e55af-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="e55af-140">Koleksiyonda belirtilen Hizmetleri iş akışı çalışma zamanı altyapısı tarafından başlatılan ve hizmetlerinin için eklenen zaman uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e55af-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="e55af-141">Bu nedenle, koleksiyonda belirtilen hizmetlerden, oluşturucuları imzalarını hakkında belirli kurallara uymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e55af-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="e55af-142">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e55af-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e55af-143">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e55af-143">Parent Elements</span></span>  
  
|<span data-ttu-id="e55af-144">Öğe</span><span class="sxs-lookup"><span data-stu-id="e55af-144">Element</span></span>|<span data-ttu-id="e55af-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e55af-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e55af-146">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e55af-146">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e55af-147">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e55af-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e55af-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e55af-148">Remarks</span></span>  
 <span data-ttu-id="e55af-149">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesne bir Windows Workflow Foundation ana bilgisayar uygulaması bakın [iş akışı yapılandırma dosyalarını](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e55af-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e55af-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="e55af-150">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e55af-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e55af-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="e55af-152">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e55af-152">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
