---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855283"
---
# \<entries>
<span data-ttu-id="1bb5d-101">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="1bb5d-101">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="1bb5d-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bb5d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bb5d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bb5d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1bb5d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1bb5d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bb5d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1bb5d-105">Attributes</span></span>  
 <span data-ttu-id="1bb5d-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="1bb5d-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1bb5d-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bb5d-107">Child Elements</span></span>  
  
|<span data-ttu-id="1bb5d-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="1bb5d-108">Element</span></span>|<span data-ttu-id="1bb5d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bb5d-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="1bb5d-110">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="1bb5d-110">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="1bb5d-111">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="1bb5d-111">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1bb5d-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1bb5d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1bb5d-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="1bb5d-113">Element</span></span>|<span data-ttu-id="1bb5d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bb5d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="1bb5d-115">Yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="1bb5d-115">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bb5d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bb5d-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
