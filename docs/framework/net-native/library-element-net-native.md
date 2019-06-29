---
title: <Library> Öğesi (.NET yerel)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce001ed25d7704301d7f809887a445e3492e93fc
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422532"
---
# <a name="library-element-net-native"></a>\<Kitaplık > öğesi (.NET yerel)
Türler ve tür üyeleri olan meta verilerini yansıma çalışma zamanında kullanılabilir içeren derlemeyi tanımlar.  
  
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
|`Name`|Gerekli öznitelik. Bir derlemenin adını belirtir. Alt öğelerinin bu `<Library>` öğesi türleri ve bu derlemede bulunan tür üyeleri için çalışma zamanı yansıma ilkesini tanımlayın.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*assembly_name*|Dosya uzantısı olmadan derlemenin basit adını. Bu özniteliğe karşılık gelen <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliği. Örneğin, Extensions.dll adlı bir derleme adı "Uzantıları" dir. Özel için Açıklamalar bölümüne bakın *assembly_name* , koşullu dahil etme derlemesinden meta verileri destekler.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|İlke, belirli bir derlemedeki tüm türleri için geçerlidir.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|İlke, belirli bir ad alanındaki tüm türlere uygulanır.|  
|[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|İlke, bir sınıf veya yapı gibi belirli bir türe uygulanır.|  
|[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|İlke oluşturulmuş bir genel türü için geçerlidir. Örneğin, bir [ \<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) öğesi için ilke tanımlamak için kullanılabilir bir `List<String>` türü.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md)|Bir çalışma zamanı yönergeleri dosyasının kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ \<Yönergeleri >](../../../docs/framework/net-native/directives-element-net-native.md) sıfır, bir veya daha fazla öğe içerebilir `<Library>` öğeleri.  
  
 `<Library>` Olan meta verileri çalışma zamanında gereken program öğeleri tanımlamak için bir kapsayıcı öğe görür; bu öğe ilkesini ifade etmez. Derleme zamanında derleyici araçları yalnızca belirlenen kitaplık arama `<Library>` program öğeleri alt öğeleri tarafından tanımlanan öğe. Buna karşılık, derleyici arama araçları tüm kitaplıkları, alt öğeler tarafından tanıtılan program öğeler için including.NET Framework Çekirdek kitaplıkları [ \<uygulama >](../../../docs/framework/net-native/application-element-net-native.md) öğesi.  
  
 `<Library>` yönergeleri koşullu olarak kullanılabilir. Varsa adını `<Library>` öğesi başlar ve biter yıldız işaretiyle (\*), `<Library>` yönergesi, yalnızca uygulama tarafından arasında yıldız belirtilen derleme başvuruluyorsa bir etkiye sahiptir. Örneğin, yalnızca, uygulama tarafından Utilities.dll derlemeye başvurulduğundan durumunda aşağıdaki çalışma zamanı yönerge geçerlidir.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Uygulama > öğesi](../../../docs/framework/net-native/application-element-net-native.md)
- [\<Yönergeleri > öğesi](../../../docs/framework/net-native/directives-element-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
