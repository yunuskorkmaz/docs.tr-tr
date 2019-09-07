---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399570"
---
# <a name="servicethrottling"></a><span data-ttu-id="cda28-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="cda28-101">\<serviceThrottling></span></span>
<span data-ttu-id="cda28-102">Bir Windows Communication Foundation (WCF) hizmetinin azaltma mekanizmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cda28-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="cda28-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cda28-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cda28-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cda28-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cda28-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cda28-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="cda28-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cda28-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="cda28-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cda28-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="cda28-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Serviceazaltma >**</span><span class="sxs-lookup"><span data-stu-id="cda28-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda28-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cda28-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cda28-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cda28-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cda28-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cda28-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cda28-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cda28-112">Attributes</span></span>  
  
|<span data-ttu-id="cda28-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cda28-113">Attribute</span></span>|<span data-ttu-id="cda28-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cda28-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cda28-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="cda28-115">maxConcurrentCalls</span></span>|<span data-ttu-id="cda28-116">Üzerinde şu anda işleyen ileti sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cda28-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="cda28-117">Sınırın fazla olan çağrıları sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="cda28-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="cda28-118">Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cda28-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="cda28-119">Varsayılan değer 16 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cda28-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="cda28-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="cda28-120">maxConcurrentInstances</span></span>|<span data-ttu-id="cda28-121">Bir defada bir <xref:System.ServiceModel.InstanceContext> <xref:System.ServiceModel.ServiceHost>kez yürütülen nesne sayısını sınırlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cda28-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="cda28-122">Ek örnek oluşturma istekleri sıraya alınır ve sınırın altına bir yuva kullanılabilir hale geldiğinde tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="cda28-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="cda28-123">Varsayılan değer, maxConcurrentSessions ve Maxconcurrentçağrılarının toplamıdır</span><span class="sxs-lookup"><span data-stu-id="cda28-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="cda28-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="cda28-124">maxConcurrentSessions</span></span>|<span data-ttu-id="cda28-125">Bir <xref:System.ServiceModel.ServiceHost> nesnenin kabul edebileceği oturum sayısını sınırlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cda28-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="cda28-126">Hizmet sınırı aşan bağlantıları kabul eder, ancak yalnızca sınırın altındaki kanallar etkin olur (iletiler kanaldan okur).</span><span class="sxs-lookup"><span data-stu-id="cda28-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="cda28-127">Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="cda28-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="cda28-128">Varsayılan değer 100 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cda28-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cda28-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cda28-129">Child Elements</span></span>  
 <span data-ttu-id="cda28-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="cda28-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cda28-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cda28-131">Parent Elements</span></span>  
  
|<span data-ttu-id="cda28-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="cda28-132">Element</span></span>|<span data-ttu-id="cda28-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cda28-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cda28-134">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="cda28-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="cda28-135">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cda28-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cda28-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cda28-136">Remarks</span></span>  
 <span data-ttu-id="cda28-137">Azaltma denetimleri, kaynakların aşırı kullanımını önlemeye yönelik eşzamanlı çağrı, örnek veya oturum sayısına yönelik sınırlar yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="cda28-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="cda28-138">Her öznitelik değeri her ulaşıldığında bir izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="cda28-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="cda28-139">İlk izleme uyarı olarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cda28-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cda28-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="cda28-140">Example</span></span>  
 <span data-ttu-id="cda28-141">Aşağıdaki yapılandırma örneği, hizmetin maksimum eşzamanlı çağrı sayısını 2 ' ye ve en fazla eşzamanlı örnek sayısını 10 ' a sınırlandırdığından emin olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="cda28-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="cda28-142">Bu örneği çalıştırmanın ayrıntılı bir örneği için bkz. [azaltma](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="cda28-142">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cda28-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cda28-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="cda28-144">WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma</span><span class="sxs-lookup"><span data-stu-id="cda28-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
