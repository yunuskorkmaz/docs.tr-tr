---
title: Dinamik güncelleştirme
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: dea930de2103a24aa48b1d0a31a3cbf5fc0ae26c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536225"
---
# <a name="dynamic-update"></a>Dinamik güncelleştirme
Dinamik güncelleştirme, uygulama geliştiricilerinin'bir kalıcı iş akışı örneği iş akışı tanımını güncelleştirmek için iş akışı için bir mekanizma sağlar. Bu, bir hata düzeltmesi, yeni gereksinimleri uygulamak için veya beklenmeyen değişiklikleri uyum sağlamak için olabilir. Bu konuda sunulan dinamik güncelleştirme işlevlerine genel bakış sağlar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
## <a name="dynamic-update"></a>Dinamik güncelleştirme  
 Bir kalıcı iş akışı örneği için dinamik güncelleştirmeleri uygulamak için bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> oluşturulur, istediğiniz değişiklikleri yansıtacak şekilde kalıcı iş akışı örneği değişiklik yapma açıklayan yönergeler çalışma zamanı için içerir. Güncelleştirme eşlemesi oluşturulduktan sonra bu istenen kalıcı iş akışı örneklerine uygulanır. Dinamik güncelleştirme uygulandıktan sonra yeni güncelleştirilmiş iş akışı tanımı kullanarak iş akışı örneği sürdürülebilir. Oluşturma ve bir güncelleştirme eşlemesi uygulamak için gereken dört adım vardır.  
  
1.  [Dinamik güncelleştirme iş akışı tanımı hazırlama](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [İş akışı tanımı, istediğiniz değişiklikleri yansıtacak şekilde güncelleştirin](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [Güncelleştirme eşlemesi oluşturma](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [Güncelleştirme eşlemesi istenen kalıcı iş akışı örnekleri için geçerlidir](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  Adımlar güncelleştirme eşlemesi oluşturulmasını kapsar, 3, 1 güncelleştirmeyi uygulamadan bağımsız olarak gerçekleştirilebilir unutmayın. İş akışı Geliştirici güncelleştirme oluşturduğunuz çevrimdışı harita sık karşılaşılan bir senaryodur ve bir yönetici, güncelleştirmeyi daha sonra uygulanır.  
  
 Bu konu, yeni bir etkinlik için derlenmiş Xaml iş akışı kalıcı bir örneğini ekleme dinamik güncelleştirme işlemine genel bakış sağlar.  
  
###  <a name="Prepare"></a> Dinamik güncelleştirme iş akışı tanımı hazırlama  
 Dinamik güncelleştirme işleminin ilk adımı, istenen iş akışı tanım güncelleştirmesi için hazırlama sağlamaktır. Bu çağrılarak gerçekleştirilir <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi ve değiştirmek için iş akışı tanımında geçirme. Bu yöntem, doğrulama ve iş akışı ağacında, tüm genel etkinlikleri ve bunlar daha sonra değiştirilen iş akışı tanımıyla karşılaştırılabilir şekilde etiketlenmesi gereken değişkenleri gibi nesneleri tanımlamak için size yol gösterir. Bu tamamlandığında iş akışı ağaç kopyalanabilir ve orijinal iş akışının tanımına bağlı. Güncelleştirme eşlemesi oluşturulduğunda, iş akışı tanımının güncelleştirilmiş sürümü özgün iş akışı tanımı ile karşılaştırılır ve güncelleştirme eşlemesi temel farklar üzerinde oluşturulur.  
  
 Dinamik güncelleştirme, yüklenemeyen içine bir Xaml iş akışı hazırlamak için bir <xref:System.Activities.ActivityBuilder>, ardından <xref:System.Activities.ActivityBuilder> yöntemlere geçirilen <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  İle çalışma hakkında daha fazla bilgi için iş akışları seri hale getirilmiş ve <xref:System.Activities.ActivityBuilder>, bkz: [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
 Aşağıdaki örnekte, bir `MortgageWorkflow` tanımı (oluşur, bir <xref:System.Activities.Statements.Sequence> birkaç alt etkinliklerle) içine yüklenen bir <xref:System.Activities.ActivityBuilder>ve ardından dinamik güncelleştirme için hazır. Yöntemin dönüşünün ardından, <xref:System.Activities.ActivityBuilder> özgün iş akışı tanımı ve bunun yanı sıra bir kopyasını içerir.  
  
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
>  Bu konuda eşlik eden örnek kodu indirmek için bkz [dinamik güncelleştirme örnek kodu](https://go.microsoft.com/fwlink/?LinkId=227905).  
  
###  <a name="Update"></a> İş akışı tanımı, istediğiniz değişiklikleri yansıtacak şekilde güncelleştirin  
 İş akışı tanımını güncelleştirmek için hazırlandıktan sonra istenen bir değişiklik yapılamaz. Ekleme veya etkinlikleri kaldırabileceğiniz, Ekle, taşıyın veya genel değişkenleri Sil, ekleyin veya bağımsız değişkenlerini kaldırın ve etkinlik temsilcileri imzası için değişiklik. Çalışan etkinlik kaldıramaz veya çalışan bir temsilcinin imzasını değiştirin. Kodu kullanarak bu değişiklikler yapılması veya yeniden barındırılan iş akışı Tasarımcısı'nda. Aşağıdaki örnekte, özel bir `VerifyAppraisal` etkinlik gövdesini oluşturan yapar dizisi eklenen `MortgageWorkflow` önceki örnekte.  
  
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
  
###  <a name="Create"></a> Güncelleştirme eşlemesi oluşturma  
 Güncelleştirme için hazırlanan iş akışı tanımı değiştirildi sonra güncelleştirme eşleme oluşturulabilir. Bir dinamik güncelleştirme eşlemesi oluşturmak için <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> yöntemi çağrılır. Bu döndürür bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> çalışma zamanı gerekir böylece onu yüklenebilir ve yeni iş akışı tanımıyla sürdürüldü kalıcı iş akışı örneği değiştirmek için bilgileri içerir. Aşağıdaki örnekte, dinamik bir harita oluşturulur için değiştirilmiş `MortgageWorkflow` önceki örnekte tanımı.  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 Bu güncelleştirme eşlemesi kalıcı iş akışı örnekleri değiştirmek için hemen kullanılabilir veya genellikle kaydedilebilir ve daha sonra güncelleştirmelerin uygulanması. Güncelleştirme eşlemesi kaydetmek için tek bir dosyaya seri hale getirmek için aşağıdaki örnekte gösterildiği gibi yoludur.  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 Zaman <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> döndürür, kopyalanan iş akışı tanımı ve çağrıda eklenen diğer dinamik güncelleştirme bilgilerini <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> kaldırılır ve değiştirilen iş akışı tanımı sürdürme güncelleştirildiğinde daha sonra kullanılabilir kaydedilmesi hazır İş akışı örnekleri. Aşağıdaki örnekte, değiştirilen iş akışı tanımı için kaydedilen `MortgageWorkflow_v2.xaml`.  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a> Güncelleştirme eşlemesi istenen kalıcı iş akışı örnekleri için geçerlidir  
 Güncelleştirme eşlemesi uygulama oluşturduktan sonra herhangi bir zamanda gerçekleştirilebilir. Hemen kullanmaya yapılabilir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> tarafından döndürülen örnek <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, ya da daha sonra güncelleştirme haritanın kaydedilen bir kopya kullanılarak yapılabilir. Bir iş akışı örneği güncelleştirmek için içine yüklemek bir <xref:System.Activities.WorkflowApplicationInstance> kullanarak <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>. Ardından, oluşturun bir <xref:System.Activities.WorkflowApplication> güncelleştirilmiş iş akışı tanımı ve istenen kullanarak <xref:System.Activities.WorkflowIdentity>. Bu <xref:System.Activities.WorkflowIdentity> özgün iş akışı kalıcı hale getirmek için kullanılan ve genellikle kalıcı örneği değiştirilmiş yansıtmak için hesaptan farklı olabilir. Bir kez <xref:System.Activities.WorkflowApplication> olan oluşturulan aşırı yüklemesini kullanarak yüklendiği <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> almayan bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>ve ardından bir çağrı ile kaldırıldığında <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>. Bu dinamik güncelleştirme uygulanır ve güncelleştirilmiş iş akışı örneğinin devam ettirir.  
  
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
  
### <a name="resuming-an-updated-workflow-instance"></a>Güncelleştirilmiş iş akışı örneği sürdürme  
 Dinamik güncelleştirme uygulandıktan sonra iş akışı örneği sürdürülebilir. Yeni tanım güncelleştirme olduğunu unutmayın ve <xref:System.Activities.WorkflowIdentity> kullanılmalıdır.  
  
> [!NOTE]
>  İle çalışma hakkında daha fazla bilgi için <xref:System.Activities.WorkflowApplication> ve <xref:System.Activities.WorkflowIdentity>, bkz: [Workflowıdentity kullanma ve sürüm oluşturma](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
 Aşağıdaki örnekte, `MortgageWorkflow_v1.1.xaml` önceki örnekte iş akışı derlendiğinden, yüklenir ve güncelleştirilmiş iş akışı tanımı kullanarak devam ettirildi.  
  
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
>  Bu konuda eşlik eden örnek kodu indirmek için bkz [dinamik güncelleştirme örnek kodu](https://go.microsoft.com/fwlink/?LinkId=227905).
