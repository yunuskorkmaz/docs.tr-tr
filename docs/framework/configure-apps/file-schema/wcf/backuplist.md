---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 1e2b3eacbc845ad40030f3a48be2ef93c4ddbd8c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262441"
---
# <a name="backuplist"></a><span data-ttu-id="a6da6-101">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="a6da6-101">\<backupList></span></span>
<span data-ttu-id="a6da6-102">Bir birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç nokta kümesine numaralandırır yedek listesini tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a6da6-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="a6da6-103">Listedeki ilk uç kapalı ise, yönlendirme hizmeti otomatik olarak bir listesi için devredilmesini.</span><span class="sxs-lookup"><span data-stu-id="a6da6-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="a6da6-104">Bu istemci uygulamanıza karmaşık desenlerle nasıl ele alınacağını ya da tüm hizmetlerinizin dağıtıldığı öğretmek zorunda kalmadan uygulamanıza güvenilirlik eklemeniz için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6da6-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="a6da6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a6da6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a6da6-106">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="a6da6-106">\<routing></span></span>  
<span data-ttu-id="a6da6-107">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="a6da6-107">\<backupLists></span></span>  
<span data-ttu-id="a6da6-108">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="a6da6-108">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6da6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6da6-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6da6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6da6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a6da6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6da6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6da6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a6da6-112">Attributes</span></span>  
  
|<span data-ttu-id="a6da6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a6da6-113">Attribute</span></span>|<span data-ttu-id="a6da6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6da6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6da6-115">name</span><span class="sxs-lookup"><span data-stu-id="a6da6-115">name</span></span>|<span data-ttu-id="a6da6-116">Bu uç nokta listesini tanımlamak için kullanılan adı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a6da6-116">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6da6-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6da6-117">Child Elements</span></span>  
  
|<span data-ttu-id="a6da6-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6da6-118">Element</span></span>|<span data-ttu-id="a6da6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6da6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6da6-120">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="a6da6-120">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="a6da6-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6da6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a6da6-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6da6-122">Element</span></span>|<span data-ttu-id="a6da6-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6da6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6da6-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="a6da6-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="a6da6-125">Yedekleme uç noktaları listesi.</span><span class="sxs-lookup"><span data-stu-id="a6da6-125">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6da6-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6da6-126">Remarks</span></span>  
 <span data-ttu-id="a6da6-127">Bu bölümde, bir ileti için bir iletişim özel durumu olması durumunda birincil uç noktasına gönderilirken aktarılmaz uç noktaları sıralı bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a6da6-127">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="a6da6-128">Birincil uç noktaya gönderme listelenen `endpointName` özniteliği [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) bir iletişim özel durumu ile başarısız oluyor, yönlendirme hizmeti ilk uç noktasına bu iletiyi göndermeyi deneyecek yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="a6da6-128">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="a6da6-129">Bu da bir iletişim özel durumu ile başarısız olursa, yönlendirme hizmeti iletişim özel durumu veya tüm uç noktaların dışındaki bir hata gönderme girişimi başarılı olana kadar döndürür, bu bölümde yer alan sonraki iletiye ileti göndermeye çalışır koleksiyonu bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="a6da6-129">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="a6da6-130">Bir iletişim özel durumu "Hedef" adlı birincil uç noktaya gönderme döndürürse, aşağıdaki örnekte, "alternateServiceQueue" ileti göndermek hizmet dener.</span><span class="sxs-lookup"><span data-stu-id="a6da6-130">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="a6da6-131">Bu deneme bir iletişim özel durumu da döndürürse, yönlendirme hizmeti koleksiyonda sonraki uç nokta ileti göndermek dener.</span><span class="sxs-lookup"><span data-stu-id="a6da6-131">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6da6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6da6-132">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
