---
description: 'Hakkında daha fazla bilgi edinin: <commonParameters>'
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a9d230fb0f205315dc52357119e6b35752abc96d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698381"
---
# \<commonParameters>

<span data-ttu-id="5211d-102">Birden çok hizmet arasında genel olarak kullanılan parametrelerin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5211d-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="5211d-103">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5211d-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="5211d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5211d-104">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5211d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5211d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5211d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5211d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5211d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5211d-107">Attributes</span></span>  

 <span data-ttu-id="5211d-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="5211d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5211d-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5211d-109">Child Elements</span></span>  
  
|<span data-ttu-id="5211d-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="5211d-110">Element</span></span>|<span data-ttu-id="5211d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5211d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|<span data-ttu-id="5211d-112">, Hizmet tarafından koleksiyona kullanılan ortak parametrelerin ad-değer çiftini ekler.</span><span class="sxs-lookup"><span data-stu-id="5211d-112">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5211d-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5211d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5211d-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="5211d-114">Element</span></span>|<span data-ttu-id="5211d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5211d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="5211d-116"><xref:System.Workflow.Runtime.WorkflowRuntime>İş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5211d-116">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5211d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5211d-117">Remarks</span></span>  

 <span data-ttu-id="5211d-118">`<commonParameters>`Öğesi, ' yi kullanırken, birden çok hizmet arasında genel olarak kullanılan tüm parametreleri tanımlar `ConnectionString` <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="5211d-118">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5211d-119">SQL Izleme hizmeti `ConnectionString` , bölümünde belirtilmişse değeri sürekli olarak kullanmaz `<commonParameters>` .</span><span class="sxs-lookup"><span data-stu-id="5211d-119">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="5211d-120">Özelliği alma gibi bazı işlemler `StateMachineWorkflowInstance.StateHistory` başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="5211d-120">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="5211d-121">Bu sorunu geçici olarak belirlemek için, `ConnectionString` Aşağıdaki örnekte gösterildiği gibi, izleme sağlayıcısına ait yapılandırma bölümünde özniteliğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="5211d-121">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="5211d-122">Ve gibi, kalıcılık depolarına iş toplu işleri uygulayan hizmetler için <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , `EnableRetries` Aşağıdaki örnekte gösterildiği gibi, parametresini kullanarak işlemini yeniden denemesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5211d-122">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="5211d-123">`EnableRetries`Parametrenin genel düzeyde ( *CommonParameters* bölümünde gösterildiği gibi) ya da tarafından desteklenen bireysel hizmetlerin `EnableRetries` ( *Hizmetler* bölümünde gösterildiği gibi) ayarlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5211d-123">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="5211d-124">Aşağıdaki örnek kod, programlama yoluyla ortak parametrelerin nasıl değiştirileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5211d-124">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="5211d-125">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için <xref:System.Workflow.Runtime.WorkflowRuntime> bkz. [Iş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5211d-125">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5211d-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="5211d-126">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="5211d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5211d-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="5211d-128">[İş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5211d-128">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<add>](add-of-commonparameters.md)
