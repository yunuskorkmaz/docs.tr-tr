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
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="be599-102">WorkflowServiceHost Yan Yana Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="be599-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="be599-103">.NET Framework 4.5'te tanıtılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> yan yana sürüm, bir iş akışı hizmetinin birden çok sürümünü tek bir uç noktada barındırma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="be599-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="be599-104">Sağlanan yan yana işlevsellik, iş akışı hizmetinin yeni iş akışı tanımı kullanılarak oluşturulacak şekilde yapılandırılmasına olanak sağlarken, örnekleri varolan tanım kullanılarak tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="be599-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="be599-105">Bu konu, iş akışı hizmetinin yan yana <xref:System.ServiceModel.Activities.WorkflowServiceHost>yürütülmesine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="be599-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be599-106">Bir örneği indirmek ve iş akışı hizmetinin yan yana sürümvideosunu izlemek için, [Web tarafından Barındırılan Xamlx İş Akışı Hizmeti ile Yan Yan Sürümleme](https://go.microsoft.com/fwlink/?LinkId=393746)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="be599-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="be599-107">İş Akışı Hizmetinde Birden Çok Sürümü Barındırma</span><span class="sxs-lookup"><span data-stu-id="be599-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="be599-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>bir iş akışının birden çok sürümüyan yana yürütmek için izin için <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> yapılandırılabilir iki özellik içerir: ve <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="be599-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="be599-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>iş akışı hizmetinin desteklenen sürümlerini <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> içerir ve her iş akışı hizmetini benzersiz olarak tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be599-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="be599-110">Bu iş akışı hizmeti ile <xref:System.Activities.WorkflowIdentity> bir ilişki içinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="be599-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="be599-111">A, <xref:System.Activities.WorkflowIdentity> tanımlayıcı üç bilgi parçası içerir.</span><span class="sxs-lookup"><span data-stu-id="be599-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="be599-112"><xref:System.Activities.WorkflowIdentity.Name%2A>ve <xref:System.Activities.WorkflowIdentity.Version%2A> bir ad <xref:System.Version> ve a içerir <xref:System.Activities.WorkflowIdentity.Package%2A> ve gereklidir ve isteğe bağlıdır ve montaj adı veya diğer istenen bilgiler gibi bilgileri içeren ek bir dize belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be599-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="be599-113">Koleksiyonda yer alan <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> her iş akışı <xref:System.Activities.WorkflowIdentity>hizmetinin benzersiz bir .</span><span class="sxs-lookup"><span data-stu-id="be599-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="be599-114">A, <xref:System.Activities.WorkflowIdentity> üç özelliğinden herhangi biri diğerinden <xref:System.Activities.WorkflowIdentity>farklıysa benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="be599-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="be599-115">A `null` <xref:System.Activities.WorkflowIdentity> için <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>izin verilebilen bir değerdir, ancak iş akışı `null` <xref:System.Activities.WorkflowIdentity>hizmetinin yalnızca bir önceki sürümü .</span><span class="sxs-lookup"><span data-stu-id="be599-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="be599-116">A, <xref:System.Activities.WorkflowIdentity> kişisel olarak tanımlayıcı bilgiler (PII) içermemelidir.</span><span class="sxs-lookup"><span data-stu-id="be599-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="be599-117"><xref:System.Activities.WorkflowIdentity>üç bölümden oluşur: <xref:System.Activities.WorkflowIdentity.Name%2A> <xref:System.String>a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), <xref:System.Activities.WorkflowIdentity.Package%2A> a<xref:System.String>( ), ve a ( ).</span><span class="sxs-lookup"><span data-stu-id="be599-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="be599-118">Bir örnek <xref:System.Activities.WorkflowIdentity> oluşturmak için kullanılan bilgiler, çalışma süresine göre etkinlik yaşam döngüsünün birkaç farklı noktasında yapılandırılmış izleme hizmetlerine yayılır.</span><span class="sxs-lookup"><span data-stu-id="be599-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="be599-119">WF İzleme'nin KIŞISEL Bilgileri (hassas kullanıcı verilerini) gizlemek için herhangi bir mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="be599-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="be599-120">Bu nedenle, bir örnek, izleme kayıtlarında çalışma zamanı tarafından yayılacağı için herhangi bir <xref:System.Activities.WorkflowIdentity> KIŞISEL veri içermemelidir ve izleme kayıtlarını görüntülemek için erişimi olan herkes tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="be599-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="be599-121">İş Akışı Hizmetinin Birden Çok Sürümü barındırma kuralları</span><span class="sxs-lookup"><span data-stu-id="be599-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="be599-122">Bir kullanıcı <xref:System.ServiceModel.Activities.WorkflowServiceHost>, bir iş akışı hizmetinin aynı uç nokta ve açıklama kümesiyle barındırılabilmesi için karşılanması gereken birkaç koşul vardır.</span><span class="sxs-lookup"><span data-stu-id="be599-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="be599-123">Ek sürümlerden herhangi biri bu koşulları <xref:System.ServiceModel.Activities.WorkflowServiceHost> karşılamazsa, `Open` çağrıldığında bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be599-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="be599-124">Ek sürüm olarak ana bilgisayara sağlanan her iş akışı tanımı aşağıdaki gereksinimleri karşılamalıdır (birincil sürüm, ana bilgisayar oluşturucuya sağlanan iş akışı hizmeti tanımıdır).</span><span class="sxs-lookup"><span data-stu-id="be599-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="be599-125">Ek iş akışı sürümü şunları yapmalı:</span><span class="sxs-lookup"><span data-stu-id="be599-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="be599-126">İş akışı <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> hizmetinin birincil sürümüyle aynı sıyrıkta dır.</span><span class="sxs-lookup"><span data-stu-id="be599-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="be599-127">Birincil sürümde <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> <xref:System.ServiceModel.Activities.SendReply> olmayan herhangi bir faaliyetveya faaliyet olmamalıdır ve işlem sözleşmesine uymaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="be599-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="be599-128">Benzersiz <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>bir var .</span><span class="sxs-lookup"><span data-stu-id="be599-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="be599-129">Bir ve tek bir iş `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>akışı tanımı .</span><span class="sxs-lookup"><span data-stu-id="be599-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="be599-130">Bazı değişikliklere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="be599-130">Some changes are permitted.</span></span> <span data-ttu-id="be599-131">Aşağıdaki öğeler sürümler arasında farklı olabilir:</span><span class="sxs-lookup"><span data-stu-id="be599-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="be599-132">Birincil <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> sürümden farklı bir Ad ve Paket olabilir.</span><span class="sxs-lookup"><span data-stu-id="be599-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="be599-133">Değer <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> birincil sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="be599-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="be599-134">Birincil <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="be599-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="be599-135">Birincil <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> sürümden farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="be599-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="be599-136">Tanımlı Kimliğin Yapılandırılması</span><span class="sxs-lookup"><span data-stu-id="be599-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="be599-137">İş akışı tasarımcısı kullanılarak bir iş akışı <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> hizmeti oluşturulduğunda, **Özellikler** penceresi kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="be599-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="be599-138">İş akışı hizmetini seçmek için tasarımcıda hizmetin kök etkinliğinin dışına tıklayın ve **Görünüm** menüsünden **Özellikler Penceresi'ni** seçin.</span><span class="sxs-lookup"><span data-stu-id="be599-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="be599-139">**DefinitionIdentity** özelliğinin yanında görünen açılır listeden **İş Akışı Kimliği'ni** seçin ve <xref:System.Activities.WorkflowIdentity> ardından istediğiniz özellikleri genişletip belirtin.</span><span class="sxs-lookup"><span data-stu-id="be599-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="be599-140">Aşağıdaki örnekte <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> ve a <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` <xref:System.Activities.WorkflowIdentity.Version%2A> ile `1.0.0.0`yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="be599-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="be599-141"><xref:System.Activities.WorkflowIdentity.Package%2A>isteğe bağlıdır ve `null`bu örnekte .</span><span class="sxs-lookup"><span data-stu-id="be599-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![DefinitionIdentity özelliğini gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="be599-143">Bir iş akışı hizmeti kendi kendine <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> barındırıldığında, iş akışı hizmeti oluşturulduğunda yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="be599-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="be599-144">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> önceki örnekle <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` aynı değerlerle yapılandırılır, <xref:System.Activities.WorkflowIdentity.Name%2A> `1.0.0.0`ve bir .</span><span class="sxs-lookup"><span data-stu-id="be599-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
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
  
 <span data-ttu-id="be599-145">İş <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> akışı hizmetinin yalnızca bir sürümü **nde null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>olsa da, A gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="be599-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be599-146">Bu, hizmet başlangıçta <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> yapılandırılmadan dağıtıldıysa ve daha sonra güncelleştirilmiş bir sürüm oluşturulduysa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="be599-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="be599-147">Web tarafından barındırılan İş Akışı Hizmetine Yeni Sürüm Ekleme</span><span class="sxs-lookup"><span data-stu-id="be599-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="be599-148">Web tarafından barındırılan bir hizmette iş akışı hizmetinin yeni bir sürümünü yapılandırmanın `App_Code` ilk adımı, klasörde hizmet dosyasıyla aynı ada sahip yeni bir klasör oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="be599-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="be599-149">Hizmetin `xamlx` dosyası adlandırılmışsa, `MortgageWorkflow.xamlx`klasörün adı `MortgageWorkflow`gerekir.</span><span class="sxs-lookup"><span data-stu-id="be599-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="be599-150">Özgün hizmetdosyasının `xamlx` bir kopyasını bu klasöre yerleştirin ve `MortgageWorkflowV1.xamlx`yeni bir ada yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="be599-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="be599-151">Birincil hizmette istenen değişiklikleri yapın, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>hizmetini güncelleştirin ve sonra dağıtın.</span><span class="sxs-lookup"><span data-stu-id="be599-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="be599-152">Aşağıdaki <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> örnekte bir <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` ve bir <xref:System.Activities.WorkflowIdentity.Version%2A> ile güncellendi `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="be599-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![İş Akışı Kimliğinin Tanımını gösteren ekran görüntüsü.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="be599-154">Hizmet yeniden başlatıldığında, belirlenen <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> `App_Code` alt klasörde bulunduğundan önceki sürüm otomatik olarak koleksiyona eklenir.</span><span class="sxs-lookup"><span data-stu-id="be599-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="be599-155">İş akışı hizmetinin `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> birincil sürümünde önceki sürümler eklenmez.</span><span class="sxs-lookup"><span data-stu-id="be599-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="be599-156">Bir sürümün `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>bir , ancak birden çok sürümü varsa birincil sürümü `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> veya başka önceki sürümleri <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> ile bir koleksiyona eklenmez olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="be599-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="be599-157">Kendi Barındırılan İş Akışı Hizmetine Yeni Sürüm Ekleme</span><span class="sxs-lookup"><span data-stu-id="be599-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="be599-158">Kendi kendine barındırılan iş akışı hizmetine <xref:System.ServiceModel.Activities.WorkflowServiceHost> yeni bir sürüm eklerken, iş akışı hizmetinin birincil sürümüyle yapılandırılır ve önceki sürümlerin <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona açıkça eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="be599-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="be599-159">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı tanımı kullanan `MortgageWorkflowV2` birincil iş akışı hizmetiyle bir yapılandırılır ve `MortgageWorkflowV1` <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> koleksiyona iş akışı tanımıyla yapılandırılan bir iş akışı hizmeti eklenir.</span><span class="sxs-lookup"><span data-stu-id="be599-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="be599-160">Her iş akışı hizmeti, iş <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> akışı tanımının sürümünü yansıtan benzersiz bir şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="be599-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
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
