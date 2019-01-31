---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 842f989ab1f2f0b9e8fe08e8fd729f983e846ffc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261574"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="130ed-101">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="130ed-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="130ed-102">İstek iletisi başlıklarından meta verisi adresi bilgilerine alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="130ed-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="130ed-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="130ed-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="130ed-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="130ed-104">\<behaviors></span></span>  
<span data-ttu-id="130ed-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="130ed-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="130ed-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="130ed-106">\<behavior></span></span>  
<span data-ttu-id="130ed-107">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="130ed-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="130ed-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="130ed-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="130ed-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="130ed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="130ed-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="130ed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="130ed-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="130ed-111">Attributes</span></span>  
 <span data-ttu-id="130ed-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="130ed-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="130ed-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="130ed-113">Child Elements</span></span>  
  
|<span data-ttu-id="130ed-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="130ed-114">Element</span></span>|<span data-ttu-id="130ed-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="130ed-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="130ed-116">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="130ed-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="130ed-117">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="130ed-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="130ed-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="130ed-118">Parent Elements</span></span>  
  
|<span data-ttu-id="130ed-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="130ed-119">Element</span></span>|<span data-ttu-id="130ed-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="130ed-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="130ed-121">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="130ed-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="130ed-122">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="130ed-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="130ed-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="130ed-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
