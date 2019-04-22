---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 6e44dbe3c0966c6d243db343b9f9b0dec2480cb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134452"
---
# <a name="backuplists"></a><span data-ttu-id="2da26-101">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="2da26-101">\<backupLists></span></span>
<span data-ttu-id="2da26-102">Hata işlemede kullanılan yedek hizmetlerin kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2da26-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="2da26-103">Bir birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç nokta kümesine numaralandırır listesini yedekleme her alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="2da26-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="2da26-104">Listedeki ilk uç kapalı ise, yönlendirme hizmeti otomatik olarak bir listesi için devredilmesini.</span><span class="sxs-lookup"><span data-stu-id="2da26-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="2da26-105">Bu istemci uygulamanıza karmaşık desenlerle nasıl ele alınacağını ya da tüm hizmetlerinizin dağıtıldığı öğretmek zorunda kalmadan uygulamanıza güvenilirlik eklemeniz için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2da26-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="2da26-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2da26-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2da26-107">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="2da26-107">\<routing></span></span>  
<span data-ttu-id="2da26-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="2da26-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2da26-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2da26-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2da26-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2da26-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2da26-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2da26-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2da26-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2da26-112">Attributes</span></span>  
 <span data-ttu-id="2da26-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="2da26-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2da26-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2da26-114">Child Elements</span></span>  
  
|<span data-ttu-id="2da26-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="2da26-115">Element</span></span>|<span data-ttu-id="2da26-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2da26-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2da26-117">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="2da26-117">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="2da26-118">Birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2da26-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="2da26-119">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="2da26-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2da26-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2da26-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2da26-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2da26-121">Element</span></span>|<span data-ttu-id="2da26-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2da26-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2da26-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="2da26-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="2da26-124">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak ne zaman eşleşen bir filtre, iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="2da26-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2da26-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2da26-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
