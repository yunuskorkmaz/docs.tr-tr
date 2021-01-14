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
# <a name="dynamic-update"></a>Dinamik Güncelleştirme

Dinamik güncelleştirme, iş akışı uygulama geliştiricilerinin kalıcı bir iş akışı örneğinin iş akışı tanımını güncelleştirmesine yönelik bir mekanizma sağlar. Bu, bir hata düzeltmesini veya yeni gereksinimleri uygulayabilir ya da beklenmeyen değişikliklere uyum sağlayabilir. Bu konuda .NET Framework 4,5 ' de tanıtılan dinamik güncelleştirme işlevselliğine genel bakış sunulmaktadır.

## <a name="dynamic-update"></a>Dinamik Güncelleştirme

Kalıcı bir iş akışı örneğine dinamik güncelleştirmeleri uygulamak için, <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> kalıcı iş akışı örneğinin istenen değişiklikleri yansıtacak şekilde nasıl değiştirileceğini açıklayan çalışma zamanına yönelik yönergeler içeren bir oluşturulur. Güncelleştirme haritası oluşturulduktan sonra, istenen kalıcı iş akışı örneklerine uygulanır. Dinamik güncelleştirme uygulandıktan sonra, iş akışı örneği yeni güncelleştirilmiş iş akışı tanımı kullanılarak devam edebilir. Bir güncelleştirme eşlemesi oluşturmak ve uygulamak için dört adım gereklidir.

1. [Dinamik güncelleştirme için iş akışı tanımını hazırlama](dynamic-update.md#Prepare)

2. [İş akışı tanımını istenen değişiklikleri yansıtacak şekilde Güncelleştir](dynamic-update.md#Update)

3. [Güncelleştirme haritasını oluşturma](dynamic-update.md#Create)

4. [Güncelleştirme haritasını istenen kalıcı iş akışı örneklerine Uygula](dynamic-update.md#Apply)

> [!NOTE]
> Güncelleştirme haritasının oluşturulmasını kapsayan 1 ile 3 arasındaki adımların, güncelleştirmeyi uygulamadan bağımsız olarak gerçekleştirilebileceğini unutmayın. İş akışı geliştiricisinin güncelleştirme haritasını çevrimdışı olarak oluşturacak ortak bir senaryo ve daha sonra bir yönetici güncelleştirmeyi uygulayacaktır.

Bu konu, derlenmiş xaml iş akışının kalıcı bir örneğine yeni bir etkinlik eklemenin dinamik güncelleştirme sürecine genel bir bakış sağlar.

### <a name="prepare-the-workflow-definition-for-dynamic-update"></a><a name="Prepare"></a> Dinamik güncelleştirme için iş akışı tanımını hazırlama

Dinamik güncelleştirme işlemindeki ilk adım, istenen iş akışı tanımını güncelleştirme için hazırlamaktır. Bu, <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi çağırarak ve değiştirmek için iş akışı tanımına geçerek yapılır. Bu yöntem, daha sonra değiştirilmiş iş akışı tanımıyla karşılaştırılabilmesi için, genel etkinlikler ve etiketlenmesi gereken değişkenler gibi tüm nesneleri tanımlamak üzere iş akışı ağacını doğrular ve yönlendirir. Bu tamamlandığında, iş akışı ağacı kopyalanır ve özgün iş akışı tanımına eklenir. Güncelleştirme haritası oluşturulduğunda, iş akışı tanımının güncelleştirilmiş sürümü orijinal iş akışı tanımıyla karşılaştırılır ve güncelleştirme haritası farklılıklara göre oluşturulur.

Dinamik güncelleştirme için bir XAML iş akışını hazırlamak üzere, bir öğesine yüklenebilir <xref:System.Activities.ActivityBuilder> ve sonra <xref:System.Activities.ActivityBuilder> öğesine geçirilir <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> .

> [!NOTE]
> Serileştirilmiş iş akışlarıyla çalışma hakkında daha fazla bilgi için <xref:System.Activities.ActivityBuilder> , bkz. [xaml 'de ve xaml 'de iş akışlarını ve etkinlikleri serileştirme](serializing-workflows-and-activities-to-and-from-xaml.md).

Aşağıdaki örnekte, bir `MortgageWorkflow` tanım ( <xref:System.Activities.Statements.Sequence> birkaç alt etkinlikten oluşan bir) bir <xref:System.Activities.ActivityBuilder> olarak yüklenir ve dinamik güncelleştirme için hazırlanır. Yöntem çağrıldıktan sonra, <xref:System.Activities.ActivityBuilder> özgün iş akışı tanımını ve bir kopyayı içerir.

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

### <a name="update-the-workflow-definition-to-reflect-the-desired-changes"></a><a name="Update"></a> İş akışı tanımını istenen değişiklikleri yansıtacak şekilde Güncelleştir

İş akışı tanımı güncelleştirme için hazırlandıktan sonra, istenen değişiklikler yapılabilir. Etkinlik ekleyebilir veya kaldırabilir, ortak değişkenler ekleyebilir, taşıyabilir veya silebilir, bağımsız değişken ekleyebilir veya kaldırabilir ve etkinlik temsilcilerinin imzasında değişiklik yapabilirsiniz. Çalışan bir etkinliği kaldıramaz veya çalışan bir temsilcinin imzasını değiştiremezsiniz. Bu değişiklikler kod kullanılarak veya yeniden barındırılan bir iş akışı tasarımcısında yapılabilir. Aşağıdaki örnekte, bir `VerifyAppraisal` önceki örnekteki öğesinin gövdesini oluşturan diziye özel bir etkinlik eklenir `MortgageWorkflow` .

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

### <a name="create-the-update-map"></a><a name="Create"></a> Güncelleştirme haritasını oluşturma

Güncelleştirme için hazırlanan iş akışı tanımı değiştirildikten sonra, güncelleştirme haritası oluşturulabilir. Dinamik bir güncelleştirme eşlemesi oluşturmak için <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> yöntemi çağrılır. Bu <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> , çalışma zamanının, yeni iş akışı tanımıyla yüklenip devam edebilmesi için kalıcı bir iş akışı örneğini değiştirmesi gereken bilgileri içeren bir döndürür. Aşağıdaki örnekte, önceki örnekteki değiştirilmiş tanım için dinamik bir eşleme oluşturulur `MortgageWorkflow` .

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

Bu güncelleştirme eşlemesi kalıcı iş akışı örneklerini değiştirmek için hemen kullanılabilir veya genellikle kaydedilebilir ve güncelleştirmeler daha sonra uygulanabilir. Güncelleştirme haritasını kaydetmek için bir yol, aşağıdaki örnekte gösterildiği gibi bir dosyaya serileştirilmelidir.

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>Döndüğünde, kopyalanmış iş akışı tanımı ve çağrısına eklenen diğer dinamik güncelleştirme bilgileri <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> kaldırılır ve değiştirilen iş akışı örnekleri, daha sonra güncelleştirilmiş iş akışı örneklerine devam edilirken kullanılabilmesi için kaydedilir. Aşağıdaki örnekte, değiştirilen iş akışı tanımı öğesine kaydedilir `MortgageWorkflow_v1.1.xaml` .

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="apply-the-update-map-to-the-desired-persisted-workflow-instances"></a><a name="Apply"></a> Güncelleştirme haritasını istenen kalıcı iş akışı örneklerine Uygula

Güncelleştirme haritasının uygulanması, oluşturulduktan sonra herhangi bir zamanda yapılabilir. <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>Tarafından döndürülen örneği kullanarak hemen yapılabilir <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> veya daha sonra güncelleştirme haritasının kaydedilmiş bir kopyası kullanılarak yapılabilir. Bir iş akışı örneğini güncelleştirmek için bir <xref:System.Activities.WorkflowApplicationInstance> kullanarak yükleyin <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType> . Ardından, <xref:System.Activities.WorkflowApplication> güncelleştirilmiş iş akışı tanımını ve istediğiniz öğesini kullanarak bir oluşturun <xref:System.Activities.WorkflowIdentity> . Bu, <xref:System.Activities.WorkflowIdentity> özgün iş akışını sürdürmek için kullanılandan farklı olabilir ve genellikle kalıcı örneğin değiştirildiğini yansıtacak şekilde yapılır. Oluşturulduktan sonra, <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> ' a sahip olan aşırı yüklemesi kullanılarak yüklenir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> ve sonra öğesine çağrısıyla birlikte kaldırılır <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType> . Bu, dinamik güncelleştirmeyi uygular ve güncelleştirilmiş iş akışı örneği devam ettirir.

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

### <a name="resuming-an-updated-workflow-instance"></a>Güncelleştirilmiş Iş akışı örneği sürdürülüyor

Dinamik güncelleştirme uygulandıktan sonra iş akışı örneği devam edebilir. Yeni güncelleştirilmiş tanımın ve <xref:System.Activities.WorkflowIdentity> kullanılması gerektiğini unutmayın.

> [!NOTE]
> Ve ile çalışma hakkında daha fazla bilgi için <xref:System.Activities.WorkflowApplication> <xref:System.Activities.WorkflowIdentity> bkz. [Workflowwıdentity ve sürümü kullanma](using-workflowidentity-and-versioning.md).

Aşağıdaki örnekte, `MortgageWorkflow_v1.1.xaml` önceki örnekteki iş akışı derlenmiştir ve güncelleştirilmiş iş akışı tanımı kullanılarak yüklenir ve sürdürülür.

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
