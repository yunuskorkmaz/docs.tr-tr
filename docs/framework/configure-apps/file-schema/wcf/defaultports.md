---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 595970a56e05c4fc1c9b2c0eb669ec3b3a120fe1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262401"
---
# <a name="defaultports"></a><span data-ttu-id="ef935-101">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="ef935-101">\<defaultPorts></span></span>
<span data-ttu-id="ef935-102">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ef935-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="ef935-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef935-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef935-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="ef935-104">\<behaviors></span></span>  
<span data-ttu-id="ef935-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ef935-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ef935-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="ef935-106">\<behavior></span></span>  
<span data-ttu-id="ef935-107">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="ef935-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="ef935-108">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="ef935-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef935-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef935-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef935-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef935-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ef935-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef935-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef935-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ef935-112">Attributes</span></span>  
 <span data-ttu-id="ef935-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="ef935-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ef935-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef935-114">Child Elements</span></span>  
  
|<span data-ttu-id="ef935-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef935-115">Element</span></span>|<span data-ttu-id="ef935-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef935-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef935-117">\<Ekle >, \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="ef935-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="ef935-118">İstemci uygulamasının dinleyeceği bir varsayılan iletişim bitiş noktaları.</span><span class="sxs-lookup"><span data-stu-id="ef935-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef935-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef935-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ef935-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef935-120">Element</span></span>|<span data-ttu-id="ef935-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef935-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef935-122">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="ef935-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="ef935-123">Varsayılan bağlantı noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="ef935-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef935-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef935-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
