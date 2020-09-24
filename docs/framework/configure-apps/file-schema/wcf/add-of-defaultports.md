---
title: <add> / <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 2c6b5de51e6508965daf6022a47d12d8d73f2a4d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149133"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="b1877-102">\<add> / \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="b1877-102">\<add> of \<defaultPorts></span></span>

<span data-ttu-id="b1877-103">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="b1877-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b1877-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1877-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1877-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1877-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b1877-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1877-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1877-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1877-107">Attributes</span></span>  
  
|<span data-ttu-id="b1877-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b1877-108">Attribute</span></span>|<span data-ttu-id="b1877-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1877-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1877-110">port</span><span class="sxs-lookup"><span data-stu-id="b1877-110">port</span></span>|<span data-ttu-id="b1877-111">Varsayılan iletişim bağlantı noktası numarasını belirten bir tamsayı</span><span class="sxs-lookup"><span data-stu-id="b1877-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="b1877-112">düzen</span><span class="sxs-lookup"><span data-stu-id="b1877-112">scheme</span></span>|<span data-ttu-id="b1877-113">İletişim bağlantı noktası ile ilişkili protokol ayarları grubunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b1877-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1877-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1877-114">Child Elements</span></span>  

 <span data-ttu-id="b1877-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1877-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1877-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b1877-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b1877-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1877-117">Element</span></span>|<span data-ttu-id="b1877-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1877-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="b1877-119">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="b1877-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1877-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1877-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
