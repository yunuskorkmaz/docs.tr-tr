---
title: '&lt;namespaceTable&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 1d3b61fa6653b3910e65b95fa96fd0657e72bf7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632917"
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="d0b16-102">&lt;namespaceTable&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="d0b16-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="d0b16-103">Eşleme sonra yönlendirme için XPath filtrelerinde kullanılan önek için ad alanı içeren bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0b16-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="d0b16-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d0b16-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d0b16-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="d0b16-105">\<routing></span></span>  
<span data-ttu-id="d0b16-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="d0b16-106">\<namespaceTable></span></span>  
<span data-ttu-id="d0b16-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d0b16-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b16-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0b16-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0b16-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0b16-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d0b16-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0b16-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0b16-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0b16-111">Attributes</span></span>  
  
|<span data-ttu-id="d0b16-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0b16-112">Attribute</span></span>|<span data-ttu-id="d0b16-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0b16-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0b16-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="d0b16-114">namespace</span></span>|<span data-ttu-id="d0b16-115">Ad alanı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="d0b16-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="d0b16-116">Ön eki</span><span class="sxs-lookup"><span data-stu-id="d0b16-116">prefix</span></span>|<span data-ttu-id="d0b16-117">Bu ad alanı ön eki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="d0b16-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0b16-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0b16-118">Child Elements</span></span>  
 <span data-ttu-id="d0b16-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0b16-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0b16-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0b16-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d0b16-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0b16-121">Element</span></span>|<span data-ttu-id="d0b16-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0b16-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0b16-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="d0b16-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="d0b16-124">Ardından yönlendirme için XPath filtrelerinde kullanılan önek eşletirmeleri için ad alanı içeren bir öğe kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d0b16-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0b16-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0b16-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
