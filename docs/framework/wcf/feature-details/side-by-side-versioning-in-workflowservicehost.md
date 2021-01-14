---
title: WorkflowServiceHost Yan Yana Sürüm Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 1505582e5ac7303a2df20539fdcf67435746b9d3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190500"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="d7cd3-102">WorkflowServiceHost Yan Yana Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7cd3-102">Side by Side Versioning in WorkflowServiceHost</span></span>

<span data-ttu-id="d7cd3-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost>.NET Framework 4,5 ' de sunulan yan yana sürüm oluşturma, bir iş akışı hizmetinin birden çok sürümünü tek bir uç noktada barındırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="d7cd3-104">Belirtilen yan yana işlevsellik, iş akışı hizmeti 'nin yeni iş akışı tanımı kullanılarak oluşturulması için bir iş akışı hizmetinin yapılandırılmasına izin verir, böylece örnekleri mevcut tanımı kullanarak tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="d7cd3-105">Bu konu, kullanarak iş akışı hizmeti 'nin yan yana yürütmeye genel bir bakış sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="d7cd3-106">Bir Iş akışı hizmetinde birden çok sürümü barındırma</span><span class="sxs-lookup"><span data-stu-id="d7cd3-106">Hosting Multiple Versions in a Workflow Service</span></span>  

 <span data-ttu-id="d7cd3-107"><xref:System.ServiceModel.Activities.WorkflowServiceHost> , bir iş akışının birden çok sürümünün yan yana yürütülmesine izin vermek için yapılandırılabilecek iki özellik içerir: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-107"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="d7cd3-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> , iş akışı hizmetinin desteklenen sürümlerini içerir ve her bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmetini benzersiz şekilde tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="d7cd3-109">Bu <xref:System.Activities.WorkflowIdentity> , bir iş akışı hizmeti ile ilişkilendirerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-109">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="d7cd3-110"><xref:System.Activities.WorkflowIdentity>, Üç tanımlayıcı bilgi parçasını içerir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-110">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="d7cd3-111"><xref:System.Activities.WorkflowIdentity.Name%2A> ve bir <xref:System.Activities.WorkflowIdentity.Version%2A> ad ve bir içerir ve <xref:System.Version> gereklidir ve <xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve derleme adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-111"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="d7cd3-112">Koleksiyonda bulunan her iş akışı hizmetinin <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> benzersiz olması gerekir <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-112">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="d7cd3-113">, <xref:System.Activities.WorkflowIdentity> Üç özelliklerinden biri diğerinden farklıysa benzersizdir <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-113">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="d7cd3-114">`null` <xref:System.Activities.WorkflowIdentity> , İçin izin verilen bir değerdir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , ancak bir iş akışı hizmetinin yalnızca bir önceki sürümü olabilir `null` <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-114">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d7cd3-115">Bir <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlanabilir bilgiler (PII) içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-115">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="d7cd3-116"><xref:System.Activities.WorkflowIdentity> üç bölümden oluşur: a <xref:System.Activities.WorkflowIdentity.Name%2A> ( <xref:System.String> ), a <xref:System.Activities.WorkflowIdentity.Version%2A> ( <xref:System.Version> ) ve a <xref:System.Activities.WorkflowIdentity.Package%2A> ( <xref:System.String> ).</span><span class="sxs-lookup"><span data-stu-id="d7cd3-116"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="d7cd3-117"><xref:System.Activities.WorkflowIdentity>Örnek oluşturmak için kullanılan hakkında bilgiler, çalışma zamanına göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-117">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="d7cd3-118">WF Izlemenin PII (hassas Kullanıcı verileri) ' i gizlemek için herhangi bir mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-118">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="d7cd3-119">Bu nedenle, <xref:System.Activities.WorkflowIdentity> kayıtlar izlenirken çalışma zamanı tarafından yayınlandığından ve izleme kayıtlarını görüntülemek için erişimi olan herkese görünebilir olabileceğinden bir örnek herhangi BIR PII verisi içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-119">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="d7cd3-120">Bir Iş akışı hizmetinin birden çok sürümünü barındırmak için kurallar</span><span class="sxs-lookup"><span data-stu-id="d7cd3-120">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  

 <span data-ttu-id="d7cd3-121">Bir Kullanıcı öğesine ek bir sürüm eklediğinde <xref:System.ServiceModel.Activities.WorkflowServiceHost> , bir iş akışı hizmetinin aynı uç nokta ve açıklama kümesiyle barındırılması için karşılanması gereken birkaç koşul vardır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-121">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="d7cd3-122">Ek sürümlerden herhangi biri bu koşulları karşılamıyorsa, <xref:System.ServiceModel.Activities.WorkflowServiceHost> çağrıldığında bir özel durum oluşturur `Open` .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-122">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="d7cd3-123">Ana bilgisayara ek sürüm olarak sunulan her iş akışı tanımı, aşağıdaki gereksinimleri karşılamalıdır (birincil sürüm, ana bilgisayar oluşturucusuna sunulan iş akışı hizmeti tanımıdır).</span><span class="sxs-lookup"><span data-stu-id="d7cd3-123">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="d7cd3-124">Ek iş akışı sürümü şunları içermelidir:</span><span class="sxs-lookup"><span data-stu-id="d7cd3-124">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="d7cd3-125">, <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> İş akışı hizmetinin birincil sürümüyle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-125">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="d7cd3-126">, <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> Birincil sürümde olmayan bir veya etkinliği olmaması <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> ve işlem sözleşmesiyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-126">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="d7cd3-127">Benzersiz bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-127">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="d7cd3-128">Bir ve yalnızca bir iş akışı tanımının bir tane olabilir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-128">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="d7cd3-129">Bazı değişikliklere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-129">Some changes are permitted.</span></span> <span data-ttu-id="d7cd3-130">Aşağıdaki öğeler sürümler arasında farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="d7cd3-130">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="d7cd3-131">, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Birincil sürümden farklı bir ada ve pakete sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-131">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="d7cd3-132"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A>Değer, birincil sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-132">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="d7cd3-133">, <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Birincil sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-133">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="d7cd3-134">, <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Birincil sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-134">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="d7cd3-135">DefinitionIdentity yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7cd3-135">Configuring the DefinitionIdentity</span></span>  

 <span data-ttu-id="d7cd3-136">Bir iş akışı hizmeti, iş akışı Tasarımcısı kullanılarak oluşturulduğunda, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> **Özellikler** penceresi kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-136">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="d7cd3-137">İş akışı hizmetini seçmek için tasarımcıda hizmetin kök etkinliğinin dışını tıklatın ve **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-137">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="d7cd3-138">**DefinitionIdentity** özelliğinin yanında görünen açılan listeden **WorkflowIdentity** ' ı seçin ve ardından istediğiniz özellikleri genişletin ve belirtin <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-138">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="d7cd3-139">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve ile yapılandırılır <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Version%2A> `1.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-139">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="d7cd3-140"><xref:System.Activities.WorkflowIdentity.Package%2A> isteğe bağlıdır ve bu örnekte `null` .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-140"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![DefinitionIdentity özelliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="d7cd3-142">Bir iş akışı hizmeti kendiliğinden barındırıldığı zaman, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmeti oluşturulduğunda yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-142">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="d7cd3-143">Aşağıdaki örnekte,, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve içeren önceki örnekle aynı değerlerle yapılandırılır <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-143">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="d7cd3-144">Bir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı hizmetinin yalnızca bir sürümü **null** olabilir, ancak bu gerekli değildir <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-144">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7cd3-145">Bu, hizmet başlangıçta yapılandırıldıktan sonra dağıtılmışsa <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve sonra güncelleştirilmiş bir sürüm oluşturulduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-145">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="d7cd3-146">Web 'de barındırılan Iş akışı hizmetine yeni bir sürüm ekleme</span><span class="sxs-lookup"><span data-stu-id="d7cd3-146">Adding a New Version to a Web-hosted Workflow Service</span></span>  

 <span data-ttu-id="d7cd3-147">Web 'de barındırılan bir hizmette iş akışı hizmetinin yeni bir sürümünü yapılandırmanın ilk adımı, `App_Code` klasörde hizmet dosyası ile aynı ada sahip yeni bir klasör oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-147">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="d7cd3-148">Hizmetin `xamlx` dosyası adlandırılmışsa `MortgageWorkflow.xamlx` , klasörün adlandırılmış olması gerekir `MortgageWorkflow` .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-148">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="d7cd3-149">Özgün hizmetin dosyasının bir kopyasını `xamlx` Bu klasöre yerleştirin ve gibi yeni bir adla yeniden adlandırın `MortgageWorkflowV1.xamlx` .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-149">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="d7cd3-150">Birincil hizmette istenen değişiklikleri yapın, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> öğesini güncelleştirin ve ardından hizmeti dağıtın.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-150">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="d7cd3-151">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve ' a ile güncelleştirilmiştir <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Version%2A> `2.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-151">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![WorkflowIdentity 'nin Definitionkimliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="d7cd3-153">Hizmet yeniden başlatıldığında, <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> belirtilen alt klasörde bulunduğu için önceki sürüm otomatik olarak koleksiyona eklenecektir `App_Code` .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-153">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="d7cd3-154">İş akışı hizmetinin birincil sürümünde `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki sürümlerin eklenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-154">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="d7cd3-155">Bir sürüm bir olabilir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , ancak birden çok sürüm varsa, birincil sürüm veya ' ı içeren bir `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki sürümler <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona eklenmez.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-155">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="d7cd3-156">Şirket içinde barındırılan Iş akışı hizmetine yeni bir sürüm ekleme</span><span class="sxs-lookup"><span data-stu-id="d7cd3-156">Adding a New Version to a Self-hosted Workflow Service</span></span>  

 <span data-ttu-id="d7cd3-157">Şirket içinde barındırılan bir iş akışı hizmetine yeni bir sürüm eklerken,, <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı hizmetinin birincil sürümüyle yapılandırılır ve önceki sürümlerin koleksiyona açıkça eklenmesi gerekir <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> .</span><span class="sxs-lookup"><span data-stu-id="d7cd3-157">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="d7cd3-158">Aşağıdaki örnekte, bir iş akışı <xref:System.ServiceModel.Activities.WorkflowServiceHost> tanımı kullanan birincil iş akışı hizmeti ile yapılandırılır ve bir iş akışı `MortgageWorkflowV2` tanımıyla yapılandırılmış bir iş akışı hizmeti `MortgageWorkflowV1` <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona eklenir.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-158">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="d7cd3-159">Her iş akışı hizmeti, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> iş akışı tanımının sürümünü yansıtan benzersiz bir şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d7cd3-159">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
