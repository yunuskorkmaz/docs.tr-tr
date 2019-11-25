---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: ab21be7b5e2738ac6a7c9bea676d8180c69d1afd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968562"
---
# <a name="commonparameters"></a><span data-ttu-id="278f5-101">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="278f5-101">\<commonParameters></span></span>
<span data-ttu-id="278f5-102">Birden çok hizmet arasında genel olarak kullanılan parametrelerin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="278f5-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="278f5-103">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="278f5-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="278f5-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="278f5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="278f5-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="278f5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="278f5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışları >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="278f5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="278f5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışları >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="278f5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="278f5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="278f5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="278f5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowRuntime >** ](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="278f5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="278f5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<commonParameters >**</span><span class="sxs-lookup"><span data-stu-id="278f5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278f5-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="278f5-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="278f5-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="278f5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="278f5-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="278f5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="278f5-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="278f5-114">Attributes</span></span>  
 <span data-ttu-id="278f5-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="278f5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="278f5-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="278f5-116">Child Elements</span></span>  
  
|<span data-ttu-id="278f5-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="278f5-117">Element</span></span>|<span data-ttu-id="278f5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="278f5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="278f5-119">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="278f5-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="278f5-120">, Hizmet tarafından koleksiyona kullanılan ortak parametrelerin ad-değer çiftini ekler.</span><span class="sxs-lookup"><span data-stu-id="278f5-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="278f5-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="278f5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="278f5-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="278f5-122">Element</span></span>|<span data-ttu-id="278f5-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="278f5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="278f5-124">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="278f5-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="278f5-125">İş akışı tabanlı Windows Communication Foundation (WCF) Hizmetleri barındırmak için bir <xref:System.Workflow.Runtime.WorkflowRuntime> örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="278f5-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="278f5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="278f5-126">Remarks</span></span>  
 <span data-ttu-id="278f5-127">`<commonParameters>` öğesi, birden çok hizmet arasında genel olarak kullanılan parametreleri tanımlar, örneğin <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>kullanılırken `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="278f5-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="278f5-128">`<commonParameters>` bölümünde belirtilmişse SQL Izleme hizmeti `ConnectionString` değeri sürekli olarak kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="278f5-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="278f5-129">`StateMachineWorkflowInstance.StateHistory` özelliğini alma gibi bazı işlemler başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="278f5-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="278f5-130">Bu sorunu geçici olarak belirlemek için, aşağıdaki örnekte gösterildiği gibi, İzleme sağlayıcısının yapılandırma bölümünde `ConnectionString` özniteliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="278f5-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" 
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="278f5-131"><xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>gibi Kalıcılık depolarına iş toplu işleri uygulayan hizmetler için, aşağıdaki örnekte gösterildiği gibi `EnableRetries` parametresini kullanarak işlemlerini yeniden denemesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="278f5-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="278f5-132">`EnableRetries` parametresinin küresel bir düzeyde ( *CommonParameters* bölümünde gösterildiği gibi) veya `EnableRetries` destekleyen bireysel hizmetlerden ( *Hizmetler* bölümünde gösterildiği gibi) ayarlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="278f5-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="278f5-133">Aşağıdaki örnek kod, programlama yoluyla ortak parametrelerin nasıl değiştirileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="278f5-133">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="278f5-134">Bir Windows Workflow Foundation ana bilgisayar uygulamasının <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için bkz. [Iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="278f5-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="278f5-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="278f5-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="278f5-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="278f5-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="278f5-137">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="278f5-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="278f5-138">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="278f5-138">\<add></span></span>](add-of-commonparameters.md)
