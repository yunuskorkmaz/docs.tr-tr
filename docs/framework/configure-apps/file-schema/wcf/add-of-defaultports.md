---
title: <add> / <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400649"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="6e955-102">\<\<defaultPort > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="6e955-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="6e955-103">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="6e955-103">A default communications endpoint that the client application listens to.</span></span>  
  
<span data-ttu-id="6e955-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e955-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6e955-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6e955-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6e955-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6e955-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="6e955-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6e955-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="6e955-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6e955-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="6e955-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="6e955-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="6e955-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultPorts >** ](defaultports.md)</span><span class="sxs-lookup"><span data-stu-id="6e955-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)</span></span>\
<span data-ttu-id="6e955-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="6e955-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e955-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e955-112">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e955-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e955-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6e955-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e955-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e955-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e955-115">Attributes</span></span>  
  
|<span data-ttu-id="6e955-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e955-116">Attribute</span></span>|<span data-ttu-id="6e955-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e955-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e955-118">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="6e955-118">port</span></span>|<span data-ttu-id="6e955-119">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="6e955-119">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="6e955-120">düzen</span><span class="sxs-lookup"><span data-stu-id="6e955-120">scheme</span></span>|<span data-ttu-id="6e955-121">İletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6e955-121">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e955-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e955-122">Child Elements</span></span>  
 <span data-ttu-id="6e955-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e955-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e955-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e955-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6e955-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e955-125">Element</span></span>|<span data-ttu-id="6e955-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e955-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e955-127">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="6e955-127">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="6e955-128">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="6e955-128">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e955-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e955-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
