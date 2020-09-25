---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 940bf28958251e7257b2cc19a9c5ff0059411bcd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201557"
---
# \<backupLists>

<span data-ttu-id="55a02-101">Hata işlemede kullanılan bir yedekleme hizmetleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="55a02-101">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="55a02-102">Her alt öğe, yönlendirme hizmetinin birincil uç noktaya ulaşılamadığından kullanmasını istediğiniz uç nokta kümesini belirten bir yedekleme listesidir.</span><span class="sxs-lookup"><span data-stu-id="55a02-102">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="55a02-103">Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.</span><span class="sxs-lookup"><span data-stu-id="55a02-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="55a02-104">Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="55a02-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="55a02-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="55a02-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55a02-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55a02-106">Attributes and Elements</span></span>  

 <span data-ttu-id="55a02-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55a02-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55a02-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55a02-108">Attributes</span></span>  

 <span data-ttu-id="55a02-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="55a02-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55a02-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55a02-110">Child Elements</span></span>  
  
|<span data-ttu-id="55a02-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="55a02-111">Element</span></span>|<span data-ttu-id="55a02-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55a02-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="55a02-113">Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="55a02-113">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="55a02-114">.</span><span class="sxs-lookup"><span data-stu-id="55a02-114">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55a02-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55a02-115">Parent Elements</span></span>  
  
|<span data-ttu-id="55a02-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="55a02-116">Element</span></span>|<span data-ttu-id="55a02-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55a02-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="55a02-118">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> . Ayrıca, bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55a02-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55a02-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55a02-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
