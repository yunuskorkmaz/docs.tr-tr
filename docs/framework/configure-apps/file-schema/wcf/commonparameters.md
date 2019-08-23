---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a92a81062e92f832be78af2bfd75270390eaac3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919490"
---
# <a name="commonparameters"></a><span data-ttu-id="482ff-101">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="482ff-101">\<commonParameters></span></span>
<span data-ttu-id="482ff-102">Birden çok hizmet arasında genel olarak kullanılan parametrelerin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="482ff-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="482ff-103">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="482ff-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="482ff-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="482ff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="482ff-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="482ff-105">\<behaviors></span></span>  
<span data-ttu-id="482ff-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="482ff-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="482ff-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="482ff-107">\<behavior></span></span>  
<span data-ttu-id="482ff-108">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="482ff-108">\<workflowRuntime></span></span>  
<span data-ttu-id="482ff-109">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="482ff-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="482ff-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="482ff-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="482ff-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="482ff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="482ff-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="482ff-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="482ff-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="482ff-113">Attributes</span></span>  
 <span data-ttu-id="482ff-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="482ff-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="482ff-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="482ff-115">Child Elements</span></span>  
  
|<span data-ttu-id="482ff-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="482ff-116">Element</span></span>|<span data-ttu-id="482ff-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="482ff-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="482ff-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="482ff-118">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="482ff-119">, Hizmet tarafından koleksiyona kullanılan ortak parametrelerin ad-değer çiftini ekler.</span><span class="sxs-lookup"><span data-stu-id="482ff-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="482ff-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="482ff-120">Parent Elements</span></span>  
  
|<span data-ttu-id="482ff-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="482ff-121">Element</span></span>|<span data-ttu-id="482ff-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="482ff-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="482ff-123">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="482ff-123">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="482ff-124">İş akışı tabanlı Windows Communication Foundation (WCF <xref:System.Workflow.Runtime.WorkflowRuntime> ) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="482ff-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="482ff-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="482ff-125">Remarks</span></span>  
 <span data-ttu-id="482ff-126">Öğesi, ' yi kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>, `ConnectionString` birden çok hizmet arasında genel olarak kullanılan tüm parametreleri tanımlar. `<commonParameters>`</span><span class="sxs-lookup"><span data-stu-id="482ff-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="482ff-127">SQL izleme hizmeti, `ConnectionString` `<commonParameters>` bölümünde belirtilmişse değeri sürekli olarak kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="482ff-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="482ff-128">`StateMachineWorkflowInstance.StateHistory` Özelliği alma gibi bazı işlemler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="482ff-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="482ff-129">Bu sorunu geçici olarak belirlemek için `ConnectionString` , aşağıdaki örnekte gösterildiği gibi, izleme sağlayıcısına ait yapılandırma bölümünde özniteliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="482ff-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="482ff-130"><xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> Ve `EnableRetries` gibi, kalıcılık depolarına iş toplu işleri uygulayan hizmetler için, aşağıdaki örnekte gösterildiği gibi, parametresini kullanarak işlemini yeniden denemesini sağlayabilirsiniz: <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService></span><span class="sxs-lookup"><span data-stu-id="482ff-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="482ff-131">Parametrenin genel düzeyde ( *CommonParameters* bölümünde gösterildiği gibi) ya da tarafından desteklenen `EnableRetries` bireysel hizmetlerin ( *Hizmetler* bölümünde gösterildiği gibi) ayarlandığına dikkat edin. `EnableRetries`</span><span class="sxs-lookup"><span data-stu-id="482ff-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="482ff-132">Aşağıdaki örnek kod, programlama yoluyla ortak parametrelerin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="482ff-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="482ff-133">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için bkz. [iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="482ff-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="482ff-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="482ff-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="482ff-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="482ff-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="482ff-136">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="482ff-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="482ff-137">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="482ff-137">\<add></span></span>](add-of-commonparameters.md)
