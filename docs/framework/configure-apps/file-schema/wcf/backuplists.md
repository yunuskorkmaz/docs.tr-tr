---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: b65cc4d04b5304e93b70509c9db3bc2248accb7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926430"
---
# <a name="backuplists"></a><span data-ttu-id="65171-101">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="65171-101">\<backupLists></span></span>
<span data-ttu-id="65171-102">Hata işlemede kullanılan bir yedekleme hizmetleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="65171-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="65171-103">Her alt öğe, yönlendirme hizmetinin birincil uç noktaya ulaşılamadığından kullanmasını istediğiniz uç nokta kümesini belirten bir yedekleme listesidir.</span><span class="sxs-lookup"><span data-stu-id="65171-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="65171-104">Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.</span><span class="sxs-lookup"><span data-stu-id="65171-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="65171-105">Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="65171-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="65171-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="65171-106">\<system.serviceModel></span></span>  
<span data-ttu-id="65171-107">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="65171-107">\<routing></span></span>  
<span data-ttu-id="65171-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="65171-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65171-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65171-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65171-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="65171-110">Attributes and Elements</span></span>  
 <span data-ttu-id="65171-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="65171-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65171-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="65171-112">Attributes</span></span>  
 <span data-ttu-id="65171-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="65171-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="65171-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="65171-114">Child Elements</span></span>  
  
|<span data-ttu-id="65171-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="65171-115">Element</span></span>|<span data-ttu-id="65171-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65171-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65171-117">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="65171-117">\<filter></span></span>](filter.md)|<span data-ttu-id="65171-118">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="65171-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="65171-119">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="65171-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65171-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="65171-120">Parent Elements</span></span>  
  
|<span data-ttu-id="65171-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="65171-121">Element</span></span>|<span data-ttu-id="65171-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65171-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65171-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="65171-123">\<routing></span></span>](routing.md)|<span data-ttu-id="65171-124">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.</span><span class="sxs-lookup"><span data-stu-id="65171-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65171-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65171-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
