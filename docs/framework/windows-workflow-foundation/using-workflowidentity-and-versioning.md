---
title: WorkflowIdentity Kullanma ve Sürüm Oluşturma
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 1d31739c135dbb518f05c40ba802c782b6817bff
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855640"
---
# <a name="using-workflowidentity-and-versioning"></a>WorkflowIdentity Kullanma ve Sürüm Oluşturma

<xref:System.Activities.WorkflowIdentity>, iş akışı uygulama geliştiricilerinin bir adı ve <xref:System.Version> ile bir iş akışı tanımıyla ilişkilendirilmesi ve bu bilgilerin kalıcı bir iş akışı örneğiyle ilişkilendirilmesi için bir yol sağlar. Bu kimlik bilgileri, bir iş akışı tanımının birden çok sürümünün yan yana yürütülmesi gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevler için de temel pulu sağlar. Bu konu, barındırma ile kullanmayla ilgili genel bakış sağlar <xref:System.Activities.WorkflowIdentity> <xref:System.Activities.WorkflowApplication> . Bir iş akışı hizmetindeki iş akışı tanımlarının yan yana yürütülmesi hakkında daha fazla bilgi için bkz. [WorkflowServiceHost 'Da yan yana sürüm oluşturma](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Dinamik güncelleştirme hakkında bilgi için bkz. [dinamik güncelleştirme](dynamic-update.md).

## <a name="in-this-topic"></a>Bu konuda

- [WorkflowIdentity kullanma](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [WorkflowIdentity kullanarak yan yana yürütme](using-workflowidentity-and-versioning.md#SxS)

- [.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [Veritabanı şemasını yükseltmek için](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="using-workflowidentity"></a><a name="UsingWorkflowIdentity"></a>WorkflowIdentity kullanma

Kullanmak için <xref:System.Activities.WorkflowIdentity> bir örnek oluşturun, yapılandırın ve bir <xref:System.Activities.WorkflowApplication> örnekle ilişkilendirin. <xref:System.Activities.WorkflowIdentity>Örnek, üç tanımlayıcı bilgi parçasını içerir. <xref:System.Activities.WorkflowIdentity.Name%2A>ve bir <xref:System.Activities.WorkflowIdentity.Version%2A> ad ve bir içerir ve <xref:System.Version> gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir. , <xref:System.Activities.WorkflowIdentity> Üç özelliklerinden biri diğerinden farklıysa benzersizdir <xref:System.Activities.WorkflowIdentity> .

> [!IMPORTANT]
> Bir <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlanabilir bilgiler (PII) içermemelidir. <xref:System.Activities.WorkflowIdentity>Örnek oluşturmak için kullanılan hakkında bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır. WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur. Bu nedenle, <xref:System.Activities.WorkflowIdentity> kayıtlar izlenirken çalışma zamanı tarafından yayınlandığından ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir olabileceğinden bir örnek herhangi BIR PII verisi içermemelidir.

Aşağıdaki örnekte, bir <xref:System.Activities.WorkflowIdentity> iş akışı tanımı kullanılarak oluşturulan bir iş akışı örneğiyle oluşturulur ve ilişkilendirilir `MortgageWorkflow` .

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

Bir iş akışını yeniden yüklerken ve sürdürülürken, <xref:System.Activities.WorkflowIdentity> <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneğinin ile eşleşecek şekilde yapılandırılan bir, kullanılmalıdır.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

<xref:System.Activities.WorkflowIdentity>İş akışı örneğini yeniden yüklerken kullanılan, kalıcı ile eşleşmezse <xref:System.Activities.WorkflowIdentity> , bir <xref:System.Activities.VersionMismatchException> atılır. Aşağıdaki örnekte, `MortgageWorkflow` Önceki örnekte kalıcı olan örnekte bir yükleme denemesi yapılır. Bu yükleme denemesi, <xref:System.Activities.WorkflowIdentity> kalıcı örnekle eşleşmeyen ipotek iş akışının daha yeni bir sürümü için yapılandırılmış kullanılarak yapılır.

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

Önceki kod yürütüldüğünde, aşağıdakiler <xref:System.Activities.VersionMismatchException> oluşturulur.

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="side-by-side-execution-using-workflowidentity"></a><a name="SxS"></a>WorkflowIdentity kullanarak yan yana yürütme

<xref:System.Activities.WorkflowIdentity>, bir iş akışının birden çok sürümünün bir yandan çalışmasını kolaylaştırmak için kullanılabilir. Tek bir yaygın senaryo, uzun süreli bir iş akışında iş gereksinimlerini değiştiriyor. Bir iş akışının birçok örneği, güncelleştirilmiş bir sürüm dağıtıldığında çalışıyor olabilir. Konak uygulaması, yeni örnekleri başlatırken güncelleştirilmiş iş akışı tanımını kullanacak şekilde yapılandırılabilir ve örnek olarak, örneklere devam edilirken doğru iş akışı tanımını sağlamak için ana bilgisayar uygulamasının sorumluluğundadır. <xref:System.Activities.WorkflowIdentity>, iş akışı örneklerine devam edilirken eşleşen iş akışı tanımını tanımlamak ve sağlamak için kullanılabilir.

<xref:System.Activities.WorkflowIdentity>Kalıcı bir iş akışı örneğini almak için <xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi kullanılır. <xref:System.Activities.WorkflowApplication.GetInstance%2A>Yöntemi <xref:System.Activities.WorkflowApplication.Id%2A> kalıcı iş akışı örneğini ve <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kalıcı örneği içeren öğesini alır ve döndürür <xref:System.Activities.WorkflowApplicationInstance> . <xref:System.Activities.WorkflowApplicationInstance>, İlişkili olduğu gibi kalıcı bir iş akışı örneğiyle ilgili bilgiler içerir <xref:System.Activities.WorkflowIdentity> . Bu ilişkili, <xref:System.Activities.WorkflowIdentity> iş akışı örneğini yüklerken ve sürdürülürken doğru iş akışı tanımını sağlamak için ana bilgisayar tarafından kullanılabilir.

> [!NOTE]
> Null bir değer <xref:System.Activities.WorkflowIdentity> geçerlidir ve ana bilgisayar tarafından <xref:System.Activities.WorkflowIdentity> uygun iş akışı tanımıyla ilişkili olmadan kalıcı olan örnekleri eşlemek için kullanılabilir. Bu senaryo, bir iş akışı uygulamasının ilk olarak iş akışı sürümü oluşturma ile yazılmayan veya bir uygulama .NET Framework 4 ' ten yükseltildiğinde meydana gelebilir. Daha fazla bilgi için bkz. [Iş akışı sürümü oluşturmayı desteklemek için .NET Framework 4 kalıcılık veritabanlarını yükseltme](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

Aşağıdaki örnekte, `Dictionary<WorkflowIdentity, Activity>` <xref:System.Activities.WorkflowIdentity> örnekleri eşleşen iş akışı tanımlarıyla ilişkilendirmek için kullanılır ve bir iş akışı `MortgageWorkflow` , ile ilişkili iş akışı tanımı kullanılarak başlatılır `identityV1` <xref:System.Activities.WorkflowIdentity> .

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

Aşağıdaki örnekte, önceki örnekteki kalıcı iş akışı örneğiyle ilgili bilgiler çağırarak alınır <xref:System.Activities.WorkflowApplication.GetInstance%2A> ve kalıcı <xref:System.Activities.WorkflowIdentity> bilgiler, eşleşen iş akışı tanımını almak için kullanılır. Bu bilgiler, öğesini yapılandırmak için kullanılır <xref:System.Activities.WorkflowApplication> ve sonra iş akışı yüklenir. <xref:System.Activities.WorkflowApplication.Load%2A>Öğesinin kullanıldığı aşırı yükleme, <xref:System.Activities.WorkflowApplicationInstance> <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> üzerinde yapılandırılan öğesinin <xref:System.Activities.WorkflowApplicationInstance> tarafından kullanıldığı <xref:System.Activities.WorkflowApplication> ve bu nedenle <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliğinin yapılandırılması gerekmediği unutulmamalıdır.

> [!NOTE]
> <xref:System.Activities.WorkflowApplication.InstanceStore%2A>Özellik ayarlandıysa, tarafından kullanılan aynı örnekle ayarlanmalıdır, aksi takdirde <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> <xref:System.Activities.WorkflowApplicationInstance> <xref:System.ArgumentException> Şu iletiyle birlikte oluşturulur: `The instance is configured with a different InstanceStore than this WorkflowApplication.` .

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

## <a name="upgrading-net-framework-4-persistence-databases-to-support-workflow-versioning"></a><a name="UpdatingWF4PersistenceDatabases"></a>.NET Framework 4 kalıcılık veritabanlarını Iş akışı sürümü oluşturmayı destekleyecek şekilde yükseltme

.NET Framework 4 veritabanı betikleri kullanılarak oluşturulan kalıcı veritabanlarını yükseltmek için bir SqlWorkflowInstanceStoreSchemaUpgrade. SQL veritabanı betiği sağlanır. Bu betik, .NET Framework 4,5 ' de tanıtılan yeni sürüm oluşturma yeteneklerini destekleyecek şekilde veritabanlarını güncelleştirir. Veritabanlarındaki kalıcı iş akışı örneklerine varsayılan sürüm oluşturma değerleri verilir ve daha sonra yan yana yürütmeye ve Dinamik güncelleştirmeye katılabilirler.

.NET Framework 4,5 iş akışı uygulaması, sunulan betiği kullanılarak yükseltilmemiş bir kalıcılık veritabanında yeni sürüm oluşturma özelliklerini kullanan herhangi bir kalıcılık işlemini denerse, <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> aşağıdaki iletiye benzer bir iletiyle birlikte oluşturulur.

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="to-upgrade-the-database-schema"></a><a name="ToUpgrade"></a>Veritabanı şemasını yükseltmek için

1. SQL Server Management Studio açın ve Kalıcılık veritabanı sunucusuna bağlanın, örneğin **.\Sqlexpress**.

2. **Dosya** menüsünden **Aç**, **Dosya** ' yı seçin. Aşağıdaki klasöre gidin:`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`

3. **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** ' i seçin ve **Aç**' a tıklayın.

4. **Kullanılabilir veritabanları** açılan listesinden Kalıcılık veritabanının adını seçin.

5. **Sorgu** menüsünden **Yürüt** ' ü seçin.

Sorgu tamamlandığında, veritabanı şeması yükseltilir ve isterseniz, kalıcı iş akışı örneklerine atanmış olan varsayılan iş akışı kimliğini görüntüleyebilirsiniz. **Nesne Gezgini** **veritabanları** düğümünde Kalıcılık veritabanınızı genişletin ve ardından **Görünümler** düğümünü genişletin. **System. Activities. Durableörnek oluşturma. örnekleri** öğesine sağ tıklayın ve **en üstteki 1000 satırları Seç**' i seçin. Sütunların sonuna kaydırın ve görünüme eklenen altı sütun ( **IdentityName**, **IdentityPackage**, **Build**, **ana**, **Minor**ve **Düzeltme**) olduğunu unutmayın. Kalıcı iş akışlarının, null bir iş akışı kimliğini temsil eden bu alanlar için **null** değeri olacaktır.
