---
title: <add> / <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: d2723dad14a63c4b05fdb70157f7eb21d193d3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926704"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="116ef-102">\<\<defaultPort > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="116ef-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="116ef-103">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="116ef-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="116ef-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="116ef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="116ef-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="116ef-105">\<behaviors></span></span>  
<span data-ttu-id="116ef-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="116ef-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="116ef-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="116ef-107">\<behavior></span></span>  
<span data-ttu-id="116ef-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="116ef-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="116ef-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="116ef-109">\<defaultPorts></span></span>  
<span data-ttu-id="116ef-110">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="116ef-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="116ef-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="116ef-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="116ef-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="116ef-112">Attributes and Elements</span></span>  
 <span data-ttu-id="116ef-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="116ef-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="116ef-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="116ef-114">Attributes</span></span>  
  
|<span data-ttu-id="116ef-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="116ef-115">Attribute</span></span>|<span data-ttu-id="116ef-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="116ef-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="116ef-117">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="116ef-117">port</span></span>|<span data-ttu-id="116ef-118">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="116ef-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="116ef-119">düzen</span><span class="sxs-lookup"><span data-stu-id="116ef-119">scheme</span></span>|<span data-ttu-id="116ef-120">İletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="116ef-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="116ef-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="116ef-121">Child Elements</span></span>  
 <span data-ttu-id="116ef-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="116ef-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="116ef-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="116ef-123">Parent Elements</span></span>  
  
|<span data-ttu-id="116ef-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="116ef-124">Element</span></span>|<span data-ttu-id="116ef-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="116ef-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="116ef-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="116ef-126">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="116ef-127">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="116ef-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="116ef-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="116ef-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
