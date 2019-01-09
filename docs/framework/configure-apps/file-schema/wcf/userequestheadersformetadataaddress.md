---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: bcbf1c633e0796c6056759dfbb55014838e0e293
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151416"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="1b6c2-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="1b6c2-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="1b6c2-103">İstek iletisi başlıklarından meta verisi adresi bilgilerine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b6c2-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="1b6c2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1b6c2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1b6c2-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="1b6c2-105">\<behaviors></span></span>  
<span data-ttu-id="1b6c2-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1b6c2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1b6c2-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1b6c2-107">\<behavior></span></span>  
<span data-ttu-id="1b6c2-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="1b6c2-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b6c2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b6c2-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b6c2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b6c2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1b6c2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b6c2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b6c2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b6c2-112">Attributes</span></span>  
 <span data-ttu-id="1b6c2-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="1b6c2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b6c2-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b6c2-114">Child Elements</span></span>  
  
|<span data-ttu-id="1b6c2-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b6c2-115">Element</span></span>|<span data-ttu-id="1b6c2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b6c2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b6c2-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="1b6c2-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="1b6c2-118">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1b6c2-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b6c2-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b6c2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1b6c2-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b6c2-120">Element</span></span>|<span data-ttu-id="1b6c2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b6c2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b6c2-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1b6c2-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1b6c2-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b6c2-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b6c2-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b6c2-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
