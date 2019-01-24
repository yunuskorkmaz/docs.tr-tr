---
title: '&lt;defaultPorts&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 8b7a4730af6690616058a91cf23bb39734d81abc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541722"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="a4c39-102">&lt;defaultPorts&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="a4c39-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="a4c39-103">İstemci uygulamasının dinleyeceği bir varsayılan iletişim bitiş noktaları.</span><span class="sxs-lookup"><span data-stu-id="a4c39-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="a4c39-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a4c39-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4c39-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a4c39-105">\<behaviors></span></span>  
<span data-ttu-id="a4c39-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a4c39-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a4c39-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a4c39-107">\<behavior></span></span>  
<span data-ttu-id="a4c39-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="a4c39-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="a4c39-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="a4c39-109">\<defaultPorts></span></span>  
<span data-ttu-id="a4c39-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="a4c39-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c39-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4c39-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4c39-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4c39-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a4c39-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4c39-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4c39-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4c39-114">Attributes</span></span>  
  
|<span data-ttu-id="a4c39-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4c39-115">Attribute</span></span>|<span data-ttu-id="a4c39-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4c39-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4c39-117">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="a4c39-117">port</span></span>|<span data-ttu-id="a4c39-118">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="a4c39-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="a4c39-119">düzen</span><span class="sxs-lookup"><span data-stu-id="a4c39-119">scheme</span></span>|<span data-ttu-id="a4c39-120">Bir iletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a4c39-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4c39-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4c39-121">Child Elements</span></span>  
 <span data-ttu-id="a4c39-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4c39-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4c39-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4c39-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a4c39-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4c39-124">Element</span></span>|<span data-ttu-id="a4c39-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4c39-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4c39-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="a4c39-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="a4c39-127">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a4c39-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4c39-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4c39-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
