---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 094fbf95042c00287fb8dfcca28753cfe501a8d8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398763"
---
# <a name="etwtracking"></a><span data-ttu-id="4d654-101">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="4d654-101">\<etwTracking></span></span>
<span data-ttu-id="4d654-102">Bir hizmetin, kullanarak <xref:System.Activities.Tracking.EtwTrackingParticipant>etw izlemeyi kullanmasına izin veren bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="4d654-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="4d654-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4d654-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4d654-104">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4d654-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="4d654-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4d654-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="4d654-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4d654-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="4d654-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="4d654-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="4d654-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<etwTracking >**</span><span class="sxs-lookup"><span data-stu-id="4d654-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d654-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d654-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d654-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d654-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4d654-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d654-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d654-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4d654-112">Attributes</span></span>  
  
|<span data-ttu-id="4d654-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4d654-113">Attribute</span></span>|<span data-ttu-id="4d654-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d654-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d654-115">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="4d654-115">profileName</span></span>|<span data-ttu-id="4d654-116">Bu davranışla ilişkili izleme profili adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4d654-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d654-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d654-117">Child Elements</span></span>  
 <span data-ttu-id="4d654-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="4d654-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d654-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d654-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4d654-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d654-120">Element</span></span>|<span data-ttu-id="4d654-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d654-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d654-122">\<\<ServiceBehavior > davranış ></span><span class="sxs-lookup"><span data-stu-id="4d654-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4d654-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d654-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d654-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d654-124">Remarks</span></span>  
 <span data-ttu-id="4d654-125">Bu yapılandırma öğesi, hizmetin davranış yapılandırmasına eklendiğinde bir iş akışı hizmeti üzerinde bir izleme katılımcısı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4d654-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="4d654-126">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4d654-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="4d654-127">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="4d654-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d654-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d654-128">Example</span></span>  
 <span data-ttu-id="4d654-129">Aşağıdaki yapılandırma örneği, Web. config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d654-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="4d654-130">ETW izleme katılımcısı tarafından ETW 'ye izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği,  **\<Tanılama >** bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4d654-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="4d654-131">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="4d654-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="4d654-132">Bu,  **\<Add >** öğesinin **ProfileName** özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4d654-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="4d654-133">Bunlar tanımlandıktan sonra, izleme katılımcısı  **\<etwTracking >** hizmeti davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="4d654-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="4d654-134">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="4d654-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d654-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d654-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="4d654-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4d654-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4d654-137">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="4d654-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
