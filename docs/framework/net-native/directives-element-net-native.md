---
title: <Directives> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 524c30872e218f6428491507bbfb4ca54b6061b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251106"
---
# <a name="directives-element-net-native"></a>\<Directives> Öğesi (.NET Native)

.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a>Syntax  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`xmlns`|XML ad alanı. Değeri her zaman `http://schemas.microsoft.com/netfx/2013/01/metadata` .|  
  
## <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri yansıma için kullanılabilen tür üyeleri.|  
|[\<Library>](library-element-net-native.md)|Alt türleri ve tür üyeleri çalışma zamanında meta veri gerektiren derlemeyi tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Her çalışma zamanı yönergeleri dosyası yalnızca bir `<Directives>` öğe içerebilir.  
  
 `<Directives>`Öğesi sıfır veya bir [\<Application>](application-element-net-native.md) öğe, sıfır, bir veya daha fazla öğe içerebilir [\<Library>](library-element-net-native.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
