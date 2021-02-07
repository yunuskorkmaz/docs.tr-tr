---
description: WCF hakkında daha fazla bilgi edinin <participants>
title: <participants> WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 4e0285025864a8c70c75bc409a79bc61002f29a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683833"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="185ae-103">\<participants> WCF</span><span class="sxs-lookup"><span data-stu-id="185ae-103">\<participants> of WCF</span></span>

<span data-ttu-id="185ae-104">Çalışma zamanından doğrudan yayılmakta olan izleme kayıtlarını dinleyen bir izleme katılımcıları listesini yapılandırın ve bunları yapılandırıldıklarında her türlü şekilde işleyin.</span><span class="sxs-lookup"><span data-stu-id="185ae-104">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="185ae-105">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="185ae-105">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="185ae-106">İş akışı izleme ve İzleme katılımcıları hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) Izleme ve [İzleme katılımcıları](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="185ae-106">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="185ae-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="185ae-107">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="185ae-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="185ae-108">Attributes and Elements</span></span>  

 <span data-ttu-id="185ae-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="185ae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="185ae-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="185ae-110">Attributes</span></span>  

 <span data-ttu-id="185ae-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="185ae-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="185ae-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="185ae-112">Child Elements</span></span>  
  
|<span data-ttu-id="185ae-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="185ae-113">Element</span></span>|<span data-ttu-id="185ae-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="185ae-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="185ae-115">İzleme katılımcısı için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="185ae-115">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="185ae-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="185ae-116">Parent Elements</span></span>  
  
|<span data-ttu-id="185ae-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="185ae-117">Element</span></span>|<span data-ttu-id="185ae-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="185ae-118">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="185ae-119">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="185ae-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="185ae-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="185ae-120">Remarks</span></span>  

 <span data-ttu-id="185ae-121">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="185ae-121">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="185ae-122">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="185ae-122">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="185ae-123">Birden çok izleme katılımcısı izleme olaylarını eşzamanlı olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="185ae-123">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="185ae-124">Her izleme katılımcısı, farklı bir izleme profiliyle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="185ae-124">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="185ae-125">İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="185ae-125">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="185ae-126">Katılımcı bir yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek bir iş akışı hizmeti üzerinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="185ae-126">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="185ae-127">ETW izleme katılımcısının etkinleştirilmesi, Olay Görüntüleyicisi 'nde izleme kayıtlarının görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="185ae-127">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="185ae-128">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="185ae-128">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="185ae-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="185ae-129">Example</span></span>  

 <span data-ttu-id="185ae-130">Aşağıdaki yapılandırma örneği, Web.config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="185ae-130">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="185ae-131">ETW Izleme katılımcısı tarafından ETW 'ye Izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği `<diagnostics>` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="185ae-131">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="185ae-132">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="185ae-132">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="185ae-133">Bu, `profileName` öğesinin özniteliği tarafından tanımlanır `<add>` .</span><span class="sxs-lookup"><span data-stu-id="185ae-133">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="185ae-134">Bunlar tanımlandıktan sonra, Izleme katılımcısı `<etwTracking>` hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="185ae-134">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="185ae-135">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="185ae-135">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="185ae-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="185ae-136">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="185ae-137">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="185ae-137">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="185ae-138">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="185ae-138">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
