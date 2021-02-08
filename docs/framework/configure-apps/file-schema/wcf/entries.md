---
description: 'Hakkında daha fazla bilgi edinin: <entries>'
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: e5aefce4328c341b6d132765c8e726910241aae1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782110"
---
# \<entries>

<span data-ttu-id="66c22-102">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="66c22-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="66c22-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="66c22-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66c22-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="66c22-104">Attributes and Elements</span></span>  

 <span data-ttu-id="66c22-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66c22-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66c22-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="66c22-106">Attributes</span></span>  

 <span data-ttu-id="66c22-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="66c22-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66c22-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="66c22-108">Child Elements</span></span>  
  
|<span data-ttu-id="66c22-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="66c22-109">Element</span></span>|<span data-ttu-id="66c22-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66c22-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="66c22-111">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="66c22-111">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="66c22-112">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="66c22-112">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66c22-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="66c22-113">Parent Elements</span></span>  
  
|<span data-ttu-id="66c22-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="66c22-114">Element</span></span>|<span data-ttu-id="66c22-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66c22-115">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="66c22-116">Yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="66c22-116">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66c22-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66c22-117">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
