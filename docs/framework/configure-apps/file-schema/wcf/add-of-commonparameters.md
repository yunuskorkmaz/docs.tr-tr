---
title: '&lt;commonParameters&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 93e82aa3bd44a747d1e85986c51c21522d709bd0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46578913"
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a><span data-ttu-id="804e0-102">&lt;commonParameters&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="804e0-102">&lt;add&gt; of &lt;commonParameters&gt;</span></span>
<span data-ttu-id="804e0-103">Dünya çapında bir çok hizmette kullanılan parametreleri ad-değer çiftinin belirtir.</span><span class="sxs-lookup"><span data-stu-id="804e0-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="804e0-104">Genellikle bu parametre, dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="804e0-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="804e0-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="804e0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="804e0-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="804e0-106">\<behaviors></span></span>  
<span data-ttu-id="804e0-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="804e0-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="804e0-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="804e0-108">\<behavior></span></span>  
<span data-ttu-id="804e0-109">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="804e0-109">\<workflowRuntime></span></span>  
<span data-ttu-id="804e0-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="804e0-110">\<commonParameters></span></span>  
<span data-ttu-id="804e0-111">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="804e0-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="804e0-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="804e0-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="804e0-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="804e0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="804e0-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="804e0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="804e0-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="804e0-115">Attributes</span></span>  
  
|<span data-ttu-id="804e0-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="804e0-116">Attribute</span></span>|<span data-ttu-id="804e0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="804e0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="804e0-118">name</span><span class="sxs-lookup"><span data-stu-id="804e0-118">name</span></span>|<span data-ttu-id="804e0-119">Bir hizmet için belirtilen parametre adı.</span><span class="sxs-lookup"><span data-stu-id="804e0-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="804e0-120">value</span><span class="sxs-lookup"><span data-stu-id="804e0-120">value</span></span>|<span data-ttu-id="804e0-121">Bir hizmet için belirtilen parametre değeri.</span><span class="sxs-lookup"><span data-stu-id="804e0-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="804e0-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="804e0-122">Child Elements</span></span>  
 <span data-ttu-id="804e0-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="804e0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="804e0-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="804e0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="804e0-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="804e0-125">Element</span></span>|<span data-ttu-id="804e0-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="804e0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="804e0-127">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="804e0-127">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|<span data-ttu-id="804e0-128">Hizmetler tarafından kullanılan ortak parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="804e0-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="804e0-129">Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="804e0-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="804e0-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="804e0-130">Remarks</span></span>  
 <span data-ttu-id="804e0-131">`<commonParameters>` Öğesi, dünya çapında Örneğin çok hizmette kullanılan parametreleri tanımlar `ConnectionString` kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="804e0-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="804e0-132">İş işleme Hizmetleri için kalıcılığı mağazalarının gibi toplu işlemleri <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, bunları kendi işlemi kullanarak yeniden etkinleştirebilirsiniz `EnableRetries` aşağıdaki örnekte gösterildiği gibi parametre:</span><span class="sxs-lookup"><span data-stu-id="804e0-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="804e0-133">Dikkat `EnableRetries` parametresi ayarlanabilir ya da genel bir düzeyi (gösterildiği gibi *CommonParameters* bölümü) veya kişiye ait hizmetleri destekleyen `EnableRetries` (gösterildiği gibi *Hizmetleri*bölümü).</span><span class="sxs-lookup"><span data-stu-id="804e0-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="804e0-134">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesne bir Windows Workflow Foundation ana bilgisayar uygulaması bakın [iş akışı yapılandırma dosyalarını](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="804e0-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="804e0-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="804e0-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="804e0-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="804e0-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 <span data-ttu-id="804e0-137">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="804e0-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>  
 [<span data-ttu-id="804e0-138">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="804e0-138">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
