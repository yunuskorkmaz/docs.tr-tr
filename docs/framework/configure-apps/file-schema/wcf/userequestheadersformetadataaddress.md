---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 969461d0e5bdc9f8c49b7a019a6000af5af77eec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121192"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="3e090-101">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="3e090-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="3e090-102">İstek iletisi başlıklarından meta verisi adresi bilgilerine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e090-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="3e090-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3e090-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3e090-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="3e090-104">\<behaviors></span></span>  
<span data-ttu-id="3e090-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3e090-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="3e090-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="3e090-106">\<behavior></span></span>  
<span data-ttu-id="3e090-107">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="3e090-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e090-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e090-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e090-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e090-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3e090-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e090-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e090-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e090-111">Attributes</span></span>  
 <span data-ttu-id="3e090-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="3e090-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e090-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e090-113">Child Elements</span></span>  
  
|<span data-ttu-id="3e090-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e090-114">Element</span></span>|<span data-ttu-id="3e090-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e090-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e090-116">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="3e090-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="3e090-117">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3e090-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e090-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e090-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3e090-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e090-119">Element</span></span>|<span data-ttu-id="3e090-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e090-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e090-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="3e090-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3e090-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e090-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e090-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e090-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
