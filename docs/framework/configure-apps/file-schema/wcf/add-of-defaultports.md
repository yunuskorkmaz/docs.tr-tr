---
title: '&lt;defaultPorts&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 0932ef9afacb6278c4857dcfd6ba545595ff8f9d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147726"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="79eaf-102">&lt;defaultPorts&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="79eaf-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="79eaf-103">İstemci uygulamasının dinleyeceği bir varsayılan iletişim bitiş noktaları.</span><span class="sxs-lookup"><span data-stu-id="79eaf-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="79eaf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79eaf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="79eaf-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="79eaf-105">\<behaviors></span></span>  
<span data-ttu-id="79eaf-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="79eaf-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="79eaf-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="79eaf-107">\<behavior></span></span>  
<span data-ttu-id="79eaf-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="79eaf-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="79eaf-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="79eaf-109">\<defaultPorts></span></span>  
<span data-ttu-id="79eaf-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="79eaf-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79eaf-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79eaf-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79eaf-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79eaf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="79eaf-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79eaf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79eaf-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79eaf-114">Attributes</span></span>  
  
|<span data-ttu-id="79eaf-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="79eaf-115">Attribute</span></span>|<span data-ttu-id="79eaf-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79eaf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="79eaf-117">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="79eaf-117">port</span></span>|<span data-ttu-id="79eaf-118">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="79eaf-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="79eaf-119">düzen</span><span class="sxs-lookup"><span data-stu-id="79eaf-119">scheme</span></span>|<span data-ttu-id="79eaf-120">Bir iletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="79eaf-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79eaf-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79eaf-121">Child Elements</span></span>  
 <span data-ttu-id="79eaf-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="79eaf-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79eaf-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79eaf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="79eaf-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="79eaf-124">Element</span></span>|<span data-ttu-id="79eaf-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79eaf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79eaf-126">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="79eaf-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="79eaf-127">İstemci uygulamasının dinleyeceği, varsayılan iletişim bitiş noktalarını listeleyen varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="79eaf-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="79eaf-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79eaf-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
