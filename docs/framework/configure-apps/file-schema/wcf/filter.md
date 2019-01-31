---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278791"
---
# <a name="filter"></a><span data-ttu-id="28348-101">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="28348-101">\<filter></span></span>

<span data-ttu-id="28348-102">Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi tanımlar<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri de tüm destekleyici veri ya da filtre tarafından parametre olarak değerlendirilirken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="28348-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="28348-103">\<system.serviceModel > \<yönlendirme > \<filtreleri > \<Filtre ></span><span class="sxs-lookup"><span data-stu-id="28348-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="28348-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28348-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28348-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="28348-105">Attributes and elements</span></span>

<span data-ttu-id="28348-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="28348-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="28348-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="28348-107">Attributes</span></span>

| <span data-ttu-id="28348-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="28348-108">Attribute</span></span>  | <span data-ttu-id="28348-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28348-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="28348-110">CustomType</span><span class="sxs-lookup"><span data-stu-id="28348-110">customType</span></span> | <span data-ttu-id="28348-111">Filtre olarak kullanılmak üzere özel türünün tam olarak nitelenmiş tür adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="28348-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="28348-112">Varsa `filterType` ayarlanır `custom`, bu öznitelik sınıfı oluşturmak için tam olarak nitelenmiş tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="28348-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="28348-113">`filterData` Özel tür filtrenin değerlendirmesi sırasında kullanılacak değerler de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="28348-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="28348-114">Filtre veri</span><span class="sxs-lookup"><span data-stu-id="28348-114">filterData</span></span> | <span data-ttu-id="28348-115">Filtre verisi içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="28348-115">A string containing the filter data.</span></span> <span data-ttu-id="28348-116">Bu öznitelik belirtme hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="28348-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="28348-117">Filtre türü</span><span class="sxs-lookup"><span data-stu-id="28348-117">filterType</span></span> | <span data-ttu-id="28348-118">Filtre türü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="28348-118">A string containing the filter type.</span></span> <span data-ttu-id="28348-119">Bu özniteliktir <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.</span><span class="sxs-lookup"><span data-stu-id="28348-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="28348-120">Bu ile nasıl çalıştığı hakkında daha fazla bilgi için `filterData` özniteliği için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="28348-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="28348-121">name</span><span class="sxs-lookup"><span data-stu-id="28348-121">name</span></span>       | <span data-ttu-id="28348-122">Bu filtre öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="28348-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="28348-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="28348-123">Child elements</span></span>

<span data-ttu-id="28348-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="28348-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="28348-125">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="28348-125">Parent elements</span></span>

| <span data-ttu-id="28348-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="28348-126">Element</span></span> | <span data-ttu-id="28348-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28348-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="28348-128">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="28348-128">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="28348-129">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri değerlendirmek kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="28348-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="28348-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28348-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
