---
title: "&lt;yönlendirme&gt; &lt;filtreleri&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9dddd9f9ba5f4c2cea7e92c666e8d224ccf21cee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="c44a9-102">&lt;yönlendirme&gt; &lt;filtreleri&gt;</span><span class="sxs-lookup"><span data-stu-id="c44a9-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="c44a9-103">Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="c44a9-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="c44a9-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="c44a9-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="c44a9-105">&nbsp;&nbsp;[**\<Yönlendirme >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="c44a9-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="c44a9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filtreleri >**</span><span class="sxs-lookup"><span data-stu-id="c44a9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c44a9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c44a9-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c44a9-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c44a9-108">Attributes and elements</span></span>

<span data-ttu-id="c44a9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c44a9-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c44a9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c44a9-110">Attributes</span></span>

<span data-ttu-id="c44a9-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="c44a9-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c44a9-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c44a9-112">Child elements</span></span>

|     | <span data-ttu-id="c44a9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c44a9-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c44a9-114">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="c44a9-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="c44a9-115">Türünü belirleyen bir yönlendirme filtre içeren [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c44a9-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="c44a9-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c44a9-116">Parent elements</span></span>

|     | <span data-ttu-id="c44a9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c44a9-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c44a9-118">**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="c44a9-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="c44a9-119">Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="c44a9-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="c44a9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c44a9-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
