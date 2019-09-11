---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850277"
---
# <a name="backuplist"></a><span data-ttu-id="c83c5-101">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="c83c5-101">\<backupList></span></span>
<span data-ttu-id="c83c5-102">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz bir uç nokta kümesini belirten bir yedekleme listesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c83c5-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="c83c5-103">Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.</span><span class="sxs-lookup"><span data-stu-id="c83c5-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="c83c5-104">Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="c83c5-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="c83c5-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c83c5-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c83c5-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c83c5-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c83c5-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="c83c5-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="c83c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="c83c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="c83c5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupList >**</span><span class="sxs-lookup"><span data-stu-id="c83c5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83c5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c83c5-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c83c5-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c83c5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c83c5-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c83c5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c83c5-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c83c5-113">Attributes</span></span>  
  
|<span data-ttu-id="c83c5-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c83c5-114">Attribute</span></span>|<span data-ttu-id="c83c5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c83c5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c83c5-116">name</span><span class="sxs-lookup"><span data-stu-id="c83c5-116">name</span></span>|<span data-ttu-id="c83c5-117">Bu uç nokta listesini tanımlamak için kullanılan adı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c83c5-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c83c5-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c83c5-118">Child Elements</span></span>  
  
|<span data-ttu-id="c83c5-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c83c5-119">Element</span></span>|<span data-ttu-id="c83c5-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c83c5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c83c5-121">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="c83c5-121">\<filter></span></span>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="c83c5-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c83c5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c83c5-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c83c5-123">Element</span></span>|<span data-ttu-id="c83c5-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c83c5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c83c5-125">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="c83c5-125">\<routing></span></span>](routing.md)|<span data-ttu-id="c83c5-126">Yedekleme uç noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="c83c5-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c83c5-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c83c5-127">Remarks</span></span>  
 <span data-ttu-id="c83c5-128">Bu bölüm, birincil uç noktaya gönderilirken bir iletişim özel durumu olayında bir iletinin iletilebilecek sıralı bitiş noktaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="c83c5-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="c83c5-129">Add > özniteliğindelistelenen`endpointName` birincil uç noktaya gönderme bir iletişim özel durumuyla başarısız olursa, yönlendirme hizmeti iletiyi bu yapılandırma bölümündeki ilk uç noktaya göndermeye çalışır. [ \<](add-of-entries.md)</span><span class="sxs-lookup"><span data-stu-id="c83c5-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="c83c5-130">Aynı zamanda bir iletişim özel durumu ile başarısız olursa, yönlendirme hizmeti iletiyi bu bölümde bulunan sonraki iletiye göndermeye çalışır, çünkü gönderme girişimi başarılı olur, iletişim özel durumu dışında bir hata döndürür veya koleksiyon bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="c83c5-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="c83c5-131">Aşağıdaki örnekte, "hedef" adlı birincil uç noktaya gönderme bir iletişim özel durumu döndürürse, hizmet iletiyi "alternateServiceQueue" olarak göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c83c5-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="c83c5-132">Bu girişim ayrıca bir iletişim özel durumu döndürürse, yönlendirme hizmeti iletiyi koleksiyondaki bir sonraki uç noktaya göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c83c5-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="c83c5-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c83c5-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
