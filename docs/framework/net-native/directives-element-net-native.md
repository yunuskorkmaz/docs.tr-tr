---
title: <Directives>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ec9a09e2fc03adbfcff0d7e69489e37da6e4a5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049874"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="86b96-102">\<Yönergeler > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="86b96-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="86b96-103">.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.</span><span class="sxs-lookup"><span data-stu-id="86b96-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="86b96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86b96-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="86b96-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86b96-105">Attributes</span></span>  
  
|<span data-ttu-id="86b96-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86b96-106">Attribute</span></span>|<span data-ttu-id="86b96-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86b96-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="86b96-108">XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="86b96-108">The XML namespace.</span></span> <span data-ttu-id="86b96-109">Değeri her zaman **"http://schemas.microsoft.com/netfx/2013/01/metadata"** dir.</span><span class="sxs-lookup"><span data-stu-id="86b96-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="86b96-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="86b96-110">Child elements</span></span>  
  
|<span data-ttu-id="86b96-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="86b96-111">Element</span></span>|<span data-ttu-id="86b96-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86b96-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86b96-113">\<Uygulama ></span><span class="sxs-lookup"><span data-stu-id="86b96-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="86b96-114">Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri yansıma için kullanılabilen tür üyeleri.</span><span class="sxs-lookup"><span data-stu-id="86b96-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="86b96-115">\<Kitaplık ></span><span class="sxs-lookup"><span data-stu-id="86b96-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="86b96-116">Alt türleri ve tür üyeleri çalışma zamanında meta veri gerektiren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86b96-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86b96-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86b96-117">Remarks</span></span>  
 <span data-ttu-id="86b96-118">Her çalışma zamanı yönergeleri dosyası yalnızca bir `<Directives>` öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="86b96-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="86b96-119">Öğesi sıfır veya bir [ \<uygulama >](application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<kitaplık >](library-element-net-native.md) öğesi içerebilir. `<Directives>`</span><span class="sxs-lookup"><span data-stu-id="86b96-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b96-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86b96-120">See also</span></span>

- [<span data-ttu-id="86b96-121">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="86b96-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="86b96-122">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="86b96-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
