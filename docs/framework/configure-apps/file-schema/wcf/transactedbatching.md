---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399409"
---
# <a name="transactedbatching"></a><span data-ttu-id="3e418-101">\<Transactedtoplu işlem ></span><span class="sxs-lookup"><span data-stu-id="3e418-101">\<transactedBatching></span></span>

<span data-ttu-id="3e418-102">İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e418-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="3e418-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e418-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e418-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3e418-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3e418-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3e418-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="3e418-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3e418-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="3e418-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3e418-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="3e418-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Transactedtoplu işlem >**</span><span class="sxs-lookup"><span data-stu-id="3e418-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="3e418-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e418-109">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3e418-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e418-110">Attributes and Elements</span></span>

<span data-ttu-id="3e418-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e418-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3e418-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e418-112">Attributes</span></span>

|<span data-ttu-id="3e418-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e418-113">Attribute</span></span>|<span data-ttu-id="3e418-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e418-114">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="3e418-115">Tek bir işlemde birlikte toplu olarak oluşturulabilecek en fazla alma işlemi sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="3e418-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="3e418-116">Varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="3e418-116">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3e418-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e418-117">Child Elements</span></span>

<span data-ttu-id="3e418-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e418-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3e418-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e418-119">Parent Elements</span></span>

|<span data-ttu-id="3e418-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e418-120">Element</span></span>|<span data-ttu-id="3e418-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e418-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3e418-122">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="3e418-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3e418-123">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e418-123">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3e418-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e418-124">Remarks</span></span>

<span data-ttu-id="3e418-125">İşlem toplu işlemi ile yapılandırılan bir aktarım, birkaç alma işlemini tek bir işlemde toplu olarak dener.</span><span class="sxs-lookup"><span data-stu-id="3e418-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="3e418-126">Bu şekilde, bir işlem oluşturmanın ve her alma işleminde gerçekleştiren görece yüksek maliyetli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="3e418-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="3e418-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e418-127">Example</span></span>

<span data-ttu-id="3e418-128">Aşağıdaki örnek, bir yapılandırma dosyasındaki bir hizmete işlenen toplu işlem davranışının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e418-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3e418-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e418-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
