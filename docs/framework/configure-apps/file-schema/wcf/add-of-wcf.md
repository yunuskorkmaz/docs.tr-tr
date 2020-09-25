---
title: <add> WCF
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: b3b2883e711cea036ed8a61631e698a9d41fcadd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172937"
---
# <a name="add-of-wcf"></a><span data-ttu-id="71de3-102">\<add> WCF</span><span class="sxs-lookup"><span data-stu-id="71de3-102">\<add> of WCF</span></span>

<span data-ttu-id="71de3-103">Çalışma zamanından doğrudan yayılmakta olan izleme kayıtlarını dinleyen bir izleme katılımcısı yapılandırın ve bunları ne şekilde yapılandırdığınıza göre işleyin.</span><span class="sxs-lookup"><span data-stu-id="71de3-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="71de3-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="71de3-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="71de3-105">İş akışı izleme ve İzleme katılımcıları hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) Izleme ve [İzleme katılımcıları](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="71de3-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="71de3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="71de3-106">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71de3-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="71de3-107">Attributes and Elements</span></span>  

 <span data-ttu-id="71de3-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71de3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71de3-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="71de3-109">Attributes</span></span>  
  
|<span data-ttu-id="71de3-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="71de3-110">Element</span></span>|<span data-ttu-id="71de3-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71de3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71de3-112">name</span><span class="sxs-lookup"><span data-stu-id="71de3-112">name</span></span>|<span data-ttu-id="71de3-113">İzleme katılımcısının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="71de3-113">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="71de3-114">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="71de3-114">profileName</span></span>|<span data-ttu-id="71de3-115">İzleme katılımcının abone olduğu izleme kayıtlarını tanımlayan izleme profili adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="71de3-115">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="71de3-116">tür</span><span class="sxs-lookup"><span data-stu-id="71de3-116">type</span></span>|<span data-ttu-id="71de3-117">İzleme katılımcısı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="71de3-117">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71de3-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="71de3-118">Child Elements</span></span>  

 <span data-ttu-id="71de3-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="71de3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71de3-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="71de3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="71de3-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="71de3-121">Element</span></span>|<span data-ttu-id="71de3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71de3-122">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="71de3-123">İzleme katılımcılarının listesi</span><span class="sxs-lookup"><span data-stu-id="71de3-123">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71de3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71de3-124">Remarks</span></span>  

 <span data-ttu-id="71de3-125">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71de3-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="71de3-126">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="71de3-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="71de3-127">Birden çok izleme katılımcısı izleme olaylarını eşzamanlı olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="71de3-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="71de3-128">Her izleme katılımcısı, farklı bir izleme profiliyle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="71de3-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="71de3-129">İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="71de3-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="71de3-130">Katılımcı bir yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek bir iş akışı hizmeti üzerinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="71de3-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="71de3-131">ETW izleme katılımcısının etkinleştirilmesi, Olay Görüntüleyicisi 'nde izleme kayıtlarının görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="71de3-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="71de3-132">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71de3-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71de3-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="71de3-133">Example</span></span>  

 <span data-ttu-id="71de3-134">Aşağıdaki yapılandırma örneği, Web.config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="71de3-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="71de3-135">ETW Izleme katılımcısı tarafından ETW 'ye Izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği `<diagnostics>` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="71de3-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="71de3-136">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="71de3-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="71de3-137">Bu, `profileName` öğesinin özniteliği tarafından tanımlanır `<add>` .</span><span class="sxs-lookup"><span data-stu-id="71de3-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="71de3-138">Bunlar tanımlandıktan sonra, Izleme katılımcısı `<etwTracking>` hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="71de3-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="71de3-139">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="71de3-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="71de3-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71de3-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="71de3-141">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="71de3-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="71de3-142">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="71de3-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
