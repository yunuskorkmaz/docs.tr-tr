---
title: WorkflowIdentity Kullanma ve Sürüm Oluşturma
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 66ef4fed682554d9fab2a7b0f85bb9cfaf8e8a29
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74142040"
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="ff2f6-102">WorkflowIdentity Kullanma ve Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff2f6-102">Using WorkflowIdentity and Versioning</span></span>

<span data-ttu-id="ff2f6-103"><xref:System.Activities.WorkflowIdentity>, iş akışı uygulama geliştiricilerinin bir ad ve bir <xref:System.Version> iş akışı tanımıyla ilişkilendirilmesi ve bu bilgilerin kalıcı bir iş akışı örneğiyle ilişkilendirilmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="ff2f6-104">Bu kimlik bilgileri, bir iş akışı tanımının birden çok sürümünün yan yana yürütülmesi gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevler için de temel pulu sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="ff2f6-105">Bu konu, <xref:System.Activities.WorkflowApplication> barındırma ile <xref:System.Activities.WorkflowIdentity> kullanımı hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="ff2f6-106">Bir iş akışı hizmetindeki iş akışı tanımlarının yan yana yürütülmesi hakkında daha fazla bilgi için bkz. [WorkflowServiceHost 'Da yan yana sürüm oluşturma](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="ff2f6-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="ff2f6-107">Dinamik güncelleştirme hakkında bilgi için bkz. [dinamik güncelleştirme](dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="ff2f6-107">For information on dynamic update, see [Dynamic Update](dynamic-update.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="ff2f6-108">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="ff2f6-108">In this topic</span></span>

- [<span data-ttu-id="ff2f6-109">WorkflowIdentity kullanma</span><span class="sxs-lookup"><span data-stu-id="ff2f6-109">Using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [<span data-ttu-id="ff2f6-110">WorkflowIdentity kullanarak yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="ff2f6-110">Side-by-side Execution using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#SxS)

- [<span data-ttu-id="ff2f6-111">.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme</span><span class="sxs-lookup"><span data-stu-id="ff2f6-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [<span data-ttu-id="ff2f6-112">Veritabanı şemasını yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="ff2f6-112">To upgrade the database schema</span></span>](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="UsingWorkflowIdentity"></a><span data-ttu-id="ff2f6-113">WorkflowIdentity kullanma</span><span class="sxs-lookup"><span data-stu-id="ff2f6-113">Using WorkflowIdentity</span></span>

<span data-ttu-id="ff2f6-114"><xref:System.Activities.WorkflowIdentity>kullanmak için bir örnek oluşturun, yapılandırın ve bir <xref:System.Activities.WorkflowApplication> örneğiyle ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="ff2f6-115"><xref:System.Activities.WorkflowIdentity> örnek, üç tanımlayıcı bilgi parçasını içerir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="ff2f6-116"><xref:System.Activities.WorkflowIdentity.Name%2A> ve <xref:System.Activities.WorkflowIdentity.Version%2A> bir ad ve <xref:System.Version> içerir ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="ff2f6-117"><xref:System.Activities.WorkflowIdentity>, üç özelliklerinden herhangi biri başka bir <xref:System.Activities.WorkflowIdentity>farklıysa benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff2f6-118"><xref:System.Activities.WorkflowIdentity>, kişisel olarak tanımlanabilen bilgileri (PII) içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="ff2f6-119">Örnek oluşturmak için kullanılan <xref:System.Activities.WorkflowIdentity> hakkındaki bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="ff2f6-120">WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="ff2f6-121">Bu nedenle, <xref:System.Activities.WorkflowIdentity> bir örnek, kayıtları izlemedeki çalışma zamanı tarafından yayınlandığından PII verileri içermemelidir ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>

<span data-ttu-id="ff2f6-122">Aşağıdaki örnekte, bir <xref:System.Activities.WorkflowIdentity> oluşturulur ve bir `MortgageWorkflow` iş akışı tanımı kullanılarak oluşturulan iş akışı örneğiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>

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

<span data-ttu-id="ff2f6-123">Bir iş akışını yeniden yüklerken ve sürdürülürken, kalıcı iş akışı örneğinin <xref:System.Activities.WorkflowIdentity> eşleşecek şekilde yapılandırılan bir <xref:System.Activities.WorkflowIdentity> kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="ff2f6-124">İş akışı örneğini yeniden yüklerken kullanılan <xref:System.Activities.WorkflowIdentity> kalıcı <xref:System.Activities.WorkflowIdentity>eşleşmediğinden, bir <xref:System.Activities.VersionMismatchException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="ff2f6-125">Aşağıdaki örnekte, önceki örnekte kalıcı olan `MortgageWorkflow` örneğinde bir yükleme denemesi yapılır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="ff2f6-126">Bu yükleme denemesi, kalıcı örnekle eşleşmeyen ipotek iş akışının daha yeni bir sürümü için yapılandırılmış bir <xref:System.Activities.WorkflowIdentity> kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="ff2f6-127">Önceki kod yürütüldüğünde, aşağıdaki <xref:System.Activities.VersionMismatchException> atılır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>

```
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="SxS"></a><span data-ttu-id="ff2f6-128">WorkflowIdentity kullanarak yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="ff2f6-128">Side-by-side Execution using WorkflowIdentity</span></span>

<span data-ttu-id="ff2f6-129"><xref:System.Activities.WorkflowIdentity>, bir iş akışının birden çok sürümünün bir yandan çalışmasını kolaylaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-129"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="ff2f6-130">Tek bir yaygın senaryo, uzun süreli bir iş akışında iş gereksinimlerini değiştiriyor.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-130">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="ff2f6-131">Bir iş akışının birçok örneği, güncelleştirilmiş bir sürüm dağıtıldığında çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-131">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="ff2f6-132">Konak uygulaması, yeni örnekleri başlatırken güncelleştirilmiş iş akışı tanımını kullanacak şekilde yapılandırılabilir ve örnek olarak, örneklere devam edilirken doğru iş akışı tanımını sağlamak için ana bilgisayar uygulamasının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-132">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="ff2f6-133"><xref:System.Activities.WorkflowIdentity>, iş akışı örneklerine devam edilirken eşleşen iş akışı tanımını tanımlamak ve sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-133"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>

<span data-ttu-id="ff2f6-134">Kalıcı bir iş akışı örneğinin <xref:System.Activities.WorkflowIdentity> almak için, <xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-134">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="ff2f6-135"><xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi, kalıcı iş akışı örneği ve kalıcı örneği içeren <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> <xref:System.Activities.WorkflowApplication.Id%2A> alır ve bir <xref:System.Activities.WorkflowApplicationInstance>döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-135">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="ff2f6-136"><xref:System.Activities.WorkflowApplicationInstance>, ilişkili <xref:System.Activities.WorkflowIdentity>dahil olmak üzere kalıcı bir iş akışı örneğiyle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-136">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="ff2f6-137">Bu ilişkili <xref:System.Activities.WorkflowIdentity>, iş akışı örneğini yüklerken ve sürdürülürken doğru iş akışı tanımını sağlamak için ana bilgisayar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-137">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>

> [!NOTE]
> <span data-ttu-id="ff2f6-138">Null <xref:System.Activities.WorkflowIdentity> geçerlidir ve konak tarafından uygun iş akışı tanımına ilişkili <xref:System.Activities.WorkflowIdentity> olmadan kalıcı olan örnekleri eşlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-138">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="ff2f6-139">Bu senaryo, bir iş akışı uygulamasının ilk olarak iş akışı sürümü oluşturma ile yazılmayan veya bir uygulama .NET Framework 4 ' ten yükseltildiğinde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-139">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from .NET Framework 4.</span></span> <span data-ttu-id="ff2f6-140">Daha fazla bilgi için bkz. [Iş akışı sürümü oluşturmayı desteklemek için .NET Framework 4 kalıcılık veritabanlarını yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="ff2f6-140">For more information, see [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>

<span data-ttu-id="ff2f6-141">Aşağıdaki örnekte, <xref:System.Activities.WorkflowIdentity> örneklerinin eşleşen iş akışı tanımlarıyla ilişkilendirilmesi için `Dictionary<WorkflowIdentity, Activity>` kullanılır ve bir iş akışı, `identityV1` <xref:System.Activities.WorkflowIdentity>ilişkili `MortgageWorkflow` iş akışı tanımı kullanılarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-141">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>

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

<span data-ttu-id="ff2f6-142">Aşağıdaki örnekte, önceki örnekteki kalıcı iş akışı örneğiyle ilgili bilgiler <xref:System.Activities.WorkflowApplication.GetInstance%2A>çağırarak alınır ve kalıcı <xref:System.Activities.WorkflowIdentity> bilgileri eşleşen iş akışı tanımını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-142">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="ff2f6-143">Bu bilgiler <xref:System.Activities.WorkflowApplication>yapılandırmak için kullanılır ve sonra iş akışı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-143">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="ff2f6-144"><xref:System.Activities.WorkflowApplicationInstance> alan <xref:System.Activities.WorkflowApplication.Load%2A> aşırı yüklemesinin kullanıldığı, <xref:System.Activities.WorkflowApplicationInstance> üzerinde yapılandırılan <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> <xref:System.Activities.WorkflowApplication> tarafından kullanıldığı ve bu nedenle <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliğinin yapılandırılmasına gerek olmadığı unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-144">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>

> [!NOTE]
> <span data-ttu-id="ff2f6-145"><xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği ayarlandıysa, <xref:System.Activities.WorkflowApplicationInstance> tarafından kullanılan aynı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> örneği ile ayarlanması gerekir, aksi takdirde şu iletiyle birlikte bir <xref:System.ArgumentException> atılır: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-145">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>

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

## <a name="UpdatingWF4PersistenceDatabases"></a><span data-ttu-id="ff2f6-146">.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme</span><span class="sxs-lookup"><span data-stu-id="ff2f6-146">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>

<span data-ttu-id="ff2f6-147">.NET Framework 4 veritabanı betikleri kullanılarak oluşturulan kalıcı veritabanlarını yükseltmek için bir SqlWorkflowInstanceStoreSchemaUpgrade. SQL veritabanı betiği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-147">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the .NET Framework 4 database scripts.</span></span> <span data-ttu-id="ff2f6-148">Bu betik, .NET Framework 4,5 ' de tanıtılan yeni sürüm oluşturma yeteneklerini destekleyecek şekilde veritabanlarını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-148">This script updates the databases to support the new versioning capabilities introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="ff2f6-149">Veritabanlarındaki kalıcı iş akışı örneklerine varsayılan sürüm oluşturma değerleri verilir ve daha sonra yan yana yürütmeye ve Dinamik güncelleştirmeye katılabilirler.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-149">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>

<span data-ttu-id="ff2f6-150">.NET Framework 4,5 iş akışı uygulaması, sunulan betiği kullanılarak yükseltilmemiş bir kalıcılık veritabanında yeni sürüm oluşturma özelliklerini kullanan herhangi bir kalıcılık işlemini denerse, aşağıdaki iletiye benzer bir ileti içeren bir <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-150">If a .NET Framework 4.5 workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>

```
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="ToUpgrade"></a><span data-ttu-id="ff2f6-151">Veritabanı şemasını yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="ff2f6-151">To upgrade the database schema</span></span>

1. <span data-ttu-id="ff2f6-152">SQL Server Management Studio açın ve Kalıcılık veritabanı sunucusuna bağlanın, örneğin **.\Sqlexpress**.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-152">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>

2. <span data-ttu-id="ff2f6-153">**Dosya** menüsünden **Aç**, **Dosya** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-153">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="ff2f6-154">Şu klasöre gidin: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="ff2f6-154">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span></span>

3. <span data-ttu-id="ff2f6-155">**SqlWorkflowInstanceStoreSchemaUpgrade. SQL** ' i seçin ve **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-155">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>

4. <span data-ttu-id="ff2f6-156">**Kullanılabilir veritabanları** açılan listesinden Kalıcılık veritabanının adını seçin.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-156">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>

5. <span data-ttu-id="ff2f6-157">**Sorgu** menüsünden **Yürüt** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-157">Choose **Execute** from the **Query** menu.</span></span>

<span data-ttu-id="ff2f6-158">Sorgu tamamlandığında, veritabanı şeması yükseltilir ve isterseniz, kalıcı iş akışı örneklerine atanmış olan varsayılan iş akışı kimliğini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-158">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="ff2f6-159">**Nesne Gezgini** **veritabanları** düğümünde Kalıcılık veritabanınızı genişletin ve ardından **Görünümler** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-159">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="ff2f6-160">**System. Activities. Durableörnek oluşturma. örnekleri** öğesine sağ tıklayın ve **en üstteki 1000 satırları Seç**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-160">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="ff2f6-161">Sütunların sonuna kaydırın ve görünüme eklenen altı sütun ( **IdentityName**, **IdentityPackage**, **Build**, **ana**, **Minor**ve **Düzeltme**) olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-161">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="ff2f6-162">Kalıcı iş akışlarının, null bir iş akışı kimliğini temsil eden bu alanlar için **null** değeri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ff2f6-162">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
