---
title: '&lt;serviceThrottling&gt;'
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ebef29360f661c77f51557ae4c9ca0bdf8177b99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689487"
---
# <a name="ltservicethrottlinggt"></a><span data-ttu-id="86514-102">&lt;serviceThrottling&gt;</span><span class="sxs-lookup"><span data-stu-id="86514-102">&lt;serviceThrottling&gt;</span></span>
<span data-ttu-id="86514-103">Bir Windows Communication Foundation (WCF) hizmetinin azaltma mekanizmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86514-103">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="86514-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="86514-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="86514-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="86514-105">\<behaviors></span></span>  
<span data-ttu-id="86514-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="86514-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="86514-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="86514-107">\<behavior></span></span>  
<span data-ttu-id="86514-108">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="86514-108">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86514-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86514-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86514-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86514-110">Attributes and Elements</span></span>  
 <span data-ttu-id="86514-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86514-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86514-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86514-112">Attributes</span></span>  
  
|<span data-ttu-id="86514-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86514-113">Attribute</span></span>|<span data-ttu-id="86514-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86514-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86514-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="86514-115">maxConcurrentCalls</span></span>|<span data-ttu-id="86514-116">Şu anda üzerinde işlem iletilerinin sayısını sınırlayan pozitif bir tamsayı bir <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="86514-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="86514-117">Sınırı aşan çağrıları kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="86514-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="86514-118">Bu değerin 0 olarak ayarlanması, bu Int32.MaxValue olarak ayarlamaya eşittir.</span><span class="sxs-lookup"><span data-stu-id="86514-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="86514-119">Varsayılan değer 16 \* işlemci sayısı.</span><span class="sxs-lookup"><span data-stu-id="86514-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="86514-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="86514-120">maxConcurrentInstances</span></span>|<span data-ttu-id="86514-121">Sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.InstanceContext> arasında aynı anda yürütmek nesneleri bir <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="86514-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="86514-122">Ek örnekleri oluşturmak için istekler kuyruğa alınır ve sınırın altına bir yuva kullanıma sunulduğunda tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="86514-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="86514-123">Varsayılan maxConcurrentSessions ve MaxConcurrentCalls toplamıdır</span><span class="sxs-lookup"><span data-stu-id="86514-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="86514-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="86514-124">maxConcurrentSessions</span></span>|<span data-ttu-id="86514-125">Oturumlarının sayısını sınırlayan pozitif bir tamsayı bir <xref:System.ServiceModel.ServiceHost> nesneyi kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="86514-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="86514-126">Hizmet sınırı aşan bağlantılar kabul eder, ancak yalnızca kanalları sınırın altına etkin (kanaldan iletiler okunur).</span><span class="sxs-lookup"><span data-stu-id="86514-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="86514-127">Bu değerin 0 olarak ayarlanması, bu Int32.MaxValue olarak ayarlamaya eşittir.</span><span class="sxs-lookup"><span data-stu-id="86514-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="86514-128">Varsayılan değer 100'dür \* işlemci sayısı.</span><span class="sxs-lookup"><span data-stu-id="86514-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86514-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86514-129">Child Elements</span></span>  
 <span data-ttu-id="86514-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="86514-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86514-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86514-131">Parent Elements</span></span>  
  
|<span data-ttu-id="86514-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="86514-132">Element</span></span>|<span data-ttu-id="86514-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86514-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86514-134">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="86514-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="86514-135">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="86514-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86514-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86514-136">Remarks</span></span>  
 <span data-ttu-id="86514-137">Azaltma denetimleri sınırlarını eşzamanlı çağrıları, örnekleri veya oturumları kaynakların aşırı kullanımını önlemek için sayısına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="86514-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="86514-138">Özniteliklerin değerini ulaşıldığında her zaman bir izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="86514-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="86514-139">İlk izleme, uyarı olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="86514-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86514-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="86514-140">Example</span></span>  
 <span data-ttu-id="86514-141">Aşağıdaki yapılandırma örnek hizmet 2 ve en fazla 10 eş zamanlı örnekleri sayısı en fazla eşzamanlı çağrıların limitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="86514-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="86514-142">Bu örneği çalıştırmadan ayrıntılı örnek için bkz. [azaltma](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="86514-142">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="86514-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86514-143">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="86514-144">WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma</span><span class="sxs-lookup"><span data-stu-id="86514-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
