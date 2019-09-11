---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855203"
---
# <a name="filtertables"></a><span data-ttu-id="b47cf-101">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="b47cf-101">\<filterTables></span></span>
<span data-ttu-id="b47cf-102">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren yönlendirme tablolarını tanımlamaya yönelik bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b47cf-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="b47cf-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b47cf-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b47cf-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b47cf-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b47cf-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="b47cf-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="b47cf-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="b47cf-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47cf-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b47cf-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b47cf-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b47cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b47cf-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b47cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b47cf-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b47cf-110">Attributes</span></span>  
 <span data-ttu-id="b47cf-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="b47cf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b47cf-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b47cf-112">Child Elements</span></span>  
  
|<span data-ttu-id="b47cf-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="b47cf-113">Element</span></span>|<span data-ttu-id="b47cf-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b47cf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b47cf-115">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="b47cf-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="b47cf-116">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren bir yönlendirme tablosu.</span><span class="sxs-lookup"><span data-stu-id="b47cf-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b47cf-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b47cf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b47cf-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="b47cf-118">Element</span></span>|<span data-ttu-id="b47cf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b47cf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b47cf-120">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="b47cf-120">\<routing></span></span>](routing.md)|<span data-ttu-id="b47cf-121">Yönlendirme filtrelerini ve yönlendirme tablolarını içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="b47cf-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b47cf-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b47cf-122">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
