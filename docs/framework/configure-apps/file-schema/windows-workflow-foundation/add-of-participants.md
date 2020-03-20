---
title: <add> / <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 61832edbf7d206d6a5f7a85619eb17ebc010c193
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152365"
---
# <a name="add-of-participants"></a><span data-ttu-id="b9150-102">\<\<katılımcıların> ekleme></span><span class="sxs-lookup"><span data-stu-id="b9150-102">\<add> of \<participants></span></span>
<span data-ttu-id="b9150-103">Çalışma zamanından doğrudan yayılan izleme kayıtlarını dinleyen bir izleme katılımcısını yapılandırın ve yapılandırılan şekilde işleyin.</span><span class="sxs-lookup"><span data-stu-id="b9150-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="b9150-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="b9150-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="b9150-105">İş akışı izleme ve izleme katılımcıları hakkında daha fazla bilgi için İş [Akışı İzleme ve İzleme katılımcılarını](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) görün. [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md)</span><span class="sxs-lookup"><span data-stu-id="b9150-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="b9150-106">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b9150-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b9150-107">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b9150-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b9150-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="b9150-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="b9150-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<katılımcılar>**](participants.md)</span><span class="sxs-lookup"><span data-stu-id="b9150-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)</span></span>\
<span data-ttu-id="b9150-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>ekleyin**</span><span class="sxs-lookup"><span data-stu-id="b9150-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9150-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9150-111">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9150-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9150-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b9150-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b9150-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9150-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b9150-114">Attributes</span></span>  
  
|<span data-ttu-id="b9150-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="b9150-115">Element</span></span>|<span data-ttu-id="b9150-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9150-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9150-117">ad</span><span class="sxs-lookup"><span data-stu-id="b9150-117">name</span></span>|<span data-ttu-id="b9150-118">İzleme katılımcısının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b9150-118">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="b9150-119">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="b9150-119">profileName</span></span>|<span data-ttu-id="b9150-120">İzleme üyesinin abone olduğu izleme kayıtlarını tanımlayan izleme profilinin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="b9150-120">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="b9150-121">type</span><span class="sxs-lookup"><span data-stu-id="b9150-121">type</span></span>|<span data-ttu-id="b9150-122">İzleme katılımcısının türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b9150-122">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9150-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9150-123">Child Elements</span></span>  
 <span data-ttu-id="b9150-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="b9150-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9150-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9150-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b9150-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="b9150-126">Element</span></span>|<span data-ttu-id="b9150-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9150-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9150-128">\<katılımcılar></span><span class="sxs-lookup"><span data-stu-id="b9150-128">\<participants></span></span>](participants.md)|<span data-ttu-id="b9150-129">İzleme katılımcılarının listesi</span><span class="sxs-lookup"><span data-stu-id="b9150-129">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9150-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9150-130">Remarks</span></span>  
 <span data-ttu-id="b9150-131">İzleme katılımcıları, iş akışından yayılan izleme verilerini almak ve farklı ortamlara depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b9150-131">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="b9150-132">Aynı şekilde, izleme Kayıtları üzerinde herhangi bir posta işleme de izleme katılımcısı içinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b9150-132">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="b9150-133">Birden çok izleme katılımcısı izleme olaylarını aynı anda tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="b9150-133">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="b9150-134">Her izleme katılımcısı farklı bir izleme profili ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b9150-134">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="b9150-135">İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b9150-135">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="b9150-136">Katılımcı, yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek iş akışı hizmetinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b9150-136">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="b9150-137">Bir ETW izleme katılımcısını etkinleştirmek, izleme kayıtlarının olay görüntüleyicisinde görüntülenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9150-137">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="b9150-138">Bu gereksinimlerinizi karşılamazsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9150-138">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9150-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9150-139">Example</span></span>  
 <span data-ttu-id="b9150-140">Aşağıdaki yapılandırma örneği, Web.config dosyasında yapılandırılan standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b9150-140">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="b9150-141">ETW İzleme Katılımcısının İzleme Kayıtlarını ETW'ye yazmak için kullandığı Sağlayıcı \*\* \<Kimliği, tanılama>\*\* bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b9150-141">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="b9150-142">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için onunla ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="b9150-142">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="b9150-143">Bu, \*\* \<>öğe ekle\*\* öğesinin **profileName** özniteliği ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b9150-143">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="b9150-144">Bunlar tanımlandıktan sonra, İzleme Katılımcısı \*\* \<etwTracking>\*\* hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="b9150-144">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="b9150-145">Bu, seçili İzleme Katılımcılarını İş Akışı örneğinin uzantılarına ekleyerek İzleme Kayıtlarını almaya başlar.</span><span class="sxs-lookup"><span data-stu-id="b9150-145">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9150-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9150-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="b9150-147">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b9150-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b9150-148">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="b9150-148">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
