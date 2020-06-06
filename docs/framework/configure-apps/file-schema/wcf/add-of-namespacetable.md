---
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850387"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="221a5-102">\<add> / \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="221a5-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="221a5-103">Bu, daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşleme için bir ad alanı içeren bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="221a5-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="221a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="221a5-104">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="221a5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="221a5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="221a5-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="221a5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="221a5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="221a5-107">Attributes</span></span>  
  
|<span data-ttu-id="221a5-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="221a5-108">Attribute</span></span>|<span data-ttu-id="221a5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="221a5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="221a5-110">ad alanı</span><span class="sxs-lookup"><span data-stu-id="221a5-110">namespace</span></span>|<span data-ttu-id="221a5-111">Ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="221a5-111">A string containing the namespace.</span></span>|  
|<span data-ttu-id="221a5-112">koy</span><span class="sxs-lookup"><span data-stu-id="221a5-112">prefix</span></span>|<span data-ttu-id="221a5-113">Bu ad alanı için öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="221a5-113">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="221a5-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="221a5-114">Child Elements</span></span>  
 <span data-ttu-id="221a5-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="221a5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="221a5-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="221a5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="221a5-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="221a5-117">Element</span></span>|<span data-ttu-id="221a5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="221a5-118">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="221a5-119">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="221a5-119">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="221a5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="221a5-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
