---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855283"
---
# <a name="entries"></a><span data-ttu-id="e1dfb-101">\<girdiler ></span><span class="sxs-lookup"><span data-stu-id="e1dfb-101">\<entries></span></span>
<span data-ttu-id="e1dfb-102">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="e1dfb-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="e1dfb-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e1dfb-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e1dfb-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e1dfb-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e1dfb-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="e1dfb-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="e1dfb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="e1dfb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="e1dfb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtretablo >** ](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="e1dfb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="e1dfb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<girdiler >**</span><span class="sxs-lookup"><span data-stu-id="e1dfb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1dfb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1dfb-109">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1dfb-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1dfb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e1dfb-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1dfb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1dfb-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e1dfb-112">Attributes</span></span>  
 <span data-ttu-id="e1dfb-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="e1dfb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1dfb-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1dfb-114">Child Elements</span></span>  
  
|<span data-ttu-id="e1dfb-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1dfb-115">Element</span></span>|<span data-ttu-id="e1dfb-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1dfb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1dfb-117">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="e1dfb-117">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="e1dfb-118">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="e1dfb-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="e1dfb-119">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="e1dfb-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1dfb-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e1dfb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1dfb-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e1dfb-121">Element</span></span>|<span data-ttu-id="e1dfb-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1dfb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1dfb-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="e1dfb-123">\<routing></span></span>](routing.md)|<span data-ttu-id="e1dfb-124">Yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="e1dfb-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1dfb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1dfb-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
