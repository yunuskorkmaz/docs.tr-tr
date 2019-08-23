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
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="bc10b-102">WorkflowServiceHost Yan Yana Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bc10b-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="bc10b-103">.NET Framework 4,5 ' de sunulan yanyanasürümoluşturma,birişakışıhizmetininbirdençoksürümünütekbiruçnoktadabarındırmanızaolanaksağlar.<xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="bc10b-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="bc10b-104">Belirtilen yan yana işlevsellik, iş akışı hizmeti 'nin yeni iş akışı tanımı kullanılarak oluşturulması için bir iş akışı hizmetinin yapılandırılmasına izin verir, böylece örnekleri mevcut tanımı kullanarak tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="bc10b-105">Bu konu, kullanarak <xref:System.ServiceModel.Activities.WorkflowServiceHost>iş akışı hizmeti 'nin yan yana yürütmeye genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc10b-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc10b-106">Bir örneği indirmek ve iş akışı hizmeti 'nin yan yana sürüm oluşturma kılavuzunu izlemek için bkz. [Web 'de barındırılan xamlx Iş akışı hizmeti Ile yan yana sürüm oluşturma](https://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="bc10b-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="bc10b-107">Bir Iş akışı hizmetinde birden çok sürümü barındırma</span><span class="sxs-lookup"><span data-stu-id="bc10b-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="bc10b-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>, bir iş akışının birden çok sürümünün yan yana yürütülmesine izin vermek için yapılandırılabilecek iki özellik içerir: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ve. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="bc10b-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="bc10b-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>, iş akışı hizmetinin desteklenen sürümlerini içerir ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> her bir iş akışı hizmetini benzersiz şekilde tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="bc10b-110">Bu, bir <xref:System.Activities.WorkflowIdentity> iş akışı hizmeti ile ilişkilendirerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="bc10b-111">, Üç tanımlayıcı bilgi parçasını içerir.<xref:System.Activities.WorkflowIdentity></span><span class="sxs-lookup"><span data-stu-id="bc10b-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="bc10b-112"><xref:System.Activities.WorkflowIdentity.Name%2A>ve bir ad ve bir <xref:System.Version> <xref:System.Activities.WorkflowIdentity.Version%2A> içerir ve gereklidir <xref:System.Activities.WorkflowIdentity.Package%2A> ve isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="bc10b-113"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> Koleksiyonda bulunan her iş akışı hizmetinin benzersiz <xref:System.Activities.WorkflowIdentity>olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="bc10b-114">, Üç özelliklerinden biri diğerinden <xref:System.Activities.WorkflowIdentity>farklıysa benzersizdir. <xref:System.Activities.WorkflowIdentity></span><span class="sxs-lookup"><span data-stu-id="bc10b-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="bc10b-115">`null` ,İçin<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>izin verilen bir değerdir, ancak bir iş akışı hizmetinin `null` yalnızca bir önceki <xref:System.Activities.WorkflowIdentity>sürümü olabilir. <xref:System.Activities.WorkflowIdentity></span><span class="sxs-lookup"><span data-stu-id="bc10b-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bc10b-116">Bir <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlanabilir bilgiler (PII) içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="bc10b-117"><xref:System.Activities.WorkflowIdentity>üç bölümden oluşur: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) ve a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="bc10b-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="bc10b-118">Örnek oluşturmak için <xref:System.Activities.WorkflowIdentity> kullanılan hakkında bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="bc10b-119">WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="bc10b-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="bc10b-120">Bu nedenle, <xref:System.Activities.WorkflowIdentity> kayıtlar izlenirken çalışma zamanı tarafından yayınlandığından ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir olabileceğinden bir örnek herhangi bir PII verisi içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="bc10b-121">Bir Iş akışı hizmetinin birden çok sürümünü barındırmak için kurallar</span><span class="sxs-lookup"><span data-stu-id="bc10b-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="bc10b-122">Bir Kullanıcı öğesine <xref:System.ServiceModel.Activities.WorkflowServiceHost>ek bir sürüm eklediğinde, bir iş akışı hizmetinin aynı uç nokta ve açıklama kümesiyle barındırılması için karşılanması gereken birkaç koşul vardır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="bc10b-123">Ek sürümlerden herhangi biri bu koşulları karşılamıyorsa, <xref:System.ServiceModel.Activities.WorkflowServiceHost> çağrıldığında bir `Open` özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bc10b-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="bc10b-124">Ana bilgisayara ek sürüm olarak sunulan her iş akışı tanımı, aşağıdaki gereksinimleri karşılamalıdır (birincil sürüm, ana bilgisayar oluşturucusuna sunulan iş akışı hizmeti tanımıdır).</span><span class="sxs-lookup"><span data-stu-id="bc10b-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="bc10b-125">Ek iş akışı sürümü şunları içermelidir:</span><span class="sxs-lookup"><span data-stu-id="bc10b-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="bc10b-126">, <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> İş akışı hizmetinin birincil sürümüyle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="bc10b-127">, Birincil sürümde olmayan <xref:System.ServiceModel.Activities.Receive> bir <xref:System.ServiceModel.Activities.SendReply> veya etkinliği <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> olmaması ve işlem sözleşmesiyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="bc10b-128">Benzersiz <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>bir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="bc10b-129">Bir ve yalnızca bir iş akışı tanımının bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>tane olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="bc10b-130">Bazı değişikliklere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-130">Some changes are permitted.</span></span> <span data-ttu-id="bc10b-131">Aşağıdaki öğeler sürümler arasında farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="bc10b-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="bc10b-132">, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Birincil sürümden farklı bir ada ve pakete sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="bc10b-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Değer, birincil sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="bc10b-134">, <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Birincil sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="bc10b-135">, <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Birincil sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="bc10b-136">DefinitionIdentity yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bc10b-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="bc10b-137">Bir iş akışı hizmeti, iş akışı Tasarımcısı <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> kullanılarak oluşturulduğunda, **Özellikler** penceresi kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="bc10b-138">İş akışı hizmetini seçmek için tasarımcıda hizmetin kök etkinliğinin dışını tıklatın ve **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="bc10b-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="bc10b-139">**DefinitionIdentity** özelliğinin yanında görünen açılan listeden <xref:System.Activities.WorkflowIdentity> **WorkflowIdentity** ' ı seçin ve ardından istediğiniz özellikleri genişletin ve belirtin.</span><span class="sxs-lookup"><span data-stu-id="bc10b-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="bc10b-140">Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , ve`MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> ile<xref:System.Activities.WorkflowIdentity.Version%2A>yapılandırılır .`1.0.0.0`</span><span class="sxs-lookup"><span data-stu-id="bc10b-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="bc10b-141"><xref:System.Activities.WorkflowIdentity.Package%2A>isteğe bağlıdır ve bu örnekte `null`.</span><span class="sxs-lookup"><span data-stu-id="bc10b-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![DefinitionIdentity özelliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="bc10b-143">Bir iş akışı hizmeti kendiliğinden barındırıldığı <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> zaman, iş akışı hizmeti oluşturulduğunda yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="bc10b-144">Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ,, `MortgageWorkflow` ve <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.Activities.WorkflowIdentity.Name%2A> içerenöncekiörnekle`1.0.0.0`aynı değerlerle yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="bc10b-145">Bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmetinin yalnızca bir sürümü **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>olabilir, ancak bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc10b-146">Bu, hizmet başlangıçta <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırıldıktan sonra dağıtılmışsa ve sonra güncelleştirilmiş bir sürüm oluşturulduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="bc10b-147">Web 'de barındırılan Iş akışı hizmetine yeni bir sürüm ekleme</span><span class="sxs-lookup"><span data-stu-id="bc10b-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="bc10b-148">Web 'de barındırılan bir hizmette iş akışı hizmetinin yeni bir sürümünü yapılandırmanın ilk adımı, `App_Code` klasörde hizmet dosyası ile aynı ada sahip yeni bir klasör oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="bc10b-149">Hizmetin `xamlx` dosyası adlandırılmışsa `MortgageWorkflow.xamlx`, klasörün adlandırılmış `MortgageWorkflow`olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="bc10b-150">Özgün hizmetin `xamlx` dosyasının bir kopyasını bu klasöre yerleştirin ve gibi yeni bir adla `MortgageWorkflowV1.xamlx`yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="bc10b-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="bc10b-151">Birincil hizmette istenen değişiklikleri yapın, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>öğesini güncelleştirin ve ardından hizmeti dağıtın.</span><span class="sxs-lookup"><span data-stu-id="bc10b-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="bc10b-152">Aşağıdaki <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> örnekte, `MortgageWorkflow` ve ' <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.Activities.WorkflowIdentity.Version%2A> a`2.0.0.0`ile güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![WorkflowIdentity 'nin Definitionkimliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="bc10b-154">Hizmet yeniden başlatıldığında, belirtilen <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> `App_Code` alt klasörde bulunduğu için önceki sürüm otomatik olarak koleksiyona eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="bc10b-155">İş akışı hizmetinin `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> birincil sürümünde önceki sürümlerin eklenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bc10b-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="bc10b-156">`null`Bir sürüm bir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> `null` olabilir, ancak birden çok sürüm varsa, birincil sürüm veya ' ı içeren bir önceki sürümler koleksiyona eklenmez. <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="bc10b-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="bc10b-157">Şirket içinde barındırılan Iş akışı hizmetine yeni bir sürüm ekleme</span><span class="sxs-lookup"><span data-stu-id="bc10b-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="bc10b-158">Şirket <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> içinde barındırılan bir iş akışı hizmetine yeni bir sürüm eklerken,, iş akışı hizmetinin birincil sürümüyle yapılandırılır ve önceki sürümlerin koleksiyona açıkça eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="bc10b-159"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Aşağıdaki örnekte, bir `MortgageWorkflowV2` iş akışı tanımı kullanan birincil iş akışı hizmeti ile yapılandırılır ve bir iş akışı tanımıyla yapılandırılmış `MortgageWorkflowV1` bir iş akışı hizmeti <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona eklenir.</span><span class="sxs-lookup"><span data-stu-id="bc10b-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="bc10b-160">Her iş akışı hizmeti, iş akışı tanımının <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> sürümünü yansıtan benzersiz bir şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="bc10b-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
