---
title: <Library>Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc3c85ab99574c96d8a68d4221f218a1340e4122
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049642"
---
# <a name="library-element-net-native"></a>\<Kitaplık > öğesi (.NET Native)
Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.  
  
 \<Yönergeler > öğesi  
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
|`Name`|Gerekli öznitelik. Bir derlemenin adını belirtir. Bu `<Library>` öğenin alt öğeleri, bu derlemede bulunan türler ve tür üyeleri için çalışma zamanı yansıtma ilkesini tanımlar.|  
  
## <a name="name-attribute"></a>Ad özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|*assembly_name*|Derlemenin, dosya uzantısı olmadan basit adı. Bu öznitelik, <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> özelliğine karşılık gelir. Örneğin, Extensions. dll adlı bir derlemenin adı "Uzantılar" dır. Derlemeden meta verilerin koşullu eklenmesini destekleyen özel bir *assembly_name* formu için açıklamalar bölümüne bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Bütünleştirilmiş kod >](assembly-element-net-native.md)|İlkeyi belirli bir derlemedeki tüm türlere uygular.|  
|[\<Ad alanı >](namespace-element-net-native.md)|İlkeyi belirli bir ad alanındaki tüm türlere uygular.|  
|[\<Tür >](type-element-net-native.md)|İlkeyi sınıf veya yapı gibi belirli bir türe uygular.|  
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|İlkeyi oluşturulan genel bir türe uygular. Örneğin, [ \<](typeinstantiation-element-net-native.md) bir`List<String>` tür için ilke tanımlamak üzere bir typeörneklemesi > öğesi kullanılabilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönergeler >](directives-element-net-native.md)|Çalışma zamanı yönergeleri dosyasının kök öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönergeler > öğesi sıfır, bir veya daha fazla `<Library>` öğe içerebilir. [ \<](directives-element-net-native.md)  
  
 Öğesi `<Library>` , meta verileri çalışma zamanında gerekli olan program öğelerini tanımlamak için bir kapsayıcı görevi görür; bu öğe, ilkeyi ifade etmez. Derleme zamanında, derleyici araçları yalnızca kendi alt öğeleri tarafından tanımlanan program öğeleri `<Library>` için öğesi tarafından belirlenen kitaplığı arar. Buna karşılık, derleyici araçları, [ \<uygulama >](application-element-net-native.md) öğesinin alt öğeleri tarafından tanımlanan program öğeleri için tüm kitaplıkları, including.NET Framework Çekirdek kitaplıklarını arar.  
  
 `<Library>`yönergeler koşullu olarak kullanılıyor olabilir. `<Library>` Öğenin adı bir\*yıldız işaretiyle başlıyorsa ve bitiyorsa, `<Library>` yönerge yalnızca yıldız işaretleri arasında belirtilen derlemeye uygulama tarafından başvuruluyorsa bir etkiye sahiptir. Örneğin, aşağıdaki çalışma zamanı yönergesi yalnızca uygulama tarafından Utilities. dll derlemesine başvuruluyorsa geçerlidir.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<Uygulama > öğesi](application-element-net-native.md)
- [\<Yönergeler > öğesi](directives-element-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
