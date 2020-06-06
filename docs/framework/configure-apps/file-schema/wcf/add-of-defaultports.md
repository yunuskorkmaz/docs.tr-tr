---
title: <add> / <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400649"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="ad021-102">\<add> / \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="ad021-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="ad021-103">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="ad021-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ad021-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad021-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad021-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad021-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ad021-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ad021-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad021-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ad021-107">Attributes</span></span>  
  
|<span data-ttu-id="ad021-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ad021-108">Attribute</span></span>|<span data-ttu-id="ad021-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad021-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad021-110">port</span><span class="sxs-lookup"><span data-stu-id="ad021-110">port</span></span>|<span data-ttu-id="ad021-111">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="ad021-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="ad021-112">düzen</span><span class="sxs-lookup"><span data-stu-id="ad021-112">scheme</span></span>|<span data-ttu-id="ad021-113">İletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ad021-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad021-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad021-114">Child Elements</span></span>  
 <span data-ttu-id="ad021-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ad021-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad021-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ad021-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ad021-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ad021-117">Element</span></span>|<span data-ttu-id="ad021-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad021-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="ad021-119">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="ad021-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad021-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad021-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
