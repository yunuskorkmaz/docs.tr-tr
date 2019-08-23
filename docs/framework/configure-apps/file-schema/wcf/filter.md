---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 68de255b9f11dc4377159d1cc3efa575633db316
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918891"
---
# <a name="filter"></a><span data-ttu-id="01f51-101">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="01f51-101">\<filter></span></span>

<span data-ttu-id="01f51-102">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü, ayrıca filtrenin gerektirdiği destekleyici verileri veya parametreleri belirleyen bir yönlendirme filtresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="01f51-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="01f51-103">\<System. ServiceModel > \<yönlendirme > \<filtreleri > \<filtresi ></span><span class="sxs-lookup"><span data-stu-id="01f51-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="01f51-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01f51-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01f51-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="01f51-105">Attributes and elements</span></span>

<span data-ttu-id="01f51-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="01f51-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="01f51-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="01f51-107">Attributes</span></span>

| <span data-ttu-id="01f51-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="01f51-108">Attribute</span></span>  | <span data-ttu-id="01f51-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01f51-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="01f51-110">customType</span><span class="sxs-lookup"><span data-stu-id="01f51-110">customType</span></span> | <span data-ttu-id="01f51-111">Filtre olarak kullanılacak özel türün tam nitelikli tür adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="01f51-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="01f51-112">`filterType` , Olarak`custom`ayarlandıysa, bu öznitelik oluşturulacak sınıfın tam nitelikli tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="01f51-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="01f51-113">`filterData`özel tür filtresi değerlendirmesi sırasında kullanılacak değerleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="01f51-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="01f51-114">filterData</span><span class="sxs-lookup"><span data-stu-id="01f51-114">filterData</span></span> | <span data-ttu-id="01f51-115">Filtre verilerini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="01f51-115">A string containing the filter data.</span></span> <span data-ttu-id="01f51-116">Bu özniteliği belirtme hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="01f51-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="01f51-117">filterType</span><span class="sxs-lookup"><span data-stu-id="01f51-117">filterType</span></span> | <span data-ttu-id="01f51-118">Filtre türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="01f51-118">A string containing the filter type.</span></span> <span data-ttu-id="01f51-119">Bu öznitelik <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.</span><span class="sxs-lookup"><span data-stu-id="01f51-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="01f51-120">Bunun `filterData` özniteliğiyle nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="01f51-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="01f51-121">name</span><span class="sxs-lookup"><span data-stu-id="01f51-121">name</span></span>       | <span data-ttu-id="01f51-122">Bu filtre öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="01f51-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="01f51-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="01f51-123">Child elements</span></span>

<span data-ttu-id="01f51-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="01f51-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="01f51-125">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="01f51-125">Parent elements</span></span>

| <span data-ttu-id="01f51-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="01f51-126">Element</span></span> | <span data-ttu-id="01f51-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01f51-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="01f51-128">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="01f51-128">\<routing></span></span>](routing.md) | <span data-ttu-id="01f51-129">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="01f51-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="01f51-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01f51-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
