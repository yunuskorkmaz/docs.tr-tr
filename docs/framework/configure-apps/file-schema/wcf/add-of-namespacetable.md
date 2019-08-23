---
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e2a2e26099f2d31116e4a89297fc1ac984c480d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920072"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="b9feb-102">\<\<NamespaceTable > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="b9feb-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="b9feb-103">Bu, daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşleme için bir ad alanı içeren bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b9feb-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="b9feb-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b9feb-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b9feb-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="b9feb-105">\<routing></span></span>  
<span data-ttu-id="b9feb-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="b9feb-106">\<namespaceTable></span></span>  
<span data-ttu-id="b9feb-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="b9feb-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9feb-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b9feb-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9feb-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9feb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b9feb-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b9feb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9feb-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b9feb-111">Attributes</span></span>  
  
|<span data-ttu-id="b9feb-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b9feb-112">Attribute</span></span>|<span data-ttu-id="b9feb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9feb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9feb-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="b9feb-114">namespace</span></span>|<span data-ttu-id="b9feb-115">Ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b9feb-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="b9feb-116">prefix</span><span class="sxs-lookup"><span data-stu-id="b9feb-116">prefix</span></span>|<span data-ttu-id="b9feb-117">Bu ad alanı için öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b9feb-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9feb-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9feb-118">Child Elements</span></span>  
 <span data-ttu-id="b9feb-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="b9feb-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9feb-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b9feb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b9feb-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="b9feb-121">Element</span></span>|<span data-ttu-id="b9feb-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9feb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9feb-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="b9feb-123">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="b9feb-124">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b9feb-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9feb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9feb-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
