---
title: '&lt;etwTracking&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: f9d1acd5dafb9df181b036db9d3ad783ca618874
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684339"
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="79726-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="79726-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="79726-103">ETW İzleme kullanılarak kullanmak bir hizmet sağlayan bir hizmet davranışını bir <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="79726-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="79726-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79726-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="79726-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="79726-105">\<behaviors></span></span>  
<span data-ttu-id="79726-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="79726-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="79726-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="79726-107">\<behavior></span></span>  
<span data-ttu-id="79726-108">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="79726-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79726-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79726-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79726-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79726-110">Attributes and Elements</span></span>  
 <span data-ttu-id="79726-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79726-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79726-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79726-112">Attributes</span></span>  
  
|<span data-ttu-id="79726-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="79726-113">Attribute</span></span>|<span data-ttu-id="79726-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79726-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79726-115">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="79726-115">profileName</span></span>|<span data-ttu-id="79726-116">Bu davranışı ile ilişkili izleme profilinin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="79726-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79726-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79726-117">Child Elements</span></span>  
 <span data-ttu-id="79726-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="79726-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79726-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79726-119">Parent Elements</span></span>  
  
|<span data-ttu-id="79726-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="79726-120">Element</span></span>|<span data-ttu-id="79726-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79726-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79726-122">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="79726-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="79726-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="79726-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79726-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79726-124">Remarks</span></span>  
 <span data-ttu-id="79726-125">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi, bir iş akışı hizmeti izleme katılımcı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="79726-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="79726-126">İzleme katılımcıları akışından yayılan izleme verilerini almak için kullanılır ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="79726-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="79726-127">Benzer şekilde, herhangi işleme kayıtları da içinde izleme katılımcı yapılabilir izleme gönderin.</span><span class="sxs-lookup"><span data-stu-id="79726-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79726-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="79726-128">Example</span></span>  
 <span data-ttu-id="79726-129">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="79726-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="79726-130">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="79726-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="79726-131">İzleme katılımcı abone izleme kayıtları belirtmek için ile ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="79726-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="79726-132">Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="79726-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="79726-133">Bunlar tanımlandıktan izleme katılımcı eklenir  **\<etwTracking >** hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="79726-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="79726-134">Böylece bunlar izleme kayıtları almak başlayabilirsiniz bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="79726-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79726-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79726-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="79726-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="79726-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="79726-137">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="79726-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
