---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: ee7a0c23adca883af279addf9d1f221bd4056d00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772417"
---
# <a name="namespacetable"></a><span data-ttu-id="cc1b9-101">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="cc1b9-101">\<namespaceTable></span></span>

<span data-ttu-id="cc1b9-102">Ardından yönlendirme için XPath filtrelerinde kullanılan önek eşletirmeleri için ad alanı içeren bir öğe kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc1b9-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="cc1b9-103">**\<system.serviceModel>** </span><span class="sxs-lookup"><span data-stu-id="cc1b9-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="cc1b9-104">&nbsp;&nbsp;**\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="cc1b9-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="cc1b9-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="cc1b9-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="cc1b9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc1b9-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc1b9-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="cc1b9-107">Attributes and elements</span></span>

<span data-ttu-id="cc1b9-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc1b9-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc1b9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc1b9-109">Attributes</span></span>

<span data-ttu-id="cc1b9-110">None</span><span class="sxs-lookup"><span data-stu-id="cc1b9-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc1b9-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="cc1b9-111">Child elements</span></span>

|     | <span data-ttu-id="cc1b9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc1b9-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cc1b9-113">**\<Filtre >**</span><span class="sxs-lookup"><span data-stu-id="cc1b9-113">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="cc1b9-114">XPath ifadeleri için kullanılan ad alanı ön eki eşlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc1b9-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="cc1b9-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="cc1b9-115">Parent elements</span></span>

|     | <span data-ttu-id="cc1b9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc1b9-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cc1b9-117">**\<Yönlendirme >**</span><span class="sxs-lookup"><span data-stu-id="cc1b9-117">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="cc1b9-118">Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak ne zaman eşleşen bir filtre, iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="cc1b9-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="cc1b9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc1b9-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
