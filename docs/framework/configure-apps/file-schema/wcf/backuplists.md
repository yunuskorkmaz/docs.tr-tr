---
title: '&lt;backupLists&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fee9e455189d5be1c81fb950eff3882aa8222b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="a7467-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="a7467-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="a7467-103">Bir hata işlemede kullanılan yedekleme hizmetler kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a7467-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="a7467-104">Her alt öğesi birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalar kümesi numaralandırır yedek bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="a7467-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="a7467-105">Listedeki ilk uç noktası kapalı ise, yönlendirme hizmeti otomatik olarak yük için listedeki bir sonraki devretme.</span><span class="sxs-lookup"><span data-stu-id="a7467-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="a7467-106">Bu karmaşık desenleri nasıl ele alınacağını veya hizmetlerinizin tümünün dağıtıldığı istemci uygulamanızı öğretmek gerekmeden güvenilirlik uygulamanıza eklemek için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7467-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="a7467-107">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a7467-107">\<system.serviceModel></span></span>  
<span data-ttu-id="a7467-108">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="a7467-108">\<routing></span></span>  
<span data-ttu-id="a7467-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="a7467-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7467-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7467-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7467-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7467-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a7467-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7467-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7467-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7467-113">Attributes</span></span>  
 <span data-ttu-id="a7467-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7467-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7467-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7467-115">Child Elements</span></span>  
  
|<span data-ttu-id="a7467-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7467-116">Element</span></span>|<span data-ttu-id="a7467-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7467-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7467-118">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="a7467-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="a7467-119">Birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktaları listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a7467-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="a7467-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="a7467-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7467-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7467-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a7467-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7467-122">Element</span></span>|<span data-ttu-id="a7467-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7467-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7467-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="a7467-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="a7467-125">Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="a7467-125">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7467-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7467-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
