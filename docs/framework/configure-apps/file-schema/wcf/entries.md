---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: d3dae510ac62735138a24b8fb97a8acfffde1a98
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189974"
---
# \<entries>

<span data-ttu-id="fcd0b-101">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="fcd0b-101">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="fcd0b-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="fcd0b-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcd0b-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd0b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="fcd0b-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcd0b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcd0b-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fcd0b-105">Attributes</span></span>  

 <span data-ttu-id="fcd0b-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="fcd0b-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fcd0b-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd0b-107">Child Elements</span></span>  
  
|<span data-ttu-id="fcd0b-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcd0b-108">Element</span></span>|<span data-ttu-id="fcd0b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd0b-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="fcd0b-110">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="fcd0b-110">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="fcd0b-111">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="fcd0b-111">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fcd0b-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd0b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fcd0b-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcd0b-113">Element</span></span>|<span data-ttu-id="fcd0b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd0b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="fcd0b-115">Yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fcd0b-115">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcd0b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcd0b-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
