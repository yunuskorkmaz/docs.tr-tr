---
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7d055d4933f1ad625d6842f91a140f668c05c64e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205002"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="fd8f1-102">\<add> / \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="fd8f1-102">\<add> of \<namespaceTable></span></span>

<span data-ttu-id="fd8f1-103">Bu, daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşleme için bir ad alanı içeren bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd8f1-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="fd8f1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd8f1-104">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd8f1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd8f1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fd8f1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd8f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd8f1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd8f1-107">Attributes</span></span>  
  
|<span data-ttu-id="fd8f1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd8f1-108">Attribute</span></span>|<span data-ttu-id="fd8f1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd8f1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd8f1-110">ad alanı</span><span class="sxs-lookup"><span data-stu-id="fd8f1-110">namespace</span></span>|<span data-ttu-id="fd8f1-111">Ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fd8f1-111">A string containing the namespace.</span></span>|  
|<span data-ttu-id="fd8f1-112">koy</span><span class="sxs-lookup"><span data-stu-id="fd8f1-112">prefix</span></span>|<span data-ttu-id="fd8f1-113">Bu ad alanı için öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fd8f1-113">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd8f1-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd8f1-114">Child Elements</span></span>  

 <span data-ttu-id="fd8f1-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd8f1-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd8f1-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd8f1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fd8f1-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd8f1-117">Element</span></span>|<span data-ttu-id="fd8f1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd8f1-118">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="fd8f1-119">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd8f1-119">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd8f1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd8f1-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
