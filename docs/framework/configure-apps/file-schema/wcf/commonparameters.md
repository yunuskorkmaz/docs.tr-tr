---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153028"
---
# <a name="commonparameters"></a><span data-ttu-id="ee7e0-101">\<yaygın Parametreler></span><span class="sxs-lookup"><span data-stu-id="ee7e0-101">\<commonParameters></span></span>
<span data-ttu-id="ee7e0-102">Birden çok hizmet arasında genel olarak kullanılan parametre koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="ee7e0-103">Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılabilecek veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="ee7e0-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ee7e0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ee7e0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ee7e0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ee7e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ee7e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ee7e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ee7e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="ee7e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranış>**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ee7e0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="ee7e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<iş akışıRuntime>**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="ee7e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="ee7e0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParametreler>**</span><span class="sxs-lookup"><span data-stu-id="ee7e0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee7e0-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee7e0-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee7e0-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee7e0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ee7e0-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee7e0-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee7e0-114">Attributes</span></span>  
 <span data-ttu-id="ee7e0-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee7e0-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee7e0-116">Child Elements</span></span>  
  
|<span data-ttu-id="ee7e0-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee7e0-117">Element</span></span>|<span data-ttu-id="ee7e0-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee7e0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee7e0-119">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="ee7e0-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="ee7e0-120">Koleksiyona hizmetler tarafından kullanılan ortak parametrelerin ad değeri çiftini ekler.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee7e0-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee7e0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ee7e0-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee7e0-122">Element</span></span>|<span data-ttu-id="ee7e0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee7e0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee7e0-124">\<iş akışıRuntime></span><span class="sxs-lookup"><span data-stu-id="ee7e0-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="ee7e0-125">İş akışı tabanlı Windows <xref:System.Workflow.Runtime.WorkflowRuntime> Communication Foundation (WCF) hizmetlerini barındırmak için ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee7e0-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee7e0-126">Remarks</span></span>  
 <span data-ttu-id="ee7e0-127">Öğe, `<commonParameters>` örneğin `ConnectionString` . <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService></span><span class="sxs-lookup"><span data-stu-id="ee7e0-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee7e0-128">SQL Tracking `ConnectionString` `<commonParameters>` hizmeti, bölümde belirtilmişse değeri sürekli olarak kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="ee7e0-129">`StateMachineWorkflowInstance.StateHistory` Özelliğigeri almak gibi bazı işlemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="ee7e0-130">Bu geçici çözüm için, aşağıdaki örnekte belirtildiği gibi, izleme sağlayıcısı için yapılandırma bölümünde `ConnectionString` özniteliği belirtin.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="ee7e0-131">Aşağıdaki örnekte gösterildiği gibi <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> `EnableRetries` parametreyi kullanarak işlemlerini yeniden denemelerini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ee7e0-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="ee7e0-132">Parametrenin `EnableRetries` genel düzeyde *(Ortak Parametreler* bölümünde gösterildiği gibi) veya destekleyen `EnableRetries` tek tek hizmetler için *(Hizmetler* bölümünde gösterildiği gibi) ayarlanabildiği ne dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="ee7e0-133">Aşağıdaki örnek kod, ortak parametrelerin programlı olarak nasıl değiştirilebildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="ee7e0-133">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="ee7e0-134">Bir Windows İş Akışı Temeli ana bilgisayarı <xref:System.Workflow.Runtime.WorkflowRuntime> uygulamasının nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için [Bkz. İş Akışı Yapılandırma Dosyaları.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ee7e0-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee7e0-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee7e0-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="ee7e0-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee7e0-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="ee7e0-137">[İş Akışı Yapılandırma Dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ee7e0-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="ee7e0-138">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="ee7e0-138">\<add></span></span>](add-of-commonparameters.md)
