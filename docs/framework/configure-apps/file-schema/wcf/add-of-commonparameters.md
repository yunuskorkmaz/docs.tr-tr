---
title: <add> , <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 6aaba3f82966ad4496e6edaae06b5d7a8aef3863
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199491"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="5be50-102">\<Ekle >, \<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="5be50-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="5be50-103">Dünya çapında bir çok hizmette kullanılan parametreleri ad-değer çiftinin belirtir.</span><span class="sxs-lookup"><span data-stu-id="5be50-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="5be50-104">Genellikle bu parametre, dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5be50-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="5be50-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5be50-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5be50-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="5be50-106">\<behaviors></span></span>  
<span data-ttu-id="5be50-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5be50-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="5be50-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5be50-108">\<behavior></span></span>  
<span data-ttu-id="5be50-109">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="5be50-109">\<workflowRuntime></span></span>  
<span data-ttu-id="5be50-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="5be50-110">\<commonParameters></span></span>  
<span data-ttu-id="5be50-111">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5be50-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5be50-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5be50-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5be50-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5be50-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5be50-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5be50-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5be50-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5be50-115">Attributes</span></span>  
  
|<span data-ttu-id="5be50-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5be50-116">Attribute</span></span>|<span data-ttu-id="5be50-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5be50-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5be50-118">name</span><span class="sxs-lookup"><span data-stu-id="5be50-118">name</span></span>|<span data-ttu-id="5be50-119">Bir hizmet için belirtilen parametre adı.</span><span class="sxs-lookup"><span data-stu-id="5be50-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="5be50-120">value</span><span class="sxs-lookup"><span data-stu-id="5be50-120">value</span></span>|<span data-ttu-id="5be50-121">Bir hizmet için belirtilen parametre değeri.</span><span class="sxs-lookup"><span data-stu-id="5be50-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5be50-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5be50-122">Child Elements</span></span>  
 <span data-ttu-id="5be50-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="5be50-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5be50-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5be50-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5be50-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="5be50-125">Element</span></span>|<span data-ttu-id="5be50-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5be50-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5be50-127">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="5be50-127">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="5be50-128">Hizmetler tarafından kullanılan ortak parametreleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5be50-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="5be50-129">Bu koleksiyon genellikle dayanıklı hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5be50-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5be50-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5be50-130">Remarks</span></span>  
 <span data-ttu-id="5be50-131">`<commonParameters>` Öğesi, dünya çapında Örneğin çok hizmette kullanılan parametreleri tanımlar `ConnectionString` kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="5be50-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="5be50-132">İş işleme Hizmetleri için kalıcılığı mağazalarının gibi toplu işlemleri <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, bunları kendi işlemi kullanarak yeniden etkinleştirebilirsiniz `EnableRetries` aşağıdaki örnekte gösterildiği gibi parametre:</span><span class="sxs-lookup"><span data-stu-id="5be50-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="5be50-133">Dikkat `EnableRetries` parametresi ayarlanabilir ya da genel bir düzeyi (gösterildiği gibi *CommonParameters* bölümü) veya kişiye ait hizmetleri destekleyen `EnableRetries` (gösterildiği gibi *Hizmetleri*bölümü).</span><span class="sxs-lookup"><span data-stu-id="5be50-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="5be50-134">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesne bir Windows Workflow Foundation ana bilgisayar uygulaması bakın [iş akışı yapılandırma dosyalarını](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5be50-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5be50-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="5be50-135">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="5be50-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5be50-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [<span data-ttu-id="5be50-137">İş akışı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="5be50-137">Workflow Configuration Files</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [<span data-ttu-id="5be50-138">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="5be50-138">\<commonParameters></span></span>](commonparameters.md)
