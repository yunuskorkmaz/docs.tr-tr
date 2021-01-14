---
title: Dinamik Güncelleştirme
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: cb4b63a67aa6e9033b227198e2ecc2b1b80db927
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190162"
---
# <a name="dynamic-update"></a><span data-ttu-id="5241e-102">Dinamik Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="5241e-102">Dynamic Update</span></span>

<span data-ttu-id="5241e-103">Dinamik güncelleştirme, iş akışı uygulama geliştiricilerinin kalıcı bir iş akışı örneğinin iş akışı tanımını güncelleştirmesine yönelik bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="5241e-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="5241e-104">Bu, bir hata düzeltmesini veya yeni gereksinimleri uygulayabilir ya da beklenmeyen değişikliklere uyum sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="5241e-105">Bu konuda .NET Framework 4,5 ' de tanıtılan dinamik güncelleştirme işlevselliğine genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5241e-105">This topic provides an overview of the dynamic update functionality introduced in .NET Framework 4.5.</span></span>

## <a name="dynamic-update"></a><span data-ttu-id="5241e-106">Dinamik Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="5241e-106">Dynamic Update</span></span>

<span data-ttu-id="5241e-107">Kalıcı bir iş akışı örneğine dinamik güncelleştirmeleri uygulamak için, <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> kalıcı iş akışı örneğinin istenen değişiklikleri yansıtacak şekilde nasıl değiştirileceğini açıklayan çalışma zamanına yönelik yönergeler içeren bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5241e-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="5241e-108">Güncelleştirme haritası oluşturulduktan sonra, istenen kalıcı iş akışı örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5241e-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="5241e-109">Dinamik güncelleştirme uygulandıktan sonra, iş akışı örneği yeni güncelleştirilmiş iş akışı tanımı kullanılarak devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="5241e-110">Bir güncelleştirme eşlemesi oluşturmak ve uygulamak için dört adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5241e-110">There are four steps required to create and apply an update map.</span></span>

1. [<span data-ttu-id="5241e-111">Dinamik güncelleştirme için iş akışı tanımını hazırlama</span><span class="sxs-lookup"><span data-stu-id="5241e-111">Prepare the workflow definition for dynamic update</span></span>](dynamic-update.md#Prepare)

2. [<span data-ttu-id="5241e-112">İş akışı tanımını istenen değişiklikleri yansıtacak şekilde Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="5241e-112">Update the workflow definition to reflect the desired changes</span></span>](dynamic-update.md#Update)

3. [<span data-ttu-id="5241e-113">Güncelleştirme haritasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="5241e-113">Create the update map</span></span>](dynamic-update.md#Create)

4. [<span data-ttu-id="5241e-114">Güncelleştirme haritasını istenen kalıcı iş akışı örneklerine Uygula</span><span class="sxs-lookup"><span data-stu-id="5241e-114">Apply the update map to the desired persisted workflow instances</span></span>](dynamic-update.md#Apply)

> [!NOTE]
> <span data-ttu-id="5241e-115">Güncelleştirme haritasının oluşturulmasını kapsayan 1 ile 3 arasındaki adımların, güncelleştirmeyi uygulamadan bağımsız olarak gerçekleştirilebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5241e-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="5241e-116">İş akışı geliştiricisinin güncelleştirme haritasını çevrimdışı olarak oluşturacak ortak bir senaryo ve daha sonra bir yönetici güncelleştirmeyi uygulayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5241e-116">A common scenario that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>

<span data-ttu-id="5241e-117">Bu konu, derlenmiş xaml iş akışının kalıcı bir örneğine yeni bir etkinlik eklemenin dinamik güncelleştirme sürecine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="5241e-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>

### <a name="prepare-the-workflow-definition-for-dynamic-update"></a><a name="Prepare"></a> <span data-ttu-id="5241e-118">Dinamik güncelleştirme için iş akışı tanımını hazırlama</span><span class="sxs-lookup"><span data-stu-id="5241e-118">Prepare the workflow definition for dynamic update</span></span>

<span data-ttu-id="5241e-119">Dinamik güncelleştirme işlemindeki ilk adım, istenen iş akışı tanımını güncelleştirme için hazırlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5241e-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="5241e-120">Bu, <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi çağırarak ve değiştirmek için iş akışı tanımına geçerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="5241e-121">Bu yöntem, daha sonra değiştirilmiş iş akışı tanımıyla karşılaştırılabilmesi için, genel etkinlikler ve etiketlenmesi gereken değişkenler gibi tüm nesneleri tanımlamak üzere iş akışı ağacını doğrular ve yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="5241e-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="5241e-122">Bu tamamlandığında, iş akışı ağacı kopyalanır ve özgün iş akışı tanımına eklenir.</span><span class="sxs-lookup"><span data-stu-id="5241e-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="5241e-123">Güncelleştirme haritası oluşturulduğunda, iş akışı tanımının güncelleştirilmiş sürümü orijinal iş akışı tanımıyla karşılaştırılır ve güncelleştirme haritası farklılıklara göre oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5241e-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>

<span data-ttu-id="5241e-124">Dinamik güncelleştirme için bir XAML iş akışını hazırlamak üzere, bir öğesine yüklenebilir <xref:System.Activities.ActivityBuilder> ve sonra <xref:System.Activities.ActivityBuilder> öğesine geçirilir <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5241e-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="5241e-125">Serileştirilmiş iş akışlarıyla çalışma hakkında daha fazla bilgi için <xref:System.Activities.ActivityBuilder> , bkz. [xaml 'de ve xaml 'de iş akışlarını ve etkinlikleri serileştirme](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5241e-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

<span data-ttu-id="5241e-126">Aşağıdaki örnekte, bir `MortgageWorkflow` tanım ( <xref:System.Activities.Statements.Sequence> birkaç alt etkinlikten oluşan bir) bir <xref:System.Activities.ActivityBuilder> olarak yüklenir ve dinamik güncelleştirme için hazırlanır.</span><span class="sxs-lookup"><span data-stu-id="5241e-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="5241e-127">Yöntem çağrıldıktan sonra, <xref:System.Activities.ActivityBuilder> özgün iş akışı tanımını ve bir kopyayı içerir.</span><span class="sxs-lookup"><span data-stu-id="5241e-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

### <a name="update-the-workflow-definition-to-reflect-the-desired-changes"></a><a name="Update"></a> <span data-ttu-id="5241e-128">İş akışı tanımını istenen değişiklikleri yansıtacak şekilde Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="5241e-128">Update the workflow definition to reflect the desired changes</span></span>

<span data-ttu-id="5241e-129">İş akışı tanımı güncelleştirme için hazırlandıktan sonra, istenen değişiklikler yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-129">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="5241e-130">Etkinlik ekleyebilir veya kaldırabilir, ortak değişkenler ekleyebilir, taşıyabilir veya silebilir, bağımsız değişken ekleyebilir veya kaldırabilir ve etkinlik temsilcilerinin imzasında değişiklik yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5241e-130">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="5241e-131">Çalışan bir etkinliği kaldıramaz veya çalışan bir temsilcinin imzasını değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5241e-131">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="5241e-132">Bu değişiklikler kod kullanılarak veya yeniden barındırılan bir iş akışı tasarımcısında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-132">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="5241e-133">Aşağıdaki örnekte, bir `VerifyAppraisal` önceki örnekteki öğesinin gövdesini oluşturan diziye özel bir etkinlik eklenir `MortgageWorkflow` .</span><span class="sxs-lookup"><span data-stu-id="5241e-133">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>

```csharp
// Make desired changes to the definition. In this example, we are
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.
VerifyAppraisal va = new VerifyAppraisal
{
    Result = new VisualBasicReference<bool>("LoanCriteria")
};

// Get the Sequence that makes up the body of the workflow.
Sequence s = ab.Implementation as Sequence;

// Insert the new activity into the Sequence.
s.Activities.Insert(2, va);
```

### <a name="create-the-update-map"></a><a name="Create"></a> <span data-ttu-id="5241e-134">Güncelleştirme haritasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="5241e-134">Create the update map</span></span>

<span data-ttu-id="5241e-135">Güncelleştirme için hazırlanan iş akışı tanımı değiştirildikten sonra, güncelleştirme haritası oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-135">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="5241e-136">Dinamik bir güncelleştirme eşlemesi oluşturmak için <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-136">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="5241e-137">Bu <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> , çalışma zamanının, yeni iş akışı tanımıyla yüklenip devam edebilmesi için kalıcı bir iş akışı örneğini değiştirmesi gereken bilgileri içeren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="5241e-137">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="5241e-138">Aşağıdaki örnekte, önceki örnekteki değiştirilmiş tanım için dinamik bir eşleme oluşturulur `MortgageWorkflow` .</span><span class="sxs-lookup"><span data-stu-id="5241e-138">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

<span data-ttu-id="5241e-139">Bu güncelleştirme eşlemesi kalıcı iş akışı örneklerini değiştirmek için hemen kullanılabilir veya genellikle kaydedilebilir ve güncelleştirmeler daha sonra uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-139">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="5241e-140">Güncelleştirme haritasını kaydetmek için bir yol, aşağıdaki örnekte gösterildiği gibi bir dosyaya serileştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5241e-140">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<span data-ttu-id="5241e-141"><xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>Döndüğünde, kopyalanmış iş akışı tanımı ve çağrısına eklenen diğer dinamik güncelleştirme bilgileri <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> kaldırılır ve değiştirilen iş akışı örnekleri, daha sonra güncelleştirilmiş iş akışı örneklerine devam edilirken kullanılabilmesi için kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-141">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="5241e-142">Aşağıdaki örnekte, değiştirilen iş akışı tanımı öğesine kaydedilir `MortgageWorkflow_v1.1.xaml` .</span><span class="sxs-lookup"><span data-stu-id="5241e-142">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v1.1.xaml`.</span></span>

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="apply-the-update-map-to-the-desired-persisted-workflow-instances"></a><a name="Apply"></a> <span data-ttu-id="5241e-143">Güncelleştirme haritasını istenen kalıcı iş akışı örneklerine Uygula</span><span class="sxs-lookup"><span data-stu-id="5241e-143">Apply the update map to the desired persisted workflow instances</span></span>

<span data-ttu-id="5241e-144">Güncelleştirme haritasının uygulanması, oluşturulduktan sonra herhangi bir zamanda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-144">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="5241e-145"><xref:System.Activities.DynamicUpdate.DynamicUpdateMap>Tarafından döndürülen örneği kullanarak hemen yapılabilir <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> veya daha sonra güncelleştirme haritasının kaydedilmiş bir kopyası kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-145">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="5241e-146">Bir iş akışı örneğini güncelleştirmek için bir <xref:System.Activities.WorkflowApplicationInstance> kullanarak yükleyin <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5241e-146">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5241e-147">Ardından, <xref:System.Activities.WorkflowApplication> güncelleştirilmiş iş akışı tanımını ve istediğiniz öğesini kullanarak bir oluşturun <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="5241e-147">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="5241e-148">Bu, <xref:System.Activities.WorkflowIdentity> özgün iş akışını sürdürmek için kullanılandan farklı olabilir ve genellikle kalıcı örneğin değiştirildiğini yansıtacak şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="5241e-148">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="5241e-149">Oluşturulduktan sonra, <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> ' a sahip olan aşırı yüklemesi kullanılarak yüklenir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> ve sonra öğesine çağrısıyla birlikte kaldırılır <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5241e-149">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5241e-150">Bu, dinamik güncelleştirmeyi uygular ve güncelleştirilmiş iş akışı örneği devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="5241e-150">This applies the dynamic update and persists the updated workflow instance.</span></span>

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
{
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
    object updateMap = serializer.ReadObject(fs);
    if (updateMap == null)
    {
        throw new ApplicationException("DynamicUpdateMap is null.");
    }

    map = (DynamicUpdateMap)updateMap;
}

// Retrieve a list of workflow instance ids that corresponds to the
// workflow instances to update. This step is the responsibility of
// the application developer.
List<Guid> ids = GetPersistedWorkflowIds();
foreach (Guid id in ids)
{
    // Get a proxy to the persisted workflow instance.
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);

    // If desired, you can inspect the WorkflowIdentity of the instance
    // using the DefinitionIdentity property to determine whether to apply
    // the update.
    Console.WriteLine(instance.DefinitionIdentity);

    // Create a workflow application. You must specify the updated workflow definition, and
    // you may provide an updated WorkflowIdentity if desired to reflect the update.
    WorkflowIdentity identity = new WorkflowIdentity
    {
        Name = "MortgageWorkflow v1.1",
        Version = new Version(1, 1, 0, 0)
    };

    // Load the persisted workflow instance using the updated workflow definition
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class
    // contains the updated definition.
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

    // Apply the dynamic update on the loaded instance.
    wfApp.Load(instance, map);

    // Unload the updated instance.
    wfApp.Unload();
}
```

### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="5241e-151">Güncelleştirilmiş Iş akışı örneği sürdürülüyor</span><span class="sxs-lookup"><span data-stu-id="5241e-151">Resuming an Updated Workflow Instance</span></span>

<span data-ttu-id="5241e-152">Dinamik güncelleştirme uygulandıktan sonra iş akışı örneği devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="5241e-152">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="5241e-153">Yeni güncelleştirilmiş tanımın ve <xref:System.Activities.WorkflowIdentity> kullanılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5241e-153">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>

> [!NOTE]
> <span data-ttu-id="5241e-154">Ve ile çalışma hakkında daha fazla bilgi için <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowIdentity> bkz. [Workflowwıdentity ve sürümü kullanma](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="5241e-154">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

<span data-ttu-id="5241e-155">Aşağıdaki örnekte, `MortgageWorkflow_v1.1.xaml` önceki örnekteki iş akışı derlenmiştir ve güncelleştirilmiş iş akışı tanımı kullanılarak yüklenir ve sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="5241e-155">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>

```csharp
// Load the persisted workflow instance using the updated workflow definition
// and updated WorkflowIdentity.
WorkflowIdentity identity = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1.1",
    Version = new Version(1, 1, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure persistence and desired workflow event handlers.
// (Omitted for brevity.)
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(InstanceId);

// Resume the workflow.
// wfApp.ResumeBookmark(...);
```
