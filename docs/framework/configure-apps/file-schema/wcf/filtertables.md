---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: faa26ca108010330475725f83dfd0c6668cfc6b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178209"
---
# \<filterTables>

<span data-ttu-id="a3942-101">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren yönlendirme tablolarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a3942-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="a3942-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a3942-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3942-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3942-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a3942-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3942-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3942-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3942-105">Attributes</span></span>  

 <span data-ttu-id="a3942-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="a3942-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3942-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3942-107">Child Elements</span></span>  
  
|<span data-ttu-id="a3942-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3942-108">Element</span></span>|<span data-ttu-id="a3942-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3942-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="a3942-110">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren bir yönlendirme tablosu.</span><span class="sxs-lookup"><span data-stu-id="a3942-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3942-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3942-111">Parent Elements</span></span>  
  
|<span data-ttu-id="a3942-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3942-112">Element</span></span>|<span data-ttu-id="a3942-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3942-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="a3942-114">Yönlendirme filtrelerini ve yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="a3942-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3942-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3942-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
