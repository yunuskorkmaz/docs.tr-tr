---
title: <Library> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128365"
---
# <a name="library-element-net-native"></a>\<kitaplığı > öğesi (.NET Native)
Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.  
  
 \<yönergeleri > öğesi  
\<kitaplığı > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli öznitelik. Bir derlemenin adını belirtir. Bu `<Library>` öğesinin alt öğeleri, bu derlemede bulunan türler ve tür üyeleri için çalışma zamanı yansıma ilkesini tanımlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*assembly_name*|Derlemenin, dosya uzantısı olmadan basit adı. Bu öznitelik <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliğine karşılık gelir. Örneğin, Extensions. dll adlı bir derlemenin adı "Uzantılar" dır. Derlemeden meta verilerin koşullu eklenmesini destekleyen özel bir *assembly_name* formu için açıklamalar bölümüne bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Derleme > \<](assembly-element-net-native.md)|İlkeyi belirli bir derlemedeki tüm türlere uygular.|  
|[\<ad alanı >](namespace-element-net-native.md)|İlkeyi belirli bir ad alanındaki tüm türlere uygular.|  
|[\<türü >](type-element-net-native.md)|İlkeyi sınıf veya yapı gibi belirli bir türe uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|İlkeyi oluşturulan genel bir türe uygular. Örneğin, bir `List<String>` türünün ilkesini tanımlamak için bir [\<Typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi kullanılabilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<yönergeler >](directives-element-net-native.md)|Çalışma zamanı yönergeleri dosyasının kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [\<yönergeleri >](directives-element-net-native.md) öğesi sıfır, bir veya daha fazla `<Library>` öğesi içerebilir.  
  
 `<Library>` öğesi, meta verileri çalışma zamanında gerekli olan program öğelerini tanımlamak için bir kapsayıcı görevi görür; Bu öğe, ilkeyi ifade etmez. Derleme zamanında, derleyici araçları yalnızca kendi alt öğeleri tarafından tanımlanan program öğeleri için `<Library>` öğesi tarafından belirlenen kitaplığı arar. Buna karşılık, derleyici araçları, [\<uygulaması >](application-element-net-native.md) öğesinin alt öğeleri tarafından tanımlanan program öğeleri için tüm kitaplıkları, including.NET Framework Çekirdek kitaplıklarını arar.  
  
 `<Library>` yönergeler koşullu olarak kullanılıyor olabilir. `<Library>` öğenin adı bir yıldız işareti (\*) ile başlarsa ve bitiyorsa, `<Library>` yönergesi yalnızca, yıldız işaretleri arasında belirtilen derlemeye uygulama tarafından başvuruluyorsa devreye girer. Örneğin, aşağıdaki çalışma zamanı yönergesi yalnızca uygulama tarafından Utilities. dll derlemesine başvuruluyorsa geçerlidir.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<uygulama > öğesi](application-element-net-native.md)
- [\<yönergeleri > öğesi](directives-element-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
