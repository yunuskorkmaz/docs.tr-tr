---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: b9ab4e8ca5a71d54a80d17322b61c83d41af2b40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673595"
---
# <a name="commonparameters"></a><span data-ttu-id="2b1ec-101">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="2b1ec-101">\<commonParameters></span></span>
<span data-ttu-id="2b1ec-102">Dünya çapında bir çok hizmette kullanılan parametrelerin bir koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="2b1ec-103">Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="2b1ec-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2b1ec-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2b1ec-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="2b1ec-105">\<behaviors></span></span>  
<span data-ttu-id="2b1ec-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2b1ec-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2b1ec-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2b1ec-107">\<behavior></span></span>  
<span data-ttu-id="2b1ec-108">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="2b1ec-108">\<workflowRuntime></span></span>  
<span data-ttu-id="2b1ec-109">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="2b1ec-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b1ec-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b1ec-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b1ec-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b1ec-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2b1ec-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b1ec-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b1ec-113">Attributes</span></span>  
 <span data-ttu-id="2b1ec-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2b1ec-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b1ec-115">Child Elements</span></span>  
  
|<span data-ttu-id="2b1ec-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b1ec-116">Element</span></span>|<span data-ttu-id="2b1ec-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b1ec-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b1ec-118">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="2b1ec-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="2b1ec-119">Bir ad-değer çifti koleksiyonu için hizmetleri tarafından kullanılan ortak parametrelerinin ekler.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b1ec-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b1ec-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2b1ec-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b1ec-121">Element</span></span>|<span data-ttu-id="2b1ec-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b1ec-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b1ec-123">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="2b1ec-123">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="2b1ec-124">Örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındıran için.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b1ec-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b1ec-125">Remarks</span></span>  
 <span data-ttu-id="2b1ec-126">`<commonParameters>` Öğesi, dünya çapında Örneğin çok hizmette kullanılan parametreleri tanımlar `ConnectionString` kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b1ec-127">SQL izleme hizmeti sürekli olarak kullanmaz `ConnectionString` içinde belirtilen değeri `<commonParameters>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="2b1ec-128">Alma gibi alt işlemlerin `StateMachineWorkflowInstance.StateHistory` özelliği başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="2b1ec-129">Geçici çözüm için bunu belirtin `ConnectionString` özniteliği izleme sağlayıcısı için yapılandırma bölümünde aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="2b1ec-130">İş işleme Hizmetleri için kalıcılığı mağazalarının gibi toplu işlemleri <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, bunları kendi işlemi kullanarak yeniden etkinleştirebilirsiniz `EnableRetries` aşağıdaki örnekte gösterildiği gibi parametre:</span><span class="sxs-lookup"><span data-stu-id="2b1ec-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="2b1ec-131">Dikkat `EnableRetries` parametresi ya da genel düzeyde ayarlanabilir (gösterildiği gibi *CommonParameters* bölümü) veya kişiye ait hizmetleri destekleyen `EnableRetries` (gösterildiği gibi *Hizmetleri*bölümü).</span><span class="sxs-lookup"><span data-stu-id="2b1ec-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="2b1ec-132">Aşağıdaki örnek kod, ortak parametreleri program aracılığıyla değiştirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="2b1ec-133">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesne bir Windows Workflow Foundation ana bilgisayar uygulaması bakın [iş akışı yapılandırma dosyalarını](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2b1ec-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b1ec-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b1ec-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="2b1ec-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b1ec-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="2b1ec-136">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2b1ec-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="2b1ec-137">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="2b1ec-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
