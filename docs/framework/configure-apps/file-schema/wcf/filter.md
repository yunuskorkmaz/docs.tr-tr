---
title: '&lt;Filtre&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: f7224eab9f3c21bce9839298b50c52e9da08b6f7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146413"
---
# <a name="ltfiltergt"></a><span data-ttu-id="fb747-102">&lt;Filtre&gt;</span><span class="sxs-lookup"><span data-stu-id="fb747-102">&lt;filter&gt;</span></span>

<span data-ttu-id="fb747-103">Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi tanımlar<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri de tüm destekleyici veri ya da filtre tarafından parametre olarak değerlendirilirken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="fb747-103">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="fb747-104">\<system.serviceModel > \<yönlendirme > \<filtreleri > \<Filtre ></span><span class="sxs-lookup"><span data-stu-id="fb747-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="fb747-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb747-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb747-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="fb747-106">Attributes and elements</span></span>

<span data-ttu-id="fb747-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb747-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb747-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb747-108">Attributes</span></span>

| <span data-ttu-id="fb747-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fb747-109">Attribute</span></span>  | <span data-ttu-id="fb747-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb747-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="fb747-111">CustomType</span><span class="sxs-lookup"><span data-stu-id="fb747-111">customType</span></span> | <span data-ttu-id="fb747-112">Filtre olarak kullanılmak üzere özel türünün tam olarak nitelenmiş tür adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fb747-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="fb747-113">Varsa `filterType` ayarlanır `custom`, bu öznitelik sınıfı oluşturmak için tam olarak nitelenmiş tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="fb747-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="fb747-114">`filterData` Özel tür filtrenin değerlendirmesi sırasında kullanılacak değerler de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fb747-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="fb747-115">Filtre veri</span><span class="sxs-lookup"><span data-stu-id="fb747-115">filterData</span></span> | <span data-ttu-id="fb747-116">Filtre verisi içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fb747-116">A string containing the filter data.</span></span> <span data-ttu-id="fb747-117">Bu öznitelik belirtme hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb747-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="fb747-118">Filtre türü</span><span class="sxs-lookup"><span data-stu-id="fb747-118">filterType</span></span> | <span data-ttu-id="fb747-119">Filtre türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fb747-119">A string containing the filter type.</span></span> <span data-ttu-id="fb747-120">Bu özniteliktir <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.</span><span class="sxs-lookup"><span data-stu-id="fb747-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="fb747-121">Bu ile nasıl çalıştığı hakkında daha fazla bilgi için `filterData` özniteliği için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="fb747-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="fb747-122">name</span><span class="sxs-lookup"><span data-stu-id="fb747-122">name</span></span>       | <span data-ttu-id="fb747-123">Bu filtre öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fb747-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="fb747-124">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fb747-124">Child elements</span></span>

<span data-ttu-id="fb747-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="fb747-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fb747-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fb747-126">Parent elements</span></span>

| <span data-ttu-id="fb747-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb747-127">Element</span></span> | <span data-ttu-id="fb747-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb747-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="fb747-129">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="fb747-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="fb747-130">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri değerlendirmek kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="fb747-130">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fb747-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb747-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
