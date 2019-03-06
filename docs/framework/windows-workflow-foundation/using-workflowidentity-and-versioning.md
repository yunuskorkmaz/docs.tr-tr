---
title: Workflowıdentity ve sürüm oluşturma kullanma
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: ad1d3385801b451795c6be321094851339a55f81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373432"
---
# <a name="using-workflowidentity-and-versioning"></a>Workflowıdentity ve sürüm oluşturma kullanma
<xref:System.Activities.WorkflowIdentity> uygulama geliştiricilerinin'bir ad ilişkilendirmek için iş akışı için bir yol sağlar ve bir <xref:System.Version> bir iş akışı tanımıyla ve kalıcı iş akışı örneğiyle ilişkili olması bu bilgileri. Bu kimlik bilgileri birden çok iş akışı tanımı sürümünün yan yana yürütme gibi senaryoları etkinleştirmek için iş akışı uygulama geliştiricileri tarafından kullanılabilir ve dinamik güncelleştirme gibi diğer işlevleri için temel sağlar. Bu konuda kullanarak genel sağlanır <xref:System.Activities.WorkflowIdentity> ile <xref:System.Activities.WorkflowApplication> barındırma. Yan yana yürütme bir iş akışı hizmeti içinde iş akışı tanımları hakkında daha fazla bilgi için bkz: [WorkflowServiceHost yan yana sürüm oluşturma](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Dinamik güncelleştirme hakkında daha fazla bilgi için bkz: [dinamik güncelleştirme](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).  
  
## <a name="in-this-topic"></a>Bu konuda  
  
-   [Workflowıdentity kullanma](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [Workflowıdentity kullanma yan yana yürütme](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [İş akışı sürümü oluşturma desteği için .NET Framework 4 Kalıcılık veritabanlarını yükseltme](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [Veritabanı şemasına yükseltmek için](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
## <a name="UsingWorkflowIdentity"></a> Workflowıdentity kullanma  
 Kullanılacak <xref:System.Activities.WorkflowIdentity>, örnek oluşturma, yapılandırma ve ilişkilendirin bir <xref:System.Activities.WorkflowApplication> örneği. A <xref:System.Activities.WorkflowIdentity> örneği tanımlayıcı üç parça bilgi içerir. <xref:System.Activities.WorkflowIdentity.Name%2A> ve <xref:System.Activities.WorkflowIdentity.Version%2A> içeren bir ad ve bir <xref:System.Version> ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer gibi bilgileri içeren ek bir dize istenen bilgileri belirtmek için kullanılabilir. A <xref:System.Activities.WorkflowIdentity> üç özelliklerini birbirinden farklı olduğunda benzersiz <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> tüm kişisel bilgileri (PII) içermemelidir. Hakkında bilgi <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan bir örneği yaşam döngüsü Hizmetleri etkinliğin birkaç farklı noktalarda yapılandırılmış tüm izleme için çalışma zamanı tarafından yayılır. İzleme WF PII (hassas kullanıcı verileri) gizlemek için herhangi bir mekanizma yoktur. Bu nedenle, bir <xref:System.Activities.WorkflowIdentity> örneği kayıtları izleme, çalışma zamanı tarafından yayılan ve izleme kayıtları görüntüleme erişimi olan herkes tarafından görülebilir tüm PII verileri içermemelidir.  
  
 Aşağıdaki örnekte, bir <xref:System.Activities.WorkflowIdentity> oluşturulur ve kullanılarak oluşturulan bir iş akışı örneği ile ilişkili bir `MortgageWorkflow` iş akışı tanımı.  
  
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
  
 Yeniden yükleme ve bir iş akışını sürdürme bir <xref:System.Activities.WorkflowIdentity> eşleşecek şekilde yapılandırılmış <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneğinin kullanılması gerekir.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Varsa <xref:System.Activities.WorkflowIdentity> iş akışı örneği yeniden yükleme işlemi kalıcı eşleşmediğinde kullanılan <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> oluşturulur. Yükleme girişiminden yapılmaz aşağıdaki örnekte `MortgageWorkflow` önceki örnekte trvalý örneği. Bu yükleme girişiminden kullanılarak yapılan bir <xref:System.Activities.WorkflowIdentity> kalıcı örneği eşleşmeyen ipotek iş akışı, daha yeni bir sürümü için yapılandırılmış.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Önceki kodun ne zaman çalıştırılır, aşağıdaki <xref:System.Activities.VersionMismatchException> oluşturulur.  
  
 **Workflowıdentity ('MortgageWorkflow v1; Sürüm 1.0.0.0' =) yüklü örneğini Workflowıdentity eşleşmiyor ('; MortgageWorkflow v2 Sürüm 2.0.0.0' =) belirtilen iş akışı tanımı. Örneği farklı bir tanımı kullanılarak yüklenebilir veya dinamik güncelleştirme kullanma güncelleştirildi.**  
### <a name="SxS"></a> Workflowıdentity kullanma yan yana yürütme  
 <xref:System.Activities.WorkflowIdentity> birden çok sürümünün bir iş akışı yan yana yürütme kolaylaştırmak için kullanılabilir. Sık karşılaşılan senaryolardan biri, uzun süre çalışan iş akışı iş gereksinimlerine değişiyor. Güncelleştirilmiş bir sürümü dağıtıldığında pek çok iş akışı örneğini çalışıyor olabilir. Ana bilgisayar uygulaması, güncelleştirilmiş iş akışı tanımını yeni örnekler başlatılırken kullanmak için yapılandırılabilir ve örnekleri çıkıldığında doğru iş akışı tanımı sağlamak için konak uygulamanın sorumluluğundadır. <xref:System.Activities.WorkflowIdentity> eşleşen iş akışı tanımı sürdürme iş akışı örnekleri zaman sağlamak üzere kullanılabilir.  
  
 Alınacak <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneğinin <xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi kullanılır. <xref:System.Activities.WorkflowApplication.GetInstance%2A> Yöntemi <xref:System.Activities.WorkflowApplication.Id%2A> kalıcı iş akışı örneğinin ve <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> döndürür ve kalıcı örneği içeren bir <xref:System.Activities.WorkflowApplicationInstance>. A <xref:System.Activities.WorkflowApplicationInstance> ilişkili dahil olmak üzere bir kalıcı iş akışı örneğiyle ilgili bilgiler içeren <xref:System.Activities.WorkflowIdentity>. Bu ilişkili <xref:System.Activities.WorkflowIdentity> yükleniyor ve iş akışı örneği sürdürme doğru iş akışı tanımı sağlamak için ana bilgisayar tarafından kullanılabilir.  
  
> [!NOTE]
>  Bir null <xref:System.Activities.WorkflowIdentity> geçerli olduğundan ve ilişkili olmadan kalıcı örnekleri eşlemek için ana bilgisayar tarafından kullanılan <xref:System.Activities.WorkflowIdentity> uygun iş akışı tanımı için. Bu senaryo, iş akışı sürüm oluşturma iş akışı uygulaması başlangıçta yazılmadı olduğunda veya bir uygulama uygulamasından yükseltilen oluşabilir [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Daha fazla bilgi için [destek iş akışı sürüm oluşturma için .NET Framework 4 Kalıcılık veritabanı yükseltme](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
 Aşağıdaki örnekte bir `Dictionary<WorkflowIdentity, Activity>` ilişkilendirmek için kullanılan <xref:System.Activities.WorkflowIdentity> kullanarak eşleşen iş akışı tanımlarını ve bir iş akışı örneği başlatıldığında `MortgageWorkflow` ile ilişkili iş akışı tanımı, `identityV1` <xref:System.Activities.WorkflowIdentity>.  
  
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
  
 Aşağıdaki örnekte, önceki örnekte kalıcı iş akışı örneğiyle ilgili bilgiler çağırarak alınır <xref:System.Activities.WorkflowApplication.GetInstance%2A>ve kalıcı <xref:System.Activities.WorkflowIdentity> bilgi eşleşen iş akışı tanımı almak için kullanılır. Bu bilgileri yapılandırmak için kullanılan <xref:System.Activities.WorkflowApplication>, ve ardından iş akışını yüklenir. Dikkat edin çünkü <xref:System.Activities.WorkflowApplication.Load%2A> alan aşırı yüklemesini <xref:System.Activities.WorkflowApplicationInstance> kullanılan <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> üzerinde yapılandırılmışsa <xref:System.Activities.WorkflowApplicationInstance> tarafından kullanılan <xref:System.Activities.WorkflowApplication> ve bu nedenle kendi <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği yapılandırılması gerekmez.  
  
> [!NOTE]
>  Varsa <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği ayarlanmışsa, bunu aynı ayarlanmalıdır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> örneği tarafından kullanılan <xref:System.Activities.WorkflowApplicationInstance> veya başka bir <xref:System.ArgumentException> şu ileti ile oluşturulur: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.  
  
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
  
## <a name="UpdatingWF4PersistenceDatabases"></a> İş akışı sürümü oluşturma desteği için .NET Framework 4 Kalıcılık veritabanlarını yükseltme  
 SqlWorkflowInstanceStoreSchemaUpgrade.sql veritabanı betiği kullanılarak oluşturulan Kalıcılık veritabanları yükseltmek için sağlanan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] veritabanı komut dosyaları. Bu betik güncelleştirmeleri de kullanıma sunulan yeni sürüm oluşturma özellikleri desteklemek için veritabanlarını [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Tüm kalıcı iş akışı örnekleri veritabanlarındaki varsayılan sürüm değerleri verilir ve yan yana yürütme ve dinamik güncelleştirme içinde yer alabilirler.  
  
 Varsa bir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] iş akışı uygulama sağlanan komut dosyasını kullanarak yükseltilmedi Kalıcılık veritabanı üzerinde yeni sürüm oluşturma özelliklerine herhangi bir Kalıcılık işlemleri çalışır bir <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> aşağıdakine benzer bir ileti ile oluşturulur İleti.  
  
 **SqlWorkflowInstanceStore '4.0.0.0' veritabanı sürümüne sahip. Bu veritabanı sürümü karşı InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' çalıştırılamaz.  Lütfen '4.5.0.0' veritabanına yükseltin.**  
### <a name="ToUpgrade"></a> Veritabanı şemasına yükseltmek için  
  
1.  Örneğin Kalıcılık veritabanı sunucusuna bağlanmak ve SQL Server Management Studio'yu açın **. \SQLEXPRESS**.  
  
2.  Seçin **açık**, **dosya** gelen **dosya** menüsü. Şu klasöre göz atın: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
3.  Seçin **SqlWorkflowInstanceStoreSchemaUpgrade.sql** tıklatıp **açık**.  
  
4.  Kalıcılık veritabanı adını seçin **kullanılabilir veritabanlarını** açılır.  
  
5.  Seçin **yürütme** gelen **sorgu** menüsü.  
  
 Sorgu tamamladığında, veritabanı şemasını yükseltilir ve isterseniz, kalıcı iş akışı örnekleri için atanan varsayılan iş akışı kimliğini görüntüleyebilirsiniz. Kalıcılık veritabanınızı genişletin **veritabanları** düğümünün **Nesne Gezgini**ve ardından **görünümleri** düğümü. Sağ **System.Activities.DurableInstancing.Instances** ve **ilk 1000 satırı Seç**. Sütunları sonuna kaydırın ve görünüme eklenen altı ek sütunlar olduğuna dikkat edin: **IdentityName**, **IdentityPackage**, **derleme**, **ana**, **küçük**, ve **düzeltme**. Kalıcı bir iş akışı değerine sahip olacak **NULL** bu alanlar için null iş akışı kimliğini temsil eden.
