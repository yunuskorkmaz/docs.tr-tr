---
title: '&lt;defaultPorts&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 28ddc98bd66c1f74f857448aa710d3998ddbd3dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="067ea-102">&lt;defaultPorts&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="067ea-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="067ea-103">İstemci uygulaması dinlediği bir varsayılan iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="067ea-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="067ea-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="067ea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="067ea-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="067ea-105">\<behaviors></span></span>  
<span data-ttu-id="067ea-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="067ea-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="067ea-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="067ea-107">\<behavior></span></span>  
<span data-ttu-id="067ea-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="067ea-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="067ea-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="067ea-109">\<defaultPorts></span></span>  
<span data-ttu-id="067ea-110">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="067ea-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="067ea-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="067ea-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="067ea-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="067ea-112">Attributes and Elements</span></span>  
 <span data-ttu-id="067ea-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="067ea-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="067ea-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="067ea-114">Attributes</span></span>  
  
|<span data-ttu-id="067ea-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="067ea-115">Attribute</span></span>|<span data-ttu-id="067ea-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="067ea-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="067ea-117">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="067ea-117">port</span></span>|<span data-ttu-id="067ea-118">Varsayılan iletişim bağlantı noktası numarası belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="067ea-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="067ea-119">düzen</span><span class="sxs-lookup"><span data-stu-id="067ea-119">scheme</span></span>|<span data-ttu-id="067ea-120">Bir iletişim bağlantı noktası ile ilişkili protokolü ayarları grubu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="067ea-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="067ea-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="067ea-121">Child Elements</span></span>  
 <span data-ttu-id="067ea-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="067ea-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="067ea-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="067ea-123">Parent Elements</span></span>  
  
|<span data-ttu-id="067ea-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="067ea-124">Element</span></span>|<span data-ttu-id="067ea-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="067ea-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="067ea-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="067ea-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="067ea-127">İstemci uygulaması dinlediği varsayılan iletişim uç noktalarını listeleme varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="067ea-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="067ea-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="067ea-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
