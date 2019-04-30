---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 43415d9eac5e61f42006aecb3248dec9811eb3e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758138"
---
# <a name="transactedbatching"></a><span data-ttu-id="903c2-101">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="903c2-101">\<transactedBatching></span></span>

<span data-ttu-id="903c2-102">Hareket işlem grubu oluşturma için desteklenip desteklenmediğini belirtir alma işlemleri.</span><span class="sxs-lookup"><span data-stu-id="903c2-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="903c2-103">\<sistemi. ServiceModel > \\</span><span class="sxs-lookup"><span data-stu-id="903c2-103">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="903c2-104">\<davranışlar > \\</span><span class="sxs-lookup"><span data-stu-id="903c2-104">\<behaviors>\\</span></span>
<span data-ttu-id="903c2-105">\<endpointBehaviors>\\</span><span class="sxs-lookup"><span data-stu-id="903c2-105">\<endpointBehaviors>\\</span></span>
<span data-ttu-id="903c2-106">\<davranış > \\</span><span class="sxs-lookup"><span data-stu-id="903c2-106">\<behavior>\\</span></span>
<span data-ttu-id="903c2-107">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="903c2-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="903c2-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="903c2-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="903c2-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="903c2-109">Attributes and Elements</span></span>

<span data-ttu-id="903c2-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="903c2-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="903c2-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="903c2-111">Attributes</span></span>

|<span data-ttu-id="903c2-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="903c2-112">Attribute</span></span>|<span data-ttu-id="903c2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="903c2-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="903c2-114">En fazla sayısını belirten bir tamsayı gruplanabilecek operations birlikte tek bir işlemle alırsınız.</span><span class="sxs-lookup"><span data-stu-id="903c2-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="903c2-115">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="903c2-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="903c2-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="903c2-116">Child Elements</span></span>

<span data-ttu-id="903c2-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="903c2-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="903c2-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="903c2-118">Parent Elements</span></span>

|<span data-ttu-id="903c2-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="903c2-119">Element</span></span>|<span data-ttu-id="903c2-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="903c2-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="903c2-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="903c2-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="903c2-122">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="903c2-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="903c2-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="903c2-123">Remarks</span></span>

<span data-ttu-id="903c2-124">Birkaç batch girişimleri toplu işlem ile yapılandırılmış bir taşıma işlemlerini tek bir işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="903c2-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="903c2-125">Bunu, bir işlem oluşturmak ve bunu yapmadan görece yüksek maliyeti yaparak her alma işlemi engellenir.</span><span class="sxs-lookup"><span data-stu-id="903c2-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="903c2-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="903c2-126">Example</span></span>

<span data-ttu-id="903c2-127">Aşağıdaki örnek, bir hizmet yapılandırma dosyasında işlenen toplu işleme davranışını eklemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="903c2-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="903c2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="903c2-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
