---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5fb89ce5a942db40b07a65f59ddd05ab4cd624aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="2c49c-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="2c49c-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="2c49c-103">Bir hata işlemede kullanılan yedekleme hizmetler kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2c49c-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="2c49c-104">Her alt öğesi birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalar kümesi numaralandırır yedek bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="2c49c-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="2c49c-105">Listedeki ilk uç noktası kapalı ise, yönlendirme hizmeti otomatik olarak yük için listedeki bir sonraki devretme.</span><span class="sxs-lookup"><span data-stu-id="2c49c-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="2c49c-106">Bu karmaşık desenleri nasıl ele alınacağını veya hizmetlerinizin tümünün dağıtıldığı istemci uygulamanızı öğretmek gerekmeden güvenilirlik uygulamanıza eklemek için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c49c-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="2c49c-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2c49c-107">\<system.serviceModel></span></span>  
<span data-ttu-id="2c49c-108">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="2c49c-108">\<routing></span></span>  
<span data-ttu-id="2c49c-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="2c49c-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c49c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c49c-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c49c-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c49c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2c49c-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c49c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c49c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c49c-113">Attributes</span></span>  
 <span data-ttu-id="2c49c-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="2c49c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c49c-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c49c-115">Child Elements</span></span>  
  
|<span data-ttu-id="2c49c-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c49c-116">Element</span></span>|<span data-ttu-id="2c49c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c49c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c49c-118">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="2c49c-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="2c49c-119">Birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktaları listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2c49c-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="2c49c-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="2c49c-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c49c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c49c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2c49c-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c49c-122">Element</span></span>|<span data-ttu-id="2c49c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c49c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c49c-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="2c49c-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="2c49c-125">Windows Communication Foundation (WCF) türü belirlenemiyor yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak ne zaman bir filtre ile eşleşen için iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="2c49c-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c49c-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c49c-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
