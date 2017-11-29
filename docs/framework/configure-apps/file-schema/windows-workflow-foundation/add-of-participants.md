---
title: "&lt;ekleme&gt; , &lt;katılımcıları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d95c6d3768a26a8db92bf54bb454b350ced03d7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltparticipantsgt"></a><span data-ttu-id="9f50d-102">&lt;ekleme&gt; , &lt;katılımcıları&gt;</span><span class="sxs-lookup"><span data-stu-id="9f50d-102">&lt;add&gt; of &lt;participants&gt;</span></span>
<span data-ttu-id="9f50d-103">Çalışma zamanı ' doğrudan gösterilmesini izleme kayıtları dinleyen bir izleme katılımcı yapılandırın ve herhangi bir şekilde yapılandırılan işlem.</span><span class="sxs-lookup"><span data-stu-id="9f50d-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="9f50d-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="9f50d-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="9f50d-105">İş akışı izleme ve izleme katılımcıları daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="9f50d-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="9f50d-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9f50d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9f50d-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="9f50d-107">\<tracking></span></span>  
<span data-ttu-id="9f50d-108">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="9f50d-108">\<participants></span></span>  
<span data-ttu-id="9f50d-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="9f50d-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f50d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f50d-110">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f50d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f50d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9f50d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f50d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f50d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f50d-113">Attributes</span></span>  
  
|<span data-ttu-id="9f50d-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f50d-114">Element</span></span>|<span data-ttu-id="9f50d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f50d-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9f50d-116">name</span><span class="sxs-lookup"><span data-stu-id="9f50d-116">name</span></span>|<span data-ttu-id="9f50d-117">İzleme katılımcı adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="9f50d-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="9f50d-118">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="9f50d-118">profileName</span></span>|<span data-ttu-id="9f50d-119">İzleme katılımcı abone izleme kayıtları tanımlayan izleme profilin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="9f50d-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="9f50d-120">türü</span><span class="sxs-lookup"><span data-stu-id="9f50d-120">type</span></span>|<span data-ttu-id="9f50d-121">İzleme katılımcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9f50d-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f50d-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f50d-122">Child Elements</span></span>  
 <span data-ttu-id="9f50d-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="9f50d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f50d-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f50d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9f50d-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f50d-125">Element</span></span>|<span data-ttu-id="9f50d-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f50d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f50d-127">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="9f50d-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="9f50d-128">Katılımcıların izleme listesi</span><span class="sxs-lookup"><span data-stu-id="9f50d-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f50d-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f50d-129">Remarks</span></span>  
 <span data-ttu-id="9f50d-130">İzleme katılımcıları iş akışını yayılan izleme verilerini almak için kullanılan ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="9f50d-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="9f50d-131">Benzer şekilde, tüm kayıtları içinde izleme katılımcı de yapılabilir izleme üzerinde işlem sonrası.</span><span class="sxs-lookup"><span data-stu-id="9f50d-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="9f50d-132">Birden çok izleme katılımcıları izleme olaylarını aynı anda kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9f50d-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="9f50d-133">Her izleme katılımcı farklı izleme profili ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9f50d-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="9f50d-134">Standart izleme katılımcı hangi izleme kayıtları ETW oturumuna Yazar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9f50d-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="9f50d-135">Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranış ekleyerek yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="9f50d-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="9f50d-136">Bir ETW etkinleştirme, izleme katılımcı olmasını kayıtları izleme Olay Görüntüleyicisi görüntülenemez sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f50d-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="9f50d-137">Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f50d-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f50d-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f50d-138">Example</span></span>  
 <span data-ttu-id="9f50d-139">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f50d-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="9f50d-140">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="9f50d-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="9f50d-141">İzleme katılımcı için abone oldu izleme kayıtları belirtmek için ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="9f50d-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="9f50d-142">Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="9f50d-142">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="9f50d-143">Bunlar tanımlandıktan sonra izleme katılımcı eklenen  **\<etwTracking >** hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="9f50d-143">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="9f50d-144">Böylece izleme kayıtlarını alır başlamadan bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekler.</span><span class="sxs-lookup"><span data-stu-id="9f50d-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f50d-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f50d-145">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="9f50d-146">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="9f50d-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9f50d-147">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="9f50d-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
