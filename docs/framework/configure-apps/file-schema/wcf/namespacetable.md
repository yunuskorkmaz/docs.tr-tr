---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 31d661f39f9e3de0f7012c7fa52d4964e7ee4a69
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748886"
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="491c6-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="491c6-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="491c6-103">Ardından yönlendirme XPath filtreleri kullanılabilir önek eşlemeleri için ad alanı içeren öğeleri kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="491c6-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="491c6-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="491c6-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="491c6-105">&nbsp;&nbsp;**\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="491c6-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="491c6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="491c6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="491c6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="491c6-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="491c6-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="491c6-108">Attributes and elements</span></span>

<span data-ttu-id="491c6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="491c6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="491c6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="491c6-110">Attributes</span></span>

<span data-ttu-id="491c6-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="491c6-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="491c6-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="491c6-112">Child elements</span></span>

|     | <span data-ttu-id="491c6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="491c6-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="491c6-114">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="491c6-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="491c6-115">XPath ifadesi için kullanılan bir ad alanı öneki eşleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="491c6-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="491c6-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="491c6-116">Parent elements</span></span>

|     | <span data-ttu-id="491c6-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="491c6-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="491c6-118">**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="491c6-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="491c6-119">Windows Communication Foundation (WCF) türü belirlenemiyor yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak ne zaman bir filtre ile eşleşen için iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="491c6-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="491c6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="491c6-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
