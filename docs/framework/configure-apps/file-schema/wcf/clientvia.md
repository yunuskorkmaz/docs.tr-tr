---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398103"
---
# \<clientVia>
<span data-ttu-id="e5404-101">Taşıma kanalının oluşturulması gereken URI 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5404-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="e5404-102">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e5404-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="e5404-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5404-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5404-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5404-104">Attributes and Elements</span></span>  
 <span data-ttu-id="e5404-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5404-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5404-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5404-106">Attributes</span></span>  
  
|<span data-ttu-id="e5404-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5404-107">Attribute</span></span>|<span data-ttu-id="e5404-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5404-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="e5404-109">Bir iletinin gerçekleşmesi gereken yolu gösteren bir URI belirten dize.</span><span class="sxs-lookup"><span data-stu-id="e5404-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5404-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5404-110">Child Elements</span></span>  
 <span data-ttu-id="e5404-111">Yok</span><span class="sxs-lookup"><span data-stu-id="e5404-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5404-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5404-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e5404-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5404-113">Element</span></span>|<span data-ttu-id="e5404-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5404-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e5404-115">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5404-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5404-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5404-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
