---
title: <Library>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128365"
---
# <a name="library-element-net-native"></a>\<Library>Öğesi (.NET Native)
Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.  
  
 \<Directives> Öğesi  
\<Library> Öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli öznitelik. Bir derlemenin adını belirtir. Bu öğenin alt öğeleri `<Library>` , bu derlemede bulunan türler ve tür üyeleri için çalışma zamanı yansıtma ilkesini tanımlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*assembly_name*|Derlemenin, dosya uzantısı olmadan basit adı. Bu öznitelik, özelliğine karşılık gelir <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> . Örneğin, Extensions. dll adlı bir derlemenin adı "Uzantılar" dır. Derlemeden meta verilerin koşullu eklenmesini destekleyen *assembly_name* özel bir biçimi için açıklamalar bölümüne bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|İlkeyi belirli bir derlemedeki tüm türlere uygular.|  
|[\<Namespace>](namespace-element-net-native.md)|İlkeyi belirli bir ad alanındaki tüm türlere uygular.|  
|[\<Type>](type-element-net-native.md)|İlkeyi sınıf veya yapı gibi belirli bir türe uygular.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|İlkeyi oluşturulan genel bir türe uygular. Örneğin, bir [\<TypeInstantiation>](typeinstantiation-element-net-native.md) öğe bir tür için ilke tanımlamak üzere kullanılabilir `List<String>` .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|Çalışma zamanı yönergeleri dosyasının kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 [\<Directives>](directives-element-net-native.md)Öğesi sıfır, bir veya daha fazla `<Library>` öğe içerebilir.  
  
 `<Library>`Öğesi, meta verileri çalışma zamanında gerekli olan program öğelerini tanımlamak için bir kapsayıcı görevi görür; bu öğe, ilkeyi ifade etmez. Derleme zamanında, derleyici araçları yalnızca `<Library>` kendi alt öğeleri tarafından tanımlanan program öğeleri için öğesi tarafından belirlenen kitaplığı arar. Buna karşılık, derleyici araçları, öğesinin alt öğeleri tarafından tanımlanan program öğeleri için tüm kitaplıkları, including.NET Framework Çekirdek kitaplıklarını arar [\<Application>](application-element-net-native.md) .  
  
 `<Library>`yönergeler koşullu olarak kullanılıyor olabilir. `<Library>`Öğenin adı bir yıldız işaretiyle başlıyorsa ve bitiyorsa \* , `<Library>` yönerge yalnızca yıldız işaretleri arasında belirtilen derlemeye uygulama tarafından başvuruluyorsa bir etkiye sahiptir. Örneğin, aşağıdaki çalışma zamanı yönergesi yalnızca uygulama tarafından Utilities. dll derlemesine başvuruluyorsa geçerlidir.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Application>Dosyalarında](application-element-net-native.md)
- [\<Directives>Dosyalarında](directives-element-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
