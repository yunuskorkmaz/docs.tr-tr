---
title: WorkflowIdentity ve sürüm oluşturma kullanma
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 0d8c02dca67d24399972417f9d6485d668215742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-workflowidentity-and-versioning"></a>WorkflowIdentity ve sürüm oluşturma kullanma
<xref:System.Activities.WorkflowIdentity> İş akışı için bir ad ilişkilendirmek için uygulama geliştiricileri bir yol sağlar ve bir <xref:System.Version> bir iş akışı tanımıyla ve kalıcı iş akışı örneği ile ilişkili olması için bu bilgileri. Bu kimlik bilgileri, iş akışı uygulama geliştiriciler tarafından birden çok iş akışı tanımı sürümlerinin yan yana yürütme gibi senaryoları etkinleştirmek için kullanılabilir ve dinamik güncelleştirme gibi diğer işlevleri için dönüm sağlar. Bu konuda kullanmanın genel sağlanır <xref:System.Activities.WorkflowIdentity> ile <xref:System.Activities.WorkflowApplication> barındırma. Yan yana yürütme, bir iş akışı hizmetinde iş akışı tanımları hakkında daha fazla bilgi için bkz: [WorkflowServiceHost yan yana sürüm oluşturma](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md). Dinamik güncelleştirme hakkında daha fazla bilgi için bkz: [dinamik güncelleştirme](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).  
  
## <a name="in-this-topic"></a>Bu konuda  
  
-   [WorkflowIdentity kullanma](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [WorkflowIdentity kullanılarak yan yana yürütme](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [İş akışı sürüm desteklemek için .NET Framework 4 Kalıcılık veritabanlarını yükseltme](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [Veritabanı şeması yükseltmek için](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
##  <a name="UsingWorkflowIdentity"></a> WorkflowIdentity kullanma  
 Kullanılacak <xref:System.Activities.WorkflowIdentity>, örnek oluşturmak, yapılandırın ve bu ilişkilendirmeyi bir <xref:System.Activities.WorkflowApplication> örneği. A <xref:System.Activities.WorkflowIdentity> örneğini tanımlayan üç parça bilgi içerir. <xref:System.Activities.WorkflowIdentity.Name%2A> ve <xref:System.Activities.WorkflowIdentity.Version%2A> içeren bir ad ve bir <xref:System.Version> ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer gibi bilgileri içeren ek bir dize istenen bilgileri belirtmek için kullanılır. A <xref:System.Activities.WorkflowIdentity> üç özelliklerini birbirinden farklı olan benzersiz <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> tüm kişisel bilgileri (PII) içermemesi gerekir. Hakkında bilgi <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan örneğini etkinliğin birkaç farklı noktalarda Hizmetleri yaşam döngüsü yapılandırılmış tüm izleme için çalışma zamanı tarafından yayınlanır. İzleme WF PII (hassas kullanıcı verileri) gizlemek için herhangi bir mekanizma yok. Bu nedenle, bir <xref:System.Activities.WorkflowIdentity> örneği içeremez herhangi bir PII veri kayıtları izleme içinde çalışma zamanı tarafından gösterilen ve izleme kayıtları görüntülemek için erişimi olan herkes tarafından görülebilir.  
  
 Aşağıdaki örnekte, bir <xref:System.Activities.WorkflowIdentity> oluşturulur ve kullanılarak oluşturulan bir iş akışı örneğiyle ilişkili bir `MortgageWorkflow` iş akışı tanımı.  
  
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
  
 Yeniden yükleme ve bir iş akışını sürdürme bir <xref:System.Activities.WorkflowIdentity> eşleşecek şekilde yapılandırılmış <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneği kullanılmalıdır.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Varsa <xref:System.Activities.WorkflowIdentity> iş akışı örneği yeniden yükleme işlemi kalıcı eşleşmediğinde kullanılan <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> atılır. Aşağıdaki örnekte bir yük üzerinde girişimde `MortgageWorkflow` önceki örnekte kalıcı örneği. Bu yükleme denemesi kullanılarak yapılan bir <xref:System.Activities.WorkflowIdentity> kalıcı örneği eşleşmiyor ev kredisi iş akışı, daha yeni bir sürümü için yapılandırılmış.  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 Önceki kod zaman yürütülür, aşağıdaki <xref:System.Activities.VersionMismatchException> atılır.  
  
 **WorkflowIdentity ('MortgageWorkflow v1; Sürüm 1.0.0.0' =) yüklenen örneğini WorkflowIdentity eşleşmiyor ('MortgageWorkflow v2; Sürüm 2.0.0.0' =) sağlanan iş akışı tanımı. Örneği farklı bir tanımı kullanılarak yüklenebilir veya dinamik güncelleştirme kullanma güncelleştirildi.**  
###  <a name="SxS"></a> WorkflowIdentity kullanılarak yan yana yürütme  
 <xref:System.Activities.WorkflowIdentity> birden fazla sürümünü bir iş akışı yan yana yürütme kolaylaştırmak için kullanılabilir. Yaygın bir senaryo, bir uzun süre çalışan iş akışı iş gereksinimlerine değiştiriyor. Güncelleştirilmiş bir sürümünü dağıtıldığında birçok iş akışı örneği çalışıyor. Ana bilgisayar uygulaması, güncelleştirilmiş iş akışı tanımını yeni örnekleri başlatırken kullanmak üzere yapılandırılabilir ve örnekleri edilirken doğru iş akışı tanımı sağlamak için konak uygulamanın sorumluluğundadır. <xref:System.Activities.WorkflowIdentity> tanımlamak ve iş akışı örnekleri sürdürme eşleşen iş akışı tanımı sağlamak için kullanılabilir.  
  
 Alınacak <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneğinin <xref:System.Activities.WorkflowApplication.GetInstance%2A> yöntemi kullanılır. <xref:System.Activities.WorkflowApplication.GetInstance%2A> Yöntemi alır <xref:System.Activities.WorkflowApplication.Id%2A> kalıcı iş akışı örneğinin ve <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> kalıcı örneği içerir ve döndüren bir <xref:System.Activities.WorkflowApplicationInstance>. A <xref:System.Activities.WorkflowApplicationInstance> , ilişkili dahil olmak üzere bir kalıcı iş akışı örneği hakkında bilgi içeren <xref:System.Activities.WorkflowIdentity>. Bu ilişkili <xref:System.Activities.WorkflowIdentity> yükleme ve iş akışı örneği sürdürme doğru iş akışı tanımı sağlamak için ana bilgisayar tarafından kullanılabilir.  
  
> [!NOTE]
>  Bir null <xref:System.Activities.WorkflowIdentity> geçerli olduğundan ve ilişkili olmadan kalıcı örnekleri eşlemek için ana bilgisayar tarafından kullanılan <xref:System.Activities.WorkflowIdentity> uygun iş akışı tanımı. Bu senaryo, iş akışı sürüm oluşturma iş akışı uygulaması başlangıçta yazılmadı veya uygulamanın gelen yükseltildiğinde ortaya çıkabilir [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]. Daha fazla bilgi için bkz: [destek iş akışı sürüm oluşturma için .NET Framework 4 Kalıcılık veritabanlarını yükseltme](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
 Aşağıdaki örnekte bir `Dictionary<WorkflowIdentity, Activity>` ilişkilendirmek için kullanılan <xref:System.Activities.WorkflowIdentity> örnekleriyle eşleşen iş akışı tanımları ve iş akışı kullanarak başlatıldığından `MortgageWorkflow` ile ilişkili iş akışı tanımı `identityV1` <xref:System.Activities.WorkflowIdentity>.  
  
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
  
 Aşağıdaki örnekte, çağırarak önceki örnekten kalıcı iş akışı örneğiyle ilgili bilgiler alınır <xref:System.Activities.WorkflowApplication.GetInstance%2A>ve kalıcı <xref:System.Activities.WorkflowIdentity> bilgi eşleşen iş akışı tanımı almak için kullanılır. Bu bilgileri yapılandırmak için kullanılan <xref:System.Activities.WorkflowApplication>, ve ardından iş akışını yüklenir. Çünkü unutmayın <xref:System.Activities.WorkflowApplication.Load%2A> alan aşırı <xref:System.Activities.WorkflowApplicationInstance> kullanılan <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> üzerinde yapılandırılmışsa <xref:System.Activities.WorkflowApplicationInstance> tarafından kullanılan <xref:System.Activities.WorkflowApplication> ve bu nedenle, <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği yapılandırılması gerekmez.  
  
> [!NOTE]
>  Varsa <xref:System.Activities.WorkflowApplication.InstanceStore%2A> özelliği ayarlanmışsa, onu aynı ayarlanmalıdır <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> örneği tarafından kullanılan <xref:System.Activities.WorkflowApplicationInstance> veya başka bir <xref:System.ArgumentException> aşağıdaki iletiyle oluşturulacaktır: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.  
  
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
  
##  <a name="UpdatingWF4PersistenceDatabases"></a> İş akışı sürüm desteklemek için .NET Framework 4 Kalıcılık veritabanlarını yükseltme  
 SqlWorkflowInstanceStoreSchemaUpgrade.sql veritabanı komut dosyası kullanılarak oluşturulan Kalıcılık veritabanları yükseltmek için sağlanan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] veritabanı komut dosyaları. Bu komut dosyası içinde sunulan yeni sürüm özelliklerini desteklemek için veritabanlarını güncelleştirmeleri [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Hiç kalıcı iş akışı örneği veritabanlarında varsayılan sürüm değerleri verilir ve yan yana yürütme ve dinamik güncelleştirme yer alabilir.  
  
 Varsa bir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] iş akışı uygulama verilen betiği kullanarak yükseltilmemiş bir Kalıcılık veritabanı üzerinde yeni sürüm özelliklerini kullanma herhangi bir Kalıcılık işlem çalışır bir <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> aşağıdakine benzer bir ileti ile oluşturulur İleti.  
  
 **SqlWorkflowInstanceStore '4.0.0.0' veritabanı sürümü vardır. Bu veritabanı sürümü karşı InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' çalıştırılamıyor.  Lütfen '4.5.0.0' veritabanına yükseltin.**  
###  <a name="ToUpgrade"></a> Veritabanı şeması yükseltmek için  
  
1.  SQL Server Management Studio'yu açın ve kalıcılığı veritabanı sunucusuna, örneğin bağlanın **. \SQLEXPRESS**.  
  
2.  Seçin **açık**, **dosya** gelen **dosya** menüsü. Aşağıdaki klasöre göz atın: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
3.  Seçin **SqlWorkflowInstanceStoreSchemaUpgrade.sql** tıklatıp **açık**.  
  
4.  Kalıcılık veritabanında adını seçin **kullanılabilir veritabanları** açılır.  
  
5.  Seçin **yürütme** gelen **sorgu** menüsü.  
  
 Sorgu tamamladığında, veritabanı şeması yükseltilir ve isterseniz, kalıcı iş akışı örnekleri için atanmış varsayılan iş akışı kimliği görüntüleyebilirsiniz. Kalıcılık veritabanınızda genişletin **veritabanları** düğümünün **Object Explorer**, genişletin ve ardından **görünümleri** düğümü. Sağ **System.Activities.DurableInstancing.Instances** ve **ilk 1000 satırı Seç**. Sütunları sonuna kaydırın ve görünümüne eklenen altı ek sütunlar olduğuna dikkat edin: **IdentityName**, **IdentityPackage**, **yapı**, **önemli** , **Küçük**, ve **düzeltme**. Kalıcı bir iş akışı bir değeri olur **NULL** bu alanları için null iş akışı kimliği temsil eden.
