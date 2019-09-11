---
title: <add> / <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850515"
---
# <a name="add-of-entries"></a><span data-ttu-id="fee25-102">\<\<girişlerin > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="fee25-102">\<add> of \<entries></span></span>
<span data-ttu-id="fee25-103">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşleyen bir yönlendirme girdisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fee25-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="fee25-104">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="fee25-104">Messages matching this filter will be sent to this destination.</span></span>  
  
<span data-ttu-id="fee25-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fee25-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fee25-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fee25-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fee25-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="fee25-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="fee25-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="fee25-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="fee25-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtretablo >** ](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="fee25-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="fee25-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<girdiler >** ](entries.md)</span><span class="sxs-lookup"><span data-stu-id="fee25-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)</span></span>\
<span data-ttu-id="fee25-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="fee25-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee25-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fee25-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fee25-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fee25-113">Attributes and Elements</span></span>  
 <span data-ttu-id="fee25-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fee25-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fee25-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fee25-115">Attributes</span></span>  
  
|<span data-ttu-id="fee25-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fee25-116">Attribute</span></span>|<span data-ttu-id="fee25-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fee25-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fee25-118">backupList</span><span class="sxs-lookup"><span data-stu-id="fee25-118">backupList</span></span>|<span data-ttu-id="fee25-119">Uç noktaların yedekleme listesine bir başvuru belirten dize.</span><span class="sxs-lookup"><span data-stu-id="fee25-119">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="fee25-120">uç noktası</span><span class="sxs-lookup"><span data-stu-id="fee25-120">endpoint</span></span>|<span data-ttu-id="fee25-121">`filterName` Özniteliği tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası başvurusunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fee25-121">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="fee25-122">Süzgeç</span><span class="sxs-lookup"><span data-stu-id="fee25-122">filterName</span></span>|<span data-ttu-id="fee25-123">Bir filtre öğesine başvuruyu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="fee25-123">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="fee25-124">priority</span><span class="sxs-lookup"><span data-stu-id="fee25-124">priority</span></span>|<span data-ttu-id="fee25-125">Bu girdinin önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="fee25-125">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="fee25-126">Yönlendirme tablosundaki girişler öncelik temelinde değerlendirilir, 0 en düşük önceliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="fee25-126">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="fee25-127">Belirli bir önceliğe yönelik tüm girişler aynı anda değerlendirilir ve geçerli öncelik için eşleşen bir giriş bulunamazsa, sonraki öncelik düzeyi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fee25-127">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="fee25-128">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fee25-128">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fee25-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fee25-129">Child Elements</span></span>  
 <span data-ttu-id="fee25-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="fee25-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fee25-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fee25-131">Parent Elements</span></span>  
  
|<span data-ttu-id="fee25-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="fee25-132">Element</span></span>|<span data-ttu-id="fee25-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fee25-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fee25-134">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="fee25-134">\<routing></span></span>](routing.md)|<span data-ttu-id="fee25-135">Yönlendirme eşleme girdilerini içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fee25-135">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fee25-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fee25-136">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
