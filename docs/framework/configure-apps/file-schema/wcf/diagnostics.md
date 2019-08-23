---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 170cae5b328c86073c1d8e7710bb19e98ab5688c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925874"
---
# <a name="diagnostics"></a><span data-ttu-id="16e0f-101">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="16e0f-101">\<diagnostics></span></span>
<span data-ttu-id="16e0f-102">Öğesi `diagnostics` , çalışma zamanı incelemesi ve denetimi için bir yönetici tarafından kullanılabilecek ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16e0f-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="16e0f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="16e0f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="16e0f-104">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="16e0f-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e0f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16e0f-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16e0f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="16e0f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="16e0f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16e0f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16e0f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16e0f-108">Attributes</span></span>  
  
|<span data-ttu-id="16e0f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="16e0f-109">Attribute</span></span>|<span data-ttu-id="16e0f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16e0f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16e0f-111">EtwProviderId</span><span class="sxs-lookup"><span data-stu-id="16e0f-111">etwProviderId</span></span>|<span data-ttu-id="16e0f-112">ETW oturumlarına olayları yazan olay Izleme sağlayıcısı için tanımlayıcıyı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="16e0f-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="16e0f-113">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="16e0f-113">performanceCounters</span></span>|<span data-ttu-id="16e0f-114">Derleme için performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="16e0f-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="16e0f-115">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="16e0f-115">Valid values are</span></span><br /><br /> <span data-ttu-id="16e0f-116">Dışına Performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="16e0f-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="16e0f-117">-Yalnızca ServiceOnly: Yalnızca bu hizmetle ilgili performans sayaçları etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="16e0f-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="16e0f-118">Bütün Performans sayaçları çalışma zamanında görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="16e0f-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="16e0f-119">Varsayılanını Tek bir performans sayacı örneği _WCF_Admin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="16e0f-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="16e0f-120">Bu örnek, altyapı tarafından kullanılan SQM verilerinin toplanmasını etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16e0f-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="16e0f-121">Bu örnek için sayaç değerlerinden hiçbiri güncelleştirilmemiş ve bu nedenle sıfır olarak kalacak.</span><span class="sxs-lookup"><span data-stu-id="16e0f-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="16e0f-122">WCF için bir yapılandırma yoksa, bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="16e0f-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="16e0f-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="16e0f-123">wmiProviderEnabled</span></span>|<span data-ttu-id="16e0f-124">Derleme için WMI sağlayıcısının etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="16e0f-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="16e0f-125">Kullanıcının Windows Communication Foundation (WCF) İnceleme ve denetim özelliklerine çalışma zamanı erişimi kazanması için WMI sağlayıcısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="16e0f-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="16e0f-126">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="16e0f-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16e0f-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="16e0f-127">Child Elements</span></span>  
  
|<span data-ttu-id="16e0f-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="16e0f-128">Element</span></span>|<span data-ttu-id="16e0f-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16e0f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16e0f-130">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="16e0f-130">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="16e0f-131">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="16e0f-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="16e0f-132">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="16e0f-132">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="16e0f-133">WCF ileti günlüğe kaydetme ayarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="16e0f-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16e0f-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="16e0f-134">Parent Elements</span></span>  
  
|<span data-ttu-id="16e0f-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="16e0f-135">Element</span></span>|<span data-ttu-id="16e0f-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16e0f-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16e0f-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="16e0f-137">serviceModel</span></span>|<span data-ttu-id="16e0f-138">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="16e0f-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16e0f-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16e0f-139">Remarks</span></span>  
 <span data-ttu-id="16e0f-140">`diagnostics` Bölümü bir derlemede bulunan tüm hizmetler için tanılama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16e0f-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="16e0f-141">Derlemede yalnızca bir hizmet olmadığı takdirde, hizmet düzeyinde ayrı Tanılama ayarları tanımlamak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="16e0f-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="16e0f-142">Öznitelikler, bölümün gereksinimlerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="16e0f-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16e0f-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="16e0f-143">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
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
  
## <a name="see-also"></a><span data-ttu-id="16e0f-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16e0f-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
