---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: e1048cf3a9f56e4177f3ffe2dcd561a1babadacd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198775"
---
# \<etwTracking>

<span data-ttu-id="00ee5-101">Bir hizmetin, kullanarak ETW izlemeyi kullanmasına izin veren bir hizmet davranışı <xref:System.Activities.Tracking.EtwTrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="00ee5-101">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="00ee5-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="00ee5-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00ee5-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="00ee5-103">Attributes and Elements</span></span>  

 <span data-ttu-id="00ee5-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00ee5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00ee5-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="00ee5-105">Attributes</span></span>  
  
|<span data-ttu-id="00ee5-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="00ee5-106">Attribute</span></span>|<span data-ttu-id="00ee5-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00ee5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00ee5-108">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="00ee5-108">profileName</span></span>|<span data-ttu-id="00ee5-109">Bu davranışla ilişkili izleme profili adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="00ee5-109">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00ee5-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="00ee5-110">Child Elements</span></span>  

 <span data-ttu-id="00ee5-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="00ee5-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00ee5-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="00ee5-112">Parent Elements</span></span>  
  
|<span data-ttu-id="00ee5-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="00ee5-113">Element</span></span>|<span data-ttu-id="00ee5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00ee5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00ee5-115">\<behavior> durumunu \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="00ee5-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="00ee5-116">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="00ee5-116">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00ee5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00ee5-117">Remarks</span></span>  

 <span data-ttu-id="00ee5-118">Bu yapılandırma öğesi, hizmetin davranış yapılandırmasına eklendiğinde bir iş akışı hizmeti üzerinde bir izleme katılımcısı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="00ee5-118">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="00ee5-119">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00ee5-119">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="00ee5-120">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="00ee5-120">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00ee5-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="00ee5-121">Example</span></span>  

 <span data-ttu-id="00ee5-122">Aşağıdaki yapılandırma örneği, Web.config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="00ee5-122">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="00ee5-123">ETW Izleme katılımcısı tarafından ETW 'ye Izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği **\<diagnostics>** bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="00ee5-123">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="00ee5-124">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="00ee5-124">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="00ee5-125">Bu, öğesinin **ProfileName** özniteliği tarafından tanımlanır **\<add>** .</span><span class="sxs-lookup"><span data-stu-id="00ee5-125">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="00ee5-126">Bunlar tanımlandıktan sonra, Izleme katılımcısı **\<etwTracking>** hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="00ee5-126">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="00ee5-127">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="00ee5-127">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00ee5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00ee5-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="00ee5-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="00ee5-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="00ee5-130">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="00ee5-130">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
