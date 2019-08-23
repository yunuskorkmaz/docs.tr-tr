---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 12369f1053638583a3864fab396869d0e7045732
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918672"
---
# <a name="transactedbatching"></a><span data-ttu-id="dbaab-101">\<Transactedtoplu işlem ></span><span class="sxs-lookup"><span data-stu-id="dbaab-101">\<transactedBatching></span></span>

<span data-ttu-id="dbaab-102">İşlem toplu işleminin alma işlemleri için desteklenip desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbaab-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="dbaab-103">\<sistemin. ServiceModel > </span><span class="sxs-lookup"><span data-stu-id="dbaab-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="dbaab-104">\<davranışlar > </span><span class="sxs-lookup"><span data-stu-id="dbaab-104">\<behaviors></span></span>\
<span data-ttu-id="dbaab-105">\<Endpointdavranışlar > </span><span class="sxs-lookup"><span data-stu-id="dbaab-105">\<endpointBehaviors></span></span>\
<span data-ttu-id="dbaab-106">\<davranış > </span><span class="sxs-lookup"><span data-stu-id="dbaab-106">\<behavior></span></span>\
<span data-ttu-id="dbaab-107">\<Transactedtoplu işlem ></span><span class="sxs-lookup"><span data-stu-id="dbaab-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="dbaab-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbaab-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dbaab-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbaab-109">Attributes and Elements</span></span>

<span data-ttu-id="dbaab-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbaab-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="dbaab-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbaab-111">Attributes</span></span>

|<span data-ttu-id="dbaab-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbaab-112">Attribute</span></span>|<span data-ttu-id="dbaab-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbaab-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="dbaab-114">Tek bir işlemde birlikte toplu olarak oluşturulabilecek en fazla alma işlemi sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="dbaab-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="dbaab-115">Varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="dbaab-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="dbaab-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbaab-116">Child Elements</span></span>

<span data-ttu-id="dbaab-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="dbaab-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dbaab-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbaab-118">Parent Elements</span></span>

|<span data-ttu-id="dbaab-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbaab-119">Element</span></span>|<span data-ttu-id="dbaab-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbaab-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dbaab-121">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="dbaab-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dbaab-122">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbaab-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dbaab-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbaab-123">Remarks</span></span>

<span data-ttu-id="dbaab-124">İşlem toplu işlemi ile yapılandırılan bir aktarım, birkaç alma işlemini tek bir işlemde toplu olarak dener.</span><span class="sxs-lookup"><span data-stu-id="dbaab-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="dbaab-125">Bu şekilde, bir işlem oluşturmanın ve her alma işleminde gerçekleştiren görece yüksek maliyetli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="dbaab-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="dbaab-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbaab-126">Example</span></span>

<span data-ttu-id="dbaab-127">Aşağıdaki örnek, bir yapılandırma dosyasındaki bir hizmete işlenen toplu işlem davranışının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbaab-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dbaab-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbaab-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
