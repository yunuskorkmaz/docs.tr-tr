---
title: "&lt;İş akışı workflowRuntime&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ad33eee445e04d1e43fa8b15e92c08cd48c11b11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowruntimegt"></a><span data-ttu-id="bcdee-102">&lt;İş akışı workflowRuntime&gt;</span><span class="sxs-lookup"><span data-stu-id="bcdee-102">&lt;workflowRuntime&gt;</span></span>
<span data-ttu-id="bcdee-103">Öğesinin bir örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı barındırmak için [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="bcdee-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>  
  
 <span data-ttu-id="bcdee-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bcdee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bcdee-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="bcdee-105">\<behaviors></span></span>  
<span data-ttu-id="bcdee-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bcdee-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bcdee-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="bcdee-107">\<behavior></span></span>  
<span data-ttu-id="bcdee-108">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="bcdee-108">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcdee-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bcdee-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcdee-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bcdee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bcdee-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bcdee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcdee-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bcdee-112">Attributes</span></span>  
  
|<span data-ttu-id="bcdee-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bcdee-113">Attribute</span></span>|<span data-ttu-id="bcdee-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcdee-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bcdee-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="bcdee-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="bcdee-116">İsteğe bağlı bir <xref:System.TimeSpan> bir iş akışı örneği bellek içi kalarak en uzun süreyi belirten değer zorla yüklenmemiş veya iptal önce boşta durumda.</span><span class="sxs-lookup"><span data-stu-id="bcdee-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="bcdee-117">Workflowruntime varsa `PersistenceService` unloadOnIdle gerçekleştirir, bu öznitelik dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="bcdee-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="bcdee-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="bcdee-118">enablePerformanceCounters</span></span>|<span data-ttu-id="bcdee-119">Performans sayaçları etkinleştirilip etkinleştirilmediğini belirten isteğe bağlı bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="bcdee-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="bcdee-120">Performans sayaçları bilgisi çeşitli iş akışı ile ilgili istatistikler sağlar. ancak iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalışırken performans cezası neden olurlar.</span><span class="sxs-lookup"><span data-stu-id="bcdee-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="bcdee-121">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="bcdee-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="bcdee-122">name</span><span class="sxs-lookup"><span data-stu-id="bcdee-122">name</span></span>|<span data-ttu-id="bcdee-123">İş akışı çalışma zamanı altyapısı adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="bcdee-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="bcdee-124">Çıktıda sistemde, örneğin, performans sayaçları çalışan diğer çalışma zamanları ile bu çalışma zamanı birbirinden ayırmak için kullanılan adı.</span><span class="sxs-lookup"><span data-stu-id="bcdee-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="bcdee-125">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="bcdee-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="bcdee-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="bcdee-126">validateOnCreate</span></span>|<span data-ttu-id="bcdee-127">WorkflowServiceHost açık olduğunda doğrulama iş akışı tanımının oluşup oluşmadığına belirten isteğe bağlı bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="bcdee-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="bcdee-128">Bu öznitelik ayarlandığında `true`, iş akışı doğrulama her zaman yürütülür `WorkflowServiceHost.Open` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="bcdee-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="bcdee-129">Doğrulama hataları bulunursa, bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="bcdee-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="bcdee-130">Bu özellik ayarlandığında `false`, bir iş akışı tanımı doğrulama gerçekleşecek.</span><span class="sxs-lookup"><span data-stu-id="bcdee-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="bcdee-131">Bu özellik için varsayılan değer `true`.</span><span class="sxs-lookup"><span data-stu-id="bcdee-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcdee-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bcdee-132">Child Elements</span></span>  
  
|<span data-ttu-id="bcdee-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="bcdee-133">Element</span></span>|<span data-ttu-id="bcdee-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcdee-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bcdee-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="bcdee-135">commonParameters</span></span>|<span data-ttu-id="bcdee-136">Hizmetler tarafından kullanılan ortak parametreleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="bcdee-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="bcdee-137">Bu koleksiyon genellikle sürekli hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="bcdee-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="bcdee-138">hizmetler</span><span class="sxs-lookup"><span data-stu-id="bcdee-138">services</span></span>|<span data-ttu-id="bcdee-139">Eklenecek hizmetler koleksiyonu <xref:System.Workflow.Runtime.WorkflowRuntime> altyapısı.</span><span class="sxs-lookup"><span data-stu-id="bcdee-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="bcdee-140">Tür öğeleridir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bcdee-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="bcdee-141">Koleksiyonda belirtilen hizmetler iş akışı çalışma zamanı altyapısı tarafından başlatılan ve hizmetlerinin için eklenen zaman uygun <xref:System.Workflow.Runtime.WorkflowRuntime> Oluşturucusu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bcdee-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="bcdee-142">Bu nedenle, koleksiyonda belirtilen hizmetlerden kendi oluşturucular imzalarını hakkında belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="bcdee-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="bcdee-143">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bcdee-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bcdee-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bcdee-144">Parent Elements</span></span>  
  
|<span data-ttu-id="bcdee-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="bcdee-145">Element</span></span>|<span data-ttu-id="bcdee-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcdee-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcdee-147">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="bcdee-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bcdee-148">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bcdee-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcdee-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bcdee-149">Remarks</span></span>  
 <span data-ttu-id="bcdee-150">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesi bir Windows Workflow Foundation ana bilgisayar uygulamasının bkz [iş akışı yapılandırma dosyalarını](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="bcdee-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcdee-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="bcdee-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bcdee-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bcdee-152">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="bcdee-153">İş akışı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="bcdee-153">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
