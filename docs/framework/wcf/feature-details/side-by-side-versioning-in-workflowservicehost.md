---
title: WorkflowServiceHost Yan Yana Sürüm Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: ba0bcdf152ab0ee6632ae472db0bc81496cb6381
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969218"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>WorkflowServiceHost Yan Yana Sürüm Oluşturma
.NET Framework 4,5 ' de sunulan yanyanasürümoluşturma,birişakışıhizmetininbirdençoksürümünütekbiruçnoktadabarındırmanızaolanaksağlar.<xref:System.ServiceModel.Activities.WorkflowServiceHost> Belirtilen yan yana işlevsellik, iş akışı hizmeti 'nin yeni iş akışı tanımı kullanılarak oluşturulması için bir iş akışı hizmetinin yapılandırılmasına izin verir, böylece örnekleri mevcut tanımı kullanarak tamamlanır. Bu konu, kullanarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>iş akışı hizmeti 'nin yan yana yürütmeye genel bir bakış sağlar.  
  
> [!NOTE]
> Bir örneği indirmek ve iş akışı hizmeti 'nin yan yana sürüm oluşturma kılavuzunu izlemek için bkz. [Web 'de barındırılan xamlx Iş akışı hizmeti Ile yan yana sürüm oluşturma](https://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Bir Iş akışı hizmetinde birden çok sürümü barındırma  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bir iş akışının birden çok sürümünün yan yana yürütülmesine izin vermek için yapılandırılabilecek iki özellik içerir: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ve. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>, iş akışı hizmetinin desteklenen sürümlerini içerir ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> her bir iş akışı hizmetini benzersiz şekilde tanımlamak için kullanılır. Bu, bir <xref:System.Activities.WorkflowIdentity> iş akışı hizmeti ile ilişkilendirerek yapılır. , Üç tanımlayıcı bilgi parçasını içerir.<xref:System.Activities.WorkflowIdentity> <xref:System.Activities.WorkflowIdentity.Name%2A>ve bir ad ve bir <xref:System.Version> <xref:System.Activities.WorkflowIdentity.Version%2A> içerir ve gereklidir <xref:System.Activities.WorkflowIdentity.Package%2A> ve isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> Koleksiyonda bulunan her iş akışı hizmetinin benzersiz <xref:System.Activities.WorkflowIdentity>olması gerekir. , Üç özelliklerinden biri diğerinden <xref:System.Activities.WorkflowIdentity>farklıysa benzersizdir. <xref:System.Activities.WorkflowIdentity> `null` ,İçin<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>izin verilen bir değerdir, ancak bir iş akışı hizmetinin `null` yalnızca bir önceki <xref:System.Activities.WorkflowIdentity>sürümü olabilir. <xref:System.Activities.WorkflowIdentity>  
  
> [!IMPORTANT]
> Bir <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlanabilir bilgiler (PII) içermemelidir. <xref:System.Activities.WorkflowIdentity>üç bölümden oluşur: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) ve a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>). Örnek oluşturmak için <xref:System.Activities.WorkflowIdentity> kullanılan hakkında bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır. WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur. Bu nedenle, <xref:System.Activities.WorkflowIdentity> kayıtlar izlenirken çalışma zamanı tarafından yayınlandığından ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir olabileceğinden bir örnek herhangi bir PII verisi içermemelidir.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Bir Iş akışı hizmetinin birden çok sürümünü barındırmak için kurallar  
 Bir Kullanıcı öğesine <xref:System.ServiceModel.Activities.WorkflowServiceHost>ek bir sürüm eklediğinde, bir iş akışı hizmetinin aynı uç nokta ve açıklama kümesiyle barındırılması için karşılanması gereken birkaç koşul vardır. Ek sürümlerden herhangi biri bu koşulları karşılamıyorsa, <xref:System.ServiceModel.Activities.WorkflowServiceHost> çağrıldığında bir `Open` özel durum oluşturur. Ana bilgisayara ek sürüm olarak sunulan her iş akışı tanımı, aşağıdaki gereksinimleri karşılamalıdır (birincil sürüm, ana bilgisayar oluşturucusuna sunulan iş akışı hizmeti tanımıdır). Ek iş akışı sürümü şunları içermelidir:  
  
- , <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> İş akışı hizmetinin birincil sürümüyle aynı olmalıdır.  
  
- , Birincil sürümde olmayan <xref:System.ServiceModel.Activities.Receive> bir <xref:System.ServiceModel.Activities.SendReply> veya etkinliği <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> olmaması ve işlem sözleşmesiyle eşleşmesi gerekir.  
  
- Benzersiz <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>bir. Bir ve yalnızca bir iş akışı tanımının bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>tane olabilir.  
  
 Bazı değişikliklere izin verilir. Aşağıdaki öğeler sürümler arasında farklı olabilir:  
  
- , <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Birincil sürümden farklı bir ada ve pakete sahip olabilir.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Değer, birincil sürümden farklı olabilir.  
  
- , <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Birincil sürümden farklı olabilir.  
  
- , <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Birincil sürümden farklı olabilir.  
  
### <a name="configuring-the-definitionidentity"></a>DefinitionIdentity yapılandırma  
 Bir iş akışı hizmeti, iş akışı Tasarımcısı <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> kullanılarak oluşturulduğunda, **Özellikler** penceresi kullanılarak ayarlanır. İş akışı hizmetini seçmek için tasarımcıda hizmetin kök etkinliğinin dışını tıklatın ve **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin. **DefinitionIdentity** özelliğinin yanında görünen açılan listeden <xref:System.Activities.WorkflowIdentity> **WorkflowIdentity** ' ı seçin ve ardından istediğiniz özellikleri genişletin ve belirtin. Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , ve`MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> ile<xref:System.Activities.WorkflowIdentity.Version%2A>yapılandırılır .`1.0.0.0` <xref:System.Activities.WorkflowIdentity.Package%2A>isteğe bağlıdır ve bu örnekte `null`.  
  
 ![DefinitionIdentity özelliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Bir iş akışı hizmeti kendiliğinden barındırıldığı <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> zaman, iş akışı hizmeti oluşturulduğunda yapılandırılır. Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ,, `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.Activities.WorkflowIdentity.Name%2A> içerenöncekiörnekle`1.0.0.0`aynı değerlerle yapılandırılır.  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 Bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmetinin yalnızca bir sürümü **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>olabilir, ancak bu gerekli değildir.  
  
> [!NOTE]
> Bu, hizmet başlangıçta <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırıldıktan sonra dağıtılmışsa ve sonra güncelleştirilmiş bir sürüm oluşturulduğunda yararlıdır.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Web 'de barındırılan Iş akışı hizmetine yeni bir sürüm ekleme  
 Web 'de barındırılan bir hizmette iş akışı hizmetinin yeni bir sürümünü yapılandırmanın ilk adımı, `App_Code` klasörde hizmet dosyası ile aynı ada sahip yeni bir klasör oluşturmaktır. Hizmetin `xamlx` dosyası adlandırılmışsa `MortgageWorkflow.xamlx`, klasörün adlandırılmış `MortgageWorkflow`olması gerekir. Özgün hizmetin `xamlx` dosyasının bir kopyasını bu klasöre yerleştirin ve gibi yeni bir adla `MortgageWorkflowV1.xamlx`yeniden adlandırın. Birincil hizmette istenen değişiklikleri yapın, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>öğesini güncelleştirin ve ardından hizmeti dağıtın. Aşağıdaki <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> örnekte, `MortgageWorkflow` ve ' <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.Activities.WorkflowIdentity.Version%2A> a`2.0.0.0`ile güncelleştirilmiştir.  
  
 ![WorkflowIdentity 'nin Definitionkimliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Hizmet yeniden başlatıldığında, belirtilen <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> `App_Code` alt klasörde bulunduğu için önceki sürüm otomatik olarak koleksiyona eklenecektir. İş akışı hizmetinin `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> birincil sürümünde önceki sürümlerin eklenmediğini unutmayın. `null`Bir sürüm bir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> `null` olabilir, ancak birden çok sürüm varsa, birincil sürüm veya ' ı içeren bir önceki sürümler koleksiyona eklenmez. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Şirket içinde barındırılan Iş akışı hizmetine yeni bir sürüm ekleme  
 Şirket <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> içinde barındırılan bir iş akışı hizmetine yeni bir sürüm eklerken,, iş akışı hizmetinin birincil sürümüyle yapılandırılır ve önceki sürümlerin koleksiyona açıkça eklenmesi gerekir. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Aşağıdaki örnekte, bir `MortgageWorkflowV2` iş akışı tanımı kullanan birincil iş akışı hizmeti ile yapılandırılır ve bir iş akışı tanımıyla yapılandırılmış `MortgageWorkflowV1` bir iş akışı hizmeti <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona eklenir. Her iş akışı hizmeti, iş akışı tanımının <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> sürümünü yansıtan benzersiz bir şekilde yapılandırılır.  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,   
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```
