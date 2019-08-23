---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: f04a5ee3940986cabc08895452c12ebcfd631694
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947577"
---
# <a name="participants"></a><span data-ttu-id="a1b0e-101">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="a1b0e-101">\<participants></span></span>
<span data-ttu-id="a1b0e-102">Çalışma zamanından doğrudan yayılmakta olan izleme kayıtlarını dinleyen bir izleme katılımcıları listesini yapılandırın ve bunları yapılandırıldıklarında her türlü şekilde işleyin.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="a1b0e-103">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="a1b0e-104">İş akışı izleme ve İzleme katılımcıları hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) Izleme ve [İzleme katılımcıları](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="a1b0e-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="a1b0e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a1b0e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a1b0e-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a1b0e-106">\<tracking></span></span>  
<span data-ttu-id="a1b0e-107">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="a1b0e-107">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b0e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1b0e-108">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1b0e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1b0e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a1b0e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1b0e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a1b0e-111">Attributes</span></span>  
 <span data-ttu-id="a1b0e-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1b0e-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1b0e-113">Child Elements</span></span>  
  
|<span data-ttu-id="a1b0e-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1b0e-114">Element</span></span>|<span data-ttu-id="a1b0e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1b0e-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1b0e-116">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="a1b0e-116">\<add></span></span>](add-of-participants.md)|<span data-ttu-id="a1b0e-117">İzleme katılımcısı için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-117">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1b0e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1b0e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a1b0e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1b0e-119">Element</span></span>|<span data-ttu-id="a1b0e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1b0e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1b0e-121">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a1b0e-121">\<tracking></span></span>](tracking.md)|<span data-ttu-id="a1b0e-122">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1b0e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1b0e-123">Remarks</span></span>  
 <span data-ttu-id="a1b0e-124">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-124">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="a1b0e-125">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-125">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="a1b0e-126">Birden çok izleme katılımcısı izleme olaylarını eşzamanlı olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-126">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="a1b0e-127">Her izleme katılımcısı, farklı bir izleme profiliyle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-127">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="a1b0e-128">İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-128">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="a1b0e-129">Katılımcı bir yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek bir iş akışı hizmeti üzerinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-129">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="a1b0e-130">ETW izleme katılımcısının etkinleştirilmesi, Olay Görüntüleyicisi 'nde izleme kayıtlarının görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-130">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="a1b0e-131">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-131">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1b0e-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1b0e-132">Example</span></span>  
 <span data-ttu-id="a1b0e-133">Aşağıdaki yapılandırma örneği, Web. config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-133">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="a1b0e-134">ETW izleme katılımcısı tarafından ETW 'ye izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği,  **\<Tanılama >** bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-134">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="a1b0e-135">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-135">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="a1b0e-136">Bu,  **\<Add >** öğesinin **ProfileName** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-136">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="a1b0e-137">Bunlar tanımlandıktan sonra, izleme katılımcısı  **\<etwTracking >** hizmeti davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-137">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="a1b0e-138">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-138">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1b0e-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1b0e-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="a1b0e-140">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a1b0e-140">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a1b0e-141">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="a1b0e-141">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
