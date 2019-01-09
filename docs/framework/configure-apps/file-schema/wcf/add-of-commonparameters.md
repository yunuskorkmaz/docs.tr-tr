---
title: '&lt;commonParameters&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 431a4b6a58a0c2d2ecd6c448e05e7f2104dd10ed
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145204"
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a><span data-ttu-id="27ca2-102">&lt;commonParameters&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="27ca2-102">&lt;add&gt; of &lt;commonParameters&gt;</span></span>
<span data-ttu-id="27ca2-103">Dünya çapında bir çok hizmette kullanılan parametreleri ad-değer çiftinin belirtir.</span><span class="sxs-lookup"><span data-stu-id="27ca2-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="27ca2-104">Genellikle bu parametre, dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="27ca2-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="27ca2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="27ca2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="27ca2-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="27ca2-106">\<behaviors></span></span>  
<span data-ttu-id="27ca2-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="27ca2-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="27ca2-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="27ca2-108">\<behavior></span></span>  
<span data-ttu-id="27ca2-109">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="27ca2-109">\<workflowRuntime></span></span>  
<span data-ttu-id="27ca2-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="27ca2-110">\<commonParameters></span></span>  
<span data-ttu-id="27ca2-111">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="27ca2-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27ca2-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27ca2-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27ca2-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27ca2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="27ca2-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27ca2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27ca2-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27ca2-115">Attributes</span></span>  
  
|<span data-ttu-id="27ca2-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27ca2-116">Attribute</span></span>|<span data-ttu-id="27ca2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27ca2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27ca2-118">name</span><span class="sxs-lookup"><span data-stu-id="27ca2-118">name</span></span>|<span data-ttu-id="27ca2-119">Bir hizmet için belirtilen parametre adı.</span><span class="sxs-lookup"><span data-stu-id="27ca2-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="27ca2-120">value</span><span class="sxs-lookup"><span data-stu-id="27ca2-120">value</span></span>|<span data-ttu-id="27ca2-121">Bir hizmet için belirtilen parametre değeri.</span><span class="sxs-lookup"><span data-stu-id="27ca2-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27ca2-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27ca2-122">Child Elements</span></span>  
 <span data-ttu-id="27ca2-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="27ca2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27ca2-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27ca2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="27ca2-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="27ca2-125">Element</span></span>|<span data-ttu-id="27ca2-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27ca2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27ca2-127">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="27ca2-127">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|<span data-ttu-id="27ca2-128">Hizmetler tarafından kullanılan ortak parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="27ca2-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="27ca2-129">Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="27ca2-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27ca2-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27ca2-130">Remarks</span></span>  
 <span data-ttu-id="27ca2-131">`<commonParameters>` Öğesi, dünya çapında Örneğin çok hizmette kullanılan parametreleri tanımlar `ConnectionString` kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="27ca2-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="27ca2-132">İş işleme Hizmetleri için kalıcılığı mağazalarının gibi toplu işlemleri <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, bunları kendi işlemi kullanarak yeniden etkinleştirebilirsiniz `EnableRetries` aşağıdaki örnekte gösterildiği gibi parametre:</span><span class="sxs-lookup"><span data-stu-id="27ca2-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="27ca2-133">Dikkat `EnableRetries` parametresi ayarlanabilir ya da genel bir düzeyi (gösterildiği gibi *CommonParameters* bölümü) veya kişiye ait hizmetleri destekleyen `EnableRetries` (gösterildiği gibi *Hizmetleri*bölümü).</span><span class="sxs-lookup"><span data-stu-id="27ca2-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="27ca2-134">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesne bir Windows Workflow Foundation ana bilgisayar uygulaması bakın [iş akışı yapılandırma dosyalarını](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="27ca2-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27ca2-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="27ca2-135">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="27ca2-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27ca2-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 <span data-ttu-id="27ca2-137">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="27ca2-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>  
 [<span data-ttu-id="27ca2-138">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="27ca2-138">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
