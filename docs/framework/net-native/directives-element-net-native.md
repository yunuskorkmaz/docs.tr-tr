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
# <a name="directives-element-net-native"></a>\<Yönergeler > öğesi (.NET Native)
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
|`xmlns`|XML ad alanı. Değeri her zaman **"http://schemas.microsoft.com/netfx/2013/01/metadata"** dir.|  
  
## <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri yansıma için kullanılabilen tür üyeleri.|  
|[\<Kitaplık >](library-element-net-native.md)|Alt türleri ve tür üyeleri çalışma zamanında meta veri gerektiren derlemeyi tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her çalışma zamanı yönergeleri dosyası yalnızca bir `<Directives>` öğe içerebilir.  
  
 Öğesi sıfır veya bir [ \<uygulama >](application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<kitaplık >](library-element-net-native.md) öğesi içerebilir. `<Directives>`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
