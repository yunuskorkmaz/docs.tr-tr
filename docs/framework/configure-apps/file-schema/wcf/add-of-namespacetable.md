---
description: 'Hakkında daha fazla bilgi <add> edinin: <namespaceTable>'
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: b7804bdec4a1fb2199c81ba0dde031b80b451d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750266"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="8e01d-103">\<add> / \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="8e01d-103">\<add> of \<namespaceTable></span></span>

<span data-ttu-id="8e01d-104">Bu, daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşleme için bir ad alanı içeren bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e01d-104">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="8e01d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e01d-105">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e01d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e01d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="8e01d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e01d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e01d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8e01d-108">Attributes</span></span>  
  
|<span data-ttu-id="8e01d-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8e01d-109">Attribute</span></span>|<span data-ttu-id="8e01d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e01d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e01d-111">ad alanı</span><span class="sxs-lookup"><span data-stu-id="8e01d-111">namespace</span></span>|<span data-ttu-id="8e01d-112">Ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="8e01d-112">A string containing the namespace.</span></span>|  
|<span data-ttu-id="8e01d-113">koy</span><span class="sxs-lookup"><span data-stu-id="8e01d-113">prefix</span></span>|<span data-ttu-id="8e01d-114">Bu ad alanı için öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="8e01d-114">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e01d-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e01d-115">Child Elements</span></span>  

 <span data-ttu-id="8e01d-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="8e01d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e01d-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8e01d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8e01d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="8e01d-118">Element</span></span>|<span data-ttu-id="8e01d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e01d-119">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="8e01d-120">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e01d-120">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e01d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e01d-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
