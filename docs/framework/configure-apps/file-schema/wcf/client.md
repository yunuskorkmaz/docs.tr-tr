---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 2e0352efdd5b709984338fe4484b120bddb7d545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704303"
---
# <a name="client"></a><span data-ttu-id="bb751-101">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="bb751-101">\<client></span></span>
<span data-ttu-id="bb751-102">`client` Öğesi, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bb751-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="bb751-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bb751-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bb751-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="bb751-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb751-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb751-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb751-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb751-106">Attributes and Elements</span></span>  
 <span data-ttu-id="bb751-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb751-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb751-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb751-108">Attributes</span></span>  
 <span data-ttu-id="bb751-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="bb751-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bb751-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb751-110">Child Elements</span></span>  
  
|<span data-ttu-id="bb751-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb751-111">Element</span></span>|<span data-ttu-id="bb751-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb751-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb751-113">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="bb751-113">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="bb751-114">Bu istemcinin bağlanabileceği uç noktaları belirttiğiniz bitiş noktası öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="bb751-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="bb751-115">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="bb751-115">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="bb751-116">İşleme meta veri ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="bb751-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb751-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb751-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bb751-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb751-118">Element</span></span>|<span data-ttu-id="bb751-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb751-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb751-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bb751-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="bb751-121">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="bb751-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb751-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb751-122">Remarks</span></span>  
 <span data-ttu-id="bb751-123">`client` Bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bb751-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="bb751-124">Kendi bağlama davranışı ve sözleşme istemci bölümünde listelenen her bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bb751-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="bb751-125">Birleşimiyle benzersiz şekilde tanımlanır `name` ve `contract` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="bb751-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="bb751-126">İstemci kodu belirtir `name` uygulayan istemci hizmeti için bir uç noktaya bağlanmak için.</span><span class="sxs-lookup"><span data-stu-id="bb751-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="bb751-127">Varsa `name` özniteliği atlanırsa, uç nokta sözleşmesinin varsayılan uç nokta, uygular işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="bb751-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="bb751-128">Ayrıca, bu bölümde Ayrıca işlem meta veri ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb751-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb751-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb751-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb751-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb751-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="bb751-131">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="bb751-131">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="bb751-132">İstemciler</span><span class="sxs-lookup"><span data-stu-id="bb751-132">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
