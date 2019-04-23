---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 3fc7828d399555f7c459f6dd067ce9a24b8998b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108036"
---
# <a name="diagnostics"></a><span data-ttu-id="77c90-101">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="77c90-101">\<diagnostics></span></span>
<span data-ttu-id="77c90-102">`diagnostics` Öğesi, bir yönetici tarafından çalışma zamanı incelemesi ve denetimi için kullanılan ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77c90-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="77c90-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="77c90-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="77c90-104">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="77c90-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77c90-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77c90-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77c90-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="77c90-106">Attributes and Elements</span></span>  
 <span data-ttu-id="77c90-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77c90-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77c90-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="77c90-108">Attributes</span></span>  
  
|<span data-ttu-id="77c90-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="77c90-109">Attribute</span></span>|<span data-ttu-id="77c90-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77c90-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77c90-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="77c90-111">etwProviderId</span></span>|<span data-ttu-id="77c90-112">ETW oturumlarına olayları yazan Olay İzleyici sağlayıcısı için tanımlayıcıyı belirleyen bir dize.</span><span class="sxs-lookup"><span data-stu-id="77c90-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="77c90-113">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="77c90-113">performanceCounters</span></span>|<span data-ttu-id="77c90-114">Derleme için performans sayaçlarının etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="77c90-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="77c90-115">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="77c90-115">Valid values are</span></span><br /><br /> <span data-ttu-id="77c90-116">-Kapalı: Performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="77c90-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="77c90-117">-ServiceOnly: Yalnızca bu hizmetle ilgili performans sayaçları etkindir.</span><span class="sxs-lookup"><span data-stu-id="77c90-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="77c90-118">-Tüm: Performans sayaçları, çalışma zamanında görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="77c90-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="77c90-119">-Varsayılan: Tek performans sayacı örneği _WCF_Admin oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="77c90-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="77c90-120">Bu örnek, altyapısı tarafından kullanılan SQM Veri toplamayı etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77c90-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="77c90-121">Bu örneğin sayacı değerlerini hiçbiri güncelleştirilir ve bu nedenle sıfırdan kalacaktır.</span><span class="sxs-lookup"><span data-stu-id="77c90-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="77c90-122">WCF için yapılandırma varsa varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="77c90-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="77c90-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="77c90-123">wmiProviderEnabled</span></span>|<span data-ttu-id="77c90-124">Derleme için WMI sağlayıcısı etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="77c90-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="77c90-125">WMI sağlayıcısı, çalışma zamanı incelemesi ve denetimi özellikleri Windows Communication Foundation (WCF) erişmek kullanıcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77c90-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="77c90-126">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="77c90-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77c90-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="77c90-127">Child Elements</span></span>  
  
|<span data-ttu-id="77c90-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="77c90-128">Element</span></span>|<span data-ttu-id="77c90-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77c90-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77c90-130">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="77c90-130">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="77c90-131">Enable ve disable uçtan uca izleme hizmet uygulamasının çalışması sırasında farklı yönlerini olanak tanıyan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="77c90-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="77c90-132">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="77c90-132">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="77c90-133">WCF iletileri günlüğe kaydetme ayarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="77c90-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77c90-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="77c90-134">Parent Elements</span></span>  
  
|<span data-ttu-id="77c90-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="77c90-135">Element</span></span>|<span data-ttu-id="77c90-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77c90-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77c90-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="77c90-137">serviceModel</span></span>|<span data-ttu-id="77c90-138">Tüm WCF yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="77c90-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77c90-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77c90-139">Remarks</span></span>  
 <span data-ttu-id="77c90-140">`diagnostics` Bölümü, bir derlemede bulunan tüm hizmetler için tanılama ayarları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77c90-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="77c90-141">Derlemede yalnızca bir hizmet olmadığı sürece hizmet düzeyinde ayrı tanılama ayarları tanımlamak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="77c90-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="77c90-142">Öznitelikleri bölüm gereksinimlerine göre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="77c90-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77c90-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="77c90-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77c90-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77c90-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
