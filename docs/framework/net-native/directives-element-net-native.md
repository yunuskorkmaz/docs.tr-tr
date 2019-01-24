---
title: '&lt;Directives&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 497ec1a432352e3b9f50bd94e03e95e98edcfd55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725655"
---
# <a name="ltdirectivesgt-element-net-native"></a>&lt;Directives&gt; Öğesi (.NET Yerel)
.NET Native her çalışma zamanı yönergeleri dosyasının kök öğesi.  
  
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
|`xmlns`|XML ad alanı. Değeri her zaman olduğu **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.|  
  
## <a name="child-elements"></a>Alt öğeleri  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|Birçok farklı uygulama türleri ve tür üyeleri için yansıma olan meta veri kullanılabilir için kapsayıcı görevi görür.|  
|[\<Kitaplık >](../../../docs/framework/net-native/library-element-net-native.md)|Ayarlanmış alt tür ve tür üyelerinin çalışma zamanında meta verileri gerekir. derleme tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her çalışma zamanı yönergeleri dosyası yalnızca bir içerebilir `<Directives>` öğesi.  
  
 `<Directives>` Sıfır veya bir öğe içerebilir [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi ve sıfır, bir veya daha fazla [ \<kitaplığı >](../../../docs/framework/net-native/library-element-net-native.md) öğeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
