---
title: '&lt;Library&gt; Öğesi (.NET Yerel)'
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eabaf1dd99fce7cd4c45f80666534f904fcdfdf9
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34311981"
---
# <a name="ltlibrarygt-element-net-native"></a>&lt;Library&gt; Öğesi (.NET Yerel)
Türleri ve tür üyeleri olan meta verilerini yansıma çalışma zamanında yüklenebilir içeren derlemenin tanımlar.  
  
 \<Yönergeleri > öğesi  
\<Kitaplık > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli öznitelik. Bir bütünleştirilmiş kodun adını belirtir. Bu alt öğelerinin `<Library>` öğesi türleri ve bu derleme içinde bulunan tür üyeleri için çalışma zamanı yansıma ilkesi tanımlayın.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*assembly_name*|Derlemenin dosya uzantısı olmadan basit adı. Bu özniteliğe karşılık gelen <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliği. Örneğin, Extensions.dll adlı bir derleme "Uzantılarla" adıdır. Özel bir tür için Açıklamalar bölümüne bakın *assembly_name* koşullu derleme meta verilerini edilmesi destekler.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|Belirli bir derleme içindeki tüm türler için ilke uygulanır.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Belirli bir ad alanı içindeki tüm türler için ilke uygulanır.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|Bir sınıf veya yapı gibi belirli türde bir ilke uygulanır.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|İlke oluşturulan genel bir tür için geçerlidir. Örneğin, bir [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi için ilke tanımlamak için kullanılan bir `List<String>` türü.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md)|Bir çalışma zamanı yönergeleri dosyasının kök öğesinin.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ \<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) sıfır, bir veya daha fazla öğe içerebilir `<Library>` öğeleri.  
  
 `<Library>` Olan meta veri çalışma zamanında gereken program öğeleri tanımlamak için bir kapsayıcı öğe görür; bu öğe ilkesini ifade değil. Derleme zamanında arama derleyici araçları yalnızca belirlenen kitaplık `<Library>` öğesi alt öğeleri tarafından tanıtılan program öğeleri için. Buna karşılık, derleyici arama araçları tüm kitaplıkları, alt öğeleri tarafından tanımlanan programı öğelerin including.NET Framework core kitaplıkları [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi.  
  
 `<Library>` yönergeleri koşullu yararlı. Varsa adını `<Library>` öğesi başlar ve biter yıldız işaretiyle (\*), `<Library>` yönergesi yalnızca yıldız arasında belirtilen derlemesi uygulama tarafından başvurulduğunda bir etkisi vardır. Örneğin, yalnızca Utillities.dll derleme uygulama tarafından başvurulduğunda aşağıdaki çalışma zamanı yönerge geçerlidir.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Uygulama > öğesi](../../../docs/framework/net-native/application-element-net-native.md)  
 [\<Yönergeleri > öğesi](../../../docs/framework/net-native/directives-element-net-native.md)  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
