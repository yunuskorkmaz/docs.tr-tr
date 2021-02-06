---
description: 'Hakkında daha fazla bilgi edinin: <clientVia>'
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 651af0c310504f7672ca172d7df609365c319506
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638781"
---
# \<clientVia>

<span data-ttu-id="75c28-102">Taşıma kanalının oluşturulması gereken URI 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="75c28-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="75c28-103">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="75c28-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="75c28-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="75c28-104">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75c28-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="75c28-105">Attributes and Elements</span></span>  

 <span data-ttu-id="75c28-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75c28-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75c28-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75c28-107">Attributes</span></span>  
  
|<span data-ttu-id="75c28-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75c28-108">Attribute</span></span>|<span data-ttu-id="75c28-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75c28-109">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="75c28-110">Bir iletinin gerçekleşmesi gereken yolu gösteren bir URI belirten dize.</span><span class="sxs-lookup"><span data-stu-id="75c28-110">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75c28-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="75c28-111">Child Elements</span></span>  

 <span data-ttu-id="75c28-112">Yok</span><span class="sxs-lookup"><span data-stu-id="75c28-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75c28-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="75c28-113">Parent Elements</span></span>  
  
|<span data-ttu-id="75c28-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="75c28-114">Element</span></span>|<span data-ttu-id="75c28-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75c28-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="75c28-116">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="75c28-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75c28-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75c28-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
