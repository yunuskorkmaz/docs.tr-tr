---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 5e62201a38dc4dc251996531a4af5f294dd2395f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151109"
---
# \<clientVia>

<span data-ttu-id="c19a6-101">Taşıma kanalının oluşturulması gereken URI 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c19a6-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="c19a6-102">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="c19a6-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="c19a6-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="c19a6-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c19a6-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c19a6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c19a6-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c19a6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c19a6-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c19a6-106">Attributes</span></span>  
  
|<span data-ttu-id="c19a6-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c19a6-107">Attribute</span></span>|<span data-ttu-id="c19a6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c19a6-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="c19a6-109">Bir iletinin gerçekleşmesi gereken yolu gösteren bir URI belirten dize.</span><span class="sxs-lookup"><span data-stu-id="c19a6-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c19a6-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c19a6-110">Child Elements</span></span>  

 <span data-ttu-id="c19a6-111">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c19a6-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c19a6-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c19a6-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c19a6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="c19a6-113">Element</span></span>|<span data-ttu-id="c19a6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c19a6-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c19a6-115">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c19a6-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c19a6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c19a6-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
