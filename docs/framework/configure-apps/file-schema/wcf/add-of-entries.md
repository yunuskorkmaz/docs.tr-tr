---
description: 'Hakkında daha fazla bilgi <add> edinin: <entries>'
title: <add> / <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 0be24fb9d2327d411368dd05afc21156dfaf3d3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803977"
---
# <a name="add-of-entries"></a><span data-ttu-id="6dd78-103">\<add> / \<entries></span><span class="sxs-lookup"><span data-stu-id="6dd78-103">\<add> of \<entries></span></span>

<span data-ttu-id="6dd78-104">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşleyen bir yönlendirme girdisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6dd78-104">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="6dd78-105">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="6dd78-105">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6dd78-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6dd78-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dd78-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6dd78-107">Attributes and Elements</span></span>  

 <span data-ttu-id="6dd78-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6dd78-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dd78-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6dd78-109">Attributes</span></span>  
  
|<span data-ttu-id="6dd78-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6dd78-110">Attribute</span></span>|<span data-ttu-id="6dd78-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6dd78-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6dd78-112">backupList</span><span class="sxs-lookup"><span data-stu-id="6dd78-112">backupList</span></span>|<span data-ttu-id="6dd78-113">Uç noktaların yedekleme listesine bir başvuru belirten dize.</span><span class="sxs-lookup"><span data-stu-id="6dd78-113">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="6dd78-114">endpoint</span><span class="sxs-lookup"><span data-stu-id="6dd78-114">endpoint</span></span>|<span data-ttu-id="6dd78-115">Özniteliği tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası başvurusunu belirten bir dize `filterName` .</span><span class="sxs-lookup"><span data-stu-id="6dd78-115">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="6dd78-116">Süzgeç</span><span class="sxs-lookup"><span data-stu-id="6dd78-116">filterName</span></span>|<span data-ttu-id="6dd78-117">Bir filtre öğesine başvuruyu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="6dd78-117">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="6dd78-118">Priority</span><span class="sxs-lookup"><span data-stu-id="6dd78-118">priority</span></span>|<span data-ttu-id="6dd78-119">Bu girdinin önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6dd78-119">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="6dd78-120">Yönlendirme tablosundaki girişler öncelik temelinde değerlendirilir, 0 en düşük önceliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="6dd78-120">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="6dd78-121">Belirli bir önceliğe yönelik tüm girişler aynı anda değerlendirilir ve geçerli öncelik için eşleşen bir giriş bulunamazsa, sonraki öncelik düzeyi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6dd78-121">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="6dd78-122">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6dd78-122">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6dd78-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6dd78-123">Child Elements</span></span>  

 <span data-ttu-id="6dd78-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="6dd78-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6dd78-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6dd78-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6dd78-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="6dd78-126">Element</span></span>|<span data-ttu-id="6dd78-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6dd78-127">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="6dd78-128">Yönlendirme eşleme girdilerini içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="6dd78-128">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6dd78-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dd78-129">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
