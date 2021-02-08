---
description: 'Hakkında daha fazla bilgi edinin: <transactedBatching>'
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 9a57226c3a2f2b026c69324e37b00e87fd3dd693
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773699"
---
# \<transactedBatching>

<span data-ttu-id="20fd4-102">İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="20fd4-102">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="20fd4-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="20fd4-103">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20fd4-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20fd4-104">Attributes and Elements</span></span>

<span data-ttu-id="20fd4-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20fd4-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="20fd4-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20fd4-106">Attributes</span></span>

|<span data-ttu-id="20fd4-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20fd4-107">Attribute</span></span>|<span data-ttu-id="20fd4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20fd4-108">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="20fd4-109">Tek bir işlemde birlikte toplu olarak oluşturulabilecek en fazla alma işlemi sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="20fd4-109">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="20fd4-110">Varsayılan değer, 0'dur.</span><span class="sxs-lookup"><span data-stu-id="20fd4-110">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="20fd4-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20fd4-111">Child Elements</span></span>

<span data-ttu-id="20fd4-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="20fd4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20fd4-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20fd4-113">Parent Elements</span></span>

|<span data-ttu-id="20fd4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="20fd4-114">Element</span></span>|<span data-ttu-id="20fd4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20fd4-115">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="20fd4-116">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="20fd4-116">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20fd4-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20fd4-117">Remarks</span></span>

<span data-ttu-id="20fd4-118">İşlem toplu işlemi ile yapılandırılan bir aktarım, birkaç alma işlemini tek bir işlemde toplu olarak dener.</span><span class="sxs-lookup"><span data-stu-id="20fd4-118">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="20fd4-119">Bu şekilde, bir işlem oluşturmanın ve her alma işleminde gerçekleştiren görece yüksek maliyetli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="20fd4-119">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="20fd4-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="20fd4-120">Example</span></span>

<span data-ttu-id="20fd4-121">Aşağıdaki örnek, bir yapılandırma dosyasındaki bir hizmete işlenen toplu işlem davranışının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20fd4-121">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

## <a name="see-also"></a><span data-ttu-id="20fd4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20fd4-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
