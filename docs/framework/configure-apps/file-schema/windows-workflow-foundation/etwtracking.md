---
description: 'Hakkında daha fazla bilgi edinin: <etwTracking>'
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: b89d832e73440d5b60a05477ccf85178c2f43a2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795085"
---
# \<etwTracking>

<span data-ttu-id="a61a3-102">Bir hizmetin, kullanarak ETW izlemeyi kullanmasına izin veren bir hizmet davranışı <xref:System.Activities.Tracking.EtwTrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="a61a3-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="a61a3-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="a61a3-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a61a3-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61a3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a61a3-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a61a3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a61a3-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a61a3-106">Attributes</span></span>  
  
|<span data-ttu-id="a61a3-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a61a3-107">Attribute</span></span>|<span data-ttu-id="a61a3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a61a3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a61a3-109">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="a61a3-109">profileName</span></span>|<span data-ttu-id="a61a3-110">Bu davranışla ilişkili izleme profili adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a61a3-110">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a61a3-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61a3-111">Child Elements</span></span>  

 <span data-ttu-id="a61a3-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="a61a3-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a61a3-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61a3-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a61a3-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="a61a3-114">Element</span></span>|<span data-ttu-id="a61a3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a61a3-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a61a3-116">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a61a3-116">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="a61a3-117">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a61a3-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a61a3-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a61a3-118">Remarks</span></span>  

 <span data-ttu-id="a61a3-119">Bu yapılandırma öğesi, hizmetin davranış yapılandırmasına eklendiğinde bir iş akışı hizmeti üzerinde bir izleme katılımcısı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a61a3-119">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="a61a3-120">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a61a3-120">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="a61a3-121">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a61a3-121">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a61a3-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="a61a3-122">Example</span></span>  

 <span data-ttu-id="a61a3-123">Aşağıdaki yapılandırma örneği, Web.config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a61a3-123">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="a61a3-124">ETW Izleme katılımcısı tarafından ETW 'ye Izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği **\<diagnostics>** bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a61a3-124">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="a61a3-125">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="a61a3-125">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="a61a3-126">Bu, öğesinin **ProfileName** özniteliği tarafından tanımlanır **\<add>** .</span><span class="sxs-lookup"><span data-stu-id="a61a3-126">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="a61a3-127">Bunlar tanımlandıktan sonra, Izleme katılımcısı **\<etwTracking>** hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="a61a3-127">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="a61a3-128">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="a61a3-128">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a61a3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a61a3-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="a61a3-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a61a3-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a61a3-131">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="a61a3-131">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
