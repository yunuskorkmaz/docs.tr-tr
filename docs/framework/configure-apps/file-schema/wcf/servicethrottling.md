---
description: 'Hakkında daha fazla bilgi edinin: <serviceThrottling>'
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: eb65f6d60a266a367789d87e4e6ea10ebfd2c7a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786687"
---
# \<serviceThrottling>

<span data-ttu-id="23313-102">Bir Windows Communication Foundation (WCF) hizmetinin azaltma mekanizmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="23313-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="23313-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="23313-103">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23313-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="23313-104">Attributes and Elements</span></span>  

 <span data-ttu-id="23313-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="23313-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23313-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="23313-106">Attributes</span></span>  
  
|<span data-ttu-id="23313-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="23313-107">Attribute</span></span>|<span data-ttu-id="23313-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23313-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23313-109">Maxconcurrentçağrıları</span><span class="sxs-lookup"><span data-stu-id="23313-109">maxConcurrentCalls</span></span>|<span data-ttu-id="23313-110">Üzerinde şu anda işleyen ileti sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="23313-110">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="23313-111">Sınırın fazla olan çağrıları sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="23313-111">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="23313-112">Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="23313-112">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="23313-113">Varsayılan değer 16 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="23313-113">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="23313-114">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="23313-114">maxConcurrentInstances</span></span>|<span data-ttu-id="23313-115"><xref:System.ServiceModel.InstanceContext>Bir defada bir kez yürütülen nesne sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="23313-115">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="23313-116">Ek örnek oluşturma istekleri sıraya alınır ve sınırın altına bir yuva kullanılabilir hale geldiğinde tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="23313-116">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="23313-117">Varsayılan değer, maxConcurrentSessions ve Maxconcurrentçağrılarının toplamıdır</span><span class="sxs-lookup"><span data-stu-id="23313-117">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="23313-118">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="23313-118">maxConcurrentSessions</span></span>|<span data-ttu-id="23313-119">Bir nesnenin kabul edebileceği oturum sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="23313-119">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="23313-120">Hizmet sınırı aşan bağlantıları kabul eder, ancak yalnızca sınırın altındaki kanallar etkin olur (iletiler kanaldan okur).</span><span class="sxs-lookup"><span data-stu-id="23313-120">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="23313-121">Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="23313-121">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="23313-122">Varsayılan değer 100 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="23313-122">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23313-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="23313-123">Child Elements</span></span>  

 <span data-ttu-id="23313-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="23313-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23313-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="23313-125">Parent Elements</span></span>  
  
|<span data-ttu-id="23313-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="23313-126">Element</span></span>|<span data-ttu-id="23313-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23313-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="23313-128">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="23313-128">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23313-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23313-129">Remarks</span></span>  

 <span data-ttu-id="23313-130">Azaltma denetimleri, kaynakların aşırı kullanımını önlemeye yönelik eşzamanlı çağrı, örnek veya oturum sayısına yönelik sınırlar yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="23313-130">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="23313-131">Her öznitelik değeri her ulaşıldığında bir izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="23313-131">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="23313-132">İlk izleme uyarı olarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="23313-132">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23313-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="23313-133">Example</span></span>  

 <span data-ttu-id="23313-134">Aşağıdaki yapılandırma örneği, hizmetin maksimum eşzamanlı çağrı sayısını 2 ' ye ve en fazla eşzamanlı örnek sayısını 10 ' a sınırlandırdığından emin olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="23313-134">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="23313-135">Bu örneği çalıştırmanın ayrıntılı bir örneği için bkz. [azaltma](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="23313-135">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23313-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23313-136">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="23313-137">WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma</span><span class="sxs-lookup"><span data-stu-id="23313-137">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
