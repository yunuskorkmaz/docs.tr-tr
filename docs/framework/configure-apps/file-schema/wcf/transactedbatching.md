---
title: '&lt;transactedBatching&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fc5d5cc77fcb227efd36106f1f8cb31efad24cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="1793e-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="1793e-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="1793e-103">İşlem toplu işlerin desteklenip desteklenmediğini belirtir alma işlemleri.</span><span class="sxs-lookup"><span data-stu-id="1793e-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="1793e-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1793e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1793e-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="1793e-105">\<behaviors></span></span>  
<span data-ttu-id="1793e-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1793e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1793e-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1793e-107">\<behavior></span></span>  
<span data-ttu-id="1793e-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="1793e-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1793e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1793e-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1793e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1793e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1793e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1793e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1793e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1793e-112">Attributes</span></span>  
  
|<span data-ttu-id="1793e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1793e-113">Attribute</span></span>|<span data-ttu-id="1793e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1793e-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="1793e-115">En fazla sayısını belirten bir tamsayı toplu hale işlemleri birlikte tek bir işlemle alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1793e-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="1793e-116">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="1793e-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1793e-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1793e-117">Child Elements</span></span>  
 <span data-ttu-id="1793e-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="1793e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1793e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1793e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1793e-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="1793e-120">Element</span></span>|<span data-ttu-id="1793e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1793e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1793e-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1793e-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1793e-123">Bir uç nokta davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1793e-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1793e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1793e-124">Remarks</span></span>  
 <span data-ttu-id="1793e-125">Birkaç toplu girişimleri toplu işlem ile yapılandırılmış bir aktarım işlemleri tek bir hareket halinde alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1793e-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="1793e-126">Bunu, bir işlem oluşturma ve bunu gerçekleştirmeden görece yüksek maliyet yaparak her alma işlemi engellenir.</span><span class="sxs-lookup"><span data-stu-id="1793e-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1793e-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1793e-127">Example</span></span>  
 <span data-ttu-id="1793e-128">Aşağıdaki örnek, bir hizmet yapılandırma dosyasında işlenen toplu işleme davranışını eklemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1793e-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
        </baseAddresses>  
      </host>  
  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />  
  
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
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
  
## <a name="see-also"></a><span data-ttu-id="1793e-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1793e-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
