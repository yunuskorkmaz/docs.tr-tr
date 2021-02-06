---
description: 'Hakkında daha fazla bilgi edinin: <client>'
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 9765460602738f49963ea521b3f00ed7c63cc568
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638866"
---
# \<client>

<span data-ttu-id="51e83-102">`client`Öğesi, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51e83-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="51e83-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="51e83-103">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="51e83-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="51e83-104">Attributes and Elements</span></span>

 <span data-ttu-id="51e83-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="51e83-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="51e83-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="51e83-106">Attributes</span></span>

 <span data-ttu-id="51e83-107">Yok</span><span class="sxs-lookup"><span data-stu-id="51e83-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="51e83-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="51e83-108">Child Elements</span></span>

|<span data-ttu-id="51e83-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="51e83-109">Element</span></span>|<span data-ttu-id="51e83-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51e83-110">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="51e83-111">Bu istemcinin bağlanabileceği uç noktaları belirten bir uç nokta öğeleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="51e83-111">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="51e83-112">Meta verileri işlemeye yönelik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="51e83-112">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="51e83-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="51e83-113">Parent Elements</span></span>

|<span data-ttu-id="51e83-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="51e83-114">Element</span></span>|<span data-ttu-id="51e83-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51e83-115">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="51e83-116">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="51e83-116">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="51e83-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51e83-117">Remarks</span></span>

 <span data-ttu-id="51e83-118">`client`Bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51e83-118">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="51e83-119">İstemci bölümünde listelenen her bir uç nokta kendi bağlamasını, davranışını ve sözleşmesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51e83-119">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="51e83-120">Ve özniteliklerinin birleşimiyle benzersiz şekilde tanımlanır `name` `contract` .</span><span class="sxs-lookup"><span data-stu-id="51e83-120">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="51e83-121">İstemci kodu, `name` istemcinin uyguladığı hizmet için bir uç noktaya bağlanmak üzere öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="51e83-121">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="51e83-122">`name`Özniteliği atlanırsa, uç noktası uyguladığı sözleşmenin varsayılan uç noktası olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="51e83-122">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="51e83-123">Ayrıca, bu bölüm meta verileri işlemeye yönelik ayarları da belirtir.</span><span class="sxs-lookup"><span data-stu-id="51e83-123">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="51e83-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="51e83-124">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="51e83-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51e83-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="51e83-126">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="51e83-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="51e83-127">İstemciler</span><span class="sxs-lookup"><span data-stu-id="51e83-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
