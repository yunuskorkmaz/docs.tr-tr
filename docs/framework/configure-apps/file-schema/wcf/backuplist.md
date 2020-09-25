---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 8f4dcf8f7d71cfa2ed9944822d7cce974e7f1979
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201570"
---
# \<backupList>

<span data-ttu-id="aa01e-101">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz bir uç nokta kümesini belirten bir yedekleme listesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aa01e-101">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="aa01e-102">Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.</span><span class="sxs-lookup"><span data-stu-id="aa01e-102">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="aa01e-103">Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="aa01e-103">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a><span data-ttu-id="aa01e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="aa01e-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa01e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa01e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="aa01e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa01e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa01e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa01e-107">Attributes</span></span>  
  
|<span data-ttu-id="aa01e-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aa01e-108">Attribute</span></span>|<span data-ttu-id="aa01e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa01e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa01e-110">name</span><span class="sxs-lookup"><span data-stu-id="aa01e-110">name</span></span>|<span data-ttu-id="aa01e-111">Bu uç nokta listesini tanımlamak için kullanılan adı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="aa01e-111">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa01e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa01e-112">Child Elements</span></span>  
  
|<span data-ttu-id="aa01e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa01e-113">Element</span></span>|<span data-ttu-id="aa01e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa01e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="aa01e-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa01e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="aa01e-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa01e-116">Element</span></span>|<span data-ttu-id="aa01e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa01e-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="aa01e-118">Yedekleme uç noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="aa01e-118">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa01e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa01e-119">Remarks</span></span>  

 <span data-ttu-id="aa01e-120">Bu bölüm, birincil uç noktaya gönderilirken bir iletişim özel durumu olayında bir iletinin iletilebilecek sıralı bitiş noktaları koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="aa01e-120">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="aa01e-121">Özniteliğinde listelenen birincil uç noktaya gönderme bir `endpointName` [\<add>](add-of-entries.md) iletişim özel durumuyla başarısız olursa, yönlendirme hizmeti iletiyi bu yapılandırma bölümünde ilk uç noktaya göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="aa01e-121">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="aa01e-122">Bu aynı zamanda bir iletişim özel durumu ile başarısız olursa, yönlendirme hizmeti iletiyi bu bölümde yer alan sonraki iletiye göndermeye çalışır, bu da gönderme girişimi başarılı olur, iletişim özel durumu dışında bir hata döndürür veya koleksiyondaki tüm uç noktalar bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="aa01e-122">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="aa01e-123">Aşağıdaki örnekte, "hedef" adlı birincil uç noktaya gönderme bir iletişim özel durumu döndürürse, hizmet iletiyi "alternateServiceQueue" olarak göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="aa01e-123">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="aa01e-124">Bu girişim ayrıca bir iletişim özel durumu döndürürse, yönlendirme hizmeti iletiyi koleksiyondaki bir sonraki uç noktaya göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="aa01e-124">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa01e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa01e-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
