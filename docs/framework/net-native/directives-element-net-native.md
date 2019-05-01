---
title: <Directives> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cfc9dc5c8122f9b1b1696cedcd5d9a8ceead403
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868595"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="7610e-102">\<Yönergeleri > öğesi (.NET yerel)</span><span class="sxs-lookup"><span data-stu-id="7610e-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="7610e-103">.NET Native her çalışma zamanı yönergeleri dosyasının kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="7610e-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="7610e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7610e-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="7610e-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7610e-105">Attributes</span></span>  
  
|<span data-ttu-id="7610e-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7610e-106">Attribute</span></span>|<span data-ttu-id="7610e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7610e-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="7610e-108">XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7610e-108">The XML namespace.</span></span> <span data-ttu-id="7610e-109">Değeri her zaman olduğu **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="7610e-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="7610e-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="7610e-110">Child elements</span></span>  
  
|<span data-ttu-id="7610e-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="7610e-111">Element</span></span>|<span data-ttu-id="7610e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7610e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7610e-113">\<Uygulama ></span><span class="sxs-lookup"><span data-stu-id="7610e-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="7610e-114">Birçok farklı uygulama türleri ve tür üyeleri için yansıma olan meta veri kullanılabilir için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="7610e-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="7610e-115">\<Kitaplık ></span><span class="sxs-lookup"><span data-stu-id="7610e-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="7610e-116">Ayarlanmış alt tür ve tür üyelerinin çalışma zamanında meta verileri gerekir. derleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7610e-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7610e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7610e-117">Remarks</span></span>  
 <span data-ttu-id="7610e-118">Her çalışma zamanı yönergeleri dosyası yalnızca bir içerebilir `<Directives>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7610e-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="7610e-119">`<Directives>` Sıfır veya bir öğe içerebilir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="7610e-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7610e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7610e-120">See also</span></span>

- [<span data-ttu-id="7610e-121">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7610e-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7610e-122">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="7610e-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
