---
title: <add> , <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 799715ef008274ead6b745e8ab97e769cb59e6b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261611"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="7b3ae-102">\<Ekle >, \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="7b3ae-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="7b3ae-103">İstemci uygulamasının dinleyeceği bir varsayılan iletişim bitiş noktaları.</span><span class="sxs-lookup"><span data-stu-id="7b3ae-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="7b3ae-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b3ae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b3ae-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="7b3ae-105">\<behaviors></span></span>  
<span data-ttu-id="7b3ae-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7b3ae-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7b3ae-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7b3ae-107">\<behavior></span></span>  
<span data-ttu-id="7b3ae-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="7b3ae-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="7b3ae-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="7b3ae-109">\<defaultPorts></span></span>  
<span data-ttu-id="7b3ae-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="7b3ae-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3ae-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b3ae-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b3ae-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b3ae-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7b3ae-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b3ae-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b3ae-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7b3ae-114">Attributes</span></span>  
  
|<span data-ttu-id="7b3ae-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7b3ae-115">Attribute</span></span>|<span data-ttu-id="7b3ae-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b3ae-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b3ae-117">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="7b3ae-117">port</span></span>|<span data-ttu-id="7b3ae-118">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="7b3ae-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="7b3ae-119">düzen</span><span class="sxs-lookup"><span data-stu-id="7b3ae-119">scheme</span></span>|<span data-ttu-id="7b3ae-120">Bir iletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7b3ae-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b3ae-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b3ae-121">Child Elements</span></span>  
 <span data-ttu-id="7b3ae-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="7b3ae-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b3ae-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b3ae-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7b3ae-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="7b3ae-124">Element</span></span>|<span data-ttu-id="7b3ae-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b3ae-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b3ae-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="7b3ae-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="7b3ae-127">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7b3ae-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b3ae-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b3ae-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
