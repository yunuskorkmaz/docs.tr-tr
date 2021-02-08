---
description: 'Hakkında daha fazla bilgi <add> edinin: <defaultPorts>'
title: <add> / <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 9db7afa5183b185eb842530b051d98236e7fa381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803964"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="8aa84-103">\<add> / \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="8aa84-103">\<add> of \<defaultPorts></span></span>

<span data-ttu-id="8aa84-104">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="8aa84-104">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="8aa84-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8aa84-105">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8aa84-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa84-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8aa84-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8aa84-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8aa84-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8aa84-108">Attributes</span></span>  
  
|<span data-ttu-id="8aa84-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8aa84-109">Attribute</span></span>|<span data-ttu-id="8aa84-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aa84-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8aa84-111">port</span><span class="sxs-lookup"><span data-stu-id="8aa84-111">port</span></span>|<span data-ttu-id="8aa84-112">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="8aa84-112">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="8aa84-113">düzen</span><span class="sxs-lookup"><span data-stu-id="8aa84-113">scheme</span></span>|<span data-ttu-id="8aa84-114">İletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8aa84-114">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8aa84-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa84-115">Child Elements</span></span>  

 <span data-ttu-id="8aa84-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="8aa84-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8aa84-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa84-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8aa84-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="8aa84-118">Element</span></span>|<span data-ttu-id="8aa84-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aa84-119">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="8aa84-120">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="8aa84-120">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8aa84-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8aa84-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
