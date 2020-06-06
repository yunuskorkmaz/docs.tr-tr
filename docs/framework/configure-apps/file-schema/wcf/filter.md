---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855248"
---
# \<filter>

<span data-ttu-id="f81d2-101">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü <xref:System.ServiceModel.Dispatcher.MessageFilter> , ayrıca filtrenin gerektirdiği destekleyici verileri veya parametreleri belirleyen bir yönlendirme filtresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f81d2-101">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="f81d2-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f81d2-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f81d2-103">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="f81d2-103">Attributes and elements</span></span>

<span data-ttu-id="f81d2-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f81d2-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f81d2-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f81d2-105">Attributes</span></span>

| <span data-ttu-id="f81d2-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f81d2-106">Attribute</span></span>  | <span data-ttu-id="f81d2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f81d2-107">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="f81d2-108">customType</span><span class="sxs-lookup"><span data-stu-id="f81d2-108">customType</span></span> | <span data-ttu-id="f81d2-109">Filtre olarak kullanılacak özel türün tam nitelikli tür adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f81d2-109">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="f81d2-110">, `filterType` Olarak ayarlandıysa `custom` , bu öznitelik oluşturulacak sınıfın tam nitelikli tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="f81d2-110">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="f81d2-111">`filterData`özel tür filtresi değerlendirmesi sırasında kullanılacak değerleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f81d2-111">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="f81d2-112">filterData</span><span class="sxs-lookup"><span data-stu-id="f81d2-112">filterData</span></span> | <span data-ttu-id="f81d2-113">Filtre verilerini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f81d2-113">A string containing the filter data.</span></span> <span data-ttu-id="f81d2-114">Bu özniteliği belirtme hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> ..</span><span class="sxs-lookup"><span data-stu-id="f81d2-114">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f81d2-115">filterType</span><span class="sxs-lookup"><span data-stu-id="f81d2-115">filterType</span></span> | <span data-ttu-id="f81d2-116">Filtre türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f81d2-116">A string containing the filter type.</span></span> <span data-ttu-id="f81d2-117">Bu öznitelik <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.</span><span class="sxs-lookup"><span data-stu-id="f81d2-117">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="f81d2-118">Bunun özniteliğiyle nasıl çalıştığı hakkında daha fazla bilgi için `filterData` bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> ..</span><span class="sxs-lookup"><span data-stu-id="f81d2-118">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f81d2-119">name</span><span class="sxs-lookup"><span data-stu-id="f81d2-119">name</span></span>       | <span data-ttu-id="f81d2-120">Bu filtre öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f81d2-120">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f81d2-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f81d2-121">Child elements</span></span>

<span data-ttu-id="f81d2-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="f81d2-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f81d2-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f81d2-123">Parent elements</span></span>

| <span data-ttu-id="f81d2-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="f81d2-124">Element</span></span> | <span data-ttu-id="f81d2-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f81d2-125">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="f81d2-126">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümü <xref:System.ServiceModel.Dispatcher.MessageFilter> .</span><span class="sxs-lookup"><span data-stu-id="f81d2-126">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f81d2-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f81d2-127">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
