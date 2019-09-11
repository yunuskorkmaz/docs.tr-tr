---
title: <filters> / <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855243"
---
# <a name="filters-of-routing"></a><span data-ttu-id="2e9f1-102">\<\<yönlendirme > > filtreler</span><span class="sxs-lookup"><span data-stu-id="2e9f1-102">\<filters> of \<routing></span></span>

<span data-ttu-id="2e9f1-103">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e9f1-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="2e9f1-104">[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2e9f1-104">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2e9f1-105">&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="2e9f1-105">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="2e9f1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Filtreler >**</span><span class="sxs-lookup"><span data-stu-id="2e9f1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9f1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e9f1-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e9f1-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="2e9f1-108">Attributes and elements</span></span>

<span data-ttu-id="2e9f1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e9f1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e9f1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2e9f1-110">Attributes</span></span>

<span data-ttu-id="2e9f1-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="2e9f1-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e9f1-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2e9f1-112">Child elements</span></span>

|     | <span data-ttu-id="2e9f1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e9f1-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2e9f1-114"> **\<Filtre >** </span><span class="sxs-lookup"><span data-stu-id="2e9f1-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="2e9f1-115">Gelen iletiler değerlendirilirken Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü belirleyen bir yönlendirme filtresi içerir.</span><span class="sxs-lookup"><span data-stu-id="2e9f1-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="2e9f1-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="2e9f1-116">Parent elements</span></span>

|     | <span data-ttu-id="2e9f1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e9f1-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2e9f1-118"> **\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="2e9f1-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="2e9f1-119">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.</span><span class="sxs-lookup"><span data-stu-id="2e9f1-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="2e9f1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e9f1-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
