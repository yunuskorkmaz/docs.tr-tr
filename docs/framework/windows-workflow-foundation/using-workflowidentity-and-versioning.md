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
# <a name="using-workflowidentity-and-versioning"></a>WorkflowIdentity Kullanma ve Sürüm Oluşturma

<xref:System.Activities.WorkflowIdentity>, iş akışı uygulama geliştiricilerinin bir ad ve bir <xref:System.Version> iş akışı tanımıyla ilişkilendirilmesi ve bu bilgilerin kalıcı bir iş akışı örneğiyle ilişkilendirilmesi için bir yol sağlar. Bu kimlik bilgileri, bir iş akışı tanımının birden çok sürümünün yan yana yürütülmesi gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevler için de temel pulu sağlar. Bu konu, <xref:System.Activities.WorkflowApplication> barındırma ile <xref:System.Activities.WorkflowIdentity> kullanımı hakkında genel bakış sağlar. Bir iş akışı hizmetindeki iş akışı tanımlarının yan yana yürütülmesi hakkında daha fazla bilgi için bkz. [WorkflowServiceHost 'Da yan yana sürüm oluşturma](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Dinamik güncelleştirme hakkında bilgi için bkz. [dinamik güncelleştirme](dynamic-update.md).

## <a name="in-this-topic"></a>Bu konuda

- [WorkflowIdentity kullanma](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [WorkflowIdentity kullanarak yan yana yürütme](using-workflowidentity-and-versioning.md#SxS)

- [.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [Veritabanı şemasını yükseltmek için](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="UsingWorkflowIdentity"></a>WorkflowIdentity kullanma

<xref:System.Activities.WorkflowIdentity>kullanmak için bir örnek oluşturun, yapılandırın ve bir <xref:System.Activities.WorkflowApplication> örneğiyle ilişkilendirin. <xref:System.Activities.WorkflowIdentity> örnek, üç tanımlayıcı bilgi parçasını içerir. <xref:System.Activities.WorkflowIdentity.Name%2A> ve <xref:System.Activities.WorkflowIdentity.Version%2A> bir ad ve <xref:System.Version> içerir ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir. <xref:System.Activities.WorkflowIdentity>, üç özelliklerinden herhangi biri başka bir <xref:System.Activities.WorkflowIdentity>farklıysa benzersizdir.

> [!IMPORTANT]
> <xref:System.Activities.WorkflowIdentity>, kişisel olarak tanımlanabilen bilgileri (PII) içermemelidir. Örnek oluşturmak için kullanılan <xref:System.Activities.WorkflowIdentity> hakkındaki bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır. WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur. Bu nedenle, <xref:System.Activities.WorkflowIdentity> bir örnek, kayıtları izlemedeki çalışma zamanı tarafından yayınlandığından PII verileri içermemelidir ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir.

Aşağıdaki örnekte, bir <xref:System.Activities.WorkflowIdentity> oluşturulur ve bir `MortgageWorkflow` iş akışı tanımı kullanılarak oluşturulan iş akışı örneğiyle ilişkilendirilir.

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

Bir iş akışını yeniden yüklerken ve sürdürülürken, kalıcı iş akışı örneğinin <xref:System.Activities.WorkflowIdentity> eşleşecek şekilde yapılandırılan bir <xref:System.Activities.WorkflowIdentity> kullanılmalıdır.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

İş akışı örneğini yeniden yüklerken kullanılan <xref:System.Activities.WorkflowIdentity> kalıcı <xref:System.Activities.WorkflowIdentity>eşleşmediğinden, bir <xref:System.Activities.VersionMismatchException> oluşturulur. Aşağıdaki örnekte, önceki örnekte kalıcı olan `MortgageWorkflow` örneğinde bir yükleme denemesi yapılır. Bu yükleme denemesi, kalıcı örnekle eşleşmeyen ipotek iş akışının daha yeni bir sürümü için yapılandırılmış bir <xref:System.Activities.WorkflowIdentity> kullanılarak yapılır.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

Önceki kod yürütüldüğünde, aşağıdaki <xref:System.Activities.VersionMismatchException> atılır.

```
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="SxS"></a>WorkflowIdentity kullanarak yan yana yürütme

<xref:System.Activities.WorkflowIdentity>, bir iş akışının birden çok sürümünün bir yandan çalışmasını kolaylaştırmak için kullanılabilir. Tek bir yaygın senaryo, uzun süreli bir iş akışında iş gereksinimlerini değiştiriyor. Bir iş akışının birçok örneği, güncelleştirilmiş bir sürüm dağıtıldığında çalışıyor olabilir. Konak uygulaması, yeni örnekleri başlatırken güncelleştirilmiş iş akışı tanımını kullanacak şekilde yapılandırılabilir ve örnek olarak, örneklere devam edilirken doğru iş akışı tanımını sağlamak için ana bilgisayar uygulamasının sorumluluğundadır. <xref:System.Activities.WorkflowIdentity>, iş akışı örneklerine devam edilirken eşleşen iş akışı tanımını tanımlamak ve sağlamak için kullanılabilir.

Kalıcı bir iş akışı örneğinin <xref:System.Activities.WorkflowIdentity> almak için, <xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi kullanılır. <xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi, kalıcı iş akışı örneği ve kalıcı örneği içeren <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> <xref:System.Activities.WorkflowApplication.Id%2A> alır ve bir <xref:System.Activities.WorkflowApplicationInstance>döndürür. <xref:System.Activities.WorkflowApplicationInstance>, ilişkili <xref:System.Activities.WorkflowIdentity>dahil olmak üzere kalıcı bir iş akışı örneğiyle ilgili bilgiler içerir. Bu ilişkili <xref:System.Activities.WorkflowIdentity>, iş akışı örneğini yüklerken ve sürdürülürken doğru iş akışı tanımını sağlamak için ana bilgisayar tarafından kullanılabilir.

> [!NOTE]
> Null <xref:System.Activities.WorkflowIdentity> geçerlidir ve konak tarafından uygun iş akışı tanımına ilişkili <xref:System.Activities.WorkflowIdentity> olmadan kalıcı olan örnekleri eşlemek için kullanılabilir. Bu senaryo, bir iş akışı uygulamasının ilk olarak iş akışı sürümü oluşturma ile yazılmayan veya bir uygulama .NET Framework 4 ' ten yükseltildiğinde meydana gelebilir. Daha fazla bilgi için bkz. [Iş akışı sürümü oluşturmayı desteklemek için .NET Framework 4 kalıcılık veritabanlarını yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

Aşağıdaki örnekte, <xref:System.Activities.WorkflowIdentity> örneklerinin eşleşen iş akışı tanımlarıyla ilişkilendirilmesi için `Dictionary<WorkflowIdentity, Activity>` kullanılır ve bir iş akışı, `identityV1` <xref:System.Activities.WorkflowIdentity>ilişkili `MortgageWorkflow` iş akışı tanımı kullanılarak başlatılır.

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

Aşağıdaki örnekte, önceki örnekteki kalıcı iş akışı örneğiyle ilgili bilgiler <xref:System.Activities.WorkflowApplication.GetInstance%2A>çağırarak alınır ve kalıcı <xref:System.Activities.WorkflowIdentity> bilgileri eşleşen iş akışı tanımını almak için kullanılır. Bu bilgiler <xref:System.Activities.WorkflowApplication>yapılandırmak için kullanılır ve sonra iş akışı yüklenir. <xref:System.Activities.WorkflowApplicationInstance> alan <xref:System.Activities.WorkflowApplication.Load%2A> aşırı yüklemesinin kullanıldığı, <xref:System.Activities.WorkflowApplicationInstance> üzerinde yapılandırılan <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> <xref:System.Activities.WorkflowApplication> tarafından kullanıldığı ve bu nedenle <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliğinin yapılandırılmasına gerek olmadığı unutulmamalıdır.

> [!NOTE]
> <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği ayarlandıysa, <xref:System.Activities.WorkflowApplicationInstance> tarafından kullanılan aynı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> örneği ile ayarlanması gerekir, aksi takdirde şu iletiyle birlikte bir <xref:System.ArgumentException> atılır: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.

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

## <a name="UpdatingWF4PersistenceDatabases"></a>.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme

.NET Framework 4 veritabanı betikleri kullanılarak oluşturulan kalıcı veritabanlarını yükseltmek için bir SqlWorkflowInstanceStoreSchemaUpgrade. SQL veritabanı betiği sağlanır. Bu betik, .NET Framework 4,5 ' de tanıtılan yeni sürüm oluşturma yeteneklerini destekleyecek şekilde veritabanlarını güncelleştirir. Veritabanlarındaki kalıcı iş akışı örneklerine varsayılan sürüm oluşturma değerleri verilir ve daha sonra yan yana yürütmeye ve Dinamik güncelleştirmeye katılabilirler.

.NET Framework 4,5 iş akışı uygulaması, sunulan betiği kullanılarak yükseltilmemiş bir kalıcılık veritabanında yeni sürüm oluşturma özelliklerini kullanan herhangi bir kalıcılık işlemini denerse, aşağıdaki iletiye benzer bir ileti içeren bir <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> oluşturulur.

```
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="ToUpgrade"></a>Veritabanı şemasını yükseltmek için

1. SQL Server Management Studio açın ve Kalıcılık veritabanı sunucusuna bağlanın, örneğin **.\Sqlexpress**.

2. **Dosya** menüsünden **Aç**, **Dosya** ' yı seçin. Şu klasöre gidin: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`

3. **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** ' i seçin ve **Aç**' a tıklayın.

4. **Kullanılabilir veritabanları** açılan listesinden Kalıcılık veritabanının adını seçin.

5. **Sorgu** menüsünden **Yürüt** ' ü seçin.

Sorgu tamamlandığında, veritabanı şeması yükseltilir ve isterseniz, kalıcı iş akışı örneklerine atanmış olan varsayılan iş akışı kimliğini görüntüleyebilirsiniz. **Nesne Gezgini** **veritabanları** düğümünde Kalıcılık veritabanınızı genişletin ve ardından **Görünümler** düğümünü genişletin. **System. Activities. Durableörnek oluşturma. örnekleri** öğesine sağ tıklayın ve **en üstteki 1000 satırları Seç**' i seçin. Sütunların sonuna kaydırın ve görünüme eklenen altı sütun ( **IdentityName**, **IdentityPackage**, **Build**, **ana**, **Minor**ve **Düzeltme**) olduğunu unutmayın. Kalıcı iş akışlarının, null bir iş akışı kimliğini temsil eden bu alanlar için **null** değeri olacaktır.
