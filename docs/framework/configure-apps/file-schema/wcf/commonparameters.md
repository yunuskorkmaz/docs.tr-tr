---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153028"
---
# \<commonParameters>
<span data-ttu-id="bfe7f-101">Birden çok hizmet arasında genel olarak kullanılan parametrelerin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-101">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="bfe7f-102">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-102">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="bfe7f-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfe7f-103">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfe7f-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfe7f-104">Attributes and Elements</span></span>  
 <span data-ttu-id="bfe7f-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfe7f-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bfe7f-106">Attributes</span></span>  
 <span data-ttu-id="bfe7f-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bfe7f-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfe7f-108">Child Elements</span></span>  
  
|<span data-ttu-id="bfe7f-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="bfe7f-109">Element</span></span>|<span data-ttu-id="bfe7f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfe7f-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|<span data-ttu-id="bfe7f-111">, Hizmet tarafından koleksiyona kullanılan ortak parametrelerin ad-değer çiftini ekler.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-111">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bfe7f-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bfe7f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="bfe7f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="bfe7f-113">Element</span></span>|<span data-ttu-id="bfe7f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfe7f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="bfe7f-115"><xref:System.Workflow.Runtime.WorkflowRuntime>İş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-115">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfe7f-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfe7f-116">Remarks</span></span>  
 <span data-ttu-id="bfe7f-117">`<commonParameters>`Öğesi, ' yi kullanırken, birden çok hizmet arasında genel olarak kullanılan tüm parametreleri tanımlar `ConnectionString` <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="bfe7f-117">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfe7f-118">SQL Izleme hizmeti `ConnectionString` , bölümünde belirtilmişse değeri sürekli olarak kullanmaz `<commonParameters>` .</span><span class="sxs-lookup"><span data-stu-id="bfe7f-118">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="bfe7f-119">Özelliği alma gibi bazı işlemler `StateMachineWorkflowInstance.StateHistory` başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-119">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="bfe7f-120">Bu sorunu geçici olarak belirlemek için, `ConnectionString` Aşağıdaki örnekte gösterildiği gibi, izleme sağlayıcısına ait yapılandırma bölümünde özniteliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-120">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="bfe7f-121">Ve gibi, kalıcılık depolarına iş toplu işleri uygulayan hizmetler için <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , `EnableRetries` Aşağıdaki örnekte gösterildiği gibi, parametresini kullanarak işlemini yeniden denemesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bfe7f-121">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="bfe7f-122">`EnableRetries`Parametrenin genel düzeyde ( *CommonParameters* bölümünde gösterildiği gibi) ya da tarafından desteklenen bireysel hizmetlerin `EnableRetries` ( *Hizmetler* bölümünde gösterildiği gibi) ayarlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-122">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="bfe7f-123">Aşağıdaki örnek kod, programlama yoluyla ortak parametrelerin nasıl değiştirileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="bfe7f-123">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="bfe7f-124">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için <xref:System.Workflow.Runtime.WorkflowRuntime> bkz. [Iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="bfe7f-124">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfe7f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfe7f-125">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="bfe7f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfe7f-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="bfe7f-127">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bfe7f-127">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<add>](add-of-commonparameters.md)
