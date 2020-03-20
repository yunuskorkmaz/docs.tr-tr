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
# <a name="directives-element-net-native"></a>\<> Eleman Direktifleri (.NET Yerli)
.NET Native için her çalışma zamanı yönergeleri dosyasındaki kök öğe.  
  
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
|`xmlns`|XML ad alanı. Değeri her zaman **" "http://schemas.microsoft.com/netfx/2013/01/metadata**.|  
  
## <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Başvuru>](application-element-net-native.md)|Uygulama genelinde ki türler ve meta verileri yansıtmak için kullanılabilen tür üyeleri için bir kapsayıcı görevi görehizmet eder.|  
|[\<Kütüphane>](library-element-net-native.md)|Alt türleri ve tür üyeleri çalışma zamanında meta veri gerektiren derlemeyi tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her çalışma zamanı yönergeleri dosyası `<Directives>` yalnızca bir öğe içerebilir.  
  
 Öğe `<Directives>` sıfır veya bir [ \<Uygulama>](application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<Kitaplık>](library-element-net-native.md) öğesi içerebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
