---
title: <add> / <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400673"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="d9213-102">\<\<CommonParameters > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="d9213-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="d9213-103">Birden çok hizmet arasında genel olarak kullanılan parametrelerin ad-değer çiftini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9213-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="d9213-104">Genellikle bu parametre, dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d9213-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="d9213-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d9213-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d9213-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d9213-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d9213-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9213-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="d9213-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9213-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="d9213-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9213-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="d9213-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowRuntime >** ](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="d9213-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="d9213-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<commonParameters >** ](commonparameters.md)</span><span class="sxs-lookup"><span data-stu-id="d9213-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)</span></span>\
<span data-ttu-id="d9213-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="d9213-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9213-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9213-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9213-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9213-114">Attributes and Elements</span></span>  
 <span data-ttu-id="d9213-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9213-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9213-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9213-116">Attributes</span></span>  
  
|<span data-ttu-id="d9213-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d9213-117">Attribute</span></span>|<span data-ttu-id="d9213-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9213-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9213-119">name</span><span class="sxs-lookup"><span data-stu-id="d9213-119">name</span></span>|<span data-ttu-id="d9213-120">Bir hizmet için belirtilen parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="d9213-120">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="d9213-121">value</span><span class="sxs-lookup"><span data-stu-id="d9213-121">value</span></span>|<span data-ttu-id="d9213-122">Bir hizmet için belirtilen parametrenin değeri.</span><span class="sxs-lookup"><span data-stu-id="d9213-122">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9213-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9213-123">Child Elements</span></span>  
 <span data-ttu-id="d9213-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9213-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9213-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9213-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d9213-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9213-126">Element</span></span>|<span data-ttu-id="d9213-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9213-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9213-128">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="d9213-128">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="d9213-129">Hizmetler tarafından kullanılan ortak parametrelerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d9213-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="d9213-130">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d9213-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9213-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9213-131">Remarks</span></span>  
 <span data-ttu-id="d9213-132">Öğesi, ' yi kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>, `ConnectionString` birden çok hizmet arasında genel olarak kullanılan tüm parametreleri tanımlar. `<commonParameters>`</span><span class="sxs-lookup"><span data-stu-id="d9213-132">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="d9213-133"><xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> Ve `EnableRetries` gibi, kalıcılık depolarına iş toplu işleri uygulayan hizmetler için, aşağıdaki örnekte gösterildiği gibi, parametresini kullanarak işlemini yeniden denemesini sağlayabilirsiniz: <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService></span><span class="sxs-lookup"><span data-stu-id="d9213-133">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="d9213-134">Parametrenin genel düzeyde ( *CommonParameters* bölümünde gösterildiği gibi) ya da tarafından desteklenen `EnableRetries` bireysel hizmetlerden ( *Hizmetler* bölümünde gösterildiği gibi) ayarlandığına dikkat edin. `EnableRetries`</span><span class="sxs-lookup"><span data-stu-id="d9213-134">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="d9213-135">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için bkz. [iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d9213-135">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9213-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9213-136">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="d9213-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9213-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="d9213-138">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d9213-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="d9213-139">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="d9213-139">\<commonParameters></span></span>](commonparameters.md)
