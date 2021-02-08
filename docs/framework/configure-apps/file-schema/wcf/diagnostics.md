---
description: 'Hakkında daha fazla bilgi edinin: <diagnostics>'
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: d1651d949cdc095e630e9cde0bacbe51a5eb6062
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782162"
---
# \<diagnostics>

<span data-ttu-id="81da5-102">`diagnostics`Öğesi, çalışma zamanı incelemesi ve denetimi için bir yönetici tarafından kullanılabilecek ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81da5-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="81da5-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="81da5-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81da5-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81da5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="81da5-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81da5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81da5-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81da5-106">Attributes</span></span>  
  
|<span data-ttu-id="81da5-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81da5-107">Attribute</span></span>|<span data-ttu-id="81da5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81da5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81da5-109">EtwProviderId</span><span class="sxs-lookup"><span data-stu-id="81da5-109">etwProviderId</span></span>|<span data-ttu-id="81da5-110">ETW oturumlarına olayları yazan Event-Tracing sağlayıcısı için tanımlayıcıyı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="81da5-110">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="81da5-111">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="81da5-111">performanceCounters</span></span>|<span data-ttu-id="81da5-112">Derleme için performans sayaçlarının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="81da5-112">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="81da5-113">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="81da5-113">Valid values are</span></span><br /><br /> <span data-ttu-id="81da5-114">-Off: performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="81da5-114">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="81da5-115">-Yalnızca ServiceOnly: yalnızca bu hizmetle ilgili performans sayaçları etkindir.</span><span class="sxs-lookup"><span data-stu-id="81da5-115">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="81da5-116">-All: performans sayaçları çalışma zamanında görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="81da5-116">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="81da5-117">-Varsayılan: tek bir performans sayacı örneği _WCF_Admin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="81da5-117">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="81da5-118">Bu örnek, altyapı tarafından kullanılan SQM verilerinin toplanmasını etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="81da5-118">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="81da5-119">Bu örnek için sayaç değerlerinden hiçbiri güncelleştirilmemiş ve bu nedenle sıfır olarak kalacak.</span><span class="sxs-lookup"><span data-stu-id="81da5-119">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="81da5-120">WCF için bir yapılandırma yoksa, bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="81da5-120">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="81da5-121">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="81da5-121">wmiProviderEnabled</span></span>|<span data-ttu-id="81da5-122">Derleme için WMI sağlayıcısının etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="81da5-122">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="81da5-123">Kullanıcının Windows Communication Foundation (WCF) İnceleme ve denetim özelliklerine çalışma zamanı erişimi kazanması için WMI sağlayıcısı gerekir.</span><span class="sxs-lookup"><span data-stu-id="81da5-123">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="81da5-124">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="81da5-124">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81da5-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81da5-125">Child Elements</span></span>  
  
|<span data-ttu-id="81da5-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="81da5-126">Element</span></span>|<span data-ttu-id="81da5-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81da5-127">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="81da5-128">Bir hizmet uygulamasının çalışması sırasında uçtan uca izlemenin farklı yönlerini etkinleştirmenizi ve devre dışı bırakmanızı sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="81da5-128">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="81da5-129">WCF ileti günlüğe kaydetme ayarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="81da5-129">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81da5-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81da5-130">Parent Elements</span></span>  
  
|<span data-ttu-id="81da5-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="81da5-131">Element</span></span>|<span data-ttu-id="81da5-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81da5-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81da5-133">serviceModel</span><span class="sxs-lookup"><span data-stu-id="81da5-133">serviceModel</span></span>|<span data-ttu-id="81da5-134">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="81da5-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81da5-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81da5-135">Remarks</span></span>  

 <span data-ttu-id="81da5-136">`diagnostics`Bölümü bir derlemede bulunan tüm hizmetler için tanılama ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81da5-136">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="81da5-137">Derlemede yalnızca bir hizmet olmadığı takdirde, hizmet düzeyinde ayrı Tanılama ayarları tanımlamak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="81da5-137">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="81da5-138">Öznitelikler, bölümün gereksinimlerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="81da5-138">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81da5-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="81da5-139">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81da5-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81da5-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
