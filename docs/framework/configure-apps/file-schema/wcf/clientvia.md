---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398103"
---
# <a name="clientvia"></a><span data-ttu-id="53fa8-101">\<> aracılığıyla Client</span><span class="sxs-lookup"><span data-stu-id="53fa8-101">\<clientVia></span></span>
<span data-ttu-id="53fa8-102">Taşıma kanalının oluşturulması gereken URI 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="53fa8-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="53fa8-103">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="53fa8-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
<span data-ttu-id="53fa8-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="53fa8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="53fa8-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="53fa8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="53fa8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="53fa8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="53fa8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="53fa8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="53fa8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="53fa8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="53fa8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> aracılığıyla Client**</span><span class="sxs-lookup"><span data-stu-id="53fa8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53fa8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53fa8-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53fa8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="53fa8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="53fa8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53fa8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53fa8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="53fa8-113">Attributes</span></span>  
  
|<span data-ttu-id="53fa8-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="53fa8-114">Attribute</span></span>|<span data-ttu-id="53fa8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53fa8-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="53fa8-116">Bir iletinin gerçekleşmesi gereken yolu gösteren bir URI belirten dize.</span><span class="sxs-lookup"><span data-stu-id="53fa8-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53fa8-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="53fa8-117">Child Elements</span></span>  
 <span data-ttu-id="53fa8-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="53fa8-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53fa8-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="53fa8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="53fa8-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="53fa8-120">Element</span></span>|<span data-ttu-id="53fa8-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53fa8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53fa8-122">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="53fa8-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="53fa8-123">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="53fa8-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53fa8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53fa8-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>
