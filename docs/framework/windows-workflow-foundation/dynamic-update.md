---
title: Dinamik Güncelleştirme
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: e28a34e500034eec6cf250d94cf7631ca85a7d40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945814"
---
# <a name="dynamic-update"></a><span data-ttu-id="aaf12-102">Dinamik Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="aaf12-102">Dynamic Update</span></span>

<span data-ttu-id="aaf12-103">Dinamik güncelleştirme, uygulama geliştiricilerinin'bir kalıcı iş akışı örneği iş akışı tanımını güncelleştirmek için iş akışı için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaf12-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="aaf12-104">Bu, bir hata düzeltmesi, yeni gereksinimleri uygulamak için veya beklenmeyen değişiklikleri uyum sağlamak için olabilir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="aaf12-105">Bu konuda sunulan dinamik güncelleştirme işlevlerine genel bakış sağlar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aaf12-105">This topic provides an overview of the dynamic update functionality introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>

## <a name="dynamic-update"></a><span data-ttu-id="aaf12-106">Dinamik Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="aaf12-106">Dynamic Update</span></span>

<span data-ttu-id="aaf12-107">Bir kalıcı iş akışı örneği için dinamik güncelleştirmeleri uygulamak için bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> oluşturulur, istediğiniz değişiklikleri yansıtacak şekilde kalıcı iş akışı örneği değişiklik yapma açıklayan yönergeler çalışma zamanı için içerir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="aaf12-108">Güncelleştirme eşlemesi oluşturulduktan sonra bu istenen kalıcı iş akışı örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aaf12-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="aaf12-109">Dinamik güncelleştirme uygulandıktan sonra yeni güncelleştirilmiş iş akışı tanımı kullanarak iş akışı örneği sürdürülebilir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="aaf12-110">Oluşturma ve bir güncelleştirme eşlemesi uygulamak için gereken dört adım vardır.</span><span class="sxs-lookup"><span data-stu-id="aaf12-110">There are four steps required to create and apply an update map.</span></span>

1. [<span data-ttu-id="aaf12-111">Dinamik güncelleştirme iş akışı tanımı hazırlama</span><span class="sxs-lookup"><span data-stu-id="aaf12-111">Prepare the workflow definition for dynamic update</span></span>](dynamic-update.md#Prepare)

2. [<span data-ttu-id="aaf12-112">İş akışı tanımı, istediğiniz değişiklikleri yansıtacak şekilde güncelleştirin</span><span class="sxs-lookup"><span data-stu-id="aaf12-112">Update the workflow definition to reflect the desired changes</span></span>](dynamic-update.md#Update)

3. [<span data-ttu-id="aaf12-113">Güncelleştirme eşlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="aaf12-113">Create the update map</span></span>](dynamic-update.md#Create)

4. [<span data-ttu-id="aaf12-114">Güncelleştirme eşlemesi istenen kalıcı iş akışı örnekleri için geçerlidir</span><span class="sxs-lookup"><span data-stu-id="aaf12-114">Apply the update map to the desired persisted workflow instances</span></span>](dynamic-update.md#Apply)

> [!NOTE]
> <span data-ttu-id="aaf12-115">Adımlar güncelleştirme eşlemesi oluşturulmasını kapsar, 3, 1 güncelleştirmeyi uygulamadan bağımsız olarak gerçekleştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="aaf12-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="aaf12-116">İş akışı Geliştirici çevrimdışı güncelleştirme eşlemesi oluşturur ve ardından yönetici daha sonra güncelleştirme uygulanır sık karşılaşılan bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="aaf12-116">A common scenario that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>

<span data-ttu-id="aaf12-117">Bu konu, yeni bir etkinlik için derlenmiş Xaml iş akışı kalıcı bir örneğini ekleme dinamik güncelleştirme işlemine genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaf12-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>

### <a name="Prepare"></a> <span data-ttu-id="aaf12-118">Dinamik güncelleştirme iş akışı tanımı hazırlama</span><span class="sxs-lookup"><span data-stu-id="aaf12-118">Prepare the workflow definition for dynamic update</span></span>

<span data-ttu-id="aaf12-119">Dinamik güncelleştirme işleminin ilk adımı, istenen iş akışı tanım güncelleştirmesi için hazırlama sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="aaf12-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="aaf12-120">Bu çağrılarak gerçekleştirilir <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi ve değiştirmek için iş akışı tanımında geçirme.</span><span class="sxs-lookup"><span data-stu-id="aaf12-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="aaf12-121">Bu yöntem, doğrulama ve iş akışı ağacında, tüm genel etkinlikleri ve bunlar daha sonra değiştirilen iş akışı tanımıyla karşılaştırılabilir şekilde etiketlenmesi gereken değişkenleri gibi nesneleri tanımlamak için size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="aaf12-122">Bu tamamlandığında iş akışı ağaç kopyalanabilir ve orijinal iş akışının tanımına bağlı.</span><span class="sxs-lookup"><span data-stu-id="aaf12-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="aaf12-123">Güncelleştirme eşlemesi oluşturulduğunda, iş akışı tanımının güncelleştirilmiş sürümü özgün iş akışı tanımı ile karşılaştırılır ve güncelleştirme eşlemesi temel farklar üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aaf12-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>

<span data-ttu-id="aaf12-124">Dinamik güncelleştirme, yüklenemeyen içine bir Xaml iş akışı hazırlamak için bir <xref:System.Activities.ActivityBuilder>, ardından <xref:System.Activities.ActivityBuilder> yöntemlere geçirilen <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aaf12-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="aaf12-125">İle çalışma hakkında daha fazla bilgi için iş akışları seri hale getirilmiş ve <xref:System.Activities.ActivityBuilder>, bkz: [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="aaf12-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

<span data-ttu-id="aaf12-126">Aşağıdaki örnekte, bir `MortgageWorkflow` tanımı (oluşur, bir <xref:System.Activities.Statements.Sequence> birkaç alt etkinliklerle) içine yüklenen bir <xref:System.Activities.ActivityBuilder>ve ardından dinamik güncelleştirme için hazır.</span><span class="sxs-lookup"><span data-stu-id="aaf12-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="aaf12-127">Yöntemin dönüşünün ardından, <xref:System.Activities.ActivityBuilder> özgün iş akışı tanımı ve bunun yanı sıra bir kopyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>

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

> [!NOTE]
> <span data-ttu-id="aaf12-128">Bu konuda eşlik eden örnek kodu indirmek için bkz [dinamik güncelleştirme örnek kodu](https://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="aaf12-128">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>

### <a name="Update"></a> <span data-ttu-id="aaf12-129">İş akışı tanımı, istediğiniz değişiklikleri yansıtacak şekilde güncelleştirin</span><span class="sxs-lookup"><span data-stu-id="aaf12-129">Update the workflow definition to reflect the desired changes</span></span>

<span data-ttu-id="aaf12-130">İş akışı tanımını güncelleştirmek için hazırlandıktan sonra istenen bir değişiklik yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="aaf12-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="aaf12-131">Ekleme veya etkinlikleri kaldırabileceğiniz, Ekle, taşıyın veya genel değişkenleri Sil, ekleyin veya bağımsız değişkenlerini kaldırın ve etkinlik temsilcileri imzası için değişiklik.</span><span class="sxs-lookup"><span data-stu-id="aaf12-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="aaf12-132">Çalışan etkinlik kaldıramaz veya çalışan bir temsilcinin imzasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="aaf12-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="aaf12-133">Kodu kullanarak bu değişiklikler yapılması veya yeniden barındırılan iş akışı Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="aaf12-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="aaf12-134">Aşağıdaki örnekte, özel bir `VerifyAppraisal` etkinlik gövdesini oluşturan yapar dizisi eklenen `MortgageWorkflow` önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="aaf12-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>

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

### <a name="Create"></a> <span data-ttu-id="aaf12-135">Güncelleştirme eşlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="aaf12-135">Create the update map</span></span>

<span data-ttu-id="aaf12-136">Güncelleştirme için hazırlanan iş akışı tanımı değiştirildi sonra güncelleştirme eşleme oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="aaf12-137">Bir dinamik güncelleştirme eşlemesi oluşturmak için <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="aaf12-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="aaf12-138">Bu döndürür bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> çalışma zamanı gerekir böylece onu yüklenebilir ve yeni iş akışı tanımıyla sürdürüldü kalıcı iş akışı örneği değiştirmek için bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="aaf12-139">Aşağıdaki örnekte, dinamik bir harita oluşturulur için değiştirilmiş `MortgageWorkflow` önceki örnekte tanımı.</span><span class="sxs-lookup"><span data-stu-id="aaf12-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

<span data-ttu-id="aaf12-140">Bu güncelleştirme eşlemesi kalıcı iş akışı örnekleri değiştirmek için hemen kullanılabilir veya genellikle kaydedilebilir ve daha sonra güncelleştirmelerin uygulanması.</span><span class="sxs-lookup"><span data-stu-id="aaf12-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="aaf12-141">Güncelleştirme eşlemesi kaydetmek için tek bir dosyaya seri hale getirmek için aşağıdaki örnekte gösterildiği gibi yoludur.</span><span class="sxs-lookup"><span data-stu-id="aaf12-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<span data-ttu-id="aaf12-142">Zaman <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> döndürür, kopyalanan iş akışı tanımı ve çağrıda eklenen diğer dinamik güncelleştirme bilgilerini <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> kaldırılır ve değiştirilen iş akışı tanımı sürdürme güncelleştirildiğinde daha sonra kullanılabilir kaydedilmesi hazır İş akışı örnekleri.</span><span class="sxs-lookup"><span data-stu-id="aaf12-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="aaf12-143">Aşağıdaki örnekte, değiştirilen iş akışı tanımı için kaydedilen `MortgageWorkflow_v1.1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="aaf12-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v1.1.xaml`.</span></span>

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="Apply"></a> <span data-ttu-id="aaf12-144">Güncelleştirme eşlemesi istenen kalıcı iş akışı örnekleri için geçerlidir</span><span class="sxs-lookup"><span data-stu-id="aaf12-144">Apply the update map to the desired persisted workflow instances</span></span>

<span data-ttu-id="aaf12-145">Güncelleştirme eşlemesi uygulama oluşturduktan sonra herhangi bir zamanda gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="aaf12-146">Hemen kullanmaya yapılabilir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> tarafından döndürülen örnek <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, ya da daha sonra güncelleştirme haritanın kaydedilen bir kopya kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="aaf12-147">Bir iş akışı örneği güncelleştirmek için içine yüklemek bir <xref:System.Activities.WorkflowApplicationInstance> kullanarak <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aaf12-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aaf12-148">Ardından, oluşturun bir <xref:System.Activities.WorkflowApplication> güncelleştirilmiş iş akışı tanımı ve istenen kullanarak <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="aaf12-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="aaf12-149">Bu <xref:System.Activities.WorkflowIdentity> özgün iş akışı kalıcı hale getirmek için kullanılan ve genellikle kalıcı örneği değiştirilmiş yansıtmak için hesaptan farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="aaf12-150">Bir kez <xref:System.Activities.WorkflowApplication> olan oluşturulan aşırı yüklemesini kullanarak yüklendiği <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> almayan bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>ve ardından bir çağrı ile kaldırıldığında <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aaf12-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aaf12-151">Bu dinamik güncelleştirme uygulanır ve güncelleştirilmiş iş akışı örneğinin devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-151">This applies the dynamic update and persists the updated workflow instance.</span></span>

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

### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="aaf12-152">Güncelleştirilmiş iş akışı örneği sürdürme</span><span class="sxs-lookup"><span data-stu-id="aaf12-152">Resuming an Updated Workflow Instance</span></span>

<span data-ttu-id="aaf12-153">Dinamik güncelleştirme uygulandıktan sonra iş akışı örneği sürdürülebilir.</span><span class="sxs-lookup"><span data-stu-id="aaf12-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="aaf12-154">Yeni tanım güncelleştirme olduğunu unutmayın ve <xref:System.Activities.WorkflowIdentity> kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aaf12-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>

> [!NOTE]
> <span data-ttu-id="aaf12-155">İle çalışma hakkında daha fazla bilgi için <xref:System.Activities.WorkflowApplication> ve <xref:System.Activities.WorkflowIdentity>, bkz: [Workflowıdentity kullanma ve sürüm oluşturma](using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="aaf12-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

<span data-ttu-id="aaf12-156">Aşağıdaki örnekte, `MortgageWorkflow_v1.1.xaml` önceki örnekte iş akışı derlendiğinden, yüklenir ve güncelleştirilmiş iş akışı tanımı kullanarak devam ettirildi.</span><span class="sxs-lookup"><span data-stu-id="aaf12-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>

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

> [!NOTE]
> <span data-ttu-id="aaf12-157">Bu konuda eşlik eden örnek kodu indirmek için bkz [dinamik güncelleştirme örnek kodu](https://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="aaf12-157">To download the sample code that accompanies this topic, see [Dynamic Update sample code](https://go.microsoft.com/fwlink/?LinkId=227905).</span></span>
