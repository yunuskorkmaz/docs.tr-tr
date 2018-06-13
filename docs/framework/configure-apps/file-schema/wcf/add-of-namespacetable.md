---
title: '&lt;namespaceTable&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 5ae672f12a2ef58efc9738624c113855e59e02b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748639"
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="f5a2b-102">&lt;namespaceTable&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="f5a2b-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="f5a2b-103">Ardından yönlendirme XPath filtreleri kullanılabilir eşleme öneki için bir ad alanı içeren bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5a2b-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="f5a2b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f5a2b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f5a2b-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="f5a2b-105">\<routing></span></span>  
<span data-ttu-id="f5a2b-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="f5a2b-106">\<namespaceTable></span></span>  
<span data-ttu-id="f5a2b-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="f5a2b-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5a2b-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5a2b-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5a2b-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5a2b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f5a2b-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5a2b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5a2b-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f5a2b-111">Attributes</span></span>  
  
|<span data-ttu-id="f5a2b-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f5a2b-112">Attribute</span></span>|<span data-ttu-id="f5a2b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5a2b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5a2b-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="f5a2b-114">namespace</span></span>|<span data-ttu-id="f5a2b-115">Ad alanı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f5a2b-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="f5a2b-116">önek</span><span class="sxs-lookup"><span data-stu-id="f5a2b-116">prefix</span></span>|<span data-ttu-id="f5a2b-117">Bu ad alanı öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f5a2b-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5a2b-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5a2b-118">Child Elements</span></span>  
 <span data-ttu-id="f5a2b-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="f5a2b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5a2b-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5a2b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f5a2b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f5a2b-121">Element</span></span>|<span data-ttu-id="f5a2b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5a2b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5a2b-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="f5a2b-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="f5a2b-124">Ardından yönlendirme XPath filtreleri kullanılabilir önek eşlemeleri için ad alanı içeren öğeleri kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f5a2b-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5a2b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5a2b-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
