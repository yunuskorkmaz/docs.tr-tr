---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: fc9c697aff2e9c26c7922a0acaf5577b0dea2dc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532376"
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="76a94-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="76a94-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="76a94-103">Hata işlemede kullanılan yedek hizmetlerin kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="76a94-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="76a94-104">Bir birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç nokta kümesine numaralandırır listesini yedekleme her alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="76a94-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="76a94-105">Listedeki ilk uç kapalı ise, yönlendirme hizmeti otomatik olarak bir listesi için devredilmesini.</span><span class="sxs-lookup"><span data-stu-id="76a94-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="76a94-106">Bu istemci uygulamanıza karmaşık desenlerle nasıl ele alınacağını ya da tüm hizmetlerinizin dağıtıldığı öğretmek zorunda kalmadan uygulamanıza güvenilirlik eklemeniz için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="76a94-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="76a94-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="76a94-107">\<system.serviceModel></span></span>  
<span data-ttu-id="76a94-108">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="76a94-108">\<routing></span></span>  
<span data-ttu-id="76a94-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="76a94-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a94-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76a94-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76a94-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="76a94-111">Attributes and Elements</span></span>  
 <span data-ttu-id="76a94-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76a94-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76a94-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="76a94-113">Attributes</span></span>  
 <span data-ttu-id="76a94-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="76a94-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="76a94-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="76a94-115">Child Elements</span></span>  
  
|<span data-ttu-id="76a94-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="76a94-116">Element</span></span>|<span data-ttu-id="76a94-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76a94-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76a94-118">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="76a94-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="76a94-119">Birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="76a94-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="76a94-120">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="76a94-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76a94-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="76a94-121">Parent Elements</span></span>  
  
|<span data-ttu-id="76a94-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="76a94-122">Element</span></span>|<span data-ttu-id="76a94-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76a94-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76a94-124">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="76a94-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="76a94-125">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak ne zaman eşleşen bir filtre, iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="76a94-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76a94-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76a94-126">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
