---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399570"
---
# \<serviceThrottling>
<span data-ttu-id="b3187-101">Bir Windows Communication Foundation (WCF) hizmetinin azaltma mekanizmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3187-101">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="b3187-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3187-102">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3187-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3187-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b3187-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b3187-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3187-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b3187-105">Attributes</span></span>  
  
|<span data-ttu-id="b3187-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b3187-106">Attribute</span></span>|<span data-ttu-id="b3187-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3187-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3187-108">Maxconcurrentçağrıları</span><span class="sxs-lookup"><span data-stu-id="b3187-108">maxConcurrentCalls</span></span>|<span data-ttu-id="b3187-109">Üzerinde şu anda işleyen ileti sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="b3187-109">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="b3187-110">Sınırın fazla olan çağrıları sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="b3187-110">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="b3187-111">Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b3187-111">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="b3187-112">Varsayılan değer 16 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="b3187-112">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="b3187-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="b3187-113">maxConcurrentInstances</span></span>|<span data-ttu-id="b3187-114"><xref:System.ServiceModel.InstanceContext>Bir defada bir kez yürütülen nesne sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="b3187-114">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="b3187-115">Ek örnek oluşturma istekleri sıraya alınır ve sınırın altına bir yuva kullanılabilir hale geldiğinde tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="b3187-115">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="b3187-116">Varsayılan değer, maxConcurrentSessions ve Maxconcurrentçağrılarının toplamıdır</span><span class="sxs-lookup"><span data-stu-id="b3187-116">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="b3187-117">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="b3187-117">maxConcurrentSessions</span></span>|<span data-ttu-id="b3187-118">Bir nesnenin kabul edebileceği oturum sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="b3187-118">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="b3187-119">Hizmet sınırı aşan bağlantıları kabul eder, ancak yalnızca sınırın altındaki kanallar etkin olur (iletiler kanaldan okur).</span><span class="sxs-lookup"><span data-stu-id="b3187-119">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="b3187-120">Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b3187-120">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="b3187-121">Varsayılan değer 100 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="b3187-121">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3187-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3187-122">Child Elements</span></span>  
 <span data-ttu-id="b3187-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="b3187-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3187-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3187-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b3187-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="b3187-125">Element</span></span>|<span data-ttu-id="b3187-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3187-126">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b3187-127">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3187-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3187-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3187-128">Remarks</span></span>  
 <span data-ttu-id="b3187-129">Azaltma denetimleri, kaynakların aşırı kullanımını önlemeye yönelik eşzamanlı çağrı, örnek veya oturum sayısına yönelik sınırlar yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="b3187-129">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="b3187-130">Her öznitelik değeri her ulaşıldığında bir izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="b3187-130">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="b3187-131">İlk izleme uyarı olarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b3187-131">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3187-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3187-132">Example</span></span>  
 <span data-ttu-id="b3187-133">Aşağıdaki yapılandırma örneği, hizmetin maksimum eşzamanlı çağrı sayısını 2 ' ye ve en fazla eşzamanlı örnek sayısını 10 ' a sınırlandırdığından emin olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3187-133">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="b3187-134">Bu örneği çalıştırmanın ayrıntılı bir örneği için bkz. [azaltma](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="b3187-134">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3187-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3187-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="b3187-136">WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma</span><span class="sxs-lookup"><span data-stu-id="b3187-136">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
