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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68b0bea0253e32384291e5e73cc81367b0fb3305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="39d9f-102">WorkflowServiceHost Yan Yana Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="39d9f-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="39d9f-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Yan yana sürüm oluşturma kullanıma sunulan [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] birden fazla sürümünü tek bir uç noktada bir iş akışı hizmeti ana bilgisayar yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="39d9f-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="39d9f-104">Sağlanan yan yana işlevleri iş akışı hizmeti yeni örneklerini örnekleri tam varolan tanımı kullanılarak çalıştırılırken yeni iş akışı tanımı kullanılarak oluşturulan şekilde yapılandırılması bir iş akışı hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="39d9f-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="39d9f-105">Bu konuda iş akışı hizmeti kullanılarak yan yana yürütme genel bir bakış sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="39d9f-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39d9f-106">Bir örnek yükleyip videosu iş akışı hizmeti yan yana sürüm oluşturma izlemek için bkz: [Web-Hosted Xamlx iş akışı hizmeti yan yana sürüm oluşturma](http://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="39d9f-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](http://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="39d9f-107">Birden çok iş akışı hizmeti sürümlerde barındırma</span><span class="sxs-lookup"><span data-stu-id="39d9f-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="39d9f-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>yan yana yürütme için bir iş akışı birden fazla sürümünü izin verecek şekilde yapılandırılmış iki özellikleri içerir: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="39d9f-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="39d9f-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>İş akışı hizmeti desteklenen sürümlerini içerir ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> her iş akışı hizmeti benzersiz şekilde tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39d9f-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="39d9f-110">Bu ilişkilendirme tarafından yapılır bir <xref:System.Activities.WorkflowIdentity> iş akışı hizmeti ile.</span><span class="sxs-lookup"><span data-stu-id="39d9f-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="39d9f-111">A <xref:System.Activities.WorkflowIdentity> tanımlayıcı üç parça bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="39d9f-112"><xref:System.Activities.WorkflowIdentity.Name%2A>ve <xref:System.Activities.WorkflowIdentity.Version%2A> içeren bir ad ve bir <xref:System.Version> ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer gibi bilgileri içeren ek bir dize istenen bilgileri belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39d9f-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="39d9f-113">İçinde yer alan her iş akışı hizmeti <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu benzersiz olmalıdır <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="39d9f-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="39d9f-114">A <xref:System.Activities.WorkflowIdentity> üç özelliklerini birbirinden farklı olan benzersiz <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="39d9f-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="39d9f-115">A `null` <xref:System.Activities.WorkflowIdentity> için izin verilen bir değer <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ancak bir iş akışı hizmeti yalnızca bir önceki sürümü olabilir bir `null` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="39d9f-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="39d9f-116">A <xref:System.Activities.WorkflowIdentity> tüm kişisel bilgileri (PII) içermemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="39d9f-117"><xref:System.Activities.WorkflowIdentity>üç bölümden oluşur: bir <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), bir <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) ve bir <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="39d9f-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="39d9f-118">Hakkında bilgi <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan örneğini etkinliğin birkaç farklı noktalarda Hizmetleri yaşam döngüsü yapılandırılmış tüm izleme için çalışma zamanı tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="39d9f-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="39d9f-119">İzleme WF PII (hassas kullanıcı verileri) gizlemek için herhangi bir mekanizma yok.</span><span class="sxs-lookup"><span data-stu-id="39d9f-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="39d9f-120">Bu nedenle, bir <xref:System.Activities.WorkflowIdentity> örneği içeremez herhangi bir PII veri kayıtları izleme içinde çalışma zamanı tarafından gösterilen ve izleme kayıtları görüntülemek için erişimi olan herkes tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="39d9f-121">Birden çok iş akışı hizmeti sürümleri barındırmak için kurallar</span><span class="sxs-lookup"><span data-stu-id="39d9f-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="39d9f-122">Bir kullanıcı, ek bir sürüme eklediğinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bir iş akışı Hizmeti uç noktaları ve açıklama aynı kümesiyle barındırılması karşılanması gereken birkaç koşullar vardır.</span><span class="sxs-lookup"><span data-stu-id="39d9f-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="39d9f-123">Ek sürümlerinin herhangi birinin bu koşulları başarısız olursa <xref:System.ServiceModel.Activities.WorkflowServiceHost> aykırı zaman `Open` olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="39d9f-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="39d9f-124">Ek bir sürüm olarak barındırmak için sağlanan her bir iş akışı tanımı (birincil sürüm konak oluşturucuya sunulan iş akışı hizmeti tanımı olduğu) aşağıdaki gereksinimleri karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="39d9f-125">Ek iş akışı sürümü gerekir:</span><span class="sxs-lookup"><span data-stu-id="39d9f-125">The additional workflow version must:</span></span>  
  
-   <span data-ttu-id="39d9f-126">Aynı olan <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> iş akışı hizmeti birincil sürümü olarak.</span><span class="sxs-lookup"><span data-stu-id="39d9f-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
-   <span data-ttu-id="39d9f-127">Herhangi bir olmamalıdır <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.SendReply> aktivitelerde kendi <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> birincil sürümü olmayan ve işlem sözleşmesi eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
-   <span data-ttu-id="39d9f-128">Benzersiz bir sahibi <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="39d9f-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="39d9f-129">Tek bir iş akışı tanımı olabilir bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="39d9f-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="39d9f-130">Bazı değişiklikler izin verilir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-130">Some changes are permitted.</span></span> <span data-ttu-id="39d9f-131">Aşağıdaki öğeler sürümleri arasında farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="39d9f-131">The following items may be different between the versions:</span></span>  
  
-   <span data-ttu-id="39d9f-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Birincil sürümünden farklı bir ad ve paket olabilir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
-   <span data-ttu-id="39d9f-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Değeri birincil sürümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
-   <span data-ttu-id="39d9f-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Birincil sürümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
-   <span data-ttu-id="39d9f-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Birincil sürümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="39d9f-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="39d9f-136">DefinitionIdentity yapılandırma</span><span class="sxs-lookup"><span data-stu-id="39d9f-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="39d9f-137">İş Akışı Tasarımcısı'nı kullanarak bir iş akışı hizmeti oluşturulduğunda <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> kullanılarak ayarlanan **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="39d9f-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="39d9f-138">' I tıklatın hizmetin Kök etkinlik iş akışı hizmeti seçin ve için Tasarımcısı'nda dışında **Özellikler penceresini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="39d9f-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="39d9f-139">Seçin **WorkflowIdentity** yanında görüntülenen aşağı açılan listeden **DefinitionIdentity** özelliği'ni genişletin ve istenen belirtin <xref:System.Activities.WorkflowIdentity> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="39d9f-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="39d9f-140">Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ile yapılandırılmış <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Version%2A> , `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="39d9f-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="39d9f-141"><xref:System.Activities.WorkflowIdentity.Package%2A>Bu örnekte isteğe bağlıdır ve `null`.</span><span class="sxs-lookup"><span data-stu-id="39d9f-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 <span data-ttu-id="39d9f-142">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")</span><span class="sxs-lookup"><span data-stu-id="39d9f-142">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")</span></span>  
  
 <span data-ttu-id="39d9f-143">Bir iş akışı hizmeti kendini barındıran olduğunda <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmeti oluşturulduğunda yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="39d9f-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="39d9f-144">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki örnekte, aynı değerlere ile yapılandırılmış <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Name%2A> , `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="39d9f-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="39d9f-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> gerekli değil yalnızca bir iş akışı hizmeti sürümü açabilecek olsa da bir **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="39d9f-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39d9f-146">Bu hizmet başlangıçta olmadan dağıtılmışsa yararlıdır bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırılmış, ve ardından güncelleştirilmiş bir sürüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39d9f-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="39d9f-147">Bir iş akışı Web barındırılan hizmeti için yeni bir sürüm ekleme</span><span class="sxs-lookup"><span data-stu-id="39d9f-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="39d9f-148">Yeni bir klasör oluşturmak için bir web barındırılan hizmetinde bir iş akışı hizmeti yeni bir sürümü yapılandırmada ilk adım olan `App_Code` hizmet dosyası olarak aynı ada sahip klasör.</span><span class="sxs-lookup"><span data-stu-id="39d9f-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="39d9f-149">Varsa hizmetin `xamlx` dosya adlandırılan `MortgageWorkflow.xamlx`, klasörü adlandırılmalıdır `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="39d9f-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="39d9f-150">Özgün hizmetin bir kopyasını yerleştirin `xamlx` dosyasını bu klasöre ve yeni bir ad gibi yeniden adlandırın `MortgageWorkflowV1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="39d9f-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="39d9f-151">Birincil hizmete istediğiniz değişiklikleri yapın, güncelleştirme, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>ve hizmeti dağıtın.</span><span class="sxs-lookup"><span data-stu-id="39d9f-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="39d9f-152">Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ile güncelleştirilmiş bir <xref:System.Activities.WorkflowIdentity.Name%2A> , `MortageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Version%2A> , `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="39d9f-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 <span data-ttu-id="39d9f-153">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")</span><span class="sxs-lookup"><span data-stu-id="39d9f-153">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")</span></span>  
  
 <span data-ttu-id="39d9f-154">Hizmet yeniden başlatıldığında, önceki sürümü otomatik olarak eklenir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu bulunduğu olduğundan belirlenen içinde `App_Code` alt klasörü.</span><span class="sxs-lookup"><span data-stu-id="39d9f-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="39d9f-155">İş akışı hizmeti birincil sürümüne sahipse unutmayın bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki sürümler eklenmez.</span><span class="sxs-lookup"><span data-stu-id="39d9f-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="39d9f-156">Bir sürüm olabilir bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ancak birden çok sürüm varsa birincil sürümü ile bir değer olmamalıdır `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> veya aksi takdirde önceki sürümler için eklenmez <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="39d9f-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="39d9f-157">Kendini barındıran iş akışı hizmeti için yeni bir sürüm ekleme</span><span class="sxs-lookup"><span data-stu-id="39d9f-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="39d9f-158">Yeni bir sürüm kendini barındıran iş akışı hizmetine eklerken <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı hizmeti birincil sürümü ile yapılandırılmış ve önceki sürümleri açıkça eklenmelidir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="39d9f-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="39d9f-159">Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> kullanan bir birincil iş akışı hizmeti ile yapılandırılmış bir `MortgageWorkflowV2` iş akışı tanımı ve bir iş akışı hizmeti ile yapılandırılmış bir `MortgageWorkflowV1` iş akışı tanımı eklenir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="39d9f-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="39d9f-160">Her iş akışı hizmeti benzersiz bir yapılandırılmış <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı tanımı sürüm yansıtır.</span><span class="sxs-lookup"><span data-stu-id="39d9f-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
