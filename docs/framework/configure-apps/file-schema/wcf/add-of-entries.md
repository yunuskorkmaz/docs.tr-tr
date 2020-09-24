---
title: <add> / <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 156d8b8d9d0eb05efbf306434ab4555a98bc317e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149055"
---
# <a name="add-of-entries"></a><span data-ttu-id="8f964-102">\<add> / \<entries></span><span class="sxs-lookup"><span data-stu-id="8f964-102">\<add> of \<entries></span></span>

<span data-ttu-id="8f964-103">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşleyen bir yönlendirme girdisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f964-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="8f964-104">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="8f964-104">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="8f964-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f964-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f964-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f964-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8f964-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f964-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f964-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8f964-108">Attributes</span></span>  
  
|<span data-ttu-id="8f964-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8f964-109">Attribute</span></span>|<span data-ttu-id="8f964-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f964-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f964-111">backupList</span><span class="sxs-lookup"><span data-stu-id="8f964-111">backupList</span></span>|<span data-ttu-id="8f964-112">Uç noktaların yedekleme listesine bir başvuru belirten dize.</span><span class="sxs-lookup"><span data-stu-id="8f964-112">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="8f964-113">endpoint</span><span class="sxs-lookup"><span data-stu-id="8f964-113">endpoint</span></span>|<span data-ttu-id="8f964-114">Özniteliği tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası başvurusunu belirten bir dize `filterName` .</span><span class="sxs-lookup"><span data-stu-id="8f964-114">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="8f964-115">Süzgeç</span><span class="sxs-lookup"><span data-stu-id="8f964-115">filterName</span></span>|<span data-ttu-id="8f964-116">Bir filtre öğesine başvuruyu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="8f964-116">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="8f964-117">Priority</span><span class="sxs-lookup"><span data-stu-id="8f964-117">priority</span></span>|<span data-ttu-id="8f964-118">Bu girdinin önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8f964-118">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="8f964-119">Yönlendirme tablosundaki girişler öncelik temelinde değerlendirilir, 0 en düşük önceliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="8f964-119">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="8f964-120">Belirli bir önceliğe yönelik tüm girişler aynı anda değerlendirilir ve geçerli öncelik için eşleşen bir giriş bulunamazsa, sonraki öncelik düzeyi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8f964-120">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="8f964-121">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8f964-121">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f964-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f964-122">Child Elements</span></span>  

 <span data-ttu-id="8f964-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="8f964-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f964-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8f964-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8f964-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="8f964-125">Element</span></span>|<span data-ttu-id="8f964-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f964-126">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="8f964-127">Yönlendirme eşleme girdilerini içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="8f964-127">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f964-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f964-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
