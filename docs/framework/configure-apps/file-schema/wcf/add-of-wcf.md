---
title: <add>WCF
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: fa94f15a296aa03640bf0a262eb45ea1664944cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926609"
---
# <a name="add-of-wcf"></a><span data-ttu-id="8ab37-102">\<WCF > ekleyin</span><span class="sxs-lookup"><span data-stu-id="8ab37-102">\<add> of WCF</span></span>
<span data-ttu-id="8ab37-103">Çalışma zamanından doğrudan yayılmakta olan izleme kayıtlarını dinleyen bir izleme katılımcısı yapılandırın ve bunları ne şekilde yapılandırdığınıza göre işleyin.</span><span class="sxs-lookup"><span data-stu-id="8ab37-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="8ab37-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="8ab37-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="8ab37-105">İş akışı izleme ve İzleme katılımcıları hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) Izleme ve [İzleme katılımcıları](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="8ab37-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="8ab37-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8ab37-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8ab37-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="8ab37-107">\<tracking></span></span>  
<span data-ttu-id="8ab37-108">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="8ab37-108">\<participants></span></span>  
<span data-ttu-id="8ab37-109">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="8ab37-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ab37-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ab37-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ab37-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ab37-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8ab37-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ab37-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ab37-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ab37-113">Attributes</span></span>  
  
|<span data-ttu-id="8ab37-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ab37-114">Element</span></span>|<span data-ttu-id="8ab37-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ab37-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ab37-116">name</span><span class="sxs-lookup"><span data-stu-id="8ab37-116">name</span></span>|<span data-ttu-id="8ab37-117">İzleme katılımcısının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8ab37-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="8ab37-118">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="8ab37-118">profileName</span></span>|<span data-ttu-id="8ab37-119">İzleme katılımcının abone olduğu izleme kayıtlarını tanımlayan izleme profili adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8ab37-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="8ab37-120">türü</span><span class="sxs-lookup"><span data-stu-id="8ab37-120">type</span></span>|<span data-ttu-id="8ab37-121">İzleme katılımcısı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8ab37-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ab37-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ab37-122">Child Elements</span></span>  
 <span data-ttu-id="8ab37-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ab37-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ab37-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ab37-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8ab37-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ab37-125">Element</span></span>|<span data-ttu-id="8ab37-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ab37-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ab37-127">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="8ab37-127">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="8ab37-128">İzleme katılımcılarının listesi</span><span class="sxs-lookup"><span data-stu-id="8ab37-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ab37-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ab37-129">Remarks</span></span>  
 <span data-ttu-id="8ab37-130">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ab37-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="8ab37-131">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ab37-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="8ab37-132">Birden çok izleme katılımcısı izleme olaylarını eşzamanlı olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8ab37-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="8ab37-133">Her izleme katılımcısı, farklı bir izleme profiliyle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ab37-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="8ab37-134">İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8ab37-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="8ab37-135">Katılımcı bir yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek bir iş akışı hizmeti üzerinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="8ab37-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="8ab37-136">ETW izleme katılımcısının etkinleştirilmesi, Olay Görüntüleyicisi 'nde izleme kayıtlarının görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="8ab37-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="8ab37-137">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ab37-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab37-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ab37-138">Example</span></span>  
 <span data-ttu-id="8ab37-139">Aşağıdaki yapılandırma örneği, Web. config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ab37-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="8ab37-140">ETW izleme katılımcısı tarafından ETW 'ye izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği `<diagnostics>` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8ab37-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="8ab37-141">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="8ab37-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="8ab37-142">Bu, `profileName` `<add>` öğesinin özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8ab37-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="8ab37-143">Bunlar tanımlandıktan sonra, izleme katılımcısı `<etwTracking>` hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="8ab37-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="8ab37-144">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="8ab37-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="8ab37-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ab37-145">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="8ab37-146">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8ab37-146">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8ab37-147">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="8ab37-147">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
