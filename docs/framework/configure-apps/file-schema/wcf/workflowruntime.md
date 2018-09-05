---
title: '&lt;İş akışı WorkflowRuntime&gt;'
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 849b09936f303c21fe55a6a46d561590c6a4c808
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504967"
---
# <a name="ltworkflowruntimegt"></a><span data-ttu-id="fab0b-102">&lt;İş akışı WorkflowRuntime&gt;</span><span class="sxs-lookup"><span data-stu-id="fab0b-102">&lt;workflowRuntime&gt;</span></span>
<span data-ttu-id="fab0b-103">Örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındıran için.</span><span class="sxs-lookup"><span data-stu-id="fab0b-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="fab0b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fab0b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fab0b-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="fab0b-105">\<behaviors></span></span>  
<span data-ttu-id="fab0b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fab0b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fab0b-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fab0b-107">\<behavior></span></span>  
<span data-ttu-id="fab0b-108">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="fab0b-108">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fab0b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fab0b-109">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fab0b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fab0b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fab0b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fab0b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fab0b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fab0b-112">Attributes</span></span>  
  
|<span data-ttu-id="fab0b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fab0b-113">Attribute</span></span>|<span data-ttu-id="fab0b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fab0b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fab0b-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="fab0b-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="fab0b-116">İsteğe bağlı <xref:System.TimeSpan> bir iş akışı örneği bellek içi kalarak en uzun süreyi belirten bir değer zorla kaldırıldı veya sona erdirildi önce boşta durumda.</span><span class="sxs-lookup"><span data-stu-id="fab0b-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="fab0b-117">İş akışı workflowruntime varsa `PersistenceService` unloadOnIdle gerçekleştirir, bu öznitelik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="fab0b-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="fab0b-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="fab0b-118">enablePerformanceCounters</span></span>|<span data-ttu-id="fab0b-119">Performans sayaçlarının etkin olup olmadığını belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="fab0b-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="fab0b-120">Performans sayaçları, çeşitli iş akışı ile ilgili istatistikleri bilgi sağlar, ancak bunlar iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalıştırırken bir performans sorununa neden.</span><span class="sxs-lookup"><span data-stu-id="fab0b-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="fab0b-121">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fab0b-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="fab0b-122">name</span><span class="sxs-lookup"><span data-stu-id="fab0b-122">name</span></span>|<span data-ttu-id="fab0b-123">İş akışı çalışma zamanı altyapısı adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fab0b-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="fab0b-124">Çıktıda çalışma zamanı bu sistem, örneğin, performans sayaçları çalışan diğer çalışma zamanları ayırmak için kullanılan adı.</span><span class="sxs-lookup"><span data-stu-id="fab0b-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="fab0b-125">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fab0b-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="fab0b-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="fab0b-126">validateOnCreate</span></span>|<span data-ttu-id="fab0b-127">WorkflowServiceHost açıldığında iş akışı tanımı doğrulamasını gerçekleşip gerçekleşmeyeceğini belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="fab0b-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="fab0b-128">Bu öznitelik ayarlandığında `true`, iş akışı doğrulama her zaman yürütülür `WorkflowServiceHost.Open` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fab0b-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="fab0b-129">Doğrulama hatası bulunursa, bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="fab0b-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="fab0b-130">Bu özelliği ayarlandığında `false`, herhangi bir iş akışı tanımı doğrulaması gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="fab0b-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="fab0b-131">Bu özellik için varsayılan değer `true`.</span><span class="sxs-lookup"><span data-stu-id="fab0b-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fab0b-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fab0b-132">Child Elements</span></span>  
  
|<span data-ttu-id="fab0b-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="fab0b-133">Element</span></span>|<span data-ttu-id="fab0b-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fab0b-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fab0b-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="fab0b-135">commonParameters</span></span>|<span data-ttu-id="fab0b-136">Hizmetler tarafından kullanılan ortak parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fab0b-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="fab0b-137">Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="fab0b-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="fab0b-138">hizmetler</span><span class="sxs-lookup"><span data-stu-id="fab0b-138">services</span></span>|<span data-ttu-id="fab0b-139">Eklenecek hizmetler koleksiyonu <xref:System.Workflow.Runtime.WorkflowRuntime> altyapısı.</span><span class="sxs-lookup"><span data-stu-id="fab0b-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="fab0b-140">Öğeleri türlerinin <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="fab0b-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="fab0b-141">Koleksiyonda belirtilen Hizmetleri iş akışı çalışma zamanı altyapısı tarafından başlatılan ve hizmetlerinin için eklenen zaman uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fab0b-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="fab0b-142">Bu nedenle, koleksiyonda belirtilen hizmetlerden, oluşturucuları imzalarını hakkında belirli kurallara uymanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fab0b-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="fab0b-143">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="fab0b-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fab0b-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fab0b-144">Parent Elements</span></span>  
  
|<span data-ttu-id="fab0b-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="fab0b-145">Element</span></span>|<span data-ttu-id="fab0b-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fab0b-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fab0b-147">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="fab0b-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="fab0b-148">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fab0b-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fab0b-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fab0b-149">Remarks</span></span>  
 <span data-ttu-id="fab0b-150">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesne bir Windows Workflow Foundation ana bilgisayar uygulaması bakın [iş akışı yapılandırma dosyalarını](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="fab0b-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fab0b-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="fab0b-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fab0b-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fab0b-152">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <span data-ttu-id="fab0b-153">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fab0b-153">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
