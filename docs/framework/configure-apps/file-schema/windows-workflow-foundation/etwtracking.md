---
title: '&lt;etwTracking&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 6defccdd6a81a1c00a4b65fa9214c86e6cccbea2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="263e3-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="263e3-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="263e3-103">ETW İzleme kullanılarak kullanmak bir hizmet sağlayan bir hizmet davranışı bir <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="263e3-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="263e3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="263e3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="263e3-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="263e3-105">\<behaviors></span></span>  
<span data-ttu-id="263e3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="263e3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="263e3-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="263e3-107">\<behavior></span></span>  
<span data-ttu-id="263e3-108">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="263e3-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263e3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="263e3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="263e3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="263e3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="263e3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="263e3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="263e3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="263e3-112">Attributes</span></span>  
  
|<span data-ttu-id="263e3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="263e3-113">Attribute</span></span>|<span data-ttu-id="263e3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="263e3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="263e3-115">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="263e3-115">profileName</span></span>|<span data-ttu-id="263e3-116">Bu davranışı ile ilişkili izleme profilin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="263e3-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="263e3-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="263e3-117">Child Elements</span></span>  
 <span data-ttu-id="263e3-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="263e3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="263e3-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="263e3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="263e3-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="263e3-120">Element</span></span>|<span data-ttu-id="263e3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="263e3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="263e3-122">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="263e3-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="263e3-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="263e3-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="263e3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="263e3-124">Remarks</span></span>  
 <span data-ttu-id="263e3-125">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi üzerinde bir iş akışı hizmeti izleme katılımcı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="263e3-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="263e3-126">İzleme katılımcıları iş akışını yayılan izleme verilerini almak için kullanılan ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="263e3-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="263e3-127">Benzer şekilde, tüm kayıtları içinde izleme katılımcı de yapılabilir izleme üzerinde işlem sonrası.</span><span class="sxs-lookup"><span data-stu-id="263e3-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="263e3-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="263e3-128">Example</span></span>  
 <span data-ttu-id="263e3-129">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="263e3-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="263e3-130">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="263e3-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="263e3-131">İzleme katılımcı için abone oldu izleme kayıtları belirtmek için ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="263e3-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="263e3-132">Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="263e3-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="263e3-133">Bunlar tanımlandıktan sonra izleme katılımcı eklenen  **\<etwTracking >** hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="263e3-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="263e3-134">Böylece izleme kayıtlarını alır başlamadan bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekler.</span><span class="sxs-lookup"><span data-stu-id="263e3-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="263e3-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="263e3-135">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="263e3-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="263e3-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="263e3-137">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="263e3-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
