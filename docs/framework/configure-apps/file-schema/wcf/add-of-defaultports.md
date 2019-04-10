---
title: <add> , <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 5200c8893a89488b72c2c71d1a3703bf2aad1235
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136753"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="60fde-102">\<Ekle >, \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="60fde-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="60fde-103">İstemci uygulamasının dinleyeceği bir varsayılan iletişim bitiş noktaları.</span><span class="sxs-lookup"><span data-stu-id="60fde-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="60fde-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="60fde-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="60fde-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="60fde-105">\<behaviors></span></span>  
<span data-ttu-id="60fde-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="60fde-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="60fde-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="60fde-107">\<behavior></span></span>  
<span data-ttu-id="60fde-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="60fde-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="60fde-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="60fde-109">\<defaultPorts></span></span>  
<span data-ttu-id="60fde-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="60fde-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60fde-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60fde-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60fde-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60fde-112">Attributes and Elements</span></span>  
 <span data-ttu-id="60fde-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60fde-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60fde-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60fde-114">Attributes</span></span>  
  
|<span data-ttu-id="60fde-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="60fde-115">Attribute</span></span>|<span data-ttu-id="60fde-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60fde-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60fde-117">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="60fde-117">port</span></span>|<span data-ttu-id="60fde-118">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="60fde-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="60fde-119">düzen</span><span class="sxs-lookup"><span data-stu-id="60fde-119">scheme</span></span>|<span data-ttu-id="60fde-120">Bir iletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="60fde-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60fde-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60fde-121">Child Elements</span></span>  
 <span data-ttu-id="60fde-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="60fde-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60fde-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60fde-123">Parent Elements</span></span>  
  
|<span data-ttu-id="60fde-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="60fde-124">Element</span></span>|<span data-ttu-id="60fde-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60fde-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60fde-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="60fde-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="60fde-127">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="60fde-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60fde-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60fde-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
