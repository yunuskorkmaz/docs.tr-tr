---
title: WorkflowIdentity Kullanma ve Sürüm Oluşturma
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 6b769224edcd9dfc51879c2c99e061a0e3f77e8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958386"
---
# <a name="using-workflowidentity-and-versioning"></a>WorkflowIdentity Kullanma ve Sürüm Oluşturma

<xref:System.Activities.WorkflowIdentity>, iş akışı uygulama geliştiricilerinin bir adı ve ile bir <xref:System.Version> iş akışı tanımıyla ilişkilendirilmesi ve bu bilgilerin kalıcı bir iş akışı örneğiyle ilişkilendirilmesi için bir yol sağlar. Bu kimlik bilgileri, bir iş akışı tanımının birden çok sürümünün yan yana yürütülmesi gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevler için de temel pulu sağlar. Bu konu, barındırma ile <xref:System.Activities.WorkflowIdentity> <xref:System.Activities.WorkflowApplication> kullanmayla ilgili genel bakış sağlar. Bir iş akışı hizmetindeki iş akışı tanımlarının yan yana yürütülmesi hakkında daha fazla bilgi için bkz. [WorkflowServiceHost 'Da yan yana sürüm oluşturma](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Dinamik güncelleştirme hakkında bilgi için bkz. [dinamik güncelleştirme](dynamic-update.md).

## <a name="in-this-topic"></a>Bu konuda

- [WorkflowIdentity kullanma](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [WorkflowIdentity kullanarak yan yana yürütme](using-workflowidentity-and-versioning.md#SxS)

- [.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [Veritabanı şemasını yükseltmek için](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="UsingWorkflowIdentity"></a>WorkflowIdentity kullanma

Kullanmak <xref:System.Activities.WorkflowIdentity>için bir örnek oluşturun, yapılandırın ve bir <xref:System.Activities.WorkflowApplication> örnekle ilişkilendirin. <xref:System.Activities.WorkflowIdentity> Örnek, üç tanımlayıcı bilgi parçasını içerir. <xref:System.Activities.WorkflowIdentity.Name%2A>ve bir ad ve bir <xref:System.Version> <xref:System.Activities.WorkflowIdentity.Version%2A> içerir ve gereklidir <xref:System.Activities.WorkflowIdentity.Package%2A> ve isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir. , Üç özelliklerinden biri diğerinden <xref:System.Activities.WorkflowIdentity>farklıysa benzersizdir. <xref:System.Activities.WorkflowIdentity>

> [!IMPORTANT]
> Bir <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlanabilir bilgiler (PII) içermemelidir. Örnek oluşturmak için <xref:System.Activities.WorkflowIdentity> kullanılan hakkında bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır. WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur. Bu nedenle, <xref:System.Activities.WorkflowIdentity> kayıtlar izlenirken çalışma zamanı tarafından yayınlandığından ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir olabileceğinden bir örnek herhangi bir PII verisi içermemelidir.

Aşağıdaki örnekte, bir <xref:System.Activities.WorkflowIdentity> `MortgageWorkflow` iş akışı tanımı kullanılarak oluşturulan bir iş akışı örneğiyle oluşturulur ve ilişkilendirilir.

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

Bir iş akışını yeniden yüklerken ve sürdürülürken <xref:System.Activities.WorkflowIdentity> , kalıcı iş akışı örneğinin <xref:System.Activities.WorkflowIdentity> ile eşleşecek şekilde yapılandırılan bir, kullanılmalıdır.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

İş akışı örneğini yeniden yüklerken <xref:System.Activities.WorkflowIdentity> <xref:System.Activities.VersionMismatchException> kullanılan, kalıcı ile eşleşmezse, bir atılır. <xref:System.Activities.WorkflowIdentity> Aşağıdaki örnekte, önceki örnekte kalıcı olan örnekte bir yükleme denemesi `MortgageWorkflow` yapılır. Bu yükleme denemesi, kalıcı örnekle eşleşmeyen <xref:System.Activities.WorkflowIdentity> ipotek iş akışının daha yeni bir sürümü için yapılandırılmış kullanılarak yapılır.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

Önceki kod yürütüldüğünde, aşağıdakiler <xref:System.Activities.VersionMismatchException> oluşturulur.

```
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="SxS"></a>WorkflowIdentity kullanarak yan yana yürütme

<xref:System.Activities.WorkflowIdentity>, bir iş akışının birden çok sürümünün bir yandan çalışmasını kolaylaştırmak için kullanılabilir. Tek bir yaygın senaryo, uzun süreli bir iş akışında iş gereksinimlerini değiştiriyor. Bir iş akışının birçok örneği, güncelleştirilmiş bir sürüm dağıtıldığında çalışıyor olabilir. Konak uygulaması, yeni örnekleri başlatırken güncelleştirilmiş iş akışı tanımını kullanacak şekilde yapılandırılabilir ve örnek olarak, örneklere devam edilirken doğru iş akışı tanımını sağlamak için ana bilgisayar uygulamasının sorumluluğundadır. <xref:System.Activities.WorkflowIdentity>, iş akışı örneklerine devam edilirken eşleşen iş akışı tanımını tanımlamak ve sağlamak için kullanılabilir.

Kalıcı bir iş <xref:System.Activities.WorkflowIdentity> akışı örneğini <xref:System.Activities.WorkflowApplication.GetInstance%2A> almak için yöntemi kullanılır. Yöntemi kalıcı iş akışı <xref:System.Activities.WorkflowApplication.Id%2A> örneğini ve <xref:System.Activities.WorkflowApplicationInstance>kalıcı örneği içeren öğesini alır ve döndürür. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> <xref:System.Activities.WorkflowApplication.GetInstance%2A> , İlişkili<xref:System.Activities.WorkflowIdentity>olduğu gibi kalıcı bir iş akışı örneğiyle ilgili bilgiler içerir.<xref:System.Activities.WorkflowApplicationInstance> Bu ilişkili <xref:System.Activities.WorkflowIdentity> , iş akışı örneğini yüklerken ve sürdürülürken doğru iş akışı tanımını sağlamak için ana bilgisayar tarafından kullanılabilir.

> [!NOTE]
> Null <xref:System.Activities.WorkflowIdentity> bir değer geçerlidir ve ana bilgisayar tarafından uygun iş akışı tanımıyla ilişkili <xref:System.Activities.WorkflowIdentity> olmadan kalıcı olan örnekleri eşlemek için kullanılabilir. Bu senaryo, bir iş akışı uygulamasının ilk olarak iş akışı sürümü oluşturma ile yazılmayan veya bir uygulama sürümünden [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]yükseltildiğinde meydana gelebilir. Daha fazla bilgi için bkz. [Iş akışı sürümü oluşturmayı desteklemek için .NET Framework 4 kalıcılık veritabanlarını yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

Aşağıdaki örnekte `Dictionary<WorkflowIdentity, Activity>` , örnekleri eşleşen iş akışı tanımlarıyla <xref:System.Activities.WorkflowIdentity> ilişkilendirmek için kullanılır ve bir `MortgageWorkflow` iş akışı, iş akışı tanımı kullanılarak başlatılır ve bu `identityV1` <xref:System.Activities.WorkflowIdentity>.

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

Aşağıdaki örnekte, önceki örnekteki kalıcı iş akışı örneğiyle ilgili bilgiler çağırarak <xref:System.Activities.WorkflowApplication.GetInstance%2A>alınır ve kalıcı <xref:System.Activities.WorkflowIdentity> bilgiler, eşleşen iş akışı tanımını almak için kullanılır. Bu bilgiler, <xref:System.Activities.WorkflowApplication>öğesini yapılandırmak için kullanılır ve sonra iş akışı yüklenir. <xref:System.Activities.WorkflowApplicationInstance> <xref:System.Activities.WorkflowApplication> Öğesinin kullanıldığı <xref:System.Activities.WorkflowApplication.Load%2A> <xref:System.Activities.WorkflowApplication.InstanceStore%2A> aşırı yükleme, üzerinde<xref:System.Activities.WorkflowApplicationInstance> yapılandırılan öğesinin tarafından kullanıldığı ve bu nedenle özelliğinin yapılandırılması gerekmediği unutulmamalıdır. <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>

> [!NOTE]
> <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> `The instance is configured with a different InstanceStore than this WorkflowApplication.`Özellik ayarlandıysa ,<xref:System.ArgumentException> tarafından <xref:System.Activities.WorkflowApplicationInstance> kullanılan aynı örnekle ayarlanmalıdır, aksi takdirde şu iletiyle birlikte oluşturulur:. <xref:System.Activities.WorkflowApplication.InstanceStore%2A>

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

[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] Veritabanı betikleri kullanılarak oluşturulan kalıcı veritabanlarını yükseltmek için bir SqlWorkflowInstanceStoreSchemaUpgrade. SQL veritabanı betiği sağlanır. Bu betik, .NET Framework 4,5 ' de tanıtılan yeni sürüm oluşturma yeteneklerini destekleyecek şekilde veritabanlarını güncelleştirir. Veritabanlarındaki kalıcı iş akışı örneklerine varsayılan sürüm oluşturma değerleri verilir ve daha sonra yan yana yürütmeye ve Dinamik güncelleştirmeye katılabilirler.

Bir .NET Framework 4,5 iş akışı uygulaması, sunulan betiği <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> kullanılarak yükseltilmemiş bir kalıcılık veritabanında yeni sürüm oluşturma özelliklerini kullanan herhangi bir kalıcılık işlemini denerse, şuna benzer bir iletiyle birlikte oluşur Aşağıdaki ileti.

```
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="ToUpgrade"></a>Veritabanı şemasını yükseltmek için

1. SQL Server Management Studio açın ve Kalıcılık veritabanı sunucusuna bağlanın, örneğin **.\Sqlexpress**.

2. **Dosya** menüsünden **Aç**, **Dosya** ' yı seçin. Aşağıdaki klasöre gidin:`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`

3. **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** ' i seçin ve **Aç**' a tıklayın.

4. **Kullanılabilir veritabanları** açılan listesinden Kalıcılık veritabanının adını seçin.

5. **Sorgu** menüsünden **Yürüt** ' ü seçin.

Sorgu tamamlandığında, veritabanı şeması yükseltilir ve isterseniz, kalıcı iş akışı örneklerine atanmış olan varsayılan iş akışı kimliğini görüntüleyebilirsiniz. **Nesne Gezgini** **veritabanları** düğümünde Kalıcılık veritabanınızı genişletin ve ardından **Görünümler** düğümünü genişletin. **System. Activities. Durableörnek oluşturma. örnekleri** öğesine sağ tıklayın ve **en üstteki 1000 satırları Seç**' i seçin. Sütunların sonuna kaydırın ve görünüme eklenen altı sütun olduğunu unutmayın: **IdentityName**, **IdentityPackage**, **derleme**, **büyük**, **küçük**ve **Düzeltme**. Kalıcı iş akışlarının, null bir iş akışı kimliğini temsil eden bu alanlar için **null** değeri olacaktır.
