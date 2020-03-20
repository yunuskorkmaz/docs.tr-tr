---
title: <Directives>Eleman (.NET Yerel)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181050"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="27f2b-102">\<> Eleman Direktifleri (.NET Yerli)</span><span class="sxs-lookup"><span data-stu-id="27f2b-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="27f2b-103">.NET Native için her çalışma zamanı yönergeleri dosyasındaki kök öğe.</span><span class="sxs-lookup"><span data-stu-id="27f2b-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="27f2b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27f2b-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="27f2b-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27f2b-105">Attributes</span></span>  
  
|<span data-ttu-id="27f2b-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27f2b-106">Attribute</span></span>|<span data-ttu-id="27f2b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27f2b-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="27f2b-108">XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="27f2b-108">The XML namespace.</span></span> <span data-ttu-id="27f2b-109">Değeri her zaman **" "http://schemas.microsoft.com/netfx/2013/01/metadata**.</span><span class="sxs-lookup"><span data-stu-id="27f2b-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="27f2b-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="27f2b-110">Child elements</span></span>  
  
|<span data-ttu-id="27f2b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="27f2b-111">Element</span></span>|<span data-ttu-id="27f2b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27f2b-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27f2b-113">\<Başvuru></span><span class="sxs-lookup"><span data-stu-id="27f2b-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="27f2b-114">Uygulama genelinde ki türler ve meta verileri yansıtmak için kullanılabilen tür üyeleri için bir kapsayıcı görevi görehizmet eder.</span><span class="sxs-lookup"><span data-stu-id="27f2b-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="27f2b-115">\<Kütüphane></span><span class="sxs-lookup"><span data-stu-id="27f2b-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="27f2b-116">Alt türleri ve tür üyeleri çalışma zamanında meta veri gerektiren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="27f2b-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27f2b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27f2b-117">Remarks</span></span>  
 <span data-ttu-id="27f2b-118">Her çalışma zamanı yönergeleri dosyası `<Directives>` yalnızca bir öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="27f2b-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="27f2b-119">Öğe `<Directives>` sıfır veya bir [ \<Uygulama>](application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<Kitaplık>](library-element-net-native.md) öğesi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="27f2b-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f2b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27f2b-120">See also</span></span>

- [<span data-ttu-id="27f2b-121">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="27f2b-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="27f2b-122">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="27f2b-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
