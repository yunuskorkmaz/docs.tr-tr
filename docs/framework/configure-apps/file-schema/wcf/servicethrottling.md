---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 77ed5e91f09d9e658deeb7996baaca445b4e0c90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937102"
---
# <a name="servicethrottling"></a><span data-ttu-id="93f3b-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="93f3b-101">\<serviceThrottling></span></span>
<span data-ttu-id="93f3b-102">Bir Windows Communication Foundation (WCF) hizmetinin azaltma mekanizmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="93f3b-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="93f3b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="93f3b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="93f3b-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="93f3b-104">\<behaviors></span></span>  
<span data-ttu-id="93f3b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="93f3b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="93f3b-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="93f3b-106">\<behavior></span></span>  
<span data-ttu-id="93f3b-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="93f3b-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f3b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93f3b-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93f3b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="93f3b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="93f3b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93f3b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93f3b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="93f3b-111">Attributes</span></span>  
  
|<span data-ttu-id="93f3b-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="93f3b-112">Attribute</span></span>|<span data-ttu-id="93f3b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93f3b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93f3b-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="93f3b-114">maxConcurrentCalls</span></span>|<span data-ttu-id="93f3b-115">Üzerinde şu anda işleyen ileti sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="93f3b-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="93f3b-116">Sınırın fazla olan çağrıları sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="93f3b-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="93f3b-117">Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="93f3b-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="93f3b-118">Varsayılan değer 16 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="93f3b-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="93f3b-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="93f3b-119">maxConcurrentInstances</span></span>|<span data-ttu-id="93f3b-120">Bir defada bir <xref:System.ServiceModel.InstanceContext> <xref:System.ServiceModel.ServiceHost>kez yürütülen nesne sayısını sınırlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="93f3b-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="93f3b-121">Ek örnek oluşturma istekleri sıraya alınır ve sınırın altına bir yuva kullanılabilir hale geldiğinde tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="93f3b-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="93f3b-122">Varsayılan değer, maxConcurrentSessions ve Maxconcurrentçağrılarının toplamıdır</span><span class="sxs-lookup"><span data-stu-id="93f3b-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="93f3b-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="93f3b-123">maxConcurrentSessions</span></span>|<span data-ttu-id="93f3b-124">Bir <xref:System.ServiceModel.ServiceHost> nesnenin kabul edebileceği oturum sayısını sınırlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="93f3b-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="93f3b-125">Hizmet sınırı aşan bağlantıları kabul eder, ancak yalnızca sınırın altındaki kanallar etkin olur (iletiler kanaldan okur).</span><span class="sxs-lookup"><span data-stu-id="93f3b-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="93f3b-126">Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="93f3b-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="93f3b-127">Varsayılan değer 100 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="93f3b-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93f3b-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="93f3b-128">Child Elements</span></span>  
 <span data-ttu-id="93f3b-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="93f3b-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93f3b-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="93f3b-130">Parent Elements</span></span>  
  
|<span data-ttu-id="93f3b-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="93f3b-131">Element</span></span>|<span data-ttu-id="93f3b-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93f3b-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93f3b-133">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="93f3b-133">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="93f3b-134">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="93f3b-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93f3b-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93f3b-135">Remarks</span></span>  
 <span data-ttu-id="93f3b-136">Azaltma denetimleri, kaynakların aşırı kullanımını önlemeye yönelik eşzamanlı çağrı, örnek veya oturum sayısına yönelik sınırlar yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="93f3b-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="93f3b-137">Her öznitelik değeri her ulaşıldığında bir izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="93f3b-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="93f3b-138">İlk izleme uyarı olarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="93f3b-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93f3b-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="93f3b-139">Example</span></span>  
 <span data-ttu-id="93f3b-140">Aşağıdaki yapılandırma örneği, hizmetin maksimum eşzamanlı çağrı sayısını 2 ' ye ve en fazla eşzamanlı örnek sayısını 10 ' a sınırlandırdığından emin olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="93f3b-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="93f3b-141">Bu örneği çalıştırmanın ayrıntılı bir örneği için bkz. [azaltma](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="93f3b-141">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93f3b-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93f3b-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="93f3b-143">WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma</span><span class="sxs-lookup"><span data-stu-id="93f3b-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
