---
title: '&lt;Directives&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd571255f924c9f3878c00a2bc01397d63e6d777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394452"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="22d0a-102">&lt;Directives&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="22d0a-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="22d0a-103">Her çalışma zamanı yönergeleri dosyasının kök öğesinin [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22d0a-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="22d0a-104">**\<Yönergeleri xmlns = "http://schemas.microsoft.com/netfx/2013/01/metadata" >**</span><span class="sxs-lookup"><span data-stu-id="22d0a-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d0a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22d0a-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="22d0a-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="22d0a-106">Attributes</span></span>  
  
|<span data-ttu-id="22d0a-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="22d0a-107">Attribute</span></span>|<span data-ttu-id="22d0a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22d0a-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="22d0a-109">XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="22d0a-109">The XML namespace.</span></span> <span data-ttu-id="22d0a-110">Değeri her zaman olduğu **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="22d0a-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="22d0a-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="22d0a-111">Child elements</span></span>  
  
|<span data-ttu-id="22d0a-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="22d0a-112">Element</span></span>|<span data-ttu-id="22d0a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22d0a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22d0a-114">\<Uygulama ></span><span class="sxs-lookup"><span data-stu-id="22d0a-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="22d0a-115">Uygulama çapında türler ve yansıma için kullanılabilir olan meta veri türü üyeleri için bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="22d0a-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="22d0a-116">\<Kitaplık ></span><span class="sxs-lookup"><span data-stu-id="22d0a-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="22d0a-117">Alt öğe türleri ve tür üyeleri çalışma zamanında meta verileri gerekir derleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22d0a-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22d0a-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22d0a-118">Remarks</span></span>  
 <span data-ttu-id="22d0a-119">Her çalışma zamanı yönergeleri dosyası yalnızca bir tane içerebilir `<Directives>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="22d0a-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="22d0a-120">`<Directives>` Sıfır veya bir öğe içerebilir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="22d0a-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d0a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22d0a-121">See Also</span></span>  
 [<span data-ttu-id="22d0a-122">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="22d0a-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="22d0a-123">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="22d0a-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
