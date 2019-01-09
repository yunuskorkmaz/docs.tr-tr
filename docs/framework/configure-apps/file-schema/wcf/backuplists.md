---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: ff363f97b25496dc9bb3a691de7c8abf77c0dc9d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149130"
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="d0d9c-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="d0d9c-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="d0d9c-103">Hata işlemede kullanılan yedek hizmetlerin kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="d0d9c-104">Bir birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç nokta kümesine numaralandırır listesini yedekleme her alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="d0d9c-105">Listedeki ilk uç kapalı ise, yönlendirme hizmeti otomatik olarak bir listesi için devredilmesini.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="d0d9c-106">Bu istemci uygulamanıza karmaşık desenlerle nasıl ele alınacağını ya da tüm hizmetlerinizin dağıtıldığı öğretmek zorunda kalmadan uygulamanıza güvenilirlik eklemeniz için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="d0d9c-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d0d9c-107">\<system.serviceModel></span></span>  
<span data-ttu-id="d0d9c-108">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="d0d9c-108">\<routing></span></span>  
<span data-ttu-id="d0d9c-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="d0d9c-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d9c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0d9c-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0d9c-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0d9c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d0d9c-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0d9c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0d9c-113">Attributes</span></span>  
 <span data-ttu-id="d0d9c-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0d9c-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0d9c-115">Child Elements</span></span>  
  
|<span data-ttu-id="d0d9c-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0d9c-116">Element</span></span>|<span data-ttu-id="d0d9c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0d9c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0d9c-118">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="d0d9c-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="d0d9c-119">Birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="d0d9c-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0d9c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0d9c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d0d9c-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0d9c-122">Element</span></span>|<span data-ttu-id="d0d9c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0d9c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0d9c-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="d0d9c-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d0d9c-125">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak ne zaman eşleşen bir filtre, iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0d9c-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0d9c-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
