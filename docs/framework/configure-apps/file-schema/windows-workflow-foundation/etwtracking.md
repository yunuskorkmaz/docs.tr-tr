---
title: '&lt;etwTracking&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 583c5bcb1e864b79f80a9c3095ed8ce7b74a19eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="c3e6e-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="c3e6e-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="c3e6e-103">ETW İzleme kullanılarak kullanmak bir hizmet sağlayan bir hizmet davranışı bir <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="c3e6e-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c3e6e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c3e6e-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="c3e6e-105">\<behaviors></span></span>  
<span data-ttu-id="c3e6e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c3e6e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c3e6e-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c3e6e-107">\<behavior></span></span>  
<span data-ttu-id="c3e6e-108">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="c3e6e-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e6e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3e6e-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3e6e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3e6e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c3e6e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3e6e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c3e6e-112">Attributes</span></span>  
  
|<span data-ttu-id="c3e6e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c3e6e-113">Attribute</span></span>|<span data-ttu-id="c3e6e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3e6e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3e6e-115">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="c3e6e-115">profileName</span></span>|<span data-ttu-id="c3e6e-116">Bu davranışı ile ilişkili izleme profilin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3e6e-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3e6e-117">Child Elements</span></span>  
 <span data-ttu-id="c3e6e-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3e6e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3e6e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c3e6e-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="c3e6e-120">Element</span></span>|<span data-ttu-id="c3e6e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3e6e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3e6e-122">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c3e6e-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="c3e6e-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3e6e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3e6e-124">Remarks</span></span>  
 <span data-ttu-id="c3e6e-125">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi üzerinde bir iş akışı hizmeti izleme katılımcı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="c3e6e-126">İzleme katılımcıları iş akışını yayılan izleme verilerini almak için kullanılan ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="c3e6e-127">Benzer şekilde, tüm kayıtları içinde izleme katılımcı de yapılabilir izleme üzerinde işlem sonrası.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3e6e-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3e6e-128">Example</span></span>  
 <span data-ttu-id="c3e6e-129">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="c3e6e-130">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="c3e6e-131">İzleme katılımcı için abone oldu izleme kayıtları belirtmek için ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="c3e6e-132">Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="c3e6e-133">Bunlar tanımlandıktan sonra izleme katılımcı eklenen  **\<etwTracking >** hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="c3e6e-134">Böylece izleme kayıtlarını alır başlamadan bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekler.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3e6e-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3e6e-135">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="c3e6e-136">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="c3e6e-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c3e6e-137">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="c3e6e-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
