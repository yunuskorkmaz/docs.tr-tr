---
title: '&lt;namespaceTable&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f08f4b46c6e6290602fc78a2f06954b9cf0b07d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="1a5d4-102">&lt;namespaceTable&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="1a5d4-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="1a5d4-103">Ardından yönlendirme XPath filtreleri kullanılabilir eşleme öneki için bir ad alanı içeren bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a5d4-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="1a5d4-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1a5d4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1a5d4-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="1a5d4-105">\<routing></span></span>  
<span data-ttu-id="1a5d4-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="1a5d4-106">\<namespaceTable></span></span>  
<span data-ttu-id="1a5d4-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="1a5d4-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a5d4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a5d4-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a5d4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a5d4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1a5d4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a5d4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a5d4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1a5d4-111">Attributes</span></span>  
  
|<span data-ttu-id="1a5d4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1a5d4-112">Attribute</span></span>|<span data-ttu-id="1a5d4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a5d4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a5d4-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="1a5d4-114">namespace</span></span>|<span data-ttu-id="1a5d4-115">Ad alanı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="1a5d4-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="1a5d4-116">önek</span><span class="sxs-lookup"><span data-stu-id="1a5d4-116">prefix</span></span>|<span data-ttu-id="1a5d4-117">Bu ad alanı öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="1a5d4-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a5d4-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a5d4-118">Child Elements</span></span>  
 <span data-ttu-id="1a5d4-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="1a5d4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a5d4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a5d4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1a5d4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a5d4-121">Element</span></span>|<span data-ttu-id="1a5d4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a5d4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a5d4-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="1a5d4-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="1a5d4-124">Ardından yönlendirme XPath filtreleri kullanılabilir önek eşlemeleri için ad alanı içeren öğeleri kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a5d4-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a5d4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a5d4-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
