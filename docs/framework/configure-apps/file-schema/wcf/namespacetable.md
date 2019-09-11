---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855100"
---
# <a name="namespacetable"></a><span data-ttu-id="3c785-101">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="3c785-101">\<namespaceTable></span></span>

<span data-ttu-id="3c785-102">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3c785-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="3c785-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3c785-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3c785-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3c785-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3c785-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="3c785-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="3c785-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable >**</span><span class="sxs-lookup"><span data-stu-id="3c785-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c785-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c785-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c785-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="3c785-108">Attributes and elements</span></span>

<span data-ttu-id="3c785-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3c785-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c785-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3c785-110">Attributes</span></span>

<span data-ttu-id="3c785-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="3c785-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c785-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="3c785-112">Child elements</span></span>

|     | <span data-ttu-id="3c785-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c785-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3c785-114"> **\<Filtre >** </span><span class="sxs-lookup"><span data-stu-id="3c785-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="3c785-115">XPath ifadeleri için kullanılan bir ad alanı ön eki eşlemesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c785-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="3c785-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="3c785-116">Parent elements</span></span>

|     | <span data-ttu-id="3c785-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c785-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3c785-118"> **\<Yönlendirme >** </span><span class="sxs-lookup"><span data-stu-id="3c785-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="3c785-119">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.</span><span class="sxs-lookup"><span data-stu-id="3c785-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="3c785-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c785-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
