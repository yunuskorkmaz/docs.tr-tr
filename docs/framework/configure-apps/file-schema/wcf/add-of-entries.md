---
title: <add> / <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850515"
---
# <a name="add-of-entries"></a><span data-ttu-id="6f980-102">\<add> / \<entries></span><span class="sxs-lookup"><span data-stu-id="6f980-102">\<add> of \<entries></span></span>
<span data-ttu-id="6f980-103">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşleyen bir yönlendirme girdisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6f980-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="6f980-104">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="6f980-104">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6f980-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f980-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f980-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f980-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6f980-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f980-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f980-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f980-108">Attributes</span></span>  
  
|<span data-ttu-id="6f980-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6f980-109">Attribute</span></span>|<span data-ttu-id="6f980-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f980-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f980-111">backupList</span><span class="sxs-lookup"><span data-stu-id="6f980-111">backupList</span></span>|<span data-ttu-id="6f980-112">Uç noktaların yedekleme listesine bir başvuru belirten dize.</span><span class="sxs-lookup"><span data-stu-id="6f980-112">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="6f980-113">endpoint</span><span class="sxs-lookup"><span data-stu-id="6f980-113">endpoint</span></span>|<span data-ttu-id="6f980-114">Özniteliği tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası başvurusunu belirten bir dize `filterName` .</span><span class="sxs-lookup"><span data-stu-id="6f980-114">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="6f980-115">Süzgeç</span><span class="sxs-lookup"><span data-stu-id="6f980-115">filterName</span></span>|<span data-ttu-id="6f980-116">Bir filtre öğesine başvuruyu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="6f980-116">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="6f980-117">Priority</span><span class="sxs-lookup"><span data-stu-id="6f980-117">priority</span></span>|<span data-ttu-id="6f980-118">Bu girdinin önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6f980-118">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="6f980-119">Yönlendirme tablosundaki girişler öncelik temelinde değerlendirilir, 0 en düşük önceliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="6f980-119">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="6f980-120">Belirli bir önceliğe yönelik tüm girişler aynı anda değerlendirilir ve geçerli öncelik için eşleşen bir giriş bulunamazsa, sonraki öncelik düzeyi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6f980-120">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="6f980-121">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6f980-121">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f980-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f980-122">Child Elements</span></span>  
 <span data-ttu-id="6f980-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="6f980-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f980-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f980-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6f980-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f980-125">Element</span></span>|<span data-ttu-id="6f980-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f980-126">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="6f980-127">Yönlendirme eşleme girdilerini içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="6f980-127">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f980-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f980-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
