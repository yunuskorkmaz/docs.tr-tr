---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 4d7fdfb1cccb14f03d11864f1939cb578c79880a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130630"
---
# <a name="defaultports"></a><span data-ttu-id="05c48-101">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="05c48-101">\<defaultPorts></span></span>
<span data-ttu-id="05c48-102">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="05c48-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="05c48-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="05c48-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="05c48-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="05c48-104">\<behaviors></span></span>  
<span data-ttu-id="05c48-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="05c48-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="05c48-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="05c48-106">\<behavior></span></span>  
<span data-ttu-id="05c48-107">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="05c48-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="05c48-108">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="05c48-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c48-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05c48-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05c48-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c48-110">Attributes and Elements</span></span>  
 <span data-ttu-id="05c48-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05c48-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05c48-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="05c48-112">Attributes</span></span>  
 <span data-ttu-id="05c48-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="05c48-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05c48-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c48-114">Child Elements</span></span>  
  
|<span data-ttu-id="05c48-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="05c48-115">Element</span></span>|<span data-ttu-id="05c48-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05c48-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05c48-117">\<Ekle >, \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="05c48-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="05c48-118">İstemci uygulamasının dinleyeceği bir varsayılan iletişim bitiş noktaları.</span><span class="sxs-lookup"><span data-stu-id="05c48-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05c48-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="05c48-119">Parent Elements</span></span>  
  
|<span data-ttu-id="05c48-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="05c48-120">Element</span></span>|<span data-ttu-id="05c48-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05c48-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05c48-122">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="05c48-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="05c48-123">Varsayılan bağlantı noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="05c48-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05c48-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05c48-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
