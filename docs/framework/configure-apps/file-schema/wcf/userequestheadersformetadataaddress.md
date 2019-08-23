---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 84310d4ae5e04e76e4484f4fc606c9896239c776
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940547"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="647e9-101">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="647e9-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="647e9-102">İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="647e9-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="647e9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="647e9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="647e9-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="647e9-104">\<behaviors></span></span>  
<span data-ttu-id="647e9-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="647e9-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="647e9-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="647e9-106">\<behavior></span></span>  
<span data-ttu-id="647e9-107">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="647e9-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="647e9-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="647e9-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="647e9-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="647e9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="647e9-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="647e9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="647e9-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="647e9-111">Attributes</span></span>  
 <span data-ttu-id="647e9-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="647e9-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="647e9-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="647e9-113">Child Elements</span></span>  
  
|<span data-ttu-id="647e9-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="647e9-114">Element</span></span>|<span data-ttu-id="647e9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="647e9-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="647e9-116">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="647e9-116">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="647e9-117">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="647e9-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="647e9-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="647e9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="647e9-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="647e9-119">Element</span></span>|<span data-ttu-id="647e9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="647e9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="647e9-121">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="647e9-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="647e9-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="647e9-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="647e9-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="647e9-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
