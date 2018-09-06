---
title: '&lt;Directives&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8921d2841f9a7b4228ae3b8735d7047453f71bcb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800199"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="269eb-102">&lt;Directives&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="269eb-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="269eb-103">.NET Native her çalışma zamanı yönergeleri dosyasının kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="269eb-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="269eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="269eb-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="269eb-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="269eb-105">Attributes</span></span>  
  
|<span data-ttu-id="269eb-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="269eb-106">Attribute</span></span>|<span data-ttu-id="269eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="269eb-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="269eb-108">XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="269eb-108">The XML namespace.</span></span> <span data-ttu-id="269eb-109">Değeri her zaman olduğu **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="269eb-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="269eb-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="269eb-110">Child elements</span></span>  
  
|<span data-ttu-id="269eb-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="269eb-111">Element</span></span>|<span data-ttu-id="269eb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="269eb-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="269eb-113">\<Uygulama ></span><span class="sxs-lookup"><span data-stu-id="269eb-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="269eb-114">Birçok farklı uygulama türleri ve tür üyeleri için yansıma olan meta veri kullanılabilir için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="269eb-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="269eb-115">\<Kitaplık ></span><span class="sxs-lookup"><span data-stu-id="269eb-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="269eb-116">Ayarlanmış alt tür ve tür üyelerinin çalışma zamanında meta verileri gerekir. derleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="269eb-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="269eb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="269eb-117">Remarks</span></span>  
 <span data-ttu-id="269eb-118">Her çalışma zamanı yönergeleri dosyası yalnızca bir içerebilir `<Directives>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="269eb-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="269eb-119">`<Directives>` Sıfır veya bir öğe içerebilir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="269eb-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269eb-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="269eb-120">See Also</span></span>  
 [<span data-ttu-id="269eb-121">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="269eb-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="269eb-122">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="269eb-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
