---
title: '&lt;commonParameters&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef23ba0fa39b01a7cf55c8b2b6cb0beb20be8631
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a><span data-ttu-id="1e0b7-102">&lt;commonParameters&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="1e0b7-102">&lt;add&gt; of &lt;commonParameters&gt;</span></span>
<span data-ttu-id="1e0b7-103">Bir ad-değer çifti birden fazla hizmet genel olarak kullanılan parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="1e0b7-104">Bu parametre genellikle sürekli hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="1e0b7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1e0b7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1e0b7-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="1e0b7-106">\<behaviors></span></span>  
<span data-ttu-id="1e0b7-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1e0b7-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="1e0b7-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1e0b7-108">\<behavior></span></span>  
<span data-ttu-id="1e0b7-109">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="1e0b7-109">\<workflowRuntime></span></span>  
<span data-ttu-id="1e0b7-110">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="1e0b7-110">\<commonParameters></span></span>  
<span data-ttu-id="1e0b7-111">\<add></span><span class="sxs-lookup"><span data-stu-id="1e0b7-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e0b7-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e0b7-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e0b7-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e0b7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1e0b7-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e0b7-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1e0b7-115">Attributes</span></span>  
  
|<span data-ttu-id="1e0b7-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1e0b7-116">Attribute</span></span>|<span data-ttu-id="1e0b7-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e0b7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e0b7-118">name</span><span class="sxs-lookup"><span data-stu-id="1e0b7-118">name</span></span>|<span data-ttu-id="1e0b7-119">Bir hizmet için belirtilen parametre adı.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="1e0b7-120">value</span><span class="sxs-lookup"><span data-stu-id="1e0b7-120">value</span></span>|<span data-ttu-id="1e0b7-121">Bir hizmet için belirtilen parametre değeri.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e0b7-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e0b7-122">Child Elements</span></span>  
 <span data-ttu-id="1e0b7-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e0b7-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e0b7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1e0b7-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e0b7-125">Element</span></span>|<span data-ttu-id="1e0b7-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e0b7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e0b7-127">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="1e0b7-127">\<commonParameters></span></span>](http://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|<span data-ttu-id="1e0b7-128">Hizmetler tarafından kullanılan ortak parametreleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="1e0b7-129">Bu koleksiyon genellikle sürekli hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e0b7-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e0b7-130">Remarks</span></span>  
 <span data-ttu-id="1e0b7-131">`<commonParameters>` Öğesi genel olarak birden fazla hizmet, örneğin kullanılan parametreleri tanımlar `ConnectionString` kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="1e0b7-132">İş yürütme Hizmetleri için Kalıcılık depolarına gibi toplu iş <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, kendi işlem kullanarak yeniden etkinleştirebilirsiniz `EnableRetries` aşağıdaki örnekte gösterildiği gibi parametre:</span><span class="sxs-lookup"><span data-stu-id="1e0b7-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="1e0b7-133">Dikkat `EnableRetries` parametresi ayarlanabilir da genel düzeyde (gösterildiği gibi *CommonParameters* bölüm) veya bireysel destekleyen Hizmetler `EnableRetries` (gösterildiği gibi *Hizmetleri*bölümü).</span><span class="sxs-lookup"><span data-stu-id="1e0b7-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="1e0b7-134">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesi bir Windows Workflow Foundation ana bilgisayar uygulamasının bkz [iş akışı yapılandırma dosyalarını](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="1e0b7-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e0b7-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e0b7-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e0b7-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e0b7-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="1e0b7-137">İş akışı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="1e0b7-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="1e0b7-138">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="1e0b7-138">\<commonParameters></span></span>](http://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
