---
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 32eff2e7bfdf1aee4c7d37a0e06166afba3cb398
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566740"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="7df38-102">\<\<NamespaceTable > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="7df38-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="7df38-103">Bu, daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşleme için bir ad alanı içeren bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7df38-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="7df38-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7df38-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7df38-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="7df38-105">\<routing></span></span>  
<span data-ttu-id="7df38-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="7df38-106">\<namespaceTable></span></span>  
<span data-ttu-id="7df38-107">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="7df38-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df38-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7df38-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7df38-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7df38-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7df38-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7df38-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7df38-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7df38-111">Attributes</span></span>  
  
|<span data-ttu-id="7df38-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7df38-112">Attribute</span></span>|<span data-ttu-id="7df38-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df38-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7df38-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="7df38-114">namespace</span></span>|<span data-ttu-id="7df38-115">Ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="7df38-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="7df38-116">prefix</span><span class="sxs-lookup"><span data-stu-id="7df38-116">prefix</span></span>|<span data-ttu-id="7df38-117">Bu ad alanı için öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="7df38-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7df38-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7df38-118">Child Elements</span></span>  
 <span data-ttu-id="7df38-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="7df38-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7df38-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7df38-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7df38-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="7df38-121">Element</span></span>|<span data-ttu-id="7df38-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df38-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7df38-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="7df38-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="7df38-124">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7df38-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7df38-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7df38-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
