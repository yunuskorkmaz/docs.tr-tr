---
title: <Directives> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: abe2e7221e0afb984a6178b12fabc36ea24deb35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128466"
---
# <a name="directives-element-net-native"></a>\<yönergeleri > öğesi (.NET Native)
.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`xmlns`|XML ad alanı. Değeri her zaman **"http://schemas.microsoft.com/netfx/2013/01/metadata"** olur.|  
  
## <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<uygulama >](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri yansıma için kullanılabilen tür üyeleri.|  
|[\<kitaplığı >](library-element-net-native.md)|Alt türleri ve tür üyeleri çalışma zamanında meta veri gerektiren derlemeyi tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her çalışma zamanı yönergeleri dosyası yalnızca bir `<Directives>` öğesi içerebilir.  
  
 `<Directives>` öğesi sıfır veya bir [\<uygulama >](application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [\<kitaplığı >](library-element-net-native.md) öğesi içerebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
