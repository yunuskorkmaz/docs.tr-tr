---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399409"
---
# \<transactedBatching>

<span data-ttu-id="22870-101">İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="22870-101">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="22870-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22870-102">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22870-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="22870-103">Attributes and Elements</span></span>

<span data-ttu-id="22870-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22870-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="22870-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="22870-105">Attributes</span></span>

|<span data-ttu-id="22870-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="22870-106">Attribute</span></span>|<span data-ttu-id="22870-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22870-107">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="22870-108">Tek bir işlemde birlikte toplu olarak oluşturulabilecek en fazla alma işlemi sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="22870-108">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="22870-109">Varsayılan değer, 0'dur.</span><span class="sxs-lookup"><span data-stu-id="22870-109">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="22870-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="22870-110">Child Elements</span></span>

<span data-ttu-id="22870-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="22870-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22870-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="22870-112">Parent Elements</span></span>

|<span data-ttu-id="22870-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="22870-113">Element</span></span>|<span data-ttu-id="22870-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22870-114">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="22870-115">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="22870-115">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="22870-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22870-116">Remarks</span></span>

<span data-ttu-id="22870-117">İşlem toplu işlemi ile yapılandırılan bir aktarım, birkaç alma işlemini tek bir işlemde toplu olarak dener.</span><span class="sxs-lookup"><span data-stu-id="22870-117">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="22870-118">Bu şekilde, bir işlem oluşturmanın ve her alma işleminde gerçekleştiren görece yüksek maliyetli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="22870-118">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="22870-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="22870-119">Example</span></span>

<span data-ttu-id="22870-120">Aşağıdaki örnek, bir yapılandırma dosyasındaki bir hizmete işlenen toplu işlem davranışının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="22870-120">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="22870-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22870-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
