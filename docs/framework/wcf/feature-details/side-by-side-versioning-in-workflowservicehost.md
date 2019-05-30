---
title: WorkflowServiceHost Yan Yana Sürüm Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 3ac8b2260e5da1e91c167e3e9ef91039deb983b2
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380240"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>WorkflowServiceHost Yan Yana Sürüm Oluşturma
<xref:System.ServiceModel.Activities.WorkflowServiceHost> .NET Framework 4. 5 ' tanıtılan yan yana sürüm oluşturma, birden çok sürümünü tek bir uç nokta bir iş akışı hizmeti barındırma olanağı sağlar. Yeni iş akışı hizmeti örnekleri çalışırken örneklerini kullanarak varolan tanımın tam yeni iş akışı tanımı kullanarak oluşturulmasını sağlayacak şekilde yapılandırılması bir iş akışı hizmeti sağlanan yan yana işlevselliği sağlar. Bu konuda, iş akışı hizmeti yan yana yürütme kullanarak genel bir bakış sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
> [!NOTE]
>  Bir örnek yükleyin ve iş akışı hizmeti yan yana sürüm oluşturma videosu izlemek için bkz: [Web-Hosted Xamlx iş akışı hizmeti ile yan yana sürüm oluşturma](https://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Birden çok sürümlerinde bir iş akışı hizmeti barındırma  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> birden çok sürümünü yan yana yürütme için bir iş akışı izin verecek şekilde yapılandırılmış iki özellik içerir: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> İş akışı hizmeti desteklenen sürümlerini içerir ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> her iş akışı hizmeti benzersiz şekilde tanımlamak için kullanılır. Bu ilişkilendirme yapılır bir <xref:System.Activities.WorkflowIdentity> ile iş akışı hizmeti. A <xref:System.Activities.WorkflowIdentity> tanımlayıcı üç parça bilgi içerir. <xref:System.Activities.WorkflowIdentity.Name%2A> ve <xref:System.Activities.WorkflowIdentity.Version%2A> içeren bir ad ve bir <xref:System.Version> ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer gibi bilgileri içeren ek bir dize istenen bilgileri belirtmek için kullanılabilir. İçindeki her iş akışı hizmeti <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu benzersiz olmalıdır <xref:System.Activities.WorkflowIdentity>. A <xref:System.Activities.WorkflowIdentity> üç özelliklerini birbirinden farklı olduğunda benzersiz <xref:System.Activities.WorkflowIdentity>. A `null` <xref:System.Activities.WorkflowIdentity> için izin verilen bir değer <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ancak bir iş akışı hizmeti yalnızca bir önceki sürümü olabilir bir `null` <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> tüm kişisel bilgileri (PII) içermemelidir. <xref:System.Activities.WorkflowIdentity> üç bölümden oluşur: bir <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) ve <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>). Hakkında bilgi <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan bir örneği yaşam döngüsü Hizmetleri etkinliğin birkaç farklı noktalarda yapılandırılmış tüm izleme için çalışma zamanı tarafından yayılır. İzleme WF PII (hassas kullanıcı verileri) gizlemek için herhangi bir mekanizma yoktur. Bu nedenle, bir <xref:System.Activities.WorkflowIdentity> örneği kayıtları izleme, çalışma zamanı tarafından yayılan ve izleme kayıtları görüntüleme erişimi olan herkes tarafından görülebilir tüm PII verileri içermemelidir.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Birden çok sürümünü bir iş akışı hizmeti barındırma kuralları  
 Bir kullanıcı için ek bir sürüm eklediğinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bir iş akışı Hizmeti uç noktaları ve tanım aynı kümesiyle barındırılması karşılanması gereken birkaç durum vardır. Bu koşullar karşılamak ek sürümlerinin herhangi birinin başarısız olursa <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir özel durum oluşturur, `Open` çağrılır. Ana bilgisayara ek bir sürüm olarak sağlanan her bir iş akışı tanımı (birincil sürüm konak oluşturucuya sunulan iş akışı hizmet tanımı olduğu) aşağıdaki gereksinimleri karşılaması gerekir. Ek iş akışı sürümü gerekir:  
  
- Aynı <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> iş akışı hizmetinin birincil sürümü olarak.  
  
- Tüm olmamalıdır <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.SendReply> etkinlikler, <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> birincil sürümü olmayan ve işlem anlaşması eşleşmesi gerekir.  
  
- Benzersiz bir sahip <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Bir ve yalnızca bir iş akışı tanımı olabilir bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
 Bazı değişikliklere izin verilmez. Aşağıdaki öğeler, sürümler arasında farklı olabilir:  
  
- <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Birincil sürümünden farklı bir ad ve paket olabilir.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Değeri birincil sürümünden farklı olabilir.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Birincil sürümünden farklı olabilir.  
  
- <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Birincil sürümünden farklı olabilir.  
  
### <a name="configuring-the-definitionidentity"></a>DefinitionIdentity yapılandırma  
 İş Akışı Tasarımcısı'nı kullanarak bir iş akışı hizmeti oluşturulduğunda <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> kullanılarak ayarlanan **özellikleri** penceresi. ' A tıklayın hizmetin Kök etkinlik iş akışı hizmeti seçin ve tasarımcıda dışında **Özellikler penceresi** gelen **görünümü** menüsü. Seçin **Workflowıdentity** yanında görüntülenen aşağı açılan listeden **DefinitionIdentity** özelliğini genişletin ve ardından istenen belirtin <xref:System.Activities.WorkflowIdentity> özellikleri. Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırılmış <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Version%2A> , `1.0.0.0`. <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve bu örnekte `null`.  
  
 ![DefinitionIdentity özelliği gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Bir iş akışı hizmeti, şirket içinde barındırılan olduğunda <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmeti oluşturulduğunda yapılandırılır. Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki örnekle aynı değerleri ile yapılandırılmış <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Name%2A> , `1.0.0.0`.  
  
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
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmeti yalnızca bir sürümüne sahip, ancak gerekli değildir bir **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
>  Hizmet olmadan başlangıçta dağıtıldıysa kullanışlıdır bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırılmış, ve ardından güncelleştirilmiş bir sürüm oluşturulur.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Bir Web barındırılan iş akışı hizmeti için yeni bir sürüm ekleme  
 Bir iş akışı hizmeti yeni bir sürümü web barındırılan bir hizmete yapılandırmada ilk adım, yeni bir klasöre oluşturmaktır `App_Code` hizmet dosyası aynı ada sahip bir klasör. Varsa bu hizmetin `xamlx` dosya adlı `MortgageWorkflow.xamlx`, klasörü adlandırılmalıdır `MortgageWorkflow`. Özgün hizmetin bir kopyasını yerleştirmek `xamlx` gibi yeni bir ad ile yeniden adlandırın ve bu klasöre dosya `MortgageWorkflowV1.xamlx`. İstediğiniz değişiklikleri birincil hizmetinize, güncelleştirme, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>ve ardından hizmeti dağıtmak. Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ile güncelleştirilmiş bir <xref:System.Activities.WorkflowIdentity.Name%2A> , `MortageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Version%2A> , `2.0.0.0`.  
  
 ![DefinitionIdentity, Workflowıdentity gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Hizmet yeniden başlatıldığında, önceki sürümü otomatik olarak eklenir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyon yer olduğu için belirlenen `App_Code` alt. İş akışı hizmetinin birincil sürümü gerçekleştiriyorsanız bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki sürümleri eklenmeyecektir. Bir sürümü olabilir bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ancak birden çok sürüm varsa birincil sürüm sahip olmamalıdır `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ya da aksi takdirde önceki sürümler için eklenmeyecek <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Şirket içinde barındırılan iş akışı hizmeti için yeni bir sürüm ekleme  
 Yeni bir sürümü, şirket içinde barındırılan iş akışı hizmetine eklerken <xref:System.ServiceModel.Activities.WorkflowServiceHost> birincil iş akışı hizmeti sürümü ile yapılandırılmış ve önceki sürümleri açıkça eklenmelidir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu. Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> kullanan bir birincil iş akışı hizmeti ile yapılandırılmış bir `MortgageWorkflowV2` iş akışı tanımı ve bir iş akışı hizmeti ile yapılandırılmış bir `MortgageWorkflowV1` iş akışı tanımı eklenir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu. Her iş akışı hizmeti benzersiz bir yapılandırılmış <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , iş akışı tanımının sürümü yansıtır.  
  
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
