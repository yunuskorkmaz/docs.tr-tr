---
title: "WorkflowIdentity ve sürüm oluşturma kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02620abf421256b53fb5919b39f441f7346a2e7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="53024-102">WorkflowIdentity ve sürüm oluşturma kullanma</span><span class="sxs-lookup"><span data-stu-id="53024-102">Using WorkflowIdentity and Versioning</span></span>
<span data-ttu-id="53024-103"><xref:System.Activities.WorkflowIdentity>İş akışı için bir ad ilişkilendirmek için uygulama geliştiricileri bir yol sağlar ve bir <xref:System.Version> bir iş akışı tanımıyla ve kalıcı iş akışı örneği ile ilişkili olması için bu bilgileri.</span><span class="sxs-lookup"><span data-stu-id="53024-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="53024-104">Bu kimlik bilgileri, iş akışı uygulama geliştiriciler tarafından birden çok iş akışı tanımı sürümlerinin yan yana yürütme gibi senaryoları etkinleştirmek için kullanılabilir ve dinamik güncelleştirme gibi diğer işlevleri için dönüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="53024-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="53024-105">Bu konuda kullanmanın genel sağlanır <xref:System.Activities.WorkflowIdentity> ile <xref:System.Activities.WorkflowApplication> barındırma.</span><span class="sxs-lookup"><span data-stu-id="53024-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="53024-106">Yan yana yürütme, bir iş akışı hizmetinde iş akışı tanımları hakkında daha fazla bilgi için bkz: [WorkflowServiceHost yan yana sürüm oluşturma](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="53024-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="53024-107">Dinamik güncelleştirme hakkında daha fazla bilgi için bkz: [dinamik güncelleştirme](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="53024-107">For information on dynamic update, see [Dynamic Update](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="53024-108">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="53024-108">In this topic</span></span>  
  
-   [<span data-ttu-id="53024-109">WorkflowIdentity kullanma</span><span class="sxs-lookup"><span data-stu-id="53024-109">Using WorkflowIdentity</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [<span data-ttu-id="53024-110">WorkflowIdentity kullanılarak yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="53024-110">Side-by-side Execution using WorkflowIdentity</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [<span data-ttu-id="53024-111">İş akışı sürüm desteklemek için .NET Framework 4 Kalıcılık veritabanlarını yükseltme</span><span class="sxs-lookup"><span data-stu-id="53024-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [<span data-ttu-id="53024-112">Veritabanı şeması yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="53024-112">To upgrade the database schema</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
##  <a name="UsingWorkflowIdentity"></a><span data-ttu-id="53024-113">WorkflowIdentity kullanma</span><span class="sxs-lookup"><span data-stu-id="53024-113">Using WorkflowIdentity</span></span>  
 <span data-ttu-id="53024-114">Kullanılacak <xref:System.Activities.WorkflowIdentity>, örnek oluşturmak, yapılandırın ve bu ilişkilendirmeyi bir <xref:System.Activities.WorkflowApplication> örneği.</span><span class="sxs-lookup"><span data-stu-id="53024-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="53024-115">A <xref:System.Activities.WorkflowIdentity> örneğini tanımlayan üç parça bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="53024-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="53024-116"><xref:System.Activities.WorkflowIdentity.Name%2A>ve <xref:System.Activities.WorkflowIdentity.Version%2A> içeren bir ad ve bir <xref:System.Version> ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer gibi bilgileri içeren ek bir dize istenen bilgileri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53024-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="53024-117">A <xref:System.Activities.WorkflowIdentity> üç özelliklerini birbirinden farklı olan benzersiz <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="53024-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="53024-118">A <xref:System.Activities.WorkflowIdentity> tüm kişisel bilgileri (PII) içermemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="53024-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="53024-119">Hakkında bilgi <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan örneğini etkinliğin birkaç farklı noktalarda Hizmetleri yaşam döngüsü yapılandırılmış tüm izleme için çalışma zamanı tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="53024-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="53024-120">İzleme WF PII (hassas kullanıcı verileri) gizlemek için herhangi bir mekanizma yok.</span><span class="sxs-lookup"><span data-stu-id="53024-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="53024-121">Bu nedenle, bir <xref:System.Activities.WorkflowIdentity> örneği içeremez herhangi bir PII veri kayıtları izleme içinde çalışma zamanı tarafından gösterilen ve izleme kayıtları görüntülemek için erişimi olan herkes tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="53024-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
 <span data-ttu-id="53024-122">Aşağıdaki örnekte, bir <xref:System.Activities.WorkflowIdentity> oluşturulur ve kullanılarak oluşturulan bir iş akışı örneğiyle ilişkili bir `MortgageWorkflow` iş akışı tanımı.</span><span class="sxs-lookup"><span data-stu-id="53024-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 <span data-ttu-id="53024-123">Yeniden yükleme ve bir iş akışını sürdürme bir <xref:System.Activities.WorkflowIdentity> eşleşecek şekilde yapılandırılmış <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneği kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53024-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="53024-124">Varsa <xref:System.Activities.WorkflowIdentity> iş akışı örneği yeniden yükleme işlemi kalıcı eşleşmediğinde kullanılan <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> atılır.</span><span class="sxs-lookup"><span data-stu-id="53024-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="53024-125">Aşağıdaki örnekte bir yük üzerinde girişimde `MortgageWorkflow` önceki örnekte kalıcı örneği.</span><span class="sxs-lookup"><span data-stu-id="53024-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="53024-126">Bu yükleme denemesi kullanılarak yapılan bir <xref:System.Activities.WorkflowIdentity> kalıcı örneği eşleşmiyor ev kredisi iş akışı, daha yeni bir sürümü için yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="53024-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="53024-127">Önceki kod zaman yürütülür, aşağıdaki <xref:System.Activities.VersionMismatchException> atılır.</span><span class="sxs-lookup"><span data-stu-id="53024-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>  
  
 <span data-ttu-id="53024-128">**WorkflowIdentity ('MortgageWorkflow v1; Sürüm 1.0.0.0' =) yüklenen örneğini WorkflowIdentity eşleşmiyor ('MortgageWorkflow v2; Sürüm 2.0.0.0' =) sağlanan iş akışı tanımı. Örneği farklı bir tanımı kullanılarak yüklenebilir veya dinamik güncelleştirme kullanma güncelleştirildi.**</span><span class="sxs-lookup"><span data-stu-id="53024-128">**The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.**</span></span>  
###  <a name="SxS"></a><span data-ttu-id="53024-129">WorkflowIdentity kullanılarak yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="53024-129">Side-by-side Execution using WorkflowIdentity</span></span>  
 <span data-ttu-id="53024-130"><xref:System.Activities.WorkflowIdentity>birden fazla sürümünü bir iş akışı yan yana yürütme kolaylaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53024-130"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="53024-131">Yaygın bir senaryo, bir uzun süre çalışan iş akışı iş gereksinimlerine değiştiriyor.</span><span class="sxs-lookup"><span data-stu-id="53024-131">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="53024-132">Güncelleştirilmiş bir sürümünü dağıtıldığında birçok iş akışı örneği çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="53024-132">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="53024-133">Ana bilgisayar uygulaması, güncelleştirilmiş iş akışı tanımını yeni örnekleri başlatırken kullanmak üzere yapılandırılabilir ve örnekleri edilirken doğru iş akışı tanımı sağlamak için konak uygulamanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="53024-133">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="53024-134"><xref:System.Activities.WorkflowIdentity>tanımlamak ve iş akışı örnekleri sürdürme eşleşen iş akışı tanımı sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53024-134"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>  
  
 <span data-ttu-id="53024-135">Alınacak <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneğinin <xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53024-135">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="53024-136"><xref:System.Activities.WorkflowApplication.GetInstance%2A> Yöntemi alır <xref:System.Activities.WorkflowApplication.Id%2A> kalıcı iş akışı örneğinin ve <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kalıcı örneği içerir ve döndüren bir <xref:System.Activities.WorkflowApplicationInstance>.</span><span class="sxs-lookup"><span data-stu-id="53024-136">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="53024-137">A <xref:System.Activities.WorkflowApplicationInstance> , ilişkili dahil olmak üzere bir kalıcı iş akışı örneği hakkında bilgi içeren <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="53024-137">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="53024-138">Bu ilişkili <xref:System.Activities.WorkflowIdentity> yükleme ve iş akışı örneği sürdürme doğru iş akışı tanımı sağlamak için ana bilgisayar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="53024-138">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53024-139">Bir null <xref:System.Activities.WorkflowIdentity> geçerli olduğundan ve ilişkili olmadan kalıcı örnekleri eşlemek için ana bilgisayar tarafından kullanılan <xref:System.Activities.WorkflowIdentity> uygun iş akışı tanımı.</span><span class="sxs-lookup"><span data-stu-id="53024-139">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="53024-140">Bu senaryo, iş akışı sürüm oluşturma iş akışı uygulaması başlangıçta yazılmadı veya uygulamanın gelen yükseltildiğinde ortaya çıkabilir [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53024-140">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="53024-141">[İş akışı sürüm desteklemek için .NET Framework 4 Kalıcılık veritabanlarını yükseltme](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="53024-141"> [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>  
  
 <span data-ttu-id="53024-142">Aşağıdaki örnekte bir `Dictionary<WorkflowIdentity, Activity>` ilişkilendirmek için kullanılan <xref:System.Activities.WorkflowIdentity> örnekleriyle eşleşen iş akışı tanımları ve iş akışı kullanarak başlatıldığından `MortgageWorkflow` ile ilişkili iş akışı tanımı `identityV1` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="53024-142">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowIdentity identityV2 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v2",  
    Version = new Version(2, 0, 0, 0)  
};  
  
Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();  
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());  
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 <span data-ttu-id="53024-143">Aşağıdaki örnekte, çağırarak önceki örnekten kalıcı iş akışı örneğiyle ilgili bilgiler alınır <xref:System.Activities.WorkflowApplication.GetInstance%2A>ve kalıcı <xref:System.Activities.WorkflowIdentity> bilgi eşleşen iş akışı tanımı almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53024-143">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="53024-144">Bu bilgileri yapılandırmak için kullanılan <xref:System.Activities.WorkflowApplication>, ve ardından iş akışını yüklenir.</span><span class="sxs-lookup"><span data-stu-id="53024-144">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="53024-145">Çünkü unutmayın <xref:System.Activities.WorkflowApplication.Load%2A> alan aşırı <xref:System.Activities.WorkflowApplicationInstance> kullanılan <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> üzerinde yapılandırılmışsa <xref:System.Activities.WorkflowApplicationInstance> tarafından kullanılan <xref:System.Activities.WorkflowApplication> ve bu nedenle, <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği yapılandırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="53024-145">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53024-146">Varsa <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği ayarlanmışsa, onu aynı ayarlanmalıdır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> örneği tarafından kullanılan <xref:System.Activities.WorkflowApplicationInstance> veya başka bir <xref:System.ArgumentException> aşağıdaki iletiyle oluşturulacaktır: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span><span class="sxs-lookup"><span data-stu-id="53024-146">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>  
  
```csharp  
// Get the WorkflowApplicationInstance of the desired workflow from the specified  
// SqlWorkflowInstanceStore.  
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);  
  
// Use the persisted WorkflowIdentity to retrieve the correct workflow  
// definition from the dictionary.  
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];  
  
WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(instance);  
  
// Resume the workflow...  
```  
  
##  <a name="UpdatingWF4PersistenceDatabases"></a><span data-ttu-id="53024-147">İş akışı sürüm desteklemek için .NET Framework 4 Kalıcılık veritabanlarını yükseltme</span><span class="sxs-lookup"><span data-stu-id="53024-147">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>  
 <span data-ttu-id="53024-148">SqlWorkflowInstanceStoreSchemaUpgrade.sql veritabanı komut dosyası kullanılarak oluşturulan Kalıcılık veritabanları yükseltmek için sağlanan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] veritabanı komut dosyaları.</span><span class="sxs-lookup"><span data-stu-id="53024-148">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] database scripts.</span></span> <span data-ttu-id="53024-149">Bu komut dosyası içinde sunulan yeni sürüm özelliklerini desteklemek için veritabanlarını güncelleştirmeleri [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53024-149">This script updates the databases to support the new versioning capabilities introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="53024-150">Hiç kalıcı iş akışı örneği veritabanlarında varsayılan sürüm değerleri verilir ve yan yana yürütme ve dinamik güncelleştirme yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="53024-150">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>  
  
 <span data-ttu-id="53024-151">Varsa bir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] iş akışı uygulama verilen betiği kullanarak yükseltilmemiş bir Kalıcılık veritabanı üzerinde yeni sürüm özelliklerini kullanma herhangi bir Kalıcılık işlem çalışır bir <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> aşağıdakine benzer bir ileti ile oluşturulur İleti.</span><span class="sxs-lookup"><span data-stu-id="53024-151">If a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>  
  
 <span data-ttu-id="53024-152">**SqlWorkflowInstanceStore '4.0.0.0' veritabanı sürümü vardır. Bu veritabanı sürümü karşı InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' çalıştırılamıyor.  Lütfen '4.5.0.0' veritabanına yükseltin.**</span><span class="sxs-lookup"><span data-stu-id="53024-152">**The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.**</span></span>  
###  <a name="ToUpgrade"></a><span data-ttu-id="53024-153">Veritabanı şeması yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="53024-153">To upgrade the database schema</span></span>  
  
1.  <span data-ttu-id="53024-154">SQL Server Management Studio'yu açın ve kalıcılığı veritabanı sunucusuna, örneğin bağlanın **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="53024-154">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>  
  
2.  <span data-ttu-id="53024-155">Seçin **açık**, **dosya** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="53024-155">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="53024-156">Aşağıdaki klasöre göz atın:`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="53024-156">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span></span>  
  
3.  <span data-ttu-id="53024-157">Seçin **SqlWorkflowInstanceStoreSchemaUpgrade.sql** tıklatıp **açık**.</span><span class="sxs-lookup"><span data-stu-id="53024-157">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>  
  
4.  <span data-ttu-id="53024-158">Kalıcılık veritabanında adını seçin **kullanılabilir veritabanları** açılır.</span><span class="sxs-lookup"><span data-stu-id="53024-158">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>  
  
5.  <span data-ttu-id="53024-159">Seçin **yürütme** gelen **sorgu** menüsü.</span><span class="sxs-lookup"><span data-stu-id="53024-159">Choose **Execute** from the **Query** menu.</span></span>  
  
 <span data-ttu-id="53024-160">Sorgu tamamladığında, veritabanı şeması yükseltilir ve isterseniz, kalıcı iş akışı örnekleri için atanmış varsayılan iş akışı kimliği görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53024-160">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="53024-161">Kalıcılık veritabanınızda genişletin **veritabanları** düğümünün **Object Explorer**, genişletin ve ardından **görünümleri** düğümü.</span><span class="sxs-lookup"><span data-stu-id="53024-161">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="53024-162">Sağ **System.Activities.DurableInstancing.Instances** ve **ilk 1000 satırı Seç**.</span><span class="sxs-lookup"><span data-stu-id="53024-162">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="53024-163">Sütunları sonuna kaydırın ve görünümüne eklenen altı ek sütunlar olduğuna dikkat edin: **IdentityName**, **IdentityPackage**, **yapı**, **önemli** , **Küçük**, ve **düzeltme**.</span><span class="sxs-lookup"><span data-stu-id="53024-163">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="53024-164">Kalıcı bir iş akışı bir değeri olur **NULL** bu alanları için null iş akışı kimliği temsil eden.</span><span class="sxs-lookup"><span data-stu-id="53024-164">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
