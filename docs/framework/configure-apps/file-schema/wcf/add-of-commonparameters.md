---
title: <add> / <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400673"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="d8ddf-102">\<add> / \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="d8ddf-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="d8ddf-103">Birden çok hizmet arasında genel olarak kullanılan parametrelerin ad-değer çiftini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="d8ddf-104">Genellikle bu parametre, dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d8ddf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8ddf-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8ddf-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8ddf-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d8ddf-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8ddf-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d8ddf-108">Attributes</span></span>  
  
|<span data-ttu-id="d8ddf-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d8ddf-109">Attribute</span></span>|<span data-ttu-id="d8ddf-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8ddf-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8ddf-111">name</span><span class="sxs-lookup"><span data-stu-id="d8ddf-111">name</span></span>|<span data-ttu-id="d8ddf-112">Bir hizmet için belirtilen parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-112">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="d8ddf-113">value</span><span class="sxs-lookup"><span data-stu-id="d8ddf-113">value</span></span>|<span data-ttu-id="d8ddf-114">Bir hizmet için belirtilen parametrenin değeri.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-114">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8ddf-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8ddf-115">Child Elements</span></span>  
 <span data-ttu-id="d8ddf-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8ddf-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d8ddf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d8ddf-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d8ddf-118">Element</span></span>|<span data-ttu-id="d8ddf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8ddf-119">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="d8ddf-120">Hizmetler tarafından kullanılan ortak parametrelerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-120">A collection of common parameters used by services.</span></span> <span data-ttu-id="d8ddf-121">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-121">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8ddf-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8ddf-122">Remarks</span></span>  
 <span data-ttu-id="d8ddf-123">`<commonParameters>`Öğesi, ' yi kullanırken, birden çok hizmet arasında genel olarak kullanılan tüm parametreleri tanımlar `ConnectionString` <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="d8ddf-123">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="d8ddf-124">Ve gibi, kalıcılık depolarına iş toplu işleri uygulayan hizmetler için <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , `EnableRetries` Aşağıdaki örnekte gösterildiği gibi, parametresini kullanarak işlemini yeniden denemesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d8ddf-124">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="d8ddf-125">`EnableRetries`Parametrenin genel düzeyde ( *CommonParameters* bölümünde gösterildiği gibi) ya da tarafından desteklenen bireysel hizmetlerden `EnableRetries` ( *Hizmetler* bölümünde gösterildiği gibi) ayarlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-125">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="d8ddf-126">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için <xref:System.Workflow.Runtime.WorkflowRuntime> bkz. [Iş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d8ddf-126">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8ddf-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8ddf-127">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="d8ddf-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ddf-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="d8ddf-129">[İş akışı yapılandırma dosyaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d8ddf-129">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
