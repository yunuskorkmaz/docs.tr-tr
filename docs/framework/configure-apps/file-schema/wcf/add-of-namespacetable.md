---
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850387"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="19a89-102">\<\<NamespaceTable > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="19a89-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="19a89-103">Bu, daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşleme için bir ad alanı içeren bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="19a89-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
<span data-ttu-id="19a89-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="19a89-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="19a89-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="19a89-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="19a89-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="19a89-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="19a89-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namespaceTable >** ](namespacetable.md)</span><span class="sxs-lookup"><span data-stu-id="19a89-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)</span></span>\
<span data-ttu-id="19a89-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="19a89-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a89-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19a89-109">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19a89-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="19a89-110">Attributes and Elements</span></span>  
 <span data-ttu-id="19a89-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19a89-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19a89-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19a89-112">Attributes</span></span>  
  
|<span data-ttu-id="19a89-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="19a89-113">Attribute</span></span>|<span data-ttu-id="19a89-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19a89-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19a89-115">ad alanı</span><span class="sxs-lookup"><span data-stu-id="19a89-115">namespace</span></span>|<span data-ttu-id="19a89-116">Ad alanını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="19a89-116">A string containing the namespace.</span></span>|  
|<span data-ttu-id="19a89-117">prefix</span><span class="sxs-lookup"><span data-stu-id="19a89-117">prefix</span></span>|<span data-ttu-id="19a89-118">Bu ad alanı için öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="19a89-118">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19a89-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="19a89-119">Child Elements</span></span>  
 <span data-ttu-id="19a89-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="19a89-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19a89-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="19a89-121">Parent Elements</span></span>  
  
|<span data-ttu-id="19a89-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="19a89-122">Element</span></span>|<span data-ttu-id="19a89-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19a89-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19a89-124">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="19a89-124">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="19a89-125">Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="19a89-125">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19a89-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19a89-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
