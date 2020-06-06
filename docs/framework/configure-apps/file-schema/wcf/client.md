---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "72773941"
---
# \<client>
<span data-ttu-id="01911-101">`client`Öğesi, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01911-101">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="01911-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01911-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="01911-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="01911-103">Attributes and Elements</span></span>
 <span data-ttu-id="01911-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="01911-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="01911-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="01911-105">Attributes</span></span>
 <span data-ttu-id="01911-106">Yok</span><span class="sxs-lookup"><span data-stu-id="01911-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="01911-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="01911-107">Child Elements</span></span>

|<span data-ttu-id="01911-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="01911-108">Element</span></span>|<span data-ttu-id="01911-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01911-109">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="01911-110">Bu istemcinin bağlanabileceği uç noktaları belirten bir uç nokta öğeleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="01911-110">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="01911-111">Meta verileri işlemeye yönelik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="01911-111">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="01911-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="01911-112">Parent Elements</span></span>

|<span data-ttu-id="01911-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="01911-113">Element</span></span>|<span data-ttu-id="01911-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01911-114">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="01911-115">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="01911-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="01911-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01911-116">Remarks</span></span>
 <span data-ttu-id="01911-117">`client`Bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01911-117">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="01911-118">İstemci bölümünde listelenen her bir uç nokta kendi bağlamasını, davranışını ve sözleşmesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01911-118">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="01911-119">Ve özniteliklerinin birleşimiyle benzersiz şekilde tanımlanır `name` `contract` .</span><span class="sxs-lookup"><span data-stu-id="01911-119">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="01911-120">İstemci kodu, `name` istemcinin uyguladığı hizmet için bir uç noktaya bağlanmak üzere öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="01911-120">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="01911-121">`name`Özniteliği atlanırsa, uç noktası uyguladığı sözleşmenin varsayılan uç noktası olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="01911-121">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="01911-122">Ayrıca, bu bölüm meta verileri işlemeye yönelik ayarları da belirtir.</span><span class="sxs-lookup"><span data-stu-id="01911-122">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="01911-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="01911-123">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="01911-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01911-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="01911-125">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="01911-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="01911-126">İstemciler</span><span class="sxs-lookup"><span data-stu-id="01911-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
