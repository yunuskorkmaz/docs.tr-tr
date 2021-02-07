---
description: 'Hakkında daha fazla bilgi edinin: <backupList>'
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 5323c8dad827ebb95e3cad65b3ad527d04517e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749720"
---
# \<backupList>

<span data-ttu-id="abb6b-102">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz bir uç nokta kümesini belirten bir yedekleme listesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="abb6b-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="abb6b-103">Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.</span><span class="sxs-lookup"><span data-stu-id="abb6b-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="abb6b-104">Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="abb6b-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a><span data-ttu-id="abb6b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="abb6b-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abb6b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="abb6b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="abb6b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="abb6b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abb6b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="abb6b-108">Attributes</span></span>  
  
|<span data-ttu-id="abb6b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="abb6b-109">Attribute</span></span>|<span data-ttu-id="abb6b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abb6b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abb6b-111">name</span><span class="sxs-lookup"><span data-stu-id="abb6b-111">name</span></span>|<span data-ttu-id="abb6b-112">Bu uç nokta listesini tanımlamak için kullanılan adı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="abb6b-112">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abb6b-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="abb6b-113">Child Elements</span></span>  
  
|<span data-ttu-id="abb6b-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="abb6b-114">Element</span></span>|<span data-ttu-id="abb6b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abb6b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="abb6b-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="abb6b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="abb6b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="abb6b-117">Element</span></span>|<span data-ttu-id="abb6b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abb6b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="abb6b-119">Yedekleme uç noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="abb6b-119">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abb6b-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abb6b-120">Remarks</span></span>  

 <span data-ttu-id="abb6b-121">Bu bölüm, birincil uç noktaya gönderilirken bir iletişim özel durumu olayında bir iletinin iletilebilecek sıralı bitiş noktaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="abb6b-121">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="abb6b-122">Özniteliğinde listelenen birincil uç noktaya gönderme bir `endpointName` [\<add>](add-of-entries.md) iletişim özel durumuyla başarısız olursa, yönlendirme hizmeti iletiyi bu yapılandırma bölümünde ilk uç noktaya göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="abb6b-122">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="abb6b-123">Bu aynı zamanda bir iletişim özel durumu ile başarısız olursa, yönlendirme hizmeti iletiyi bu bölümde yer alan sonraki iletiye göndermeye çalışır, bu da gönderme girişimi başarılı olur, iletişim özel durumu dışında bir hata döndürür veya koleksiyondaki tüm uç noktalar bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="abb6b-123">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="abb6b-124">Aşağıdaki örnekte, "hedef" adlı birincil uç noktaya gönderme bir iletişim özel durumu döndürürse, hizmet iletiyi "alternateServiceQueue" olarak göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="abb6b-124">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="abb6b-125">Bu girişim ayrıca bir iletişim özel durumu döndürürse, yönlendirme hizmeti iletiyi koleksiyondaki bir sonraki uç noktaya göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="abb6b-125">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abb6b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abb6b-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
