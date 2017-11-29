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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 470dd2dcc2e8554bb89eec159c6b96b24795c5d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="0f7e1-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="0f7e1-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="0f7e1-103">Ardından yönlendirme XPath filtreleri kullanılabilir önek eşlemeleri için ad alanı içeren öğeleri kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0f7e1-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="0f7e1-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="0f7e1-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="0f7e1-105">&nbsp;&nbsp;**\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="0f7e1-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="0f7e1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="0f7e1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0f7e1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f7e1-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="0f7e1-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="0f7e1-108">Attributes and elements</span></span>

<span data-ttu-id="0f7e1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f7e1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f7e1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f7e1-110">Attributes</span></span>

<span data-ttu-id="0f7e1-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="0f7e1-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f7e1-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0f7e1-112">Child elements</span></span>

|     | <span data-ttu-id="0f7e1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f7e1-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0f7e1-114">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="0f7e1-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="0f7e1-115">XPath ifadesi için kullanılan bir ad alanı öneki eşleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f7e1-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="0f7e1-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0f7e1-116">Parent elements</span></span>

|     | <span data-ttu-id="0f7e1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f7e1-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0f7e1-118">**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="0f7e1-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="0f7e1-119">Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="0f7e1-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0f7e1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f7e1-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
