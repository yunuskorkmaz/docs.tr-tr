---
title: '&lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: fb2b324a2c128b470f1a9a21343408280c5e1862
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743250"
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="1ba17-102">&lt;namespaceTable&gt;</span><span class="sxs-lookup"><span data-stu-id="1ba17-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="1ba17-103">Ardından yönlendirme için XPath filtrelerinde kullanılan önek eşletirmeleri için ad alanı içeren bir öğe kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1ba17-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="1ba17-104">**\<system.serviceModel>** </span><span class="sxs-lookup"><span data-stu-id="1ba17-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="1ba17-105">&nbsp;&nbsp;**\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="1ba17-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="1ba17-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="1ba17-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="1ba17-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ba17-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ba17-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="1ba17-108">Attributes and elements</span></span>

<span data-ttu-id="1ba17-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ba17-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ba17-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1ba17-110">Attributes</span></span>

<span data-ttu-id="1ba17-111">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="1ba17-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ba17-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="1ba17-112">Child elements</span></span>

|     | <span data-ttu-id="1ba17-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ba17-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1ba17-114">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="1ba17-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="1ba17-115">XPath ifadeleri için kullanılan ad alanı ön eki eşlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ba17-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="1ba17-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="1ba17-116">Parent elements</span></span>

|     | <span data-ttu-id="1ba17-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ba17-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1ba17-118">**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="1ba17-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="1ba17-119">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak ne zaman eşleşen bir filtre, iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="1ba17-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="1ba17-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ba17-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
