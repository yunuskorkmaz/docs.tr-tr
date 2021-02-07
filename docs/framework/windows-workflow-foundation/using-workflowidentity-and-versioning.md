---
description: 'Hakkında daha fazla bilgi edinin: WorkflowIdentity kullanma ve sürüm oluşturma'
title: WorkflowIdentity Kullanma ve Sürüm Oluşturma
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: b51bce26b69d77e0be702e40a315dcd138d2fc03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754972"
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="d5e61-103">WorkflowIdentity Kullanma ve Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5e61-103">Using WorkflowIdentity and Versioning</span></span>

<span data-ttu-id="d5e61-104"><xref:System.Activities.WorkflowIdentity> , iş akışı uygulama geliştiricilerinin bir adı ve <xref:System.Version> ile bir iş akışı tanımıyla ilişkilendirilmesi ve bu bilgilerin kalıcı bir iş akışı örneğiyle ilişkilendirilmesi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5e61-104"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="d5e61-105">Bu kimlik bilgileri, bir iş akışı tanımının birden çok sürümünün yan yana yürütülmesi gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevler için de temel pulu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5e61-105">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="d5e61-106">Bu konu, barındırma ile kullanmayla ilgili genel bakış sağlar <xref:System.Activities.WorkflowIdentity> <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="d5e61-106">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="d5e61-107">Bir iş akışı hizmetindeki iş akışı tanımlarının yan yana yürütülmesi hakkında daha fazla bilgi için bkz. [WorkflowServiceHost 'Da yan yana sürüm oluşturma](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="d5e61-107">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="d5e61-108">Dinamik güncelleştirme hakkında bilgi için bkz. [dinamik güncelleştirme](dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="d5e61-108">For information on dynamic update, see [Dynamic Update](dynamic-update.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="d5e61-109">Bu konuda</span><span class="sxs-lookup"><span data-stu-id="d5e61-109">In this topic</span></span>

- [<span data-ttu-id="d5e61-110">WorkflowIdentity kullanma</span><span class="sxs-lookup"><span data-stu-id="d5e61-110">Using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [<span data-ttu-id="d5e61-111">WorkflowIdentity kullanarak yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="d5e61-111">Side-by-side Execution using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#SxS)

- [<span data-ttu-id="d5e61-112">.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme</span><span class="sxs-lookup"><span data-stu-id="d5e61-112">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [<span data-ttu-id="d5e61-113">Veritabanı şemasını yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="d5e61-113">To upgrade the database schema</span></span>](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="using-workflowidentity"></a><a name="UsingWorkflowIdentity"></a> <span data-ttu-id="d5e61-114">WorkflowIdentity kullanma</span><span class="sxs-lookup"><span data-stu-id="d5e61-114">Using WorkflowIdentity</span></span>

<span data-ttu-id="d5e61-115">Kullanmak için <xref:System.Activities.WorkflowIdentity> bir örnek oluşturun, yapılandırın ve bir <xref:System.Activities.WorkflowApplication> örnekle ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="d5e61-115">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="d5e61-116"><xref:System.Activities.WorkflowIdentity>Örnek, üç tanımlayıcı bilgi parçasını içerir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-116">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="d5e61-117"><xref:System.Activities.WorkflowIdentity.Name%2A> ve bir <xref:System.Activities.WorkflowIdentity.Version%2A> ad ve bir içerir ve <xref:System.Version> gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-117"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="d5e61-118">, <xref:System.Activities.WorkflowIdentity> Üç özelliklerinden biri diğerinden farklıysa benzersizdir <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="d5e61-118">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5e61-119">Bir <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlanabilir bilgiler (PII) içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-119">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="d5e61-120"><xref:System.Activities.WorkflowIdentity>Örnek oluşturmak için kullanılan hakkında bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-120">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="d5e61-121">WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="d5e61-121">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="d5e61-122">Bu nedenle, <xref:System.Activities.WorkflowIdentity> kayıtlar izlenirken çalışma zamanı tarafından yayınlandığından ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir olabileceğinden bir örnek herhangi BIR PII verisi içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-122">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>

<span data-ttu-id="d5e61-123">Aşağıdaki örnekte, bir <xref:System.Activities.WorkflowIdentity> iş akışı tanımı kullanılarak oluşturulan bir iş akışı örneğiyle oluşturulur ve ilişkilendirilir `MortgageWorkflow` .</span><span class="sxs-lookup"><span data-stu-id="d5e61-123">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>

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

<span data-ttu-id="d5e61-124">Bir iş akışını yeniden yüklerken ve sürdürülürken, <xref:System.Activities.WorkflowIdentity> <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneğinin ile eşleşecek şekilde yapılandırılan bir, kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-124">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="d5e61-125"><xref:System.Activities.WorkflowIdentity>İş akışı örneğini yeniden yüklerken kullanılan, kalıcı ile eşleşmezse <xref:System.Activities.WorkflowIdentity> , bir <xref:System.Activities.VersionMismatchException> atılır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-125">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="d5e61-126">Aşağıdaki örnekte, `MortgageWorkflow` Önceki örnekte kalıcı olan örnekte bir yükleme denemesi yapılır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-126">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="d5e61-127">Bu yükleme denemesi, <xref:System.Activities.WorkflowIdentity> kalıcı örnekle eşleşmeyen ipotek iş akışının daha yeni bir sürümü için yapılandırılmış kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-127">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="d5e61-128">Önceki kod yürütüldüğünde, aşağıdakiler <xref:System.Activities.VersionMismatchException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d5e61-128">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="side-by-side-execution-using-workflowidentity"></a><a name="SxS"></a> <span data-ttu-id="d5e61-129">WorkflowIdentity kullanarak yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="d5e61-129">Side-by-side Execution using WorkflowIdentity</span></span>

<span data-ttu-id="d5e61-130"><xref:System.Activities.WorkflowIdentity> , bir iş akışının birden çok sürümünün bir yandan çalışmasını kolaylaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-130"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="d5e61-131">Tek bir yaygın senaryo, uzun süreli bir iş akışında iş gereksinimlerini değiştiriyor.</span><span class="sxs-lookup"><span data-stu-id="d5e61-131">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="d5e61-132">Bir iş akışının birçok örneği, güncelleştirilmiş bir sürüm dağıtıldığında çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-132">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="d5e61-133">Konak uygulaması, yeni örnekleri başlatırken güncelleştirilmiş iş akışı tanımını kullanacak şekilde yapılandırılabilir ve örnek olarak, örneklere devam edilirken doğru iş akışı tanımını sağlamak için ana bilgisayar uygulamasının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-133">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="d5e61-134"><xref:System.Activities.WorkflowIdentity> , iş akışı örneklerine devam edilirken eşleşen iş akışı tanımını tanımlamak ve sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-134"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>

<span data-ttu-id="d5e61-135"><xref:System.Activities.WorkflowIdentity>Kalıcı bir iş akışı örneğini almak için <xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-135">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="d5e61-136"><xref:System.Activities.WorkflowApplication.GetInstance%2A>Yöntemi <xref:System.Activities.WorkflowApplication.Id%2A> kalıcı iş akışı örneğini ve <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kalıcı örneği içeren öğesini alır ve döndürür <xref:System.Activities.WorkflowApplicationInstance> .</span><span class="sxs-lookup"><span data-stu-id="d5e61-136">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="d5e61-137"><xref:System.Activities.WorkflowApplicationInstance>, İlişkili olduğu gibi kalıcı bir iş akışı örneğiyle ilgili bilgiler içerir <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="d5e61-137">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="d5e61-138">Bu ilişkili, <xref:System.Activities.WorkflowIdentity> iş akışı örneğini yüklerken ve sürdürülürken doğru iş akışı tanımını sağlamak için ana bilgisayar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-138">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>

> [!NOTE]
> <span data-ttu-id="d5e61-139">Null bir değer <xref:System.Activities.WorkflowIdentity> geçerlidir ve ana bilgisayar tarafından <xref:System.Activities.WorkflowIdentity> uygun iş akışı tanımıyla ilişkili olmadan kalıcı olan örnekleri eşlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-139">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="d5e61-140">Bu senaryo, bir iş akışı uygulamasının ilk olarak iş akışı sürümü oluşturma ile yazılmayan veya bir uygulama .NET Framework 4 ' ten yükseltildiğinde meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-140">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from .NET Framework 4.</span></span> <span data-ttu-id="d5e61-141">Daha fazla bilgi için bkz. [Iş akışı sürümü oluşturmayı desteklemek için .NET Framework 4 kalıcılık veritabanlarını yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="d5e61-141">For more information, see [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>

<span data-ttu-id="d5e61-142">Aşağıdaki örnekte, `Dictionary<WorkflowIdentity, Activity>` <xref:System.Activities.WorkflowIdentity> örnekleri eşleşen iş akışı tanımlarıyla ilişkilendirmek için kullanılır ve bir iş akışı `MortgageWorkflow` , ile ilişkili iş akışı tanımı kullanılarak başlatılır `identityV1` <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="d5e61-142">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>

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

<span data-ttu-id="d5e61-143">Aşağıdaki örnekte, önceki örnekteki kalıcı iş akışı örneğiyle ilgili bilgiler çağırarak alınır <xref:System.Activities.WorkflowApplication.GetInstance%2A> ve kalıcı <xref:System.Activities.WorkflowIdentity> bilgiler, eşleşen iş akışı tanımını almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-143">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="d5e61-144">Bu bilgiler, öğesini yapılandırmak için kullanılır <xref:System.Activities.WorkflowApplication> ve sonra iş akışı yüklenir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-144">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="d5e61-145"><xref:System.Activities.WorkflowApplication.Load%2A>Öğesinin kullanıldığı aşırı yükleme, <xref:System.Activities.WorkflowApplicationInstance> <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> üzerinde yapılandırılan öğesinin <xref:System.Activities.WorkflowApplicationInstance> tarafından kullanıldığı <xref:System.Activities.WorkflowApplication> ve bu nedenle <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliğinin yapılandırılması gerekmediği unutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-145">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>

> [!NOTE]
> <span data-ttu-id="d5e61-146"><xref:System.Activities.WorkflowApplication.InstanceStore%2A>Özellik ayarlandıysa, tarafından kullanılan aynı örnekle ayarlanmalıdır, aksi takdirde <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> <xref:System.Activities.WorkflowApplicationInstance> <xref:System.ArgumentException> Şu iletiyle birlikte oluşturulur: `The instance is configured with a different InstanceStore than this WorkflowApplication.` .</span><span class="sxs-lookup"><span data-stu-id="d5e61-146">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>

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

## <a name="upgrading-net-framework-4-persistence-databases-to-support-workflow-versioning"></a><a name="UpdatingWF4PersistenceDatabases"></a> <span data-ttu-id="d5e61-147">.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme</span><span class="sxs-lookup"><span data-stu-id="d5e61-147">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>

<span data-ttu-id="d5e61-148">.NET Framework 4 veritabanı betikleri kullanılarak oluşturulan kalıcı veritabanlarını yükseltmek için bir SqlWorkflowInstanceStoreSchemaUpgrade. SQL veritabanı betiği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-148">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the .NET Framework 4 database scripts.</span></span> <span data-ttu-id="d5e61-149">Bu betik, .NET Framework 4,5 ' de tanıtılan yeni sürüm oluşturma yeteneklerini destekleyecek şekilde veritabanlarını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5e61-149">This script updates the databases to support the new versioning capabilities introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="d5e61-150">Veritabanlarındaki kalıcı iş akışı örneklerine varsayılan sürüm oluşturma değerleri verilir ve daha sonra yan yana yürütmeye ve Dinamik güncelleştirmeye katılabilirler.</span><span class="sxs-lookup"><span data-stu-id="d5e61-150">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>

<span data-ttu-id="d5e61-151">.NET Framework 4,5 iş akışı uygulaması, sunulan betiği kullanılarak yükseltilmemiş bir kalıcılık veritabanında yeni sürüm oluşturma özelliklerini kullanan herhangi bir kalıcılık işlemini denerse, <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> aşağıdaki iletiye benzer bir iletiyle birlikte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d5e61-151">If a .NET Framework 4.5 workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="to-upgrade-the-database-schema"></a><a name="ToUpgrade"></a> <span data-ttu-id="d5e61-152">Veritabanı şemasını yükseltmek için</span><span class="sxs-lookup"><span data-stu-id="d5e61-152">To upgrade the database schema</span></span>

1. <span data-ttu-id="d5e61-153">SQL Server Management Studio açın ve Kalıcılık veritabanı sunucusuna bağlanın, örneğin **.\Sqlexpress**.</span><span class="sxs-lookup"><span data-stu-id="d5e61-153">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>

2. <span data-ttu-id="d5e61-154">**Dosya** menüsünden **Aç**, **Dosya** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="d5e61-154">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="d5e61-155">Aşağıdaki klasöre gidin: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="d5e61-155">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

3. <span data-ttu-id="d5e61-156">**SqlWorkflowInstanceStoreSchemaUpgrade. SQL** ' i seçin ve **Aç**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5e61-156">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>

4. <span data-ttu-id="d5e61-157">**Kullanılabilir veritabanları** açılan listesinden Kalıcılık veritabanının adını seçin.</span><span class="sxs-lookup"><span data-stu-id="d5e61-157">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>

5. <span data-ttu-id="d5e61-158">**Sorgu** menüsünden **Yürüt** ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="d5e61-158">Choose **Execute** from the **Query** menu.</span></span>

<span data-ttu-id="d5e61-159">Sorgu tamamlandığında, veritabanı şeması yükseltilir ve isterseniz, kalıcı iş akışı örneklerine atanmış olan varsayılan iş akışı kimliğini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5e61-159">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="d5e61-160">**Nesne Gezgini** **veritabanları** düğümünde Kalıcılık veritabanınızı genişletin ve ardından **Görünümler** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5e61-160">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="d5e61-161">**System. Activities. Durableörnek oluşturma. örnekleri** öğesine sağ tıklayın ve **en üstteki 1000 satırları Seç**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d5e61-161">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="d5e61-162">Sütunların sonuna kaydırın ve görünüme eklenen altı sütun ( **IdentityName**, **IdentityPackage**, **Build**, **ana**, **Minor** ve **Düzeltme**) olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d5e61-162">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="d5e61-163">Kalıcı iş akışlarının, null bir iş akışı kimliğini temsil eden bu alanlar için **null** değeri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d5e61-163">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
