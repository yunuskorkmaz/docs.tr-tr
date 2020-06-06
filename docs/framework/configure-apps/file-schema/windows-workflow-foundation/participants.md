---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: e6e996bd1cc32258167e30287e9338a4773ce921
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152034"
---
# \<participants>
<span data-ttu-id="ee952-101">Çalışma zamanından doğrudan yayılmakta olan izleme kayıtlarını dinleyen bir izleme katılımcıları listesini yapılandırın ve bunları yapılandırıldıklarında her türlü şekilde işleyin.</span><span class="sxs-lookup"><span data-stu-id="ee952-101">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="ee952-102">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="ee952-102">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="ee952-103">İş akışı izleme ve İzleme katılımcıları hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) Izleme ve [İzleme katılımcıları](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="ee952-103">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="ee952-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee952-104">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee952-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee952-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ee952-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee952-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee952-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee952-107">Attributes</span></span>  
 <span data-ttu-id="ee952-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee952-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee952-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee952-109">Child Elements</span></span>  
  
|<span data-ttu-id="ee952-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee952-110">Element</span></span>|<span data-ttu-id="ee952-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee952-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-participants.md)|<span data-ttu-id="ee952-112">İzleme katılımcısı için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ee952-112">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee952-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee952-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ee952-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee952-114">Element</span></span>|<span data-ttu-id="ee952-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee952-115">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](tracking.md)|<span data-ttu-id="ee952-116">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee952-116">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee952-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee952-117">Remarks</span></span>  
 <span data-ttu-id="ee952-118">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee952-118">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="ee952-119">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee952-119">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="ee952-120">Birden çok izleme katılımcısı izleme olaylarını eşzamanlı olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ee952-120">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="ee952-121">Her izleme katılımcısı, farklı bir izleme profiliyle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee952-121">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="ee952-122">İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ee952-122">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="ee952-123">Katılımcı bir yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek bir iş akışı hizmeti üzerinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ee952-123">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="ee952-124">ETW izleme katılımcısının etkinleştirilmesi, Olay Görüntüleyicisi 'nde izleme kayıtlarının görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="ee952-124">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="ee952-125">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee952-125">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee952-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee952-126">Example</span></span>  
 <span data-ttu-id="ee952-127">Aşağıdaki yapılandırma örneği, Web. config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee952-127">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="ee952-128">ETW Izleme katılımcısı tarafından ETW 'ye Izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği **\<diagnostics>** bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ee952-128">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="ee952-129">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="ee952-129">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="ee952-130">Bu, öğesinin **ProfileName** özniteliği tarafından tanımlanır **\<add>** .</span><span class="sxs-lookup"><span data-stu-id="ee952-130">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="ee952-131">Bunlar tanımlandıktan sonra, Izleme katılımcısı **\<etwTracking>** hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="ee952-131">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="ee952-132">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="ee952-132">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee952-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee952-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="ee952-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ee952-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ee952-135">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="ee952-135">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
