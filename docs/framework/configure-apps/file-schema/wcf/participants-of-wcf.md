---
title: "WCF &lt;katılımcıları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d797e216fd53a2572b6c457c1fc82f1693dce3f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparticipantsgt-of-wcf"></a><span data-ttu-id="17688-102">WCF &lt;katılımcıları&gt;</span><span class="sxs-lookup"><span data-stu-id="17688-102">&lt;participants&gt; of WCF</span></span>
<span data-ttu-id="17688-103">Çalışma zamanı ' doğrudan gösterilmesini izleme kayıtları dinleme ve yapılandırılmış olan herhangi bir şekilde işleyen katılımcıları izleme listesini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="17688-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="17688-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="17688-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="17688-105">İş akışı izleme ve izleme katılımcıları daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="17688-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="17688-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="17688-106">\<system.serviceModel></span></span>  
<span data-ttu-id="17688-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="17688-107">\<tracking></span></span>  
<span data-ttu-id="17688-108">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="17688-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17688-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17688-109">Syntax</span></span>  
  
```xml
   <tracking>    <participants>       <add name="String"            profileName="String"           type="String" />    </participants> </tracking>   
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17688-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="17688-110">Attributes and Elements</span></span>  
 <span data-ttu-id="17688-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="17688-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17688-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="17688-112">Attributes</span></span>  
 <span data-ttu-id="17688-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="17688-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17688-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="17688-114">Child Elements</span></span>  
  
|<span data-ttu-id="17688-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="17688-115">Element</span></span>|<span data-ttu-id="17688-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17688-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17688-117">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="17688-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="17688-118">İzleme katılımcı ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="17688-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17688-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="17688-119">Parent Elements</span></span>  
  
|<span data-ttu-id="17688-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="17688-120">Element</span></span>|<span data-ttu-id="17688-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17688-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17688-122">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="17688-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="17688-123">Bir iş akışı hizmeti izleme ayarlarını tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17688-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17688-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17688-124">Remarks</span></span>  
 <span data-ttu-id="17688-125">İzleme katılımcıları iş akışını yayılan izleme verilerini almak için kullanılan ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="17688-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="17688-126">Benzer şekilde, tüm kayıtları içinde izleme katılımcı de yapılabilir izleme üzerinde işlem sonrası.</span><span class="sxs-lookup"><span data-stu-id="17688-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="17688-127">Birden çok izleme katılımcıları izleme olaylarını aynı anda kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="17688-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="17688-128">Her izleme katılımcı farklı izleme profili ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="17688-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="17688-129">Standart izleme katılımcı hangi izleme kayıtları ETW oturumuna Yazar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="17688-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="17688-130">Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranış ekleyerek yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="17688-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="17688-131">Bir ETW etkinleştirme, izleme katılımcı olmasını kayıtları izleme Olay Görüntüleyicisi görüntülenemez sağlar.</span><span class="sxs-lookup"><span data-stu-id="17688-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="17688-132">Özel İzleme katılımcı Ayrıca, gereksinimlerinizi karşılamıyorsa yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17688-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17688-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="17688-133">Example</span></span>  
 <span data-ttu-id="17688-134">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="17688-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="17688-135">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan `<diagnostics>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="17688-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="17688-136">İzleme katılımcı için abone oldu izleme kayıtları belirtmek için ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="17688-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="17688-137">Bu tarafından tanımlanan `profileName` özniteliği `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="17688-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="17688-138">Bunlar tanımlandıktan sonra izleme katılımcı eklenen `<etwTracking>` hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="17688-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="17688-139">Böylece izleme kayıtlarını alır başlamadan bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekler.</span><span class="sxs-lookup"><span data-stu-id="17688-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17688-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17688-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 [<span data-ttu-id="17688-141">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="17688-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="17688-142">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="17688-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
