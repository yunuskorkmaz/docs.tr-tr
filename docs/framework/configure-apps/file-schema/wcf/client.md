---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7dce5984882e48c3e62efc44ef00b6256d9eb64e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919534"
---
# <a name="client"></a><span data-ttu-id="10f54-101">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="10f54-101">\<client></span></span>
<span data-ttu-id="10f54-102">Öğesi `client` , bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10f54-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="10f54-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="10f54-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="10f54-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="10f54-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f54-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10f54-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10f54-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10f54-106">Attributes and Elements</span></span>  
 <span data-ttu-id="10f54-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10f54-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10f54-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10f54-108">Attributes</span></span>  
 <span data-ttu-id="10f54-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="10f54-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10f54-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10f54-110">Child Elements</span></span>  
  
|<span data-ttu-id="10f54-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="10f54-111">Element</span></span>|<span data-ttu-id="10f54-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10f54-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10f54-113">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="10f54-113">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="10f54-114">Bu istemcinin bağlanabileceği uç noktaları belirten bir uç nokta öğeleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="10f54-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="10f54-115">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="10f54-115">\<metadata></span></span>](metadata.md)|<span data-ttu-id="10f54-116">Meta verileri işlemeye yönelik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="10f54-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10f54-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10f54-117">Parent Elements</span></span>  
  
|<span data-ttu-id="10f54-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="10f54-118">Element</span></span>|<span data-ttu-id="10f54-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10f54-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10f54-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="10f54-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="10f54-121">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="10f54-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10f54-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10f54-122">Remarks</span></span>  
 <span data-ttu-id="10f54-123">Bölümü `client` , bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10f54-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="10f54-124">İstemci bölümünde listelenen her bir uç nokta kendi bağlamasını, davranışını ve sözleşmesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10f54-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="10f54-125">`name` Ve`contract` özniteliklerinin birleşimiyle benzersiz şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="10f54-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="10f54-126">İstemci kodu, `name` istemcinin uyguladığı hizmet için bir uç noktaya bağlanmak üzere öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10f54-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="10f54-127">`name` Özniteliği atlanırsa, uç noktası uyguladığı sözleşmenin varsayılan uç noktası olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="10f54-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="10f54-128">Ayrıca, bu bölüm meta verileri işlemeye yönelik ayarları da belirtir.</span><span class="sxs-lookup"><span data-stu-id="10f54-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f54-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="10f54-129">Example</span></span>  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a><span data-ttu-id="10f54-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10f54-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="10f54-131">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="10f54-131">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="10f54-132">İstemciler</span><span class="sxs-lookup"><span data-stu-id="10f54-132">Clients</span></span>](../../../wcf/feature-details/clients.md)
