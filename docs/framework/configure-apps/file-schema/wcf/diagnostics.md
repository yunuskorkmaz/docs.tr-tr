---
title: '&lt;Tanılama&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bb5506fd72745f32194b2e3cc409ff848fd1c270
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="ltdiagnosticsgt"></a><span data-ttu-id="286c5-102">&lt;Tanılama&gt;</span><span class="sxs-lookup"><span data-stu-id="286c5-102">&lt;diagnostics&gt;</span></span>
<span data-ttu-id="286c5-103">`diagnostics` Öğe, bir yönetici tarafından çalışma zamanı denetleme ve denetimi için kullanılan ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="286c5-103">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="286c5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="286c5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="286c5-105">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="286c5-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="286c5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="286c5-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <diagnostics 
      etwProviderId="String"       
      performanceCounters="Off/ServiceOnly/All/Default"              
      wmiProviderEnabled="Boolean" >       
    <endToEndTracing 
        activityTracing="Boolean"  
        messageFlowTracing="Boolean"  
        propagateActivity="Boolean" />  
    <messageLogging 
        logEntireMessage="Boolean"  
        logMalformedMessages="Boolean"  
        logMessagesAtServiceLevel="Boolean"  
        logMessagesAtTransportLevel="Boolean"  
        maxMessagesToLog="Integer"  
        maxSizeOfMessageToLog="Integer" >  
      <filters>  
        <clear />  
      </filters>  
    </messageLogging>  
  </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="286c5-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="286c5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="286c5-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="286c5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="286c5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="286c5-109">Attributes</span></span>  
  
|<span data-ttu-id="286c5-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="286c5-110">Attribute</span></span>|<span data-ttu-id="286c5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="286c5-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="286c5-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="286c5-112">etwProviderId</span></span>|<span data-ttu-id="286c5-113">Olayları ETW oturumlarını Yazar olay izleme sağlayıcısı tanımlayıcısı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="286c5-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="286c5-114">performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="286c5-114">performanceCounters</span></span>|<span data-ttu-id="286c5-115">Derleme için performans sayaçları etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="286c5-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="286c5-116">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="286c5-116">Valid values are</span></span><br /><br /> <span data-ttu-id="286c5-117">-Kapalı: Performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="286c5-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="286c5-118">-ServiceOnly: Yalnızca bu hizmetle ilgili performans sayaçları etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="286c5-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="286c5-119">-Tüm: performans sayaçları çalışma zamanında görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="286c5-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="286c5-120">-Varsayılan: Tek bir performans sayacı örneği _WCF_Admin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="286c5-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="286c5-121">Bu örnek, altyapısı tarafından kullanılan SQM Veri toplamayı etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="286c5-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="286c5-122">Bu örnek için sayacı değerlerini hiçbiri güncelleştirilir ve bu nedenle sıfırda kalacaktır.</span><span class="sxs-lookup"><span data-stu-id="286c5-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="286c5-123">Bu, herhangi bir yapılandırma için WCF varsa, varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="286c5-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="286c5-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="286c5-124">wmiProviderEnabled</span></span>|<span data-ttu-id="286c5-125">Derleme için WMI sağlayıcısı etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="286c5-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="286c5-126">WMI sağlayıcısı denetleme ve denetim özelliklerini Windows Communication Foundation (WCF) çalışma zamanı erişmek kullanıcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="286c5-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="286c5-127">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="286c5-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="286c5-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="286c5-128">Child Elements</span></span>  
  
|<span data-ttu-id="286c5-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="286c5-129">Element</span></span>|<span data-ttu-id="286c5-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="286c5-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="286c5-131">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="286c5-131">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="286c5-132">Etkinleştirme ve devre dışı uçtan uca izleme bir hizmet uygulaması çalışması sırasında farklı yönlerini olanak sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="286c5-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="286c5-133">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="286c5-133">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="286c5-134">WCF ileti günlüğe kaydetme ayarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="286c5-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="286c5-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="286c5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="286c5-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="286c5-136">Element</span></span>|<span data-ttu-id="286c5-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="286c5-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="286c5-138">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="286c5-138">serviceModel</span></span>|<span data-ttu-id="286c5-139">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="286c5-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="286c5-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="286c5-140">Remarks</span></span>  
 <span data-ttu-id="286c5-141">`diagnostics` Bölümü, bir derlemede bulunan tüm hizmetler için tanılama ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="286c5-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="286c5-142">Derlemede yalnızca bir hizmet olmadıkça hizmet düzeyinde ayrı tanılama ayarlarını tanımlamak olası değil.</span><span class="sxs-lookup"><span data-stu-id="286c5-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="286c5-143">Öznitelikleri bölüm gereksinimlerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="286c5-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="286c5-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="286c5-144">Example</span></span>  
  
```xml  
<diagnostics
    wmiProviderEnabled="false"  
    performanceCounters="all">  
  <messageLogging 
      logEntireMessage="true"  
      logMalformedMessages="true"  
      logMessagesAtServiceLevel="true"  
      logMessagesAtTransportLevel="true"  
      maxMessagesToLog="42"  
      maxSizeOfMessageToLog="42">  
    <filters>  
      <clear />  
    </filters>  
  </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a><span data-ttu-id="286c5-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="286c5-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
