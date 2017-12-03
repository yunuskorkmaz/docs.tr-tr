---
title: "&lt;Katılımcıların&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e20cc8ed26feccf6fcf7fae40d2a219cd103dbb0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltparticipantsgt"></a><span data-ttu-id="90820-102">&lt;Katılımcıların&gt;</span><span class="sxs-lookup"><span data-stu-id="90820-102">&lt;participants&gt;</span></span>
<span data-ttu-id="90820-103">Çalışma zamanı ' doğrudan gösterilmesini izleme kayıtları dinleme ve yapılandırılmış olan herhangi bir şekilde işleyen katılımcıları izleme listesini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="90820-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="90820-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="90820-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="90820-105">İş akışı izleme ve izleme katılımcıları daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="90820-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="90820-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="90820-106">\<system.serviceModel></span></span>  
<span data-ttu-id="90820-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="90820-107">\<tracking></span></span>  
<span data-ttu-id="90820-108">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="90820-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90820-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90820-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90820-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="90820-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90820-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="90820-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90820-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="90820-112">Attributes</span></span>  
 <span data-ttu-id="90820-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="90820-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90820-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="90820-114">Child Elements</span></span>  
  
|<span data-ttu-id="90820-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="90820-115">Element</span></span>|<span data-ttu-id="90820-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90820-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90820-117">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="90820-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="90820-118">İzleme katılımcı ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="90820-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90820-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="90820-119">Parent Elements</span></span>  
  
|<span data-ttu-id="90820-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="90820-120">Element</span></span>|<span data-ttu-id="90820-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90820-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90820-122">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="90820-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="90820-123">Bir iş akışı hizmeti izleme ayarlarını tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="90820-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90820-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90820-124">Remarks</span></span>  
 <span data-ttu-id="90820-125">İzleme katılımcıları iş akışını yayılan izleme verilerini almak için kullanılan ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="90820-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="90820-126">Benzer şekilde, tüm kayıtları içinde izleme katılımcı de yapılabilir izleme üzerinde işlem sonrası.</span><span class="sxs-lookup"><span data-stu-id="90820-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="90820-127">Birden çok izleme katılımcıları izleme olaylarını aynı anda kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="90820-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="90820-128">Her izleme katılımcı farklı izleme profili ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="90820-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="90820-129">Standart izleme katılımcı hangi izleme kayıtları ETW oturumuna Yazar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="90820-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="90820-130">Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranış ekleyerek yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="90820-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="90820-131">Bir ETW etkinleştirme, izleme katılımcı olmasını kayıtları izleme Olay Görüntüleyicisi görüntülenemez sağlar.</span><span class="sxs-lookup"><span data-stu-id="90820-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="90820-132">Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90820-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90820-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="90820-133">Example</span></span>  
 <span data-ttu-id="90820-134">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="90820-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="90820-135">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="90820-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="90820-136">İzleme katılımcı için abone oldu izleme kayıtları belirtmek için ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="90820-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="90820-137">Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="90820-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="90820-138">Bunlar tanımlandıktan sonra izleme katılımcı eklenen  **\<etwTracking >** hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="90820-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="90820-139">Böylece izleme kayıtlarını alır başlamadan bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekler.</span><span class="sxs-lookup"><span data-stu-id="90820-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90820-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90820-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="90820-141">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="90820-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="90820-142">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="90820-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
