---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773941"
---
# <a name="client"></a><span data-ttu-id="c393e-101">\<client ></span><span class="sxs-lookup"><span data-stu-id="c393e-101">\<client></span></span>
<span data-ttu-id="c393e-102">@No__t_0 öğesi, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c393e-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>

<span data-ttu-id="c393e-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c393e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c393e-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c393e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c393e-105">&nbsp; &nbsp; &nbsp; &nbsp; **\<client >**</span><span class="sxs-lookup"><span data-stu-id="c393e-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c393e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c393e-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c393e-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c393e-107">Attributes and Elements</span></span>
 <span data-ttu-id="c393e-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c393e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c393e-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c393e-109">Attributes</span></span>
 <span data-ttu-id="c393e-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="c393e-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c393e-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c393e-111">Child Elements</span></span>

|<span data-ttu-id="c393e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="c393e-112">Element</span></span>|<span data-ttu-id="c393e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c393e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c393e-114">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="c393e-114">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="c393e-115">Bu istemcinin bağlanabileceği uç noktaları belirten bir uç nokta öğeleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="c393e-115">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[<span data-ttu-id="c393e-116">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="c393e-116">\<metadata></span></span>](metadata.md)|<span data-ttu-id="c393e-117">Meta verileri işlemeye yönelik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="c393e-117">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c393e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c393e-118">Parent Elements</span></span>

|<span data-ttu-id="c393e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c393e-119">Element</span></span>|<span data-ttu-id="c393e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c393e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c393e-121">\<system. serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c393e-121">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="c393e-122">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="c393e-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c393e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c393e-123">Remarks</span></span>
 <span data-ttu-id="c393e-124">@No__t_0 bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c393e-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="c393e-125">İstemci bölümünde listelenen her bir uç nokta kendi bağlamasını, davranışını ve sözleşmesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c393e-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="c393e-126">@No__t_0 ve `contract` özniteliklerinin birleşimiyle benzersiz şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c393e-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="c393e-127">İstemci kodu, istemcinin uyguladığı hizmet için bir uç noktaya bağlanmak üzere `name` belirtir.</span><span class="sxs-lookup"><span data-stu-id="c393e-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="c393e-128">@No__t_0 özniteliği atlanırsa, uç noktası uyguladığı sözleşmenin varsayılan uç noktası olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="c393e-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="c393e-129">Ayrıca, bu bölüm meta verileri işlemeye yönelik ayarları da belirtir.</span><span class="sxs-lookup"><span data-stu-id="c393e-129">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="c393e-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="c393e-130">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c393e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c393e-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="c393e-132">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c393e-132">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c393e-133">İstemciler</span><span class="sxs-lookup"><span data-stu-id="c393e-133">Clients</span></span>](../../../wcf/feature-details/clients.md)
