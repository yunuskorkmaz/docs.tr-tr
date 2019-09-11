---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850261"
---
# <a name="backuplists"></a><span data-ttu-id="b4fb1-101">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="b4fb1-101">\<backupLists></span></span>
<span data-ttu-id="b4fb1-102">Hata işlemede kullanılan bir yedekleme hizmetleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="b4fb1-103">Her alt öğe, yönlendirme hizmetinin birincil uç noktaya ulaşılamadığından kullanmasını istediğiniz uç nokta kümesini belirten bir yedekleme listesidir.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="b4fb1-104">Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="b4fb1-105">Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="b4fb1-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4fb1-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b4fb1-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b4fb1-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b4fb1-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="b4fb1-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="b4fb1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupLists >**</span><span class="sxs-lookup"><span data-stu-id="b4fb1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4fb1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4fb1-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4fb1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4fb1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b4fb1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4fb1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b4fb1-113">Attributes</span></span>  
 <span data-ttu-id="b4fb1-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4fb1-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4fb1-115">Child Elements</span></span>  
  
|<span data-ttu-id="b4fb1-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4fb1-116">Element</span></span>|<span data-ttu-id="b4fb1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4fb1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4fb1-118">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="b4fb1-118">\<filter></span></span>](filter.md)|<span data-ttu-id="b4fb1-119">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="b4fb1-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4fb1-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4fb1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b4fb1-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4fb1-122">Element</span></span>|<span data-ttu-id="b4fb1-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4fb1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4fb1-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="b4fb1-124">\<routing></span></span>](routing.md)|<span data-ttu-id="b4fb1-125">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4fb1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4fb1-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
