---
title: WorkflowServiceHost Yan Yana Sürüm Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 878e610bd1fe0b7e2496f251333a3ad21909788a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245100"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>WorkflowServiceHost Yan Yana Sürüm Oluşturma

<xref:System.ServiceModel.Activities.WorkflowServiceHost>.NET Framework 4,5 ' de sunulan yan yana sürüm oluşturma, bir iş akışı hizmetinin birden çok sürümünü tek bir uç noktada barındırmanıza olanak sağlar. Belirtilen yan yana işlevsellik, iş akışı hizmeti 'nin yeni iş akışı tanımı kullanılarak oluşturulması için bir iş akışı hizmetinin yapılandırılmasına izin verir, böylece örnekleri mevcut tanımı kullanarak tamamlanır. Bu konu, kullanarak iş akışı hizmeti 'nin yan yana yürütmeye genel bir bakış sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost> .  
  
> [!NOTE]
> Bir örneği indirmek ve iş akışı hizmeti 'nin yan yana sürüm oluşturma kılavuzunu izlemek için bkz. [bir Web-Hosted xamlx Iş akışı hizmeti Ile yan yana sürüm oluşturma](https://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Bir Iş akışı hizmetinde birden çok sürümü barındırma  

 <xref:System.ServiceModel.Activities.WorkflowServiceHost> , bir iş akışının birden çok sürümünün yan yana yürütülmesine izin vermek için yapılandırılabilecek iki özellik içerir: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> . <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> , iş akışı hizmetinin desteklenen sürümlerini içerir ve her bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmetini benzersiz şekilde tanımlamak için kullanılır. Bu <xref:System.Activities.WorkflowIdentity> , bir iş akışı hizmeti ile ilişkilendirerek yapılır. <xref:System.Activities.WorkflowIdentity>, Üç tanımlayıcı bilgi parçasını içerir. <xref:System.Activities.WorkflowIdentity.Name%2A> ve bir <xref:System.Activities.WorkflowIdentity.Version%2A> ad ve bir içerir ve <xref:System.Version> gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir. Koleksiyonda bulunan her iş akışı hizmetinin <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> benzersiz olması gerekir <xref:System.Activities.WorkflowIdentity> . , <xref:System.Activities.WorkflowIdentity> Üç özelliklerinden biri diğerinden farklıysa benzersizdir <xref:System.Activities.WorkflowIdentity> . `null` <xref:System.Activities.WorkflowIdentity> , İçin izin verilen bir değerdir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , ancak bir iş akışı hizmetinin yalnızca bir önceki sürümü olabilir `null` <xref:System.Activities.WorkflowIdentity> .  
  
> [!IMPORTANT]
> Bir <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlanabilir bilgiler (PII) içermemelidir. <xref:System.Activities.WorkflowIdentity> üç bölümden oluşur: a <xref:System.Activities.WorkflowIdentity.Name%2A> ( <xref:System.String> ), a <xref:System.Activities.WorkflowIdentity.Version%2A> ( <xref:System.Version> ) ve a <xref:System.Activities.WorkflowIdentity.Package%2A> ( <xref:System.String> ). <xref:System.Activities.WorkflowIdentity>Örnek oluşturmak için kullanılan hakkında bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır. WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur. Bu nedenle, <xref:System.Activities.WorkflowIdentity> kayıtlar izlenirken çalışma zamanı tarafından yayınlandığından ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir olabileceğinden bir örnek herhangi BIR PII verisi içermemelidir.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Bir Iş akışı hizmetinin birden çok sürümünü barındırmak için kurallar  

 Bir Kullanıcı öğesine ek bir sürüm eklediğinde <xref:System.ServiceModel.Activities.WorkflowServiceHost> , bir iş akışı hizmetinin aynı uç nokta ve açıklama kümesiyle barındırılması için karşılanması gereken birkaç koşul vardır. Ek sürümlerden herhangi biri bu koşulları karşılamıyorsa, <xref:System.ServiceModel.Activities.WorkflowServiceHost> çağrıldığında bir özel durum oluşturur `Open` . Ana bilgisayara ek sürüm olarak sunulan her iş akışı tanımı, aşağıdaki gereksinimleri karşılamalıdır (birincil sürüm, ana bilgisayar oluşturucusuna sunulan iş akışı hizmeti tanımıdır). Ek iş akışı sürümü şunları içermelidir:  
  
- , <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> İş akışı hizmetinin birincil sürümüyle aynı olmalıdır.  
  
- , <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> Birincil sürümde olmayan bir veya etkinliği olmaması <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> ve işlem sözleşmesiyle eşleşmesi gerekir.  
  
- Benzersiz bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> . Bir ve yalnızca bir iş akışı tanımının bir tane olabilir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> .  
  
 Bazı değişikliklere izin verilir. Aşağıdaki öğeler sürümler arasında farklı olabilir:  
  
- , <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Birincil sürümden farklı bir ada ve pakete sahip olabilir.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A>Değer, birincil sürümden farklı olabilir.  
  
- , <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Birincil sürümden farklı olabilir.  
  
- , <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Birincil sürümden farklı olabilir.  
  
### <a name="configuring-the-definitionidentity"></a>DefinitionIdentity yapılandırma  

 Bir iş akışı hizmeti, iş akışı Tasarımcısı kullanılarak oluşturulduğunda, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> **Özellikler** penceresi kullanılarak ayarlanır. İş akışı hizmetini seçmek için tasarımcıda hizmetin kök etkinliğinin dışını tıklatın ve **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin. **DefinitionIdentity** özelliğinin yanında görünen açılan listeden **WorkflowIdentity** ' ı seçin ve ardından istediğiniz özellikleri genişletin ve belirtin <xref:System.Activities.WorkflowIdentity> . Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve ile yapılandırılır <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0` . <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve bu örnekte `null` .  
  
 ![DefinitionIdentity özelliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Bir iş akışı hizmeti kendiliğinden barındırıldığı zaman, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmeti oluşturulduğunda yapılandırılır. Aşağıdaki örnekte,, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve içeren önceki örnekle aynı değerlerle yapılandırılır <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0` .  
  
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
  
 Bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmetinin yalnızca bir sürümü **null** olabilir, ancak bu gerekli değildir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> .  
  
> [!NOTE]
> Bu, hizmet başlangıçta yapılandırıldıktan sonra dağıtılmışsa <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve sonra güncelleştirilmiş bir sürüm oluşturulduğunda yararlıdır.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Web 'de barındırılan Iş akışı hizmetine yeni bir sürüm ekleme  

 Web 'de barındırılan bir hizmette iş akışı hizmetinin yeni bir sürümünü yapılandırmanın ilk adımı, `App_Code` klasörde hizmet dosyası ile aynı ada sahip yeni bir klasör oluşturmaktır. Hizmetin `xamlx` dosyası adlandırılmışsa `MortgageWorkflow.xamlx` , klasörün adlandırılmış olması gerekir `MortgageWorkflow` . Özgün hizmetin dosyasının bir kopyasını `xamlx` Bu klasöre yerleştirin ve gibi yeni bir adla yeniden adlandırın `MortgageWorkflowV1.xamlx` . Birincil hizmette istenen değişiklikleri yapın, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> öğesini güncelleştirin ve ardından hizmeti dağıtın. Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve ' a ile güncelleştirilmiştir <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Version%2A> `2.0.0.0` .  
  
 ![WorkflowIdentity 'nin Definitionkimliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Hizmet yeniden başlatıldığında, <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> belirtilen alt klasörde bulunduğu için önceki sürüm otomatik olarak koleksiyona eklenecektir `App_Code` . İş akışı hizmetinin birincil sürümünde `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki sürümlerin eklenmediğini unutmayın. Bir sürüm bir olabilir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , ancak birden çok sürüm varsa, birincil sürüm veya ' ı içeren bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki sürümler <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona eklenmez.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Şirket içinde barındırılan Iş akışı hizmetine yeni bir sürüm ekleme  

 Şirket içinde barındırılan bir iş akışı hizmetine yeni bir sürüm eklerken,, <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı hizmetinin birincil sürümüyle yapılandırılır ve önceki sürümlerin koleksiyona açıkça eklenmesi gerekir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> . Aşağıdaki örnekte, bir iş akışı <xref:System.ServiceModel.Activities.WorkflowServiceHost> tanımı kullanan birincil iş akışı hizmeti ile yapılandırılır ve bir iş akışı `MortgageWorkflowV2` tanımıyla yapılandırılmış bir iş akışı hizmeti `MortgageWorkflowV1` <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona eklenir. Her iş akışı hizmeti, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı tanımının sürümünü yansıtan benzersiz bir şekilde yapılandırılır.  
  
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
