---
title: '&lt;commonParameters&gt;'
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 5e4c19c48709ffd81cb00e9820e6c3cdb297ec7e
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46530066"
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="5ff2b-102">&lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="5ff2b-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="5ff2b-103">Dünya çapında bir çok hizmette kullanılan parametrelerin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="5ff2b-104">Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="5ff2b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ff2b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ff2b-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="5ff2b-106">\<behaviors></span></span>  
<span data-ttu-id="5ff2b-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5ff2b-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="5ff2b-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5ff2b-108">\<behavior></span></span>  
<span data-ttu-id="5ff2b-109">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="5ff2b-109">\<workflowRuntime></span></span>  
<span data-ttu-id="5ff2b-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="5ff2b-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff2b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ff2b-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ff2b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ff2b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5ff2b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ff2b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ff2b-114">Attributes</span></span>  
 <span data-ttu-id="5ff2b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ff2b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ff2b-116">Child Elements</span></span>  
  
|<span data-ttu-id="5ff2b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ff2b-117">Element</span></span>|<span data-ttu-id="5ff2b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ff2b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ff2b-119">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5ff2b-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="5ff2b-120">Bir ad-değer çifti koleksiyonu için hizmetleri tarafından kullanılan ortak parametrelerinin ekler.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ff2b-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ff2b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5ff2b-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ff2b-122">Element</span></span>|<span data-ttu-id="5ff2b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ff2b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ff2b-124">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="5ff2b-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="5ff2b-125">Örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındıran için.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ff2b-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ff2b-126">Remarks</span></span>  
 <span data-ttu-id="5ff2b-127">`<commonParameters>` Öğesi, dünya çapında Örneğin çok hizmette kullanılan parametreleri tanımlar `ConnectionString` kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ff2b-128">SQL izleme hizmeti sürekli olarak kullanmaz `ConnectionString` içinde belirtilen değeri `<commonParameters>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="5ff2b-129">Alma gibi alt işlemlerin `StateMachineWorkflowInstance.StateHistory` özelliği başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="5ff2b-130">Geçici çözüm için bunu belirtin `ConnectionString` özniteliği izleme sağlayıcısı için yapılandırma bölümünde aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="5ff2b-131">İş işleme Hizmetleri için kalıcılığı mağazalarının gibi toplu işlemleri <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, bunları kendi işlemi kullanarak yeniden etkinleştirebilirsiniz `EnableRetries` aşağıdaki örnekte gösterildiği gibi parametre:</span><span class="sxs-lookup"><span data-stu-id="5ff2b-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="5ff2b-132">Dikkat `EnableRetries` parametresi ya da genel düzeyde ayarlanabilir (gösterildiği gibi *CommonParameters* bölümü) veya kişiye ait hizmetleri destekleyen `EnableRetries` (gösterildiği gibi *Hizmetleri*bölümü).</span><span class="sxs-lookup"><span data-stu-id="5ff2b-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="5ff2b-133">Aşağıdaki örnek kod, ortak parametreleri program aracılığıyla değiştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="5ff2b-134">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesne bir Windows Workflow Foundation ana bilgisayar uygulaması bakın [iş akışı yapılandırma dosyalarını](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5ff2b-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff2b-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ff2b-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ff2b-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ff2b-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 <span data-ttu-id="5ff2b-137">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5ff2b-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>  
 [<span data-ttu-id="5ff2b-138">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5ff2b-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
