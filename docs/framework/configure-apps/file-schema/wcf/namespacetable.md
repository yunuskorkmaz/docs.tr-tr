---
title: '&lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a6646b94449a79c96a8720a798f48298ab32ee0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="fd5b3-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="fd5b3-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="fd5b3-103">Ardından yönlendirme XPath filtreleri kullanılabilir önek eşlemeleri için ad alanı içeren öğeleri kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd5b3-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="fd5b3-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="fd5b3-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="fd5b3-105">&nbsp;&nbsp;**\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="fd5b3-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="fd5b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="fd5b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fd5b3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd5b3-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="fd5b3-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="fd5b3-108">Attributes and elements</span></span>

<span data-ttu-id="fd5b3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd5b3-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd5b3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd5b3-110">Attributes</span></span>

<span data-ttu-id="fd5b3-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd5b3-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd5b3-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="fd5b3-112">Child elements</span></span>

|     | <span data-ttu-id="fd5b3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd5b3-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fd5b3-114">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="fd5b3-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="fd5b3-115">XPath ifadesi için kullanılan bir ad alanı öneki eşleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fd5b3-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="fd5b3-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="fd5b3-116">Parent elements</span></span>

|     | <span data-ttu-id="fd5b3-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd5b3-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fd5b3-118">**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="fd5b3-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="fd5b3-119">Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="fd5b3-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fd5b3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd5b3-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
