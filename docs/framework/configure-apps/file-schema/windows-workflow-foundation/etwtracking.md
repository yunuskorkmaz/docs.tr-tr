---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152177"
---
# <a name="etwtracking"></a><span data-ttu-id="20997-101">\<etwTracking></span><span class="sxs-lookup"><span data-stu-id="20997-101">\<etwTracking></span></span>
<span data-ttu-id="20997-102">Bir hizmetin ETW izlemesini kullanmasına izin <xref:System.Activities.Tracking.EtwTrackingParticipant>veren bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="20997-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="20997-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="20997-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="20997-104">&nbsp;&nbsp;[**\<Sistem. ServiceModel>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="20997-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="20997-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranışlar>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="20997-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="20997-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="20997-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="20997-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<davranış>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="20997-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="20997-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span><span class="sxs-lookup"><span data-stu-id="20997-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20997-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20997-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20997-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20997-110">Attributes and Elements</span></span>  
 <span data-ttu-id="20997-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20997-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20997-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20997-112">Attributes</span></span>  
  
|<span data-ttu-id="20997-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20997-113">Attribute</span></span>|<span data-ttu-id="20997-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20997-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20997-115">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="20997-115">profileName</span></span>|<span data-ttu-id="20997-116">Bu davranışla ilişkili izleme profilinin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="20997-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20997-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20997-117">Child Elements</span></span>  
 <span data-ttu-id="20997-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="20997-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20997-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20997-119">Parent Elements</span></span>  
  
|<span data-ttu-id="20997-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="20997-120">Element</span></span>|<span data-ttu-id="20997-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20997-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20997-122">\<hizmet davranış \<>Davranışlar></span><span class="sxs-lookup"><span data-stu-id="20997-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="20997-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="20997-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20997-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20997-124">Remarks</span></span>  
 <span data-ttu-id="20997-125">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi bir iş akışı hizmetinde bir izleme katılımcısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="20997-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="20997-126">İzleme katılımcıları, iş akışından yayılan izleme verilerini almak ve farklı ortamlara depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20997-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="20997-127">Aynı şekilde, izleme Kayıtları üzerinde herhangi bir posta işleme de izleme katılımcısı içinde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="20997-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20997-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="20997-128">Example</span></span>  
 <span data-ttu-id="20997-129">Aşağıdaki yapılandırma örneği, Web.config dosyasında yapılandırılan standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="20997-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="20997-130">ETW İzleme Katılımcısının İzleme Kayıtlarını ETW'ye yazmak için kullandığı Sağlayıcı \*\* \<Kimliği, tanılama>\*\* bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="20997-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="20997-131">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için onunla ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="20997-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="20997-132">Bu, \*\* \<>öğe ekle\*\* öğesinin **profileName** özniteliği ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="20997-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="20997-133">Bunlar tanımlandıktan sonra, İzleme Katılımcısı \*\* \<etwTracking>\*\* hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="20997-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="20997-134">Bu, seçili İzleme Katılımcılarını İş Akışı örneğinin uzantılarına ekleyerek İzleme Kayıtlarını almaya başlar.</span><span class="sxs-lookup"><span data-stu-id="20997-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20997-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20997-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="20997-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="20997-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="20997-137">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="20997-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
