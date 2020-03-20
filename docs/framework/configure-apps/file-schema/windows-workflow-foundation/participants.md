---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: e6e996bd1cc32258167e30287e9338a4773ce921
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152034"
---
# <a name="participants"></a><span data-ttu-id="431ee-101">\<katılımcılar></span><span class="sxs-lookup"><span data-stu-id="431ee-101">\<participants></span></span>
<span data-ttu-id="431ee-102">Çalışma zamanından doğrudan yayılan izleme kayıtlarını dinleyen izleme katılımcılarının listesini yapılandırın ve yapılandırıldıkları şekilde işleyin.</span><span class="sxs-lookup"><span data-stu-id="431ee-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="431ee-103">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="431ee-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="431ee-104">İş akışı izleme ve izleme katılımcıları hakkında daha fazla bilgi için İş [Akışı İzleme ve İzleme katılımcılarını](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) görün. [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md)</span><span class="sxs-lookup"><span data-stu-id="431ee-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="431ee-105">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="431ee-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="431ee-106">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="431ee-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="431ee-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="431ee-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="431ee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<katılımcılar>**</span><span class="sxs-lookup"><span data-stu-id="431ee-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431ee-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="431ee-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="431ee-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="431ee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="431ee-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="431ee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="431ee-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="431ee-112">Attributes</span></span>  
 <span data-ttu-id="431ee-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="431ee-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="431ee-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="431ee-114">Child Elements</span></span>  
  
|<span data-ttu-id="431ee-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="431ee-115">Element</span></span>|<span data-ttu-id="431ee-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="431ee-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="431ee-117">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="431ee-117">\<add></span></span>](add-of-participants.md)|<span data-ttu-id="431ee-118">İzleme katılımcısı için ayarlar içerir.</span><span class="sxs-lookup"><span data-stu-id="431ee-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="431ee-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="431ee-119">Parent Elements</span></span>  
  
|<span data-ttu-id="431ee-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="431ee-120">Element</span></span>|<span data-ttu-id="431ee-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="431ee-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="431ee-122">\<izleme></span><span class="sxs-lookup"><span data-stu-id="431ee-122">\<tracking></span></span>](tracking.md)|<span data-ttu-id="431ee-123">İş akışı hizmeti için izleme ayarlarını tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="431ee-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="431ee-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="431ee-124">Remarks</span></span>  
 <span data-ttu-id="431ee-125">İzleme katılımcıları, iş akışından yayılan izleme verilerini almak ve farklı ortamlara depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="431ee-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="431ee-126">Aynı şekilde, izleme Kayıtları üzerinde herhangi bir posta işleme de izleme katılımcısı içinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="431ee-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="431ee-127">Birden çok izleme katılımcısı izleme olaylarını aynı anda tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="431ee-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="431ee-128">Her izleme katılımcısı farklı bir izleme profili ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="431ee-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="431ee-129">İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="431ee-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="431ee-130">Katılımcı, yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek iş akışı hizmetinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="431ee-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="431ee-131">Bir ETW izleme katılımcısını etkinleştirmek, izleme kayıtlarının olay görüntüleyicisinde görüntülenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="431ee-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="431ee-132">Bu gereksinimlerinizi karşılamazsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="431ee-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="431ee-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="431ee-133">Example</span></span>  
 <span data-ttu-id="431ee-134">Aşağıdaki yapılandırma örneği, Web.config dosyasında yapılandırılan standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="431ee-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="431ee-135">ETW İzleme Katılımcısının İzleme Kayıtlarını ETW'ye yazmak için kullandığı Sağlayıcı \*\* \<Kimliği, tanılama>\*\* bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="431ee-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="431ee-136">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için onunla ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="431ee-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="431ee-137">Bu, \*\* \<>öğe ekle\*\* öğesinin **profileName** özniteliği ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="431ee-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="431ee-138">Bunlar tanımlandıktan sonra, İzleme Katılımcısı \*\* \<etwTracking>\*\* hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="431ee-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="431ee-139">Bu, seçili İzleme Katılımcılarını İş Akışı örneğinin uzantılarına ekleyerek İzleme Kayıtlarını almaya başlar.</span><span class="sxs-lookup"><span data-stu-id="431ee-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="431ee-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="431ee-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="431ee-141">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="431ee-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="431ee-142">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="431ee-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
