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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1d8aff19cc087cf4aea2befb7a39533422aeabd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-update"></a>Dinamik güncelleştirme
Dinamik güncelleştirme kalıcı iş akışı örneği iş akışı tanımını güncelleştirmek için uygulama geliştiricileri iş akışı için bir mekanizma sağlar. Bu yeni gereksinimleri, bir hata düzeltme uygulamak için veya beklenmeyen değişiklikleri uyum sağlayacak şekilde olabilir. Bu konuda sunulan dinamik güncelleştirme işlevlerine genel bakış sağlayan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
## <a name="dynamic-update"></a>Dinamik güncelleştirme  
 Bir kalıcı iş akışı örneği için dinamik güncelleştirmeleri uygulamak için bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> oluşturulur, istediğiniz değişiklikleri yansıtacak şekilde kalıcı iş akışı örneğini değiştirmek nasıl açıklayan çalışma zamanı için yönergeler içerir. Güncelleştirme eşlemesi oluşturulduktan sonra istenen kalıcı iş akışı örneklerine uygulanır. Dinamik güncelleştirme uygulandıktan sonra iş akışı örneği yeni güncelleştirilmiş iş akışı tanımı kullanılarak sürdürülebilir. Oluşturmak ve bir güncelleştirme eşlemesi uygulamak için gereken dört adım vardır.  
  
1.  [Dinamik güncelleştirme iş akışı tanımı hazırlama](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [İş akışı tanımını istediğiniz değişiklikleri yansıtacak şekilde güncelleştirin](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [Güncelleştirme eşlemesi oluşturma](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [İstenen kalıcı iş akışı örnekleri için güncelleştirme eşlemesi Uygula](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  1 ile güncelleştirme eşlemesi oluşturulmasını kapak, 3 adımlarını güncelleştirmeyi uygulamadan bağımsız olarak gerçekleştirilebilir unutmayın. Bu iş akışı Geliştirici güncelleştirme oluşturacak çevrimdışı eşlenen yaygın bir senaryo ve yönetici güncelleştirmeyi daha sonra geçerli olur.  
  
 Bu konu, kalıcı bir derlenmiş bir Xaml iş akışı örneği için yeni bir etkinlik ekleme dinamik güncelleştirme işlemine genel bakış sağlar.  
  
###  <a name="Prepare"></a>Dinamik güncelleştirme iş akışı tanımı hazırlama  
 İstenen iş akışı tanım güncelleştirmesi için hazırlamak için dinamik güncelleştirme işleminin ilk adımında var. Bu çağırarak yapılır <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi ve değiştirmek için iş akışı tanımında geçirme. Bu yöntem doğrular ve tüm ortak etkinlikleri ve bunlar daha sonra değiştirilmiş iş akışı tanımıyla karşılaştırılabilir şekilde etiketlenmesi gereken değişkenler gibi nesneleri tanımlamak için iş akışı ağaç anlatılmaktadır. Bu tamamlandığında, iş akışı ağaç kopyalanabilir ve orijinal iş akışı tanımını bağlı. Güncelleştirme eşlemesi oluşturulduğunda, iş akışı tanımı'nın güncelleştirilmiş sürümü özgün iş akışı tanımıyla karşılaştırılır ve güncelleştirme harita üzerinde farklar temel alınarak oluşturulur.  
  
 Dinamik güncelleştirme, yüklenmiş içine bir Xaml iş akışı hazırlamak için bir <xref:System.Activities.ActivityBuilder>ve ardından <xref:System.Activities.ActivityBuilder> içine geçirilen <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  İle çalışma hakkında daha fazla bilgi için iş akışları seri hale getirilmiş ve <xref:System.Activities.ActivityBuilder>, bkz: [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
 Aşağıdaki örnekte, bir `MortgageWorkflow` tanımı (, oluşur bir <xref:System.Activities.Statements.Sequence> birkaç alt etkinliklerle) içine yüklenir bir <xref:System.Activities.ActivityBuilder>ve dinamik güncelleştirme için hazır. Metodu döndükten sonra <xref:System.Activities.ActivityBuilder> bir kopyasını yanı sıra, orijinal iş akışı tanımını içerir.  
  
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
>  Bu konuda eşlik örnek kodunu indirmek için bkz: [dinamik güncelleştirme örnek kod](http://go.microsoft.com/fwlink/?LinkId=227905).  
  
###  <a name="Update"></a>İş akışı tanımını istediğiniz değişiklikleri yansıtacak şekilde güncelleştirin  
 İş akışı tanımı güncelleştirmek için hazırlanmış sonra istediğiniz değişiklikleri yapılabilir. Ekleyin veya etkinlikleri kaldırabileceğiniz, Ekle, taşımak veya genel değişkenleri silmek, ekleyin veya bağımsız değişkenleri kaldırın ve etkinlik temsilciler imza için değişiklik. Çalışan bir etkinlik kaldıramaz veya imza çalışan temsilcisi değiştirin. Kodu kullanarak bu değişiklikler yapılması ya da yeniden barındırılan iş akışı Tasarımcısı'nda. Aşağıdaki örnekte, özel bir `VerifyAppraisal` etkinlik gövdesini oluşturan yapar dizisi eklenen `MortgageWorkflow` önceki örnekten.  
  
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
  
###  <a name="Create"></a>Güncelleştirme eşlemesi oluşturma  
 Güncelleştirme için hazırlanan iş akışı tanımı değiştirildi sonra güncelleştirme eşlemesi oluşturulamıyor. Dinamik güncelleştirme harita oluşturmak için <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> yöntemi çağrılır. Bu döndürür bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> çalışma zamanı gerekir böylece bu yüklenmesi ve yeni iş akışı tanımıyla sürdürüldü kalıcı iş akışı örneğini değiştirmek için bilgileri içerir. Aşağıdaki örnekte, bir dinamik eşleme oluşturulur değiştirilmiş için `MortgageWorkflow` önceki örnekten tanımı.  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 Bu güncelleştirme eşlemesi kalıcı iş akışı örnekleri değiştirmek için hemen kullanılabilir veya daha fazla genellikle kaydedilmesi ve güncelleştirmeleri daha sonra uygulanır. Güncelleştirme eşlemesi kaydetmek için bir dosyaya bir seri hale getirmek için aşağıdaki örnekte gösterildiği gibi yoludur.  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 Zaman <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> döndürür, kopyalanan iş akışı tanımı ve çağrısında eklenen diğer dinamik güncelleştirme bilgileri <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> kaldırılır ve değiştirilen iş akışı tanımı sürdürme güncelleştirildiği daha sonra kullanılabilir kaydedilmesi hazır. İş akışı örnekleri. Aşağıdaki örnekte, değiştirilmiş iş akışı tanımı için kaydedilen `MortgageWorkflow_v2.xaml`.  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <a name="Apply"></a>İstenen kalıcı iş akışı örnekleri için güncelleştirme eşlemesi Uygula  
 Güncelleştirme eşlemesi uygulama oluşturduktan sonra herhangi bir zamanda yapılabilir. Hemen kullanmaya yapılabilir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> tarafından döndürülen örnek <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, ya da daha sonra güncelleştirme eşlemesi kaydedilmiş bir kopyasını kullanılarak yapılabilir. Bir iş akışı örneği güncelleştirmek için içine yük bir <xref:System.Activities.WorkflowApplicationInstance> kullanarak <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>. Ardından, oluşturun bir <xref:System.Activities.WorkflowApplication> güncelleştirilmiş iş akışı tanımı ve istenen kullanarak <xref:System.Activities.WorkflowIdentity>. Bu <xref:System.Activities.WorkflowIdentity> özgün iş akışını sürdürmek için kullanılan ve genellikle kalıcı örneği değiştirilmiş yansıtmak için olandan farklı olabilir. Bir kez <xref:System.Activities.WorkflowApplication> olan oluşturulan, aşırı yüklemesini kullanarak yüklendiği <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> alan bir <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>ve ardından bir çağrı ile kaldırıldığında <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>. Bu dinamik güncelleştirme uygulanır ve güncelleştirilmiş iş akışı örneği devam ettirir.  
  
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
  
### <a name="resuming-an-updated-workflow-instance"></a>Güncelleştirilmiş iş akışı örneği'na devam ediliyor  
 Dinamik güncelleştirme uygulandıktan sonra iş akışı örneği sürdürülebilir. Yeni tanımı güncelleştirildiğini Not ve <xref:System.Activities.WorkflowIdentity> kullanılması gerekir.  
  
> [!NOTE]
>  İle çalışma hakkında daha fazla bilgi için <xref:System.Activities.WorkflowApplication> ve <xref:System.Activities.WorkflowIdentity>, bkz:[kullanarak WorkflowIdentity ve sürüm oluşturma](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
 Aşağıdaki örnekte, `MortgageWorkflow_v1.1.xaml` iş akışı önceki örnekten derlendikten, yüklenir ve güncelleştirilmiş iş akışı tanımı kullanılarak sürdürüldü.  
  
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
>  Bu konuda eşlik örnek kodunu indirmek için bkz: [dinamik güncelleştirme örnek kod](http://go.microsoft.com/fwlink/?LinkId=227905).
