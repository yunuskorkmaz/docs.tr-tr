---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: aefe7beec7335d80341e670961800907c2bd0200
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855100"
---
# \<namespaceTable>

<span data-ttu-id="100c2-101">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="100c2-101">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a><span data-ttu-id="100c2-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="100c2-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="100c2-103">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="100c2-103">Attributes and elements</span></span>

<span data-ttu-id="100c2-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="100c2-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="100c2-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="100c2-105">Attributes</span></span>

<span data-ttu-id="100c2-106">Yok</span><span class="sxs-lookup"><span data-stu-id="100c2-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="100c2-107">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="100c2-107">Child elements</span></span>

|     | <span data-ttu-id="100c2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="100c2-108">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="100c2-109">XPath ifadeleri için kullanılan bir ad alanı ön eki eşlemesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="100c2-109">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="100c2-110">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="100c2-110">Parent elements</span></span>

|     | <span data-ttu-id="100c2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="100c2-111">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="100c2-112">Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> . Ayrıca, bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="100c2-112">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="100c2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="100c2-113">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
