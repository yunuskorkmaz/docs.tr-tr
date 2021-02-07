---
description: 'Daha fazla bilgi edinin: <Directives> öğesi (.NET Native)'
title: <Directives> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 7aa3bf3718f32d55ba8189c65705868c6fb399ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662916"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="52b9e-103">\<Directives> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="52b9e-103">\<Directives> Element (.NET Native)</span></span>

<span data-ttu-id="52b9e-104">.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.</span><span class="sxs-lookup"><span data-stu-id="52b9e-104">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="52b9e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="52b9e-105">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="52b9e-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="52b9e-106">Attributes</span></span>  
  
|<span data-ttu-id="52b9e-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="52b9e-107">Attribute</span></span>|<span data-ttu-id="52b9e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52b9e-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="52b9e-109">XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="52b9e-109">The XML namespace.</span></span> <span data-ttu-id="52b9e-110">Değeri her zaman `http://schemas.microsoft.com/netfx/2013/01/metadata` .</span><span class="sxs-lookup"><span data-stu-id="52b9e-110">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="52b9e-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="52b9e-111">Child elements</span></span>  
  
|<span data-ttu-id="52b9e-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="52b9e-112">Element</span></span>|<span data-ttu-id="52b9e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="52b9e-113">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="52b9e-114">Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri yansıma için kullanılabilen tür üyeleri.</span><span class="sxs-lookup"><span data-stu-id="52b9e-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="52b9e-115">Alt türleri ve tür üyeleri çalışma zamanında meta veri gerektiren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="52b9e-115">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52b9e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52b9e-116">Remarks</span></span>  

 <span data-ttu-id="52b9e-117">Her çalışma zamanı yönergeleri dosyası yalnızca bir `<Directives>` öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="52b9e-117">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="52b9e-118">`<Directives>`Öğesi sıfır veya bir [\<Application>](application-element-net-native.md) öğe, sıfır, bir veya daha fazla öğe içerebilir [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="52b9e-118">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b9e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52b9e-119">See also</span></span>

- [<span data-ttu-id="52b9e-120">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="52b9e-120">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="52b9e-121">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="52b9e-121">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
