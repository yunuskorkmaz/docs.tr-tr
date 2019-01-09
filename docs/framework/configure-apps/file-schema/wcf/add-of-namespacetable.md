---
title: '&lt;namespaceTable&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: ef4f1c46a0ee3b94e5548b752e4e0a6a759fd45b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149520"
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="4d334-102">&lt;namespaceTable&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="4d334-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="4d334-103">Eşleme sonra yönlendirme için XPath filtrelerinde kullanılan önek için ad alanı içeren bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4d334-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="4d334-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4d334-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4d334-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="4d334-105">\<routing></span></span>  
<span data-ttu-id="4d334-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="4d334-106">\<namespaceTable></span></span>  
<span data-ttu-id="4d334-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="4d334-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d334-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d334-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d334-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d334-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4d334-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d334-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d334-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4d334-111">Attributes</span></span>  
  
|<span data-ttu-id="4d334-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4d334-112">Attribute</span></span>|<span data-ttu-id="4d334-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d334-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d334-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="4d334-114">namespace</span></span>|<span data-ttu-id="4d334-115">Ad alanı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4d334-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="4d334-116">Ön eki</span><span class="sxs-lookup"><span data-stu-id="4d334-116">prefix</span></span>|<span data-ttu-id="4d334-117">Bu ad alanı ön eki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4d334-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d334-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d334-118">Child Elements</span></span>  
 <span data-ttu-id="4d334-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="4d334-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d334-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4d334-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4d334-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="4d334-121">Element</span></span>|<span data-ttu-id="4d334-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d334-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d334-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="4d334-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="4d334-124">Ardından yönlendirme için XPath filtrelerinde kullanılan önek eşletirmeleri için ad alanı içeren bir öğe kümesini tanımlayan bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4d334-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d334-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d334-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
