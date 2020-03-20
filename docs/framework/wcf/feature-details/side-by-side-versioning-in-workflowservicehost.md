---
title: WorkflowServiceHost Yan Yana Sürüm Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: bc662e51c96a06737e1bd6fd78d5f70f3922d080
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184467"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>WorkflowServiceHost Yan Yana Sürüm Oluşturma
.NET Framework 4.5'te tanıtılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> yan yana sürüm, bir iş akışı hizmetinin birden çok sürümünü tek bir uç noktada barındırma olanağı sağlar. Sağlanan yan yana işlevsellik, iş akışı hizmetinin yeni iş akışı tanımı kullanılarak oluşturulacak şekilde yapılandırılmasına olanak sağlarken, örnekleri varolan tanım kullanılarak tamamlandı. Bu konu, iş akışı hizmetinin yan yana <xref:System.ServiceModel.Activities.WorkflowServiceHost>yürütülmesine genel bir bakış sağlar.  
  
> [!NOTE]
> Bir örneği indirmek ve iş akışı hizmetinin yan yana sürümvideosunu izlemek için, [Web tarafından Barındırılan Xamlx İş Akışı Hizmeti ile Yan Yan Sürümleme](https://go.microsoft.com/fwlink/?LinkId=393746)bölümüne bakın.  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>İş Akışı Hizmetinde Birden Çok Sürümü Barındırma  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>bir iş akışının birden çok sürümüyan yana yürütmek için izin için <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> yapılandırılabilir iki özellik içerir: ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>iş akışı hizmetinin desteklenen sürümlerini <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> içerir ve her iş akışı hizmetini benzersiz olarak tanımlamak için kullanılır. Bu iş akışı hizmeti ile <xref:System.Activities.WorkflowIdentity> bir ilişki içinde yapılır. A, <xref:System.Activities.WorkflowIdentity> tanımlayıcı üç bilgi parçası içerir. <xref:System.Activities.WorkflowIdentity.Name%2A>ve <xref:System.Activities.WorkflowIdentity.Version%2A> bir ad <xref:System.Version> ve a içerir <xref:System.Activities.WorkflowIdentity.Package%2A> ve gereklidir ve isteğe bağlıdır ve montaj adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir. Koleksiyonda yer alan <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> her iş akışı <xref:System.Activities.WorkflowIdentity>hizmetinin benzersiz bir . A, <xref:System.Activities.WorkflowIdentity> üç özelliğinden herhangi biri diğerinden <xref:System.Activities.WorkflowIdentity>farklıysa benzersizdir. A `null` <xref:System.Activities.WorkflowIdentity> için <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>izin verilebilen bir değerdir, ancak iş akışı `null` <xref:System.Activities.WorkflowIdentity>hizmetinin yalnızca bir önceki sürümü .  
  
> [!IMPORTANT]
> A, <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlayıcı bilgiler (PII) içermemelidir. <xref:System.Activities.WorkflowIdentity>üç bölümden oluşur: <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.String>a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), <xref:System.Activities.WorkflowIdentity.Package%2A> a<xref:System.String>( ), ve a ( ). Bir örnek <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan bilgiler, çalışma süresine göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır. WF İzleme'nin KIŞISEL Bilgileri (hassas kullanıcı verilerini) gizlemek için herhangi bir mekanizması yoktur. Bu nedenle, bir örnek, izleme kayıtlarında çalışma zamanı tarafından yayılacağı için herhangi bir <xref:System.Activities.WorkflowIdentity> KIŞISEL veri içermemelidir ve izleme kayıtlarını görüntülemek için erişimi olan herkes tarafından görülebilir.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>İş Akışı Hizmetinin Birden Çok Sürümü barındırma kuralları  
 Bir kullanıcı <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bir iş akışı hizmetinin aynı uç nokta ve açıklama kümesiyle barındırılabilmesi için karşılanması gereken birkaç koşul vardır. Ek sürümlerden herhangi biri bu koşulları <xref:System.ServiceModel.Activities.WorkflowServiceHost> karşılamazsa, `Open` çağrıldığında bir özel durum oluşturur. Ek sürüm olarak ana bilgisayara sağlanan her iş akışı tanımı aşağıdaki gereksinimleri karşılamalıdır (birincil sürüm, ana bilgisayar oluşturucuya sağlanan iş akışı hizmeti tanımıdır). Ek iş akışı sürümü şunları yapmalı:  
  
- İş akışı <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> hizmetinin birincil sürümüyle aynı sıyrıkta dır.  
  
- Birincil sürümde <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> <xref:System.ServiceModel.Activities.SendReply> olmayan herhangi bir faaliyetveya faaliyet olmamalıdır ve işlem sözleşmesine uymaları gerekir.  
  
- Benzersiz <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>bir var . Bir ve tek bir iş `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>akışı tanımı .  
  
 Bazı değişikliklere izin verilir. Aşağıdaki öğeler sürümler arasında farklı olabilir:  
  
- Birincil <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> sürümden farklı bir Ad ve Paket olabilir.  
  
- Değer <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> birincil sürümden farklı olabilir.  
  
- Birincil <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> sürümden farklı olabilir.  
  
- Birincil <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> sürümden farklı olabilir.  
  
### <a name="configuring-the-definitionidentity"></a>Tanımlı Kimliğin Yapılandırılması  
 İş akışı tasarımcısı kullanılarak bir iş akışı <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> hizmeti oluşturulduğunda, **Özellikler** penceresi kullanılarak ayarlanır. İş akışı hizmetini seçmek için tasarımcıda hizmetin kök etkinliğinin dışına tıklayın ve **Görünüm** menüsünden **Özellikler Penceresi'ni** seçin. **DefinitionIdentity** özelliğinin yanında görünen açılır listeden **İş Akışı Kimliği'ni** seçin ve <xref:System.Activities.WorkflowIdentity> ardından istediğiniz özellikleri genişletip belirtin. Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve a <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Version%2A> ile `1.0.0.0`yapılandırılır. <xref:System.Activities.WorkflowIdentity.Package%2A>isteğe bağlıdır ve `null`bu örnekte .  
  
 ![DefinitionIdentity özelliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Bir iş akışı hizmeti kendi kendine <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> barındırıldığında, iş akışı hizmeti oluşturulduğunda yapılandırılır. Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki örnekle <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` aynı değerlerle yapılandırılır, <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0`ve bir .  
  
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
  
 İş <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> akışı hizmetinin yalnızca bir sürümü **nde null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>olsa da, A gerekli değildir.  
  
> [!NOTE]
> Bu, hizmet başlangıçta <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırılmadan dağıtıldıysa ve daha sonra güncelleştirilmiş bir sürüm oluşturulduysa yararlıdır.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Web tarafından barındırılan İş Akışı Hizmetine Yeni Sürüm Ekleme  
 Web tarafından barındırılan bir hizmette iş akışı hizmetinin yeni bir sürümünü yapılandırmanın `App_Code` ilk adımı, klasörde hizmet dosyasıyla aynı ada sahip yeni bir klasör oluşturmaktır. Hizmetin `xamlx` dosyası adlandırılmışsa, `MortgageWorkflow.xamlx`klasörün adı `MortgageWorkflow`gerekir. Özgün hizmetdosyasının `xamlx` bir kopyasını bu klasöre yerleştirin ve `MortgageWorkflowV1.xamlx`yeni bir ada yeniden adlandırın. Birincil hizmette istenen değişiklikleri yapın, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>hizmetini güncelleştirin ve sonra dağıtın. Aşağıdaki <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> örnekte bir <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve bir <xref:System.Activities.WorkflowIdentity.Version%2A> ile güncellendi `2.0.0.0`.  
  
 ![İş Akışı Kimliğinin Tanımını gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Hizmet yeniden başlatıldığında, belirlenen <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> `App_Code` alt klasörde bulunduğundan önceki sürüm otomatik olarak koleksiyona eklenir. İş akışı hizmetinin `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> birincil sürümünde önceki sürümler eklenmez. Bir sürümün `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>bir , ancak birden çok sürümü varsa birincil sürümü `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> veya başka önceki sürümleri <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ile bir koleksiyona eklenmez olmamalıdır.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Kendi Barındırılan İş Akışı Hizmetine Yeni Sürüm Ekleme  
 Kendi kendine barındırılan iş akışı hizmetine <xref:System.ServiceModel.Activities.WorkflowServiceHost> yeni bir sürüm eklerken, iş akışı hizmetinin birincil sürümüyle yapılandırılır ve önceki sürümlerin <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona açıkça eklenmesi gerekir. Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı tanımı kullanan `MortgageWorkflowV2` birincil iş akışı hizmetiyle bir yapılandırılır ve `MortgageWorkflowV1` <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona iş akışı tanımıyla yapılandırılan bir iş akışı hizmeti eklenir. Her iş akışı hizmeti, iş <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> akışı tanımının sürümünü yansıtan benzersiz bir şekilde yapılandırılır.  
  
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
