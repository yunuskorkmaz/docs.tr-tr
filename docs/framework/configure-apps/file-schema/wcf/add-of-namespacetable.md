---
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e65b66170465a8b3bb60754feebb7730b959d9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089724"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="5065c-102">\<Ekle >, \<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="5065c-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="5065c-103">Eşleme sonra yönlendirme için XPath filtrelerinde kullanılan önek için ad alanı içeren bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5065c-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="5065c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5065c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5065c-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="5065c-105">\<routing></span></span>  
<span data-ttu-id="5065c-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="5065c-106">\<namespaceTable></span></span>  
<span data-ttu-id="5065c-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="5065c-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5065c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5065c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5065c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5065c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5065c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5065c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5065c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5065c-111">Attributes</span></span>  
  
|<span data-ttu-id="5065c-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5065c-112">Attribute</span></span>|<span data-ttu-id="5065c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5065c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5065c-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="5065c-114">namespace</span></span>|<span data-ttu-id="5065c-115">Ad alanı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5065c-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="5065c-116">Ön eki</span><span class="sxs-lookup"><span data-stu-id="5065c-116">prefix</span></span>|<span data-ttu-id="5065c-117">Bu ad alanı ön eki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5065c-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5065c-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5065c-118">Child Elements</span></span>  
 <span data-ttu-id="5065c-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="5065c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5065c-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5065c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5065c-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="5065c-121">Element</span></span>|<span data-ttu-id="5065c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5065c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5065c-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="5065c-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="5065c-124">Ardından yönlendirme için XPath filtrelerinde kullanılan önek eşletirmeleri için ad alanı içeren bir öğe kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5065c-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5065c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5065c-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
