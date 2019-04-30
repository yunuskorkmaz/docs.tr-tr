---
title: WorkflowServiceHost Yan Yana Sürüm Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 3f180fa115453be86fa5f99fbabb776eb7198623
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747946"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="20fc4-102">WorkflowServiceHost Yan Yana Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="20fc4-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="20fc4-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Yan yana sürüm oluşturma sunulan [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] birden çok sürümünü tek bir uç nokta bir iş akışı hizmeti barındırma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="20fc4-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="20fc4-104">Yeni iş akışı hizmeti örnekleri çalışırken örneklerini kullanarak varolan tanımın tam yeni iş akışı tanımı kullanarak oluşturulmasını sağlayacak şekilde yapılandırılması bir iş akışı hizmeti sağlanan yan yana işlevselliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="20fc4-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="20fc4-105">Bu konuda, iş akışı hizmeti yan yana yürütme kullanarak genel bir bakış sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="20fc4-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20fc4-106">Bir örnek yükleyin ve iş akışı hizmeti yan yana sürüm oluşturma videosu izlemek için bkz: [Web-Hosted Xamlx iş akışı hizmeti ile yan yana sürüm oluşturma](https://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="20fc4-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="20fc4-107">Birden çok sürümlerinde bir iş akışı hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="20fc4-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="20fc4-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> birden çok sürümünü yan yana yürütme için bir iş akışı izin verecek şekilde yapılandırılmış iki özellik içerir: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="20fc4-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="20fc4-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> İş akışı hizmeti desteklenen sürümlerini içerir ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> her iş akışı hizmeti benzersiz şekilde tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20fc4-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="20fc4-110">Bu ilişkilendirme yapılır bir <xref:System.Activities.WorkflowIdentity> ile iş akışı hizmeti.</span><span class="sxs-lookup"><span data-stu-id="20fc4-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="20fc4-111">A <xref:System.Activities.WorkflowIdentity> tanımlayıcı üç parça bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="20fc4-112"><xref:System.Activities.WorkflowIdentity.Name%2A> ve <xref:System.Activities.WorkflowIdentity.Version%2A> içeren bir ad ve bir <xref:System.Version> ve gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer gibi bilgileri içeren ek bir dize istenen bilgileri belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="20fc4-113">İçindeki her iş akışı hizmeti <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu benzersiz olmalıdır <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="20fc4-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="20fc4-114">A <xref:System.Activities.WorkflowIdentity> üç özelliklerini birbirinden farklı olduğunda benzersiz <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="20fc4-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="20fc4-115">A `null` <xref:System.Activities.WorkflowIdentity> için izin verilen bir değer <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ancak bir iş akışı hizmeti yalnızca bir önceki sürümü olabilir bir `null` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="20fc4-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20fc4-116">A <xref:System.Activities.WorkflowIdentity> tüm kişisel bilgileri (PII) içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="20fc4-117"><xref:System.Activities.WorkflowIdentity> üç bölümden oluşur: bir <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) ve <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="20fc4-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="20fc4-118">Hakkında bilgi <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan bir örneği yaşam döngüsü Hizmetleri etkinliğin birkaç farklı noktalarda yapılandırılmış tüm izleme için çalışma zamanı tarafından yayılır.</span><span class="sxs-lookup"><span data-stu-id="20fc4-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="20fc4-119">İzleme WF PII (hassas kullanıcı verileri) gizlemek için herhangi bir mekanizma yoktur.</span><span class="sxs-lookup"><span data-stu-id="20fc4-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="20fc4-120">Bu nedenle, bir <xref:System.Activities.WorkflowIdentity> örneği kayıtları izleme, çalışma zamanı tarafından yayılan ve izleme kayıtları görüntüleme erişimi olan herkes tarafından görülebilir tüm PII verileri içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="20fc4-121">Birden çok sürümünü bir iş akışı hizmeti barındırma kuralları</span><span class="sxs-lookup"><span data-stu-id="20fc4-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="20fc4-122">Bir kullanıcı için ek bir sürüm eklediğinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bir iş akışı Hizmeti uç noktaları ve tanım aynı kümesiyle barındırılması karşılanması gereken birkaç durum vardır.</span><span class="sxs-lookup"><span data-stu-id="20fc4-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="20fc4-123">Bu koşullar karşılamak ek sürümlerinin herhangi birinin başarısız olursa <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir özel durum oluşturur, `Open` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="20fc4-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="20fc4-124">Ana bilgisayara ek bir sürüm olarak sağlanan her bir iş akışı tanımı (birincil sürüm konak oluşturucuya sunulan iş akışı hizmet tanımı olduğu) aşağıdaki gereksinimleri karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="20fc4-125">Ek iş akışı sürümü gerekir:</span><span class="sxs-lookup"><span data-stu-id="20fc4-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="20fc4-126">Aynı <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> iş akışı hizmetinin birincil sürümü olarak.</span><span class="sxs-lookup"><span data-stu-id="20fc4-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="20fc4-127">Tüm olmamalıdır <xref:System.ServiceModel.Activities.Receive> veya <xref:System.ServiceModel.Activities.SendReply> etkinlikler, <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> birincil sürümü olmayan ve işlem anlaşması eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="20fc4-128">Benzersiz bir sahip <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="20fc4-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="20fc4-129">Bir ve yalnızca bir iş akışı tanımı olabilir bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="20fc4-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="20fc4-130">Bazı değişikliklere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="20fc4-130">Some changes are permitted.</span></span> <span data-ttu-id="20fc4-131">Aşağıdaki öğeler, sürümler arasında farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="20fc4-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="20fc4-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Birincil sürümünden farklı bir ad ve paket olabilir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="20fc4-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Değeri birincil sürümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="20fc4-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Birincil sürümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="20fc4-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Birincil sürümünden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="20fc4-136">DefinitionIdentity yapılandırma</span><span class="sxs-lookup"><span data-stu-id="20fc4-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="20fc4-137">İş Akışı Tasarımcısı'nı kullanarak bir iş akışı hizmeti oluşturulduğunda <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> kullanılarak ayarlanan **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="20fc4-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="20fc4-138">' A tıklayın hizmetin Kök etkinlik iş akışı hizmeti seçin ve tasarımcıda dışında **Özellikler penceresi** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="20fc4-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="20fc4-139">Seçin **Workflowıdentity** yanında görüntülenen aşağı açılan listeden **DefinitionIdentity** özelliğini genişletin ve ardından istenen belirtin <xref:System.Activities.WorkflowIdentity> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="20fc4-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="20fc4-140">Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırılmış <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Version%2A> , `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="20fc4-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="20fc4-141"><xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve bu örnekte `null`.</span><span class="sxs-lookup"><span data-stu-id="20fc4-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![DefinitionIdentity özelliği gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="20fc4-143">Bir iş akışı hizmeti, şirket içinde barındırılan olduğunda <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmeti oluşturulduğunda yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="20fc4-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="20fc4-144">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki örnekle aynı değerleri ile yapılandırılmış <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Name%2A> , `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="20fc4-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="20fc4-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmeti yalnızca bir sürümüne sahip, ancak gerekli değildir bir **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="20fc4-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20fc4-146">Hizmet olmadan başlangıçta dağıtıldıysa kullanışlıdır bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırılmış, ve ardından güncelleştirilmiş bir sürüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="20fc4-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="20fc4-147">Bir Web barındırılan iş akışı hizmeti için yeni bir sürüm ekleme</span><span class="sxs-lookup"><span data-stu-id="20fc4-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="20fc4-148">Bir iş akışı hizmeti yeni bir sürümü web barındırılan bir hizmete yapılandırmada ilk adım, yeni bir klasöre oluşturmaktır `App_Code` hizmet dosyası aynı ada sahip bir klasör.</span><span class="sxs-lookup"><span data-stu-id="20fc4-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="20fc4-149">Varsa bu hizmetin `xamlx` dosya adlı `MortgageWorkflow.xamlx`, klasörü adlandırılmalıdır `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="20fc4-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="20fc4-150">Özgün hizmetin bir kopyasını yerleştirmek `xamlx` gibi yeni bir ad ile yeniden adlandırın ve bu klasöre dosya `MortgageWorkflowV1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="20fc4-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="20fc4-151">İstediğiniz değişiklikleri birincil hizmetinize, güncelleştirme, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>ve ardından hizmeti dağıtmak.</span><span class="sxs-lookup"><span data-stu-id="20fc4-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="20fc4-152">Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ile güncelleştirilmiş bir <xref:System.Activities.WorkflowIdentity.Name%2A> , `MortageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Version%2A> , `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="20fc4-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![DefinitionIdentity, Workflowıdentity gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="20fc4-154">Hizmet yeniden başlatıldığında, önceki sürümü otomatik olarak eklenir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyon yer olduğu için belirlenen `App_Code` alt.</span><span class="sxs-lookup"><span data-stu-id="20fc4-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="20fc4-155">İş akışı hizmetinin birincil sürümü gerçekleştiriyorsanız bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki sürümleri eklenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="20fc4-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="20fc4-156">Bir sürümü olabilir bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ancak birden çok sürüm varsa birincil sürüm sahip olmamalıdır `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ya da aksi takdirde önceki sürümler için eklenmeyecek <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="20fc4-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="20fc4-157">Şirket içinde barındırılan iş akışı hizmeti için yeni bir sürüm ekleme</span><span class="sxs-lookup"><span data-stu-id="20fc4-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="20fc4-158">Yeni bir sürümü, şirket içinde barındırılan iş akışı hizmetine eklerken <xref:System.ServiceModel.Activities.WorkflowServiceHost> birincil iş akışı hizmeti sürümü ile yapılandırılmış ve önceki sürümleri açıkça eklenmelidir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="20fc4-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="20fc4-159">Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> kullanan bir birincil iş akışı hizmeti ile yapılandırılmış bir `MortgageWorkflowV2` iş akışı tanımı ve bir iş akışı hizmeti ile yapılandırılmış bir `MortgageWorkflowV1` iş akışı tanımı eklenir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="20fc4-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="20fc4-160">Her iş akışı hizmeti benzersiz bir yapılandırılmış <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , iş akışı tanımının sürümü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="20fc4-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
