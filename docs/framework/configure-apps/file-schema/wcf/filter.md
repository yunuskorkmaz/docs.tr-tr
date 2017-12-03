---
title: '&lt;Filtre&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: af2095289d5f711733c71238b855c685114d1997
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltergt"></a><span data-ttu-id="0d138-102">&lt;Filtre&gt;</span><span class="sxs-lookup"><span data-stu-id="0d138-102">&lt;filter&gt;</span></span>

<span data-ttu-id="0d138-103">Türünü belirler yönlendirme filtre tanımlayan [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri de tüm destekleyici veri veya filtre tarafından gerekli parametreleri olarak hesaplanırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="0d138-103">Defines a routing filter, which determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="0d138-104">\<system.serviceModel > \<yönlendirme > \<filtreleri > \<Filtre ></span><span class="sxs-lookup"><span data-stu-id="0d138-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="0d138-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d138-105">Syntax</span></span>

```xml
<routing>
  <filters>
    <filter customType="String" 
            filterData="String" 
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
            name="String" />
  </filters>
</routing>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d138-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="0d138-106">Attributes and elements</span></span>

<span data-ttu-id="0d138-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0d138-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d138-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0d138-108">Attributes</span></span>

| <span data-ttu-id="0d138-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0d138-109">Attribute</span></span>  | <span data-ttu-id="0d138-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d138-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="0d138-111">customType</span><span class="sxs-lookup"><span data-stu-id="0d138-111">customType</span></span> | <span data-ttu-id="0d138-112">Filtre olarak kullanılacak özel türünün tam olarak nitelenmiş tür adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="0d138-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="0d138-113">Varsa `filterType` ayarlanır `custom`, bu öznitelik sınıfı oluşturmak için tam olarak nitelenmiş tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="0d138-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="0d138-114">`filterData`Ayrıca özel türü filtresi değerlendirme sırasında kullanılacak değerler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0d138-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="0d138-115">Filtre veri</span><span class="sxs-lookup"><span data-stu-id="0d138-115">filterData</span></span> | <span data-ttu-id="0d138-116">Filtre veri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="0d138-116">A string containing the filter data.</span></span> <span data-ttu-id="0d138-117">Bu öznitelik belirtme hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d138-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="0d138-118">filterType</span><span class="sxs-lookup"><span data-stu-id="0d138-118">filterType</span></span> | <span data-ttu-id="0d138-119">Filtre türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="0d138-119">A string containing the filter type.</span></span> <span data-ttu-id="0d138-120">Bu özniteliktir <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.</span><span class="sxs-lookup"><span data-stu-id="0d138-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="0d138-121">Bunun ile işleyişi hakkında daha fazla bilgi için `filterData` özniteliği için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d138-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="0d138-122">name</span><span class="sxs-lookup"><span data-stu-id="0d138-122">name</span></span>       | <span data-ttu-id="0d138-123">Bu filtre öğesinin benzersiz adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="0d138-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="0d138-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0d138-124">Child elements</span></span>

<span data-ttu-id="0d138-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="0d138-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0d138-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0d138-126">Parent elements</span></span>

| <span data-ttu-id="0d138-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="0d138-127">Element</span></span> | <span data-ttu-id="0d138-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d138-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="0d138-129">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="0d138-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="0d138-130">Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için bir yapılandırma bölümü [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="0d138-130">A configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0d138-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d138-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
