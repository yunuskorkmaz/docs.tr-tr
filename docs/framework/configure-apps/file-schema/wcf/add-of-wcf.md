---
title: <add> WCF
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: 76197120096329d0eb42121f5740a87c4f42318b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356019"
---
# <a name="add-of-wcf"></a><span data-ttu-id="1b9d2-102">\<Ekle > WCF</span><span class="sxs-lookup"><span data-stu-id="1b9d2-102">\<add> of WCF</span></span>
<span data-ttu-id="1b9d2-103">Çalışma zamanını şuradan doğrudan yayılan izleme kayıtları için bekleyen bir izleme katılımcı yapılandırın ve bunları yapılandırılan hangi yolla işlem.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="1b9d2-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="1b9d2-105">İş akışı izleme ve izleme katılımcıları daha fazla bilgi için bkz. [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="1b9d2-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="1b9d2-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1b9d2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1b9d2-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="1b9d2-107">\<tracking></span></span>  
<span data-ttu-id="1b9d2-108">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="1b9d2-108">\<participants></span></span>  
<span data-ttu-id="1b9d2-109">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="1b9d2-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9d2-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b9d2-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b9d2-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b9d2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1b9d2-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b9d2-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b9d2-113">Attributes</span></span>  
  
|<span data-ttu-id="1b9d2-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b9d2-114">Element</span></span>|<span data-ttu-id="1b9d2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b9d2-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b9d2-116">name</span><span class="sxs-lookup"><span data-stu-id="1b9d2-116">name</span></span>|<span data-ttu-id="1b9d2-117">İzleme katılımcı adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="1b9d2-118">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="1b9d2-118">profileName</span></span>|<span data-ttu-id="1b9d2-119">İzleme kayıtları tanımlayan izleme profilinin adını belirten bir dize için izleme katılımcı abone oldu.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="1b9d2-120"> türü</span><span class="sxs-lookup"><span data-stu-id="1b9d2-120">type</span></span>|<span data-ttu-id="1b9d2-121">İzleme katılımcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b9d2-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b9d2-122">Child Elements</span></span>  
 <span data-ttu-id="1b9d2-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b9d2-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b9d2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1b9d2-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b9d2-125">Element</span></span>|<span data-ttu-id="1b9d2-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b9d2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b9d2-127">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="1b9d2-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="1b9d2-128">Katılımcıların izleme listesi</span><span class="sxs-lookup"><span data-stu-id="1b9d2-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b9d2-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b9d2-129">Remarks</span></span>  
 <span data-ttu-id="1b9d2-130">İzleme katılımcıları akışından yayılan izleme verilerini almak için kullanılır ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="1b9d2-131">Benzer şekilde, herhangi işleme kayıtları da içinde izleme katılımcı yapılabilir izleme gönderin.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="1b9d2-132">Aynı anda birden çok izleme katılımcıları izleme olaylarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="1b9d2-133">Her izleme katılımcı farklı izleme profili ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="1b9d2-134">Standart izleme katılımcı, izleme kayıtları bir ETW oturumu Yazar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="1b9d2-135">Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranışı ekleyerek yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="1b9d2-136">Etkinleştirme bir ETW İzleme katılımcı olacak şekilde kayıtları izleme Olay Görüntüleyicisi'görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="1b9d2-137">Gereksinimlerinizi karşılamıyorsa, özel izleme katılımcı de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b9d2-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b9d2-138">Example</span></span>  
 <span data-ttu-id="1b9d2-139">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="1b9d2-140">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan `<diagnostics>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="1b9d2-141">İzleme katılımcı abone izleme kayıtları belirtmek için ile ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="1b9d2-142">Bu tarafından tanımlanan `profileName` özniteliği `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="1b9d2-143">Bunlar tanımlandıktan izleme katılımcı eklenir `<etwTracking>` hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="1b9d2-144">Böylece bunlar izleme kayıtları almak başlayabilirsiniz bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b9d2-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b9d2-145">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="1b9d2-146">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1b9d2-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1b9d2-147">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="1b9d2-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
