---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: d5feab6cb374f98e683cf15f797de4f478e23131
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919916"
---
# <a name="backuplist"></a><span data-ttu-id="169ff-101">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="169ff-101">\<backupList></span></span>
<span data-ttu-id="169ff-102">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz bir uç nokta kümesini belirten bir yedekleme listesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="169ff-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="169ff-103">Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.</span><span class="sxs-lookup"><span data-stu-id="169ff-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="169ff-104">Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="169ff-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="169ff-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="169ff-105">\<system.serviceModel></span></span>  
<span data-ttu-id="169ff-106">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="169ff-106">\<routing></span></span>  
<span data-ttu-id="169ff-107">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="169ff-107">\<backupLists></span></span>  
<span data-ttu-id="169ff-108">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="169ff-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="169ff-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="169ff-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="169ff-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="169ff-110">Attributes and Elements</span></span>  
 <span data-ttu-id="169ff-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="169ff-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="169ff-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="169ff-112">Attributes</span></span>  
  
|<span data-ttu-id="169ff-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="169ff-113">Attribute</span></span>|<span data-ttu-id="169ff-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169ff-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="169ff-115">name</span><span class="sxs-lookup"><span data-stu-id="169ff-115">name</span></span>|<span data-ttu-id="169ff-116">Bu uç nokta listesini tanımlamak için kullanılan adı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="169ff-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="169ff-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="169ff-117">Child Elements</span></span>  
  
|<span data-ttu-id="169ff-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="169ff-118">Element</span></span>|<span data-ttu-id="169ff-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169ff-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="169ff-120">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="169ff-120">\<filter></span></span>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="169ff-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="169ff-121">Parent Elements</span></span>  
  
|<span data-ttu-id="169ff-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="169ff-122">Element</span></span>|<span data-ttu-id="169ff-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="169ff-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="169ff-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="169ff-124">\<routing></span></span>](routing.md)|<span data-ttu-id="169ff-125">Yedekleme uç noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="169ff-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="169ff-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="169ff-126">Remarks</span></span>  
 <span data-ttu-id="169ff-127">Bu bölüm, birincil uç noktaya gönderilirken bir iletişim özel durumu olayında bir iletinin iletilebilecek sıralı bitiş noktaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="169ff-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="169ff-128">Add > özniteliğindelistelenen`endpointName` birincil uç noktaya gönderme bir iletişim özel durumuyla başarısız olursa, yönlendirme hizmeti iletiyi bu yapılandırma bölümündeki ilk uç noktaya göndermeye çalışır. [ \<](add-of-entries.md)</span><span class="sxs-lookup"><span data-stu-id="169ff-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="169ff-129">Aynı zamanda bir iletişim özel durumu ile başarısız olursa, yönlendirme hizmeti iletiyi bu bölümde bulunan sonraki iletiye göndermeye çalışır, çünkü gönderme girişimi başarılı olur, iletişim özel durumu dışında bir hata döndürür veya koleksiyon bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="169ff-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="169ff-130">Aşağıdaki örnekte, "hedef" adlı birincil uç noktaya gönderme bir iletişim özel durumu döndürürse, hizmet iletiyi "alternateServiceQueue" olarak göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="169ff-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="169ff-131">Bu girişim ayrıca bir iletişim özel durumu döndürürse, yönlendirme hizmeti iletiyi koleksiyondaki bir sonraki uç noktaya göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="169ff-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="169ff-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="169ff-132">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
