---
title: "Dinamik güncelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee6b228d729958e9e5f14cadb1e378a2944c4f85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dynamic-update"></a><span data-ttu-id="3cf33-102">Dinamik güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="3cf33-102">Dynamic Update</span></span>
<span data-ttu-id="3cf33-103">Dinamik güncelleştirme kalıcı iş akışı örneği iş akışı tanımını güncelleştirmek için uygulama geliştiricileri iş akışı için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cf33-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="3cf33-104">Bu yeni gereksinimleri, bir hata düzeltme uygulamak için veya beklenmeyen değişiklikleri uyum sağlayacak şekilde olabilir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="3cf33-105">Bu konuda sunulan dinamik güncelleştirme işlevlerine genel bakış sağlayan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3cf33-105">This topic provides an overview of the dynamic update functionality introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="dynamic-update"></a><span data-ttu-id="3cf33-106">Dinamik güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="3cf33-106">Dynamic Update</span></span>  
 <span data-ttu-id="3cf33-107">Bir kalıcı iş akışı örneği için dinamik güncelleştirmeleri uygulamak için bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> oluşturulur, istediğiniz değişiklikleri yansıtacak şekilde kalıcı iş akışı örneğini değiştirmek nasıl açıklayan çalışma zamanı için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="3cf33-108">Güncelleştirme eşlemesi oluşturulduktan sonra istenen kalıcı iş akışı örneklerine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3cf33-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="3cf33-109">Dinamik güncelleştirme uygulandıktan sonra iş akışı örneği yeni güncelleştirilmiş iş akışı tanımı kullanılarak sürdürülebilir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="3cf33-110">Oluşturmak ve bir güncelleştirme eşlemesi uygulamak için gereken dört adım vardır.</span><span class="sxs-lookup"><span data-stu-id="3cf33-110">There are four steps required to create and apply an update map.</span></span>  
  
1.  [<span data-ttu-id="3cf33-111">Dinamik güncelleştirme iş akışı tanımı hazırlama</span><span class="sxs-lookup"><span data-stu-id="3cf33-111">Prepare the workflow definition for dynamic update</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [<span data-ttu-id="3cf33-112">İş akışı tanımını istediğiniz değişiklikleri yansıtacak şekilde güncelleştirin</span><span class="sxs-lookup"><span data-stu-id="3cf33-112">Update the workflow definition to reflect the desired changes</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [<span data-ttu-id="3cf33-113">Güncelleştirme eşlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cf33-113">Create the update map</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [<span data-ttu-id="3cf33-114">İstenen kalıcı iş akışı örnekleri için güncelleştirme eşlemesi Uygula</span><span class="sxs-lookup"><span data-stu-id="3cf33-114">Apply the update map to the desired persisted workflow instances</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  <span data-ttu-id="3cf33-115">1 ile güncelleştirme eşlemesi oluşturulmasını kapak, 3 adımlarını güncelleştirmeyi uygulamadan bağımsız olarak gerçekleştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3cf33-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="3cf33-116">Bu iş akışı Geliştirici güncelleştirme oluşturacak çevrimdışı eşlenen yaygın bir senaryo ve yönetici güncelleştirmeyi daha sonra geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="3cf33-116">A common scenario that that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>  
  
 <span data-ttu-id="3cf33-117">Bu konu, kalıcı bir derlenmiş bir Xaml iş akışı örneği için yeni bir etkinlik ekleme dinamik güncelleştirme işlemine genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cf33-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>  
  
###  <a name="Prepare"></a><span data-ttu-id="3cf33-118">Dinamik güncelleştirme iş akışı tanımı hazırlama</span><span class="sxs-lookup"><span data-stu-id="3cf33-118">Prepare the workflow definition for dynamic update</span></span>  
 <span data-ttu-id="3cf33-119">İstenen iş akışı tanım güncelleştirmesi için hazırlamak için dinamik güncelleştirme işleminin ilk adımında var.</span><span class="sxs-lookup"><span data-stu-id="3cf33-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="3cf33-120">Bu çağırarak yapılır <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi ve değiştirmek için iş akışı tanımında geçirme.</span><span class="sxs-lookup"><span data-stu-id="3cf33-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="3cf33-121">Bu yöntem doğrular ve tüm ortak etkinlikleri ve bunlar daha sonra değiştirilmiş iş akışı tanımıyla karşılaştırılabilir şekilde etiketlenmesi gereken değişkenler gibi nesneleri tanımlamak için iş akışı ağaç anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3cf33-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="3cf33-122">Bu tamamlandığında, iş akışı ağaç kopyalanabilir ve orijinal iş akışı tanımını bağlı.</span><span class="sxs-lookup"><span data-stu-id="3cf33-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="3cf33-123">Güncelleştirme eşlemesi oluşturulduğunda, iş akışı tanımı'nın güncelleştirilmiş sürümü özgün iş akışı tanımıyla karşılaştırılır ve güncelleştirme harita üzerinde farklar temel alınarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3cf33-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>  
  
 <span data-ttu-id="3cf33-124">Dinamik güncelleştirme, yüklenmiş içine bir Xaml iş akışı hazırlamak için bir <xref:System.Activities.ActivityBuilder>ve ardından <xref:System.Activities.ActivityBuilder> içine geçirilen <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3cf33-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cf33-125">İle çalışma hakkında daha fazla bilgi için iş akışları seri hale getirilmiş ve <xref:System.Activities.ActivityBuilder>, bkz: [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3cf33-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
 <span data-ttu-id="3cf33-126">Aşağıdaki örnekte, bir `MortgageWorkflow` tanımı (, oluşur bir <xref:System.Activities.Statements.Sequence> birkaç alt etkinliklerle) içine yüklenir bir <xref:System.Activities.ActivityBuilder>ve dinamik güncelleştirme için hazır.</span><span class="sxs-lookup"><span data-stu-id="3cf33-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="3cf33-127">Metodu döndükten sonra <xref:System.Activities.ActivityBuilder> bir kopyasını yanı sıra, orijinal iş akışı tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>  
  
```csharp  
// Load the MortgageWorkflow definition from Xaml into  
// an ActivityBuilder.  
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
{  
    LocalAssembly = Assembly.GetExecutingAssembly()  
};  
  
XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefitinions\MortgageWorkflow.xaml",   
    readerSettings);  
  
ActivityBuilder ab = XamlServices.Load(  
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;  
  
// Prepare the workflow definition for dynamic update.  
DynamicUpdateServices.PrepareForUpdate(ab);  
```  
  
> [!NOTE]
>  <span data-ttu-id="3cf33-128">Bu konuda eşlik örnek kodunu indirmek için bkz: [dinamik güncelleştirme örnek kod](http://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="3cf33-128">To download the sample code that accompanies this topic, see [Dynamic Update sample code](http://go.microsoft.com/fwlink/?LinkId=227905).</span></span>  
  
###  <a name="Update"></a><span data-ttu-id="3cf33-129">İş akışı tanımını istediğiniz değişiklikleri yansıtacak şekilde güncelleştirin</span><span class="sxs-lookup"><span data-stu-id="3cf33-129">Update the workflow definition to reflect the desired changes</span></span>  
 <span data-ttu-id="3cf33-130">İş akışı tanımı güncelleştirmek için hazırlanmış sonra istediğiniz değişiklikleri yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="3cf33-131">Ekleyin veya etkinlikleri kaldırabileceğiniz, Ekle, taşımak veya genel değişkenleri silmek, ekleyin veya bağımsız değişkenleri kaldırın ve etkinlik temsilciler imza için değişiklik.</span><span class="sxs-lookup"><span data-stu-id="3cf33-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="3cf33-132">Çalışan bir etkinlik kaldıramaz veya imza çalışan temsilcisi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3cf33-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="3cf33-133">Kodu kullanarak bu değişiklikler yapılması ya da yeniden barındırılan iş akışı Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="3cf33-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="3cf33-134">Aşağıdaki örnekte, özel bir `VerifyAppraisal` etkinlik gövdesini oluşturan yapar dizisi eklenen `MortgageWorkflow` önceki örnekten.</span><span class="sxs-lookup"><span data-stu-id="3cf33-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>  
  
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
  
###  <a name="Create"></a><span data-ttu-id="3cf33-135">Güncelleştirme eşlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cf33-135">Create the update map</span></span>  
 <span data-ttu-id="3cf33-136">Güncelleştirme için hazırlanan iş akışı tanımı değiştirildi sonra güncelleştirme eşlemesi oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="3cf33-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="3cf33-137">Dinamik güncelleştirme harita oluşturmak için <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3cf33-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="3cf33-138">Bu döndürür bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> çalışma zamanı gerekir böylece bu yüklenmesi ve yeni iş akışı tanımıyla sürdürüldü kalıcı iş akışı örneğini değiştirmek için bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="3cf33-139">Aşağıdaki örnekte, bir dinamik eşleme oluşturulur değiştirilmiş için `MortgageWorkflow` önceki örnekten tanımı.</span><span class="sxs-lookup"><span data-stu-id="3cf33-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 <span data-ttu-id="3cf33-140">Bu güncelleştirme eşlemesi kalıcı iş akışı örnekleri değiştirmek için hemen kullanılabilir veya daha fazla genellikle kaydedilmesi ve güncelleştirmeleri daha sonra uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3cf33-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="3cf33-141">Güncelleştirme eşlemesi kaydetmek için bir dosyaya bir seri hale getirmek için aşağıdaki örnekte gösterildiği gibi yoludur.</span><span class="sxs-lookup"><span data-stu-id="3cf33-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 <span data-ttu-id="3cf33-142">Zaman <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> döndürür, kopyalanan iş akışı tanımı ve çağrısında eklenen diğer dinamik güncelleştirme bilgileri <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> kaldırılır ve değiştirilen iş akışı tanımı sürdürme güncelleştirildiği daha sonra kullanılabilir kaydedilmesi hazır. İş akışı örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3cf33-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="3cf33-143">Aşağıdaki örnekte, değiştirilmiş iş akışı tanımı için kaydedilen `MortgageWorkflow_v2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="3cf33-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v2.xaml`.</span></span>  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a><span data-ttu-id="3cf33-144">İstenen kalıcı iş akışı örnekleri için güncelleştirme eşlemesi Uygula</span><span class="sxs-lookup"><span data-stu-id="3cf33-144">Apply the update map to the desired persisted workflow instances</span></span>  
 <span data-ttu-id="3cf33-145">Güncelleştirme eşlemesi uygulama oluşturduktan sonra herhangi bir zamanda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="3cf33-146">Hemen kullanmaya yapılabilir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> tarafından döndürülen örnek <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, ya da daha sonra güncelleştirme eşlemesi kaydedilmiş bir kopyasını kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="3cf33-147">Bir iş akışı örneği güncelleştirmek için içine yük bir <xref:System.Activities.WorkflowApplicationInstance> kullanarak <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3cf33-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3cf33-148">Ardından, oluşturun bir <xref:System.Activities.WorkflowApplication> güncelleştirilmiş iş akışı tanımı ve istenen kullanarak <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="3cf33-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="3cf33-149">Bu <xref:System.Activities.WorkflowIdentity> özgün iş akışını sürdürmek için kullanılan ve genellikle kalıcı örneği değiştirilmiş yansıtmak için olandan farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="3cf33-150">Bir kez <xref:System.Activities.WorkflowApplication> olan oluşturulan, aşırı yüklemesini kullanarak yüklendiği <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> alan bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>ve ardından bir çağrı ile kaldırıldığında <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3cf33-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3cf33-151">Bu dinamik güncelleştirme uygulanır ve güncelleştirilmiş iş akışı örneği devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-151">This applies the dynamic update and persists the updated workflow instance.</span></span>  
  
```csharp  
// Load the serialized update map.  
DynamicUpdateMap map;  
using (FileStream fs = File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Open))  
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
  
### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="3cf33-152">Güncelleştirilmiş iş akışı örneği'na devam ediliyor</span><span class="sxs-lookup"><span data-stu-id="3cf33-152">Resuming an Updated Workflow Instance</span></span>  
 <span data-ttu-id="3cf33-153">Dinamik güncelleştirme uygulandıktan sonra iş akışı örneği sürdürülebilir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="3cf33-154">Yeni tanımı güncelleştirildiğini Not ve <xref:System.Activities.WorkflowIdentity> kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cf33-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cf33-155">İle çalışma hakkında daha fazla bilgi için <xref:System.Activities.WorkflowApplication> ve <xref:System.Activities.WorkflowIdentity>, bkz:[kullanarak WorkflowIdentity ve sürüm oluşturma](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="3cf33-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see[Using WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span></span>  
  
 <span data-ttu-id="3cf33-156">Aşağıdaki örnekte, `MortgageWorkflow_v1.1.xaml` iş akışı önceki örnekten derlendikten, yüklenir ve güncelleştirilmiş iş akışı tanımı kullanılarak sürdürüldü.</span><span class="sxs-lookup"><span data-stu-id="3cf33-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>  
  
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
>  <span data-ttu-id="3cf33-157">Bu konuda eşlik örnek kodunu indirmek için bkz: [dinamik güncelleştirme örnek kod](http://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="3cf33-157">To download the sample code that accompanies this topic, see [Dynamic Update sample code](http://go.microsoft.com/fwlink/?LinkId=227905).</span></span>
