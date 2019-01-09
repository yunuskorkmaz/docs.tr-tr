---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 55b5565ffe9d3e9e7ea41d2a2e2f380490be1781
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151429"
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="0b9fe-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="0b9fe-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="0b9fe-103">Ardından yönlendirme için XPath filtrelerinde kullanılan önek eşletirmeleri için ad alanı içeren bir öğe kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b9fe-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="0b9fe-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="0b9fe-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="0b9fe-105">&nbsp;&nbsp;**\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="0b9fe-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="0b9fe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="0b9fe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="0b9fe-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b9fe-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b9fe-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="0b9fe-108">Attributes and elements</span></span>

<span data-ttu-id="0b9fe-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b9fe-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b9fe-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0b9fe-110">Attributes</span></span>

<span data-ttu-id="0b9fe-111">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="0b9fe-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b9fe-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="0b9fe-112">Child elements</span></span>

|     | <span data-ttu-id="0b9fe-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b9fe-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0b9fe-114">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="0b9fe-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="0b9fe-115">XPath ifadeleri için kullanılan ad alanı ön eki eşlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b9fe-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="0b9fe-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="0b9fe-116">Parent elements</span></span>

|     | <span data-ttu-id="0b9fe-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b9fe-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0b9fe-118">**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="0b9fe-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="0b9fe-119">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak ne zaman eşleşen bir filtre, iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="0b9fe-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0b9fe-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b9fe-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
