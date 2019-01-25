---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 6c03057fca23b037702c702b9a574045ebb302b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656644"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="32c21-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="32c21-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="32c21-103">İstek iletisi başlıklarından meta verisi adresi bilgilerine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="32c21-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="32c21-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32c21-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32c21-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="32c21-105">\<behaviors></span></span>  
<span data-ttu-id="32c21-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="32c21-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="32c21-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="32c21-107">\<behavior></span></span>  
<span data-ttu-id="32c21-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="32c21-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32c21-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32c21-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32c21-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32c21-110">Attributes and Elements</span></span>  
 <span data-ttu-id="32c21-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32c21-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32c21-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32c21-112">Attributes</span></span>  
 <span data-ttu-id="32c21-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="32c21-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="32c21-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32c21-114">Child Elements</span></span>  
  
|<span data-ttu-id="32c21-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="32c21-115">Element</span></span>|<span data-ttu-id="32c21-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32c21-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32c21-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="32c21-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="32c21-118">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="32c21-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32c21-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32c21-119">Parent Elements</span></span>  
  
|<span data-ttu-id="32c21-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="32c21-120">Element</span></span>|<span data-ttu-id="32c21-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32c21-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32c21-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="32c21-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="32c21-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="32c21-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32c21-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32c21-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
