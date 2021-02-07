---
description: 'Hakkında daha fazla bilgi edinin: <filter>'
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 993d2265ac3a714475e8cbe9e8a2c3f93c46bde2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664684"
---
# \<filter>

<span data-ttu-id="47f64-102">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü <xref:System.ServiceModel.Dispatcher.MessageFilter> , ayrıca filtrenin gerektirdiği destekleyici verileri veya parametreleri belirleyen bir yönlendirme filtresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47f64-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="47f64-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="47f64-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47f64-104">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="47f64-104">Attributes and elements</span></span>

<span data-ttu-id="47f64-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47f64-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="47f64-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47f64-106">Attributes</span></span>

| <span data-ttu-id="47f64-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="47f64-107">Attribute</span></span>  | <span data-ttu-id="47f64-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47f64-108">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="47f64-109">customType</span><span class="sxs-lookup"><span data-stu-id="47f64-109">customType</span></span> | <span data-ttu-id="47f64-110">Filtre olarak kullanılacak özel türün tam nitelikli tür adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="47f64-110">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="47f64-111">, `filterType` Olarak ayarlandıysa `custom` , bu öznitelik oluşturulacak sınıfın tam nitelikli tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="47f64-111">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="47f64-112">`filterData` özel tür filtresi değerlendirmesi sırasında kullanılacak değerleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="47f64-112">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="47f64-113">filterData</span><span class="sxs-lookup"><span data-stu-id="47f64-113">filterData</span></span> | <span data-ttu-id="47f64-114">Filtre verilerini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="47f64-114">A string containing the filter data.</span></span> <span data-ttu-id="47f64-115">Bu özniteliği belirtme hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> ..</span><span class="sxs-lookup"><span data-stu-id="47f64-115">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="47f64-116">filterType</span><span class="sxs-lookup"><span data-stu-id="47f64-116">filterType</span></span> | <span data-ttu-id="47f64-117">Filtre türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="47f64-117">A string containing the filter type.</span></span> <span data-ttu-id="47f64-118">Bu öznitelik <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.</span><span class="sxs-lookup"><span data-stu-id="47f64-118">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="47f64-119">Bunun özniteliğiyle nasıl çalıştığı hakkında daha fazla bilgi için `filterData` bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> ..</span><span class="sxs-lookup"><span data-stu-id="47f64-119">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="47f64-120">name</span><span class="sxs-lookup"><span data-stu-id="47f64-120">name</span></span>       | <span data-ttu-id="47f64-121">Bu filtre öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="47f64-121">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="47f64-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="47f64-122">Child elements</span></span>

<span data-ttu-id="47f64-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="47f64-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="47f64-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="47f64-124">Parent elements</span></span>

| <span data-ttu-id="47f64-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="47f64-125">Element</span></span> | <span data-ttu-id="47f64-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47f64-126">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="47f64-127">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümü <xref:System.ServiceModel.Dispatcher.MessageFilter> .</span><span class="sxs-lookup"><span data-stu-id="47f64-127">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="47f64-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47f64-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
