---
title: "WCF &lt;iş akışı&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0443eba-d3b4-4fae-886e-9878daf77691
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8177f04f921585b422c2567bd7282dba02fedb70
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowgt-of-wcf"></a><span data-ttu-id="a07d7-102">WCF &lt;iş akışı&gt;</span><span class="sxs-lookup"><span data-stu-id="a07d7-102">&lt;workflow&gt; of WCF</span></span>
<span data-ttu-id="a07d7-103">Çalışma zamanı ' doğrudan gösterilmesini izleme kayıtları dinleyen bir izleme katılımcı yapılandırın ve herhangi bir şekilde yapılandırılan işlem.</span><span class="sxs-lookup"><span data-stu-id="a07d7-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="a07d7-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="a07d7-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="a07d7-105">İş akışı izleme ve izleme katılımcıları daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="a07d7-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="a07d7-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a07d7-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a07d7-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a07d7-107">\<tracking></span></span>  
<span data-ttu-id="a07d7-108">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="a07d7-108">\<participants></span></span>  
<span data-ttu-id="a07d7-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="a07d7-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a07d7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a07d7-110">Syntax</span></span>  
  
```xml
   <tracking>    <participants>       <add name="String"            profileName="String"           type="String" />    </participants> </tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a07d7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a07d7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a07d7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a07d7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a07d7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a07d7-113">Attributes</span></span>  
  
|<span data-ttu-id="a07d7-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a07d7-114">Element</span></span>|<span data-ttu-id="a07d7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a07d7-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a07d7-116">name</span><span class="sxs-lookup"><span data-stu-id="a07d7-116">name</span></span>|<span data-ttu-id="a07d7-117">İzleme katılımcı adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="a07d7-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="a07d7-118">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="a07d7-118">profileName</span></span>|<span data-ttu-id="a07d7-119">İzleme katılımcı abone izleme kayıtları tanımlayan izleme profilin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="a07d7-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="a07d7-120">türü</span><span class="sxs-lookup"><span data-stu-id="a07d7-120">type</span></span>|<span data-ttu-id="a07d7-121">İzleme katılımcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a07d7-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a07d7-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a07d7-122">Child Elements</span></span>  
 <span data-ttu-id="a07d7-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="a07d7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a07d7-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a07d7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a07d7-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a07d7-125">Element</span></span>|<span data-ttu-id="a07d7-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a07d7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a07d7-127">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="a07d7-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="a07d7-128">Katılımcıların izleme listesi</span><span class="sxs-lookup"><span data-stu-id="a07d7-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a07d7-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a07d7-129">Remarks</span></span>  
 <span data-ttu-id="a07d7-130">İzleme katılımcıları iş akışını yayılan izleme verilerini almak için kullanılan ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="a07d7-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="a07d7-131">Benzer şekilde, tüm kayıtları içinde izleme katılımcı de yapılabilir izleme üzerinde işlem sonrası.</span><span class="sxs-lookup"><span data-stu-id="a07d7-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="a07d7-132">Birden çok izleme katılımcıları izleme olaylarını aynı anda kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a07d7-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="a07d7-133">Her izleme katılımcı farklı izleme profili ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a07d7-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="a07d7-134">Standart izleme katılımcı hangi izleme kayıtları ETW oturumuna Yazar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a07d7-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="a07d7-135">Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranış ekleyerek yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="a07d7-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="a07d7-136">Bir ETW etkinleştirme, izleme katılımcı olmasını kayıtları izleme Olay Görüntüleyicisi görüntülenemez sağlar.</span><span class="sxs-lookup"><span data-stu-id="a07d7-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="a07d7-137">Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a07d7-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a07d7-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="a07d7-138">Example</span></span>  
 <span data-ttu-id="a07d7-139">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a07d7-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="a07d7-140">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan `<diagnostics>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="a07d7-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="a07d7-141">İzleme katılımcı için abone oldu izleme kayıtları belirtmek için ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="a07d7-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="a07d7-142">Bu tarafından tanımlanan `profileName` özniteliği `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a07d7-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="a07d7-143">Bunlar tanımlandıktan sonra izleme katılımcı eklenen `<etwTracking>` hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="a07d7-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="a07d7-144">Böylece izleme kayıtlarını alır başlamadan bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekler.</span><span class="sxs-lookup"><span data-stu-id="a07d7-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a07d7-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a07d7-145">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="a07d7-146">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="a07d7-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a07d7-147">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="a07d7-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
