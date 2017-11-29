---
title: "&lt;İstemci&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67f91f4462fc8c11b1769d5805a4ad1407385a50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientgt"></a><span data-ttu-id="a279d-102">&lt;İstemci&gt;</span><span class="sxs-lookup"><span data-stu-id="a279d-102">&lt;client&gt;</span></span>
<span data-ttu-id="a279d-103">`client` Öğe, bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a279d-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="a279d-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a279d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a279d-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="a279d-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a279d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a279d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a279d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a279d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a279d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a279d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a279d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a279d-109">Attributes</span></span>  
 <span data-ttu-id="a279d-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="a279d-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a279d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a279d-111">Child Elements</span></span>  
  
|<span data-ttu-id="a279d-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="a279d-112">Element</span></span>|<span data-ttu-id="a279d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a279d-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a279d-114">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="a279d-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="a279d-115">Bu istemcinin bağlanabileceği uç noktaları belirttiğiniz bitiş noktası öğe koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a279d-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="a279d-116">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="a279d-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="a279d-117">İşleme meta veri ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a279d-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a279d-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a279d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a279d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="a279d-119">Element</span></span>|<span data-ttu-id="a279d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a279d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a279d-121">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a279d-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="a279d-122">Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="a279d-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a279d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a279d-123">Remarks</span></span>  
 <span data-ttu-id="a279d-124">`client` Bölümü, bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a279d-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="a279d-125">İstemci bölümünde listelenen her endpoint kendi bağlama davranışı ve sözleşme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a279d-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="a279d-126">Birleşimiyle benzersiz şekilde tanımlanır `name` ve `contract` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a279d-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="a279d-127">İstemci kodu belirtir `name` istemci uygulayan hizmeti için bir uç nokta bağlanmak için.</span><span class="sxs-lookup"><span data-stu-id="a279d-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="a279d-128">Varsa `name` özniteliği atlanırsa, uç nokta sözleşme için varsayılan uç noktası, Implements görür.</span><span class="sxs-lookup"><span data-stu-id="a279d-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="a279d-129">Ayrıca, bu bölümde ayrıca işleme meta veri ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a279d-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a279d-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a279d-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a279d-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a279d-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="a279d-132">WCF istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="a279d-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="a279d-133">İstemciler</span><span class="sxs-lookup"><span data-stu-id="a279d-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
