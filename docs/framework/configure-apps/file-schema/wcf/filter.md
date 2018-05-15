---
title: '&lt;Filtre&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 93d47fc6b25a75eedae43cd70582abc863a74e6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt"></a><span data-ttu-id="e2be8-102">&lt;Filtre&gt;</span><span class="sxs-lookup"><span data-stu-id="e2be8-102">&lt;filter&gt;</span></span>

<span data-ttu-id="e2be8-103">Windows Communication Foundation (WCF) türü belirler yönlendirme filtre tanımlayan<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri de tüm destekleyici veri veya filtre tarafından gerekli parametreleri olarak hesaplanırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="e2be8-103">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="e2be8-104">\<system.serviceModel > \<yönlendirme > \<filtreleri > \<Filtre ></span><span class="sxs-lookup"><span data-stu-id="e2be8-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="e2be8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2be8-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e2be8-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e2be8-106">Attributes and elements</span></span>

<span data-ttu-id="e2be8-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2be8-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2be8-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e2be8-108">Attributes</span></span>

| <span data-ttu-id="e2be8-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e2be8-109">Attribute</span></span>  | <span data-ttu-id="e2be8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2be8-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="e2be8-111">customType</span><span class="sxs-lookup"><span data-stu-id="e2be8-111">customType</span></span> | <span data-ttu-id="e2be8-112">Filtre olarak kullanılacak özel türünün tam olarak nitelenmiş tür adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="e2be8-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="e2be8-113">Varsa `filterType` ayarlanır `custom`, bu öznitelik sınıfı oluşturmak için tam olarak nitelenmiş tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="e2be8-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="e2be8-114">`filterData` Ayrıca özel türü filtresi değerlendirme sırasında kullanılacak değerler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e2be8-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="e2be8-115">Filtre veri</span><span class="sxs-lookup"><span data-stu-id="e2be8-115">filterData</span></span> | <span data-ttu-id="e2be8-116">Filtre veri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="e2be8-116">A string containing the filter data.</span></span> <span data-ttu-id="e2be8-117">Bu öznitelik belirtme hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2be8-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="e2be8-118">filterType</span><span class="sxs-lookup"><span data-stu-id="e2be8-118">filterType</span></span> | <span data-ttu-id="e2be8-119">Filtre türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="e2be8-119">A string containing the filter type.</span></span> <span data-ttu-id="e2be8-120">Bu özniteliktir <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.</span><span class="sxs-lookup"><span data-stu-id="e2be8-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="e2be8-121">Bunun ile işleyişi hakkında daha fazla bilgi için `filterData` özniteliği için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2be8-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="e2be8-122">name</span><span class="sxs-lookup"><span data-stu-id="e2be8-122">name</span></span>       | <span data-ttu-id="e2be8-123">Bu filtre öğesinin benzersiz adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="e2be8-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="e2be8-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e2be8-124">Child elements</span></span>

<span data-ttu-id="e2be8-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="e2be8-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2be8-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e2be8-126">Parent elements</span></span>

| <span data-ttu-id="e2be8-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="e2be8-127">Element</span></span> | <span data-ttu-id="e2be8-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2be8-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="e2be8-129">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="e2be8-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="e2be8-130">Windows Communication Foundation (WCF) türü belirlenemiyor yönlendirme bir filtre kümesi tanımlamak için bir yapılandırma bölümü<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="e2be8-130">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e2be8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2be8-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
