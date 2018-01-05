---
title: "WorkflowServiceHost Yan Yana Sürüm Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db8f79fcdc1398b891933f5fef9f07410e5de11e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>WorkflowServiceHost Yan Yana Sürüm Oluşturma
<xref:System.ServiceModel.Activities.WorkflowServiceHost> Yan yana sürüm oluşturma kullanıma sunulan [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] birden fazla sürümünü tek bir uç noktada bir iş akışı hizmeti ana bilgisayar yeteneği sağlar. Sağlanan yan yana işlevleri iş akışı hizmeti yeni örneklerini örnekleri tam varolan tanımı kullanılarak çalıştırılırken yeni iş akışı tanımı kullanılarak oluşturulan şekilde yapılandırılması bir iş akışı hizmeti sağlar. Bu konuda iş akışı hizmeti kullanılarak yan yana yürütme genel bir bakış sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
> [!NOTE]
>  Bir örnek yükleyip videosu iş akışı hizmeti yan yana sürüm oluşturma izlemek için bkz: [Web-Hosted Xamlx iş akışı hizmeti yan yana sürüm oluşturma](http://go.microsoft.com/fwlink/?LinkId=393746).  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Birden çok iş akışı hizmeti sürümlerde barındırma  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>yan yana yürütme için bir iş akışı birden fazla sürümünü izin verecek şekilde yapılandırılmış iki özellikleri içerir: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>İş akışı hizmeti desteklenen sürümlerini içerir ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> her iş akışı hizmeti benzersiz şekilde tanımlamak için kullanılır. Bu ilişkilendirme tarafından yapılır bir <xref:System.Activities.WorkflowIdentity> iş akışı hizmeti ile. A <xref:System.Activities.WorkflowIdentity> tanımlayıcı üç parça bilgi içerir. <xref:System.Activities.WorkflowIdentity.Name%2A>ve <xref:System.Activities.WorkflowIdentity.Version%2A> içeren bir ad ve bir <xref:System.Version> ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer gibi bilgileri içeren ek bir dize istenen bilgileri belirtmek için kullanılır. İçinde yer alan her iş akışı hizmeti <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu benzersiz olmalıdır <xref:System.Activities.WorkflowIdentity>. A <xref:System.Activities.WorkflowIdentity> üç özelliklerini birbirinden farklı olan benzersiz <xref:System.Activities.WorkflowIdentity>. A `null` <xref:System.Activities.WorkflowIdentity> için izin verilen bir değer <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ancak bir iş akışı hizmeti yalnızca bir önceki sürümü olabilir bir `null` <xref:System.Activities.WorkflowIdentity>.  
  
> [!IMPORTANT]
>  A <xref:System.Activities.WorkflowIdentity> tüm kişisel bilgileri (PII) içermemesi gerekir. <xref:System.Activities.WorkflowIdentity>üç bölümden oluşur: bir <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), bir <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) ve bir <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>). Hakkında bilgi <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan örneğini etkinliğin birkaç farklı noktalarda Hizmetleri yaşam döngüsü yapılandırılmış tüm izleme için çalışma zamanı tarafından yayınlanır. İzleme WF PII (hassas kullanıcı verileri) gizlemek için herhangi bir mekanizma yok. Bu nedenle, bir <xref:System.Activities.WorkflowIdentity> örneği içeremez herhangi bir PII veri kayıtları izleme içinde çalışma zamanı tarafından gösterilen ve izleme kayıtları görüntülemek için erişimi olan herkes tarafından görülebilir.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Birden çok iş akışı hizmeti sürümleri barındırmak için kurallar  
 Bir kullanıcı, ek bir sürüme eklediğinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bir iş akışı Hizmeti uç noktaları ve açıklama aynı kümesiyle barındırılması karşılanması gereken birkaç koşullar vardır. Ek sürümlerinin herhangi birinin bu koşulları başarısız olursa <xref:System.ServiceModel.Activities.WorkflowServiceHost> aykırı zaman `Open` olarak adlandırılır. Ek bir sürüm olarak barındırmak için sağlanan her bir iş akışı tanımı (birincil sürüm konak oluşturucuya sunulan iş akışı hizmeti tanımı olduğu) aşağıdaki gereksinimleri karşılaması gerekir. Ek iş akışı sürümü gerekir:  
  
-   Aynı olan <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> iş akışı hizmeti birincil sürümü olarak.  
  
-   Herhangi bir olmamalıdır <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.SendReply> aktivitelerde kendi <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> birincil sürümü olmayan ve işlem sözleşmesi eşleşmesi gerekir.  
  
-   Benzersiz bir sahibi <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. Tek bir iş akışı tanımı olabilir bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
 Bazı değişiklikler izin verilir. Aşağıdaki öğeler sürümleri arasında farklı olabilir:  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Birincil sürümünden farklı bir ad ve paket olabilir.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Değeri birincil sürümünden farklı olabilir.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Birincil sürümünden farklı olabilir.  
  
-   <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Birincil sürümünden farklı olabilir.  
  
### <a name="configuring-the-definitionidentity"></a>DefinitionIdentity yapılandırma  
 İş Akışı Tasarımcısı'nı kullanarak bir iş akışı hizmeti oluşturulduğunda <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> kullanılarak ayarlanan **özellikleri** penceresi. ' I tıklatın hizmetin Kök etkinlik iş akışı hizmeti seçin ve için Tasarımcısı'nda dışında **Özellikler penceresini** gelen **Görünüm** menüsü. Seçin **WorkflowIdentity** yanında görüntülenen aşağı açılan listeden **DefinitionIdentity** özelliği'ni genişletin ve istenen belirtin <xref:System.Activities.WorkflowIdentity> özellikleri. Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ile yapılandırılmış <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Version%2A> , `1.0.0.0`. <xref:System.Activities.WorkflowIdentity.Package%2A>Bu örnekte isteğe bağlıdır ve `null`.  
  
 ![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")  
  
 Bir iş akışı hizmeti kendini barındıran olduğunda <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmeti oluşturulduğunda yapılandırılır. Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki örnekte, aynı değerlere ile yapılandırılmış <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Name%2A> , `1.0.0.0`.  
  
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
  
 A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> gerekli değil yalnızca bir iş akışı hizmeti sürümü açabilecek olsa da bir **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
> [!NOTE]
>  Bu hizmet başlangıçta olmadan dağıtılmışsa yararlıdır bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırılmış, ve ardından güncelleştirilmiş bir sürüm oluşturulur.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Bir iş akışı Web barındırılan hizmeti için yeni bir sürüm ekleme  
 Yeni bir klasör oluşturmak için bir web barındırılan hizmetinde bir iş akışı hizmeti yeni bir sürümü yapılandırmada ilk adım olan `App_Code` hizmet dosyası olarak aynı ada sahip klasör. Varsa hizmetin `xamlx` dosya adlandırılan `MortgageWorkflow.xamlx`, klasörü adlandırılmalıdır `MortgageWorkflow`. Özgün hizmetin bir kopyasını yerleştirin `xamlx` dosyasını bu klasöre ve yeni bir ad gibi yeniden adlandırın `MortgageWorkflowV1.xamlx`. Birincil hizmete istediğiniz değişiklikleri yapın, güncelleştirme, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>ve hizmeti dağıtın. Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ile güncelleştirilmiş bir <xref:System.Activities.WorkflowIdentity.Name%2A> , `MortageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Version%2A> , `2.0.0.0`.  
  
 ![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")  
  
 Hizmet yeniden başlatıldığında, önceki sürümü otomatik olarak eklenir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu bulunduğu olduğundan belirlenen içinde `App_Code` alt klasörü. İş akışı hizmeti birincil sürümüne sahipse unutmayın bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki sürümler eklenmez. Bir sürüm olabilir bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ancak birden çok sürüm varsa birincil sürümü ile bir değer olmamalıdır `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> veya aksi takdirde önceki sürümler için eklenmez <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Kendini barındıran iş akışı hizmeti için yeni bir sürüm ekleme  
 Yeni bir sürüm kendini barındıran iş akışı hizmetine eklerken <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı hizmeti birincil sürümü ile yapılandırılmış ve önceki sürümleri açıkça eklenmelidir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu. Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> kullanan bir birincil iş akışı hizmeti ile yapılandırılmış bir `MortgageWorkflowV2` iş akışı tanımı ve bir iş akışı hizmeti ile yapılandırılmış bir `MortgageWorkflowV1` iş akışı tanımı eklenir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu. Her iş akışı hizmeti benzersiz bir yapılandırılmış <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı tanımı sürüm yansıtır.  
  
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
