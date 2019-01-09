---
title: '&lt;İstemci&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 24defe7e01603f1b1be3023d07854091335d6c60
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148649"
---
# <a name="ltclientgt"></a><span data-ttu-id="5f2f3-102">&lt;İstemci&gt;</span><span class="sxs-lookup"><span data-stu-id="5f2f3-102">&lt;client&gt;</span></span>
<span data-ttu-id="5f2f3-103">`client` Öğesi, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="5f2f3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5f2f3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5f2f3-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="5f2f3-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f2f3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f2f3-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f2f3-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f2f3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5f2f3-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f2f3-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5f2f3-109">Attributes</span></span>  
 <span data-ttu-id="5f2f3-110">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="5f2f3-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f2f3-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f2f3-111">Child Elements</span></span>  
  
|<span data-ttu-id="5f2f3-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f2f3-112">Element</span></span>|<span data-ttu-id="5f2f3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f2f3-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f2f3-114">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="5f2f3-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="5f2f3-115">Bu istemcinin bağlanabileceği uç noktaları belirttiğiniz bitiş noktası öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="5f2f3-116">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="5f2f3-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="5f2f3-117">İşleme meta veri ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f2f3-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5f2f3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5f2f3-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5f2f3-119">Element</span></span>|<span data-ttu-id="5f2f3-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f2f3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f2f3-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5f2f3-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="5f2f3-122">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f2f3-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f2f3-123">Remarks</span></span>  
 <span data-ttu-id="5f2f3-124">`client` Bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="5f2f3-125">Kendi bağlama davranışı ve sözleşme istemci bölümünde listelenen her bir uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="5f2f3-126">Birleşimiyle benzersiz şekilde tanımlanır `name` ve `contract` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="5f2f3-127">İstemci kodu belirtir `name` uygulayan istemci hizmeti için bir uç noktaya bağlanmak için.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="5f2f3-128">Varsa `name` özniteliği atlanırsa, uç nokta sözleşmesinin varsayılan uç nokta, uygular işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="5f2f3-129">Ayrıca, bu bölümde Ayrıca işlem meta veri ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f2f3-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f2f3-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f2f3-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f2f3-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="5f2f3-132">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="5f2f3-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="5f2f3-133">İstemciler</span><span class="sxs-lookup"><span data-stu-id="5f2f3-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
