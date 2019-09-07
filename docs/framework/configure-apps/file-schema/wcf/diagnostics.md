---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398050"
---
# <a name="diagnostics"></a><span data-ttu-id="e2e7a-101">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="e2e7a-101">\<diagnostics></span></span>
<span data-ttu-id="e2e7a-102">Öğesi `diagnostics` , çalışma zamanı incelemesi ve denetimi için bir yönetici tarafından kullanılabilecek ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
<span data-ttu-id="e2e7a-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2e7a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2e7a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e2e7a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e2e7a-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<Tanılama >**</span><span class="sxs-lookup"><span data-stu-id="e2e7a-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e7a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2e7a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2e7a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2e7a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e2e7a-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2e7a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e2e7a-109">Attributes</span></span>  
  
|<span data-ttu-id="e2e7a-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e2e7a-110">Attribute</span></span>|<span data-ttu-id="e2e7a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2e7a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2e7a-112">EtwProviderId</span><span class="sxs-lookup"><span data-stu-id="e2e7a-112">etwProviderId</span></span>|<span data-ttu-id="e2e7a-113">ETW oturumlarına olayları yazan olay Izleme sağlayıcısı için tanımlayıcıyı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="e2e7a-114">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="e2e7a-114">performanceCounters</span></span>|<span data-ttu-id="e2e7a-115">Derleme için performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="e2e7a-116">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="e2e7a-116">Valid values are</span></span><br /><br /> <span data-ttu-id="e2e7a-117">Dışına Performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="e2e7a-118">-Yalnızca ServiceOnly: Yalnızca bu hizmetle ilgili performans sayaçları etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="e2e7a-119">Bütün Performans sayaçları çalışma zamanında görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="e2e7a-120">Varsayılanını Tek bir performans sayacı örneği _WCF_Admin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="e2e7a-121">Bu örnek, altyapı tarafından kullanılan SQM verilerinin toplanmasını etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="e2e7a-122">Bu örnek için sayaç değerlerinden hiçbiri güncelleştirilmemiş ve bu nedenle sıfır olarak kalacak.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="e2e7a-123">WCF için bir yapılandırma yoksa, bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="e2e7a-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="e2e7a-124">wmiProviderEnabled</span></span>|<span data-ttu-id="e2e7a-125">Derleme için WMI sağlayıcısının etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="e2e7a-126">Kullanıcının Windows Communication Foundation (WCF) İnceleme ve denetim özelliklerine çalışma zamanı erişimi kazanması için WMI sağlayıcısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e2e7a-127">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2e7a-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2e7a-128">Child Elements</span></span>  
  
|<span data-ttu-id="e2e7a-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2e7a-129">Element</span></span>|<span data-ttu-id="e2e7a-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2e7a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2e7a-131">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="e2e7a-131">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="e2e7a-132">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="e2e7a-133">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="e2e7a-133">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="e2e7a-134">WCF ileti günlüğe kaydetme ayarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2e7a-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e2e7a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="e2e7a-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2e7a-136">Element</span></span>|<span data-ttu-id="e2e7a-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2e7a-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2e7a-138">serviceModel</span><span class="sxs-lookup"><span data-stu-id="e2e7a-138">serviceModel</span></span>|<span data-ttu-id="e2e7a-139">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2e7a-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2e7a-140">Remarks</span></span>  
 <span data-ttu-id="e2e7a-141">`diagnostics` Bölümü bir derlemede bulunan tüm hizmetler için tanılama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="e2e7a-142">Derlemede yalnızca bir hizmet olmadığı takdirde, hizmet düzeyinde ayrı Tanılama ayarları tanımlamak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="e2e7a-143">Öznitelikler, bölümün gereksinimlerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2e7a-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2e7a-144">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e2e7a-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e7a-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
