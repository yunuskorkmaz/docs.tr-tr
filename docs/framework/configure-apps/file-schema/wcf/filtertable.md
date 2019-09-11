---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855185"
---
# <a name="filtertable"></a><span data-ttu-id="7a836-101">\<Filtretablo ></span><span class="sxs-lookup"><span data-stu-id="7a836-101">\<filterTable></span></span>
<span data-ttu-id="7a836-102">Filtrenin, filtre true olarak değerlendirilirse, iletileri yönlendirmek için bir filtre listesi ve istemci uç noktası içeren bir yönlendirme tablosunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7a836-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
<span data-ttu-id="7a836-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a836-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a836-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7a836-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7a836-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="7a836-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="7a836-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="7a836-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="7a836-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Filtretablo >**</span><span class="sxs-lookup"><span data-stu-id="7a836-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a836-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a836-108">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a836-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a836-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7a836-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7a836-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a836-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7a836-111">Attributes</span></span>  
  
|<span data-ttu-id="7a836-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a836-112">Element</span></span>|<span data-ttu-id="7a836-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a836-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a836-114">name</span><span class="sxs-lookup"><span data-stu-id="7a836-114">name</span></span>|<span data-ttu-id="7a836-115">Bu yapılandırma öğesinin benzersiz adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="7a836-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a836-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a836-116">Child Elements</span></span>  
  
|<span data-ttu-id="7a836-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a836-117">Element</span></span>|<span data-ttu-id="7a836-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a836-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a836-119">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="7a836-119">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="7a836-120">Filtre eşleştiğinde ileti göndermek için yönlendirme filtreleri ve hedef uç noktalar arasındaki eşlemeler.</span><span class="sxs-lookup"><span data-stu-id="7a836-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a836-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a836-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7a836-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a836-122">Element</span></span>|<span data-ttu-id="7a836-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a836-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a836-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="7a836-124">\<routing></span></span>](routing.md)|<span data-ttu-id="7a836-125">Yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="7a836-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a836-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a836-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
