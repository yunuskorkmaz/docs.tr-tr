---
title: <participants>WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 35ed7a49967143838a6f74c51e77c553817bd09a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855086"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="5a8e1-102">\<WCF > katılımcılar</span><span class="sxs-lookup"><span data-stu-id="5a8e1-102">\<participants> of WCF</span></span>
<span data-ttu-id="5a8e1-103">Çalışma zamanından doğrudan yayılmakta olan izleme kayıtlarını dinleyen bir izleme katılımcıları listesini yapılandırın ve bunları yapılandırıldıklarında her türlü şekilde işleyin.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="5a8e1-104">Bu yazma içerir (örneğin, dosya, konsolu ETW), belirli bir çıktısına işleme/kayıtları veya gerekli olabilir herhangi bir birleşimini toplama.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="5a8e1-105">İş akışı izleme ve İzleme katılımcıları hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) Izleme ve [İzleme katılımcıları](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="5a8e1-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="5a8e1-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a8e1-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a8e1-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5a8e1-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5a8e1-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="5a8e1-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>  
<span data-ttu-id="5a8e1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Katılımcılar >**</span><span class="sxs-lookup"><span data-stu-id="5a8e1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8e1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a8e1-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a8e1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a8e1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5a8e1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a8e1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5a8e1-113">Attributes</span></span>  
 <span data-ttu-id="5a8e1-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a8e1-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a8e1-115">Child Elements</span></span>  
  
|<span data-ttu-id="5a8e1-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a8e1-116">Element</span></span>|<span data-ttu-id="5a8e1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a8e1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a8e1-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="5a8e1-118">\<add></span></span>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="5a8e1-119">İzleme katılımcısı için ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-119">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a8e1-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a8e1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5a8e1-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a8e1-121">Element</span></span>|<span data-ttu-id="5a8e1-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a8e1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a8e1-123">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5a8e1-123">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="5a8e1-124">Bir iş akışı hizmeti için izleme ayarlarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-124">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a8e1-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a8e1-125">Remarks</span></span>  
 <span data-ttu-id="5a8e1-126">İzleme katılımcıları iş akışından yayılan izleme verilerini almak ve farklı ortalamalarına depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="5a8e1-127">Benzer şekilde, izleme kayıtlarında yapılan tüm gönderi işlemleri izleme katılımcısının içinden de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="5a8e1-128">Birden çok izleme katılımcısı izleme olaylarını eşzamanlı olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-128">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="5a8e1-129">Her izleme katılımcısı, farklı bir izleme profiliyle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-129">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="5a8e1-130">İzleme kayıtlarını bir ETW oturumuna yazan standart bir izleme katılımcısı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-130">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="5a8e1-131">Katılımcı bir yapılandırma dosyasına izlemeye özgü bir davranış ekleyerek bir iş akışı hizmeti üzerinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-131">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="5a8e1-132">ETW izleme katılımcısının etkinleştirilmesi, Olay Görüntüleyicisi 'nde izleme kayıtlarının görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-132">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="5a8e1-133">Gereksinimlerinizi karşılamıyorsa, özel bir izleme katılımcısı da yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-133">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a8e1-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a8e1-134">Example</span></span>  
 <span data-ttu-id="5a8e1-135">Aşağıdaki yapılandırma örneği, Web. config dosyasında yapılandırılmış standart ETW izleme katılımcısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-135">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="5a8e1-136">ETW izleme katılımcısı tarafından ETW 'ye izleme kayıtlarını yazmak için kullanılan sağlayıcı kimliği `<diagnostics>` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-136">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="5a8e1-137">İzleme katılımcısının, abone olduğu izleme kayıtlarını belirtmek için kendisiyle ilişkili bir profili vardır.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-137">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="5a8e1-138">Bu, `profileName` `<add>` öğesinin özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-138">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="5a8e1-139">Bunlar tanımlandıktan sonra, izleme katılımcısı `<etwTracking>` hizmet davranışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-139">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="5a8e1-140">Bu işlem, Izleme kayıtlarını almaya başlaması için seçilen Izleme katılımcılarını Iş akışı örneğinin uzantılarına ekler.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-140">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a8e1-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a8e1-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="5a8e1-142">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5a8e1-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5a8e1-143">İzleme Katılımcıları</span><span class="sxs-lookup"><span data-stu-id="5a8e1-143">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
