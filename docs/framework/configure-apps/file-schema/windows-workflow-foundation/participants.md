---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: ffc16f78b266b69e80023f177f10ad6f367b5623
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104890"
---
# <a name="participants"></a><span data-ttu-id="d4e8c-101">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="d4e8c-101">\<participants></span></span>
<span data-ttu-id="d4e8c-102">Çalışma zamanını şuradan doğrudan yayılan izleme kayıtları için dinleme ve bunları hangi şekilde yapılandırılmış olan işleyen katılımcıları izleme listesi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="d4e8c-103">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="d4e8c-104">İş akışı izleme ve izleme katılımcıları daha fazla bilgi için bkz. [takip ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [izleme katılımcıları](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="d4e8c-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="d4e8c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d4e8c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d4e8c-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d4e8c-106">\<tracking></span></span>  
<span data-ttu-id="d4e8c-107">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="d4e8c-107">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e8c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4e8c-108">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4e8c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4e8c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d4e8c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4e8c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4e8c-111">Attributes</span></span>  
 <span data-ttu-id="d4e8c-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d4e8c-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4e8c-113">Child Elements</span></span>  
  
|<span data-ttu-id="d4e8c-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4e8c-114">Element</span></span>|<span data-ttu-id="d4e8c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4e8c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4e8c-116">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d4e8c-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="d4e8c-117">Bir izleme Katılımcısı için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-117">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4e8c-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4e8c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d4e8c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4e8c-119">Element</span></span>|<span data-ttu-id="d4e8c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4e8c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4e8c-121">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="d4e8c-121">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="d4e8c-122">Bir iş akışı hizmeti için izleme ayarları tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4e8c-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4e8c-123">Remarks</span></span>  
 <span data-ttu-id="d4e8c-124">İzleme katılımcıları akışından yayılan izleme verilerini almak için kullanılır ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-124">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="d4e8c-125">Benzer şekilde, herhangi işleme kayıtları da içinde izleme katılımcı yapılabilir izleme gönderin.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-125">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="d4e8c-126">Aynı anda birden çok izleme katılımcıları izleme olaylarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-126">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="d4e8c-127">Her izleme katılımcı farklı izleme profili ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-127">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="d4e8c-128">Standart izleme katılımcı, izleme kayıtları bir ETW oturumu Yazar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-128">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="d4e8c-129">Katılımcı bir iş akışı hizmeti yapılandırma dosyasında bir izleme özgü davranışı ekleyerek yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-129">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="d4e8c-130">Etkinleştirme bir ETW İzleme katılımcı olacak şekilde kayıtları izleme Olay Görüntüleyicisi'görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-130">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="d4e8c-131">Gereksinimlerinizi karşılamıyorsa, özel izleme katılımcı de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-131">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4e8c-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4e8c-132">Example</span></span>  
 <span data-ttu-id="d4e8c-133">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-133">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="d4e8c-134">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-134">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="d4e8c-135">İzleme katılımcı abone izleme kayıtları belirtmek için ile ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-135">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="d4e8c-136">Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-136">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="d4e8c-137">Bunlar tanımlandıktan izleme katılımcı eklenir  **\<etwTracking >** hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-137">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="d4e8c-138">Böylece bunlar izleme kayıtları almak başlayabilirsiniz bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-138">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4e8c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4e8c-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="d4e8c-140">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="d4e8c-140">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d4e8c-141">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="d4e8c-141">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
