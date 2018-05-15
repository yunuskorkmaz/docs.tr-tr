---
title: '&lt;İstemci&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: b8a006d3dee4149569b3f5b573d9d765504b0d65
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclientgt"></a><span data-ttu-id="0e55a-102">&lt;İstemci&gt;</span><span class="sxs-lookup"><span data-stu-id="0e55a-102">&lt;client&gt;</span></span>
<span data-ttu-id="0e55a-103">`client` Öğe, bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e55a-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="0e55a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0e55a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0e55a-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="0e55a-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e55a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e55a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e55a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e55a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0e55a-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e55a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e55a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e55a-109">Attributes</span></span>  
 <span data-ttu-id="0e55a-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e55a-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0e55a-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e55a-111">Child Elements</span></span>  
  
|<span data-ttu-id="0e55a-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e55a-112">Element</span></span>|<span data-ttu-id="0e55a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e55a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e55a-114">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="0e55a-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="0e55a-115">Bu istemcinin bağlanabileceği uç noktaları belirttiğiniz bitiş noktası öğe koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0e55a-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="0e55a-116">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="0e55a-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="0e55a-117">İşleme meta veri ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="0e55a-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e55a-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e55a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0e55a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e55a-119">Element</span></span>|<span data-ttu-id="0e55a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e55a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e55a-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0e55a-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="0e55a-122">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="0e55a-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e55a-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e55a-123">Remarks</span></span>  
 <span data-ttu-id="0e55a-124">`client` Bölümü, bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e55a-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="0e55a-125">İstemci bölümünde listelenen her endpoint kendi bağlama davranışı ve sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e55a-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="0e55a-126">Birleşimiyle benzersiz şekilde tanımlanır `name` ve `contract` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="0e55a-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="0e55a-127">İstemci kodu belirtir `name` istemci uygulayan hizmeti için bir uç nokta bağlanmak için.</span><span class="sxs-lookup"><span data-stu-id="0e55a-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="0e55a-128">Varsa `name` özniteliği atlanırsa, uç nokta sözleşme için varsayılan uç noktası, Implements görür.</span><span class="sxs-lookup"><span data-stu-id="0e55a-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="0e55a-129">Ayrıca, bu bölümde ayrıca işleme meta veri ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e55a-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e55a-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e55a-130">Example</span></span>  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e55a-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e55a-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="0e55a-132">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="0e55a-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="0e55a-133">İstemciler</span><span class="sxs-lookup"><span data-stu-id="0e55a-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
