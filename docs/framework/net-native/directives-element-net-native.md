---
title: "&lt;Directives&gt; Öğesi (.NET Yerel)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a55048ea5b2889da82b10ac2a51865d945635143
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="6e320-102">&lt;Directives&gt; Öğesi (.NET Yerel)</span><span class="sxs-lookup"><span data-stu-id="6e320-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="6e320-103">Her çalışma zamanı yönergeleri dosyasının kök öğesinin [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e320-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="6e320-104">**\<Yönergeleri xmlns = "http://schemas.microsoft.com/netfx/2013/01/metadata" >**</span><span class="sxs-lookup"><span data-stu-id="6e320-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e320-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e320-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="6e320-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e320-106">Attributes</span></span>  
  
|<span data-ttu-id="6e320-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e320-107">Attribute</span></span>|<span data-ttu-id="6e320-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e320-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="6e320-109">XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6e320-109">The XML namespace.</span></span> <span data-ttu-id="6e320-110">Değeri her zaman olduğu **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="6e320-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="6e320-111">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6e320-111">Child elements</span></span>  
  
|<span data-ttu-id="6e320-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e320-112">Element</span></span>|<span data-ttu-id="6e320-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e320-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e320-114">\<Uygulama ></span><span class="sxs-lookup"><span data-stu-id="6e320-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="6e320-115">Uygulama çapında türler ve yansıma için kullanılabilir olan meta veri türü üyeleri için bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6e320-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="6e320-116">\<Kitaplık ></span><span class="sxs-lookup"><span data-stu-id="6e320-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="6e320-117">Alt öğe türleri ve tür üyeleri çalışma zamanında meta verileri gerekir derleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6e320-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e320-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e320-118">Remarks</span></span>  
 <span data-ttu-id="6e320-119">Her çalışma zamanı yönergeleri dosyası yalnızca bir tane içerebilir `<Directives>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6e320-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="6e320-120">`<Directives>` Sıfır veya bir öğe içerebilir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6e320-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e320-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e320-121">See Also</span></span>  
 [<span data-ttu-id="6e320-122">Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu</span><span class="sxs-lookup"><span data-stu-id="6e320-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="6e320-123">Çalışma zamanı yönerge öğeleri</span><span class="sxs-lookup"><span data-stu-id="6e320-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
