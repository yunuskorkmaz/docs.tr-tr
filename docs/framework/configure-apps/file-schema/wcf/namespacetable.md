---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 0316e983446644671ead2f8f843dc91b493b29c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933166"
---
# <a name="namespacetable"></a><span data-ttu-id="82888-101">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="82888-101">\<namespaceTable></span></span>

<span data-ttu-id="82888-102">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="82888-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="82888-103">**\<System. serviceModel >**  </span><span class="sxs-lookup"><span data-stu-id="82888-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="82888-104">&nbsp;&nbsp; **\<Yönlendirme >**  </span><span class="sxs-lookup"><span data-stu-id="82888-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="82888-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="82888-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="82888-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82888-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82888-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="82888-107">Attributes and elements</span></span>

<span data-ttu-id="82888-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82888-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="82888-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82888-109">Attributes</span></span>

<span data-ttu-id="82888-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="82888-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="82888-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="82888-111">Child elements</span></span>

|     | <span data-ttu-id="82888-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82888-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="82888-113"> **\<Filtre >** </span><span class="sxs-lookup"><span data-stu-id="82888-113">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="82888-114">XPath ifadeleri için kullanılan bir ad alanı ön eki eşlemesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82888-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="82888-115">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="82888-115">Parent elements</span></span>

|     | <span data-ttu-id="82888-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82888-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="82888-117"> **\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="82888-117">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="82888-118">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.</span><span class="sxs-lookup"><span data-stu-id="82888-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="82888-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82888-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
