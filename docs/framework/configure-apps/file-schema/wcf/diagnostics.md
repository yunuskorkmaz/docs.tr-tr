---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398050"
---
# \<diagnostics>
<span data-ttu-id="eb35b-101">`diagnostics`Öğesi, çalışma zamanı incelemesi ve denetimi için bir yönetici tarafından kullanılabilecek ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb35b-101">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="eb35b-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb35b-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb35b-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb35b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="eb35b-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb35b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb35b-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eb35b-105">Attributes</span></span>  
  
|<span data-ttu-id="eb35b-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eb35b-106">Attribute</span></span>|<span data-ttu-id="eb35b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb35b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb35b-108">EtwProviderId</span><span class="sxs-lookup"><span data-stu-id="eb35b-108">etwProviderId</span></span>|<span data-ttu-id="eb35b-109">ETW oturumlarına olayları yazan olay Izleme sağlayıcısı için tanımlayıcıyı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="eb35b-109">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="eb35b-110">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="eb35b-110">performanceCounters</span></span>|<span data-ttu-id="eb35b-111">Derleme için performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb35b-111">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="eb35b-112">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="eb35b-112">Valid values are</span></span><br /><br /> <span data-ttu-id="eb35b-113">-Off: performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="eb35b-113">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="eb35b-114">-Yalnızca ServiceOnly: yalnızca bu hizmetle ilgili performans sayaçları etkindir.</span><span class="sxs-lookup"><span data-stu-id="eb35b-114">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="eb35b-115">-All: performans sayaçları çalışma zamanında görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="eb35b-115">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="eb35b-116">-Varsayılan: tek bir performans sayacı örneği _WCF_Admin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eb35b-116">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="eb35b-117">Bu örnek, altyapı tarafından kullanılan SQM verilerinin toplanmasını etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb35b-117">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="eb35b-118">Bu örnek için sayaç değerlerinden hiçbiri güncelleştirilmemiş ve bu nedenle sıfır olarak kalacak.</span><span class="sxs-lookup"><span data-stu-id="eb35b-118">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="eb35b-119">WCF için bir yapılandırma yoksa, bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="eb35b-119">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="eb35b-120">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="eb35b-120">wmiProviderEnabled</span></span>|<span data-ttu-id="eb35b-121">Derleme için WMI sağlayıcısının etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="eb35b-121">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="eb35b-122">Kullanıcının Windows Communication Foundation (WCF) İnceleme ve denetim özelliklerine çalışma zamanı erişimi kazanması için WMI sağlayıcısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb35b-122">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="eb35b-123">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="eb35b-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb35b-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb35b-124">Child Elements</span></span>  
  
|<span data-ttu-id="eb35b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="eb35b-125">Element</span></span>|<span data-ttu-id="eb35b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb35b-126">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="eb35b-127">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="eb35b-127">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="eb35b-128">WCF ileti günlüğe kaydetme ayarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb35b-128">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb35b-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eb35b-129">Parent Elements</span></span>  
  
|<span data-ttu-id="eb35b-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="eb35b-130">Element</span></span>|<span data-ttu-id="eb35b-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb35b-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb35b-132">serviceModel</span><span class="sxs-lookup"><span data-stu-id="eb35b-132">serviceModel</span></span>|<span data-ttu-id="eb35b-133">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="eb35b-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb35b-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb35b-134">Remarks</span></span>  
 <span data-ttu-id="eb35b-135">`diagnostics`Bölümü bir derlemede bulunan tüm hizmetler için tanılama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb35b-135">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="eb35b-136">Derlemede yalnızca bir hizmet olmadığı takdirde, hizmet düzeyinde ayrı Tanılama ayarları tanımlamak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="eb35b-136">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="eb35b-137">Öznitelikler, bölümün gereksinimlerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="eb35b-137">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb35b-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb35b-138">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb35b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb35b-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
