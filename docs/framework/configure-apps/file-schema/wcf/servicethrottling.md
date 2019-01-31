---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 87952a92bab1ef7147100332bcef87b6f0534817
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270407"
---
# <a name="servicethrottling"></a><span data-ttu-id="a9867-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="a9867-101">\<serviceThrottling></span></span>
<span data-ttu-id="a9867-102">Bir Windows Communication Foundation (WCF) hizmetinin azaltma mekanizmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9867-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="a9867-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a9867-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a9867-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a9867-104">\<behaviors></span></span>  
<span data-ttu-id="a9867-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a9867-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a9867-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a9867-106">\<behavior></span></span>  
<span data-ttu-id="a9867-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="a9867-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9867-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9867-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9867-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9867-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a9867-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9867-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9867-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a9867-111">Attributes</span></span>  
  
|<span data-ttu-id="a9867-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a9867-112">Attribute</span></span>|<span data-ttu-id="a9867-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9867-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9867-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="a9867-114">maxConcurrentCalls</span></span>|<span data-ttu-id="a9867-115">Şu anda üzerinde işlem iletilerinin sayısını sınırlayan pozitif bir tamsayı bir <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a9867-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a9867-116">Sınırı aşan çağrıları kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="a9867-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="a9867-117">Bu değerin 0 olarak ayarlanması, bu Int32.MaxValue olarak ayarlamaya eşittir.</span><span class="sxs-lookup"><span data-stu-id="a9867-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="a9867-118">Varsayılan değer 16 \* işlemci sayısı.</span><span class="sxs-lookup"><span data-stu-id="a9867-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="a9867-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="a9867-119">maxConcurrentInstances</span></span>|<span data-ttu-id="a9867-120">Sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.InstanceContext> arasında aynı anda yürütmek nesneleri bir <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a9867-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a9867-121">Ek örnekleri oluşturmak için istekler kuyruğa alınır ve sınırın altına bir yuva kullanıma sunulduğunda tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="a9867-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="a9867-122">Varsayılan maxConcurrentSessions ve MaxConcurrentCalls toplamıdır</span><span class="sxs-lookup"><span data-stu-id="a9867-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="a9867-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="a9867-123">maxConcurrentSessions</span></span>|<span data-ttu-id="a9867-124">Oturumlarının sayısını sınırlayan pozitif bir tamsayı bir <xref:System.ServiceModel.ServiceHost> nesneyi kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="a9867-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="a9867-125">Hizmet sınırı aşan bağlantılar kabul eder, ancak yalnızca kanalları sınırın altına etkin (kanaldan iletiler okunur).</span><span class="sxs-lookup"><span data-stu-id="a9867-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="a9867-126">Bu değerin 0 olarak ayarlanması, bu Int32.MaxValue olarak ayarlamaya eşittir.</span><span class="sxs-lookup"><span data-stu-id="a9867-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="a9867-127">Varsayılan değer 100'dür \* işlemci sayısı.</span><span class="sxs-lookup"><span data-stu-id="a9867-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9867-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9867-128">Child Elements</span></span>  
 <span data-ttu-id="a9867-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="a9867-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9867-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9867-130">Parent Elements</span></span>  
  
|<span data-ttu-id="a9867-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9867-131">Element</span></span>|<span data-ttu-id="a9867-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9867-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9867-133">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a9867-133">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a9867-134">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9867-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9867-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9867-135">Remarks</span></span>  
 <span data-ttu-id="a9867-136">Azaltma denetimleri sınırlarını eşzamanlı çağrıları, örnekleri veya oturumları kaynakların aşırı kullanımını önlemek için sayısına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a9867-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="a9867-137">Özniteliklerin değerini ulaşıldığında her zaman bir izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="a9867-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="a9867-138">İlk izleme, uyarı olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="a9867-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9867-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9867-139">Example</span></span>  
 <span data-ttu-id="a9867-140">Aşağıdaki yapılandırma örnek hizmet 2 ve en fazla 10 eş zamanlı örnekleri sayısı en fazla eşzamanlı çağrıların limitleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9867-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="a9867-141">Bu örneği çalıştırmadan ayrıntılı örnek için bkz. [azaltma](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="a9867-141">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9867-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9867-142">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="a9867-143">WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma</span><span class="sxs-lookup"><span data-stu-id="a9867-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
