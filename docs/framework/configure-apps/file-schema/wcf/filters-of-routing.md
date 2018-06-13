---
title: '&lt;yönlendirme&gt; &lt;filtreleri&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 9f0fa9bf51d264346738172f57a8efca7950fdb7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753121"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="fcd42-102">&lt;yönlendirme&gt; &lt;filtreleri&gt;</span><span class="sxs-lookup"><span data-stu-id="fcd42-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="fcd42-103">Windows Communication Foundation (WCF) türü belirlenemiyor yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="fcd42-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="fcd42-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="fcd42-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="fcd42-105">&nbsp;&nbsp;[**\<Yönlendirme >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="fcd42-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="fcd42-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filtreleri >**</span><span class="sxs-lookup"><span data-stu-id="fcd42-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fcd42-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcd42-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="fcd42-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd42-108">Attributes and elements</span></span>

<span data-ttu-id="fcd42-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcd42-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fcd42-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fcd42-110">Attributes</span></span>

<span data-ttu-id="fcd42-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="fcd42-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="fcd42-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fcd42-112">Child elements</span></span>

|     | <span data-ttu-id="fcd42-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd42-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fcd42-114">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="fcd42-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="fcd42-115">Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtre içeren<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fcd42-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="fcd42-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd42-116">Parent elements</span></span>

|     | <span data-ttu-id="fcd42-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd42-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fcd42-118">**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="fcd42-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="fcd42-119">Windows Communication Foundation (WCF) türü belirlenemiyor yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak ne zaman bir filtre ile eşleşen için iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="fcd42-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fcd42-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcd42-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
