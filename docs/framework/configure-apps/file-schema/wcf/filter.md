---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855248"
---
# <a name="filter"></a><span data-ttu-id="391ac-101">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="391ac-101">\<filter></span></span>

<span data-ttu-id="391ac-102">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü, ayrıca filtrenin gerektirdiği destekleyici verileri veya parametreleri belirleyen bir yönlendirme filtresi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="391ac-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="391ac-103">[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="391ac-103">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="391ac-104">&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="391ac-104">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="391ac-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtreler >** ](filters-of-routing.md)</span><span class="sxs-lookup"><span data-stu-id="391ac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)</span></span>\
<span data-ttu-id="391ac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="391ac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="391ac-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="391ac-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="391ac-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="391ac-108">Attributes and elements</span></span>

<span data-ttu-id="391ac-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="391ac-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="391ac-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="391ac-110">Attributes</span></span>

| <span data-ttu-id="391ac-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="391ac-111">Attribute</span></span>  | <span data-ttu-id="391ac-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="391ac-112">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="391ac-113">customType</span><span class="sxs-lookup"><span data-stu-id="391ac-113">customType</span></span> | <span data-ttu-id="391ac-114">Filtre olarak kullanılacak özel türün tam nitelikli tür adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="391ac-114">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="391ac-115">`filterType` , Olarak`custom`ayarlandıysa, bu öznitelik oluşturulacak sınıfın tam nitelikli tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="391ac-115">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="391ac-116">`filterData`özel tür filtresi değerlendirmesi sırasında kullanılacak değerleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="391ac-116">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="391ac-117">filterData</span><span class="sxs-lookup"><span data-stu-id="391ac-117">filterData</span></span> | <span data-ttu-id="391ac-118">Filtre verilerini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="391ac-118">A string containing the filter data.</span></span> <span data-ttu-id="391ac-119">Bu özniteliği belirtme hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="391ac-119">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="391ac-120">filterType</span><span class="sxs-lookup"><span data-stu-id="391ac-120">filterType</span></span> | <span data-ttu-id="391ac-121">Filtre türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="391ac-121">A string containing the filter type.</span></span> <span data-ttu-id="391ac-122">Bu öznitelik <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.</span><span class="sxs-lookup"><span data-stu-id="391ac-122">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="391ac-123">Bunun `filterData` özniteliğiyle nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="391ac-123">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="391ac-124">name</span><span class="sxs-lookup"><span data-stu-id="391ac-124">name</span></span>       | <span data-ttu-id="391ac-125">Bu filtre öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="391ac-125">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="391ac-126">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="391ac-126">Child elements</span></span>

<span data-ttu-id="391ac-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="391ac-127">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="391ac-128">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="391ac-128">Parent elements</span></span>

| <span data-ttu-id="391ac-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="391ac-129">Element</span></span> | <span data-ttu-id="391ac-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="391ac-130">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="391ac-131">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="391ac-131">\<routing></span></span>](routing.md) | <span data-ttu-id="391ac-132">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="391ac-132">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="391ac-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="391ac-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
