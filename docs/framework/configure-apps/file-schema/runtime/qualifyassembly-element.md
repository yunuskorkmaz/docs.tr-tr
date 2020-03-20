---
title: <qualifyAssembly> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153925"
---
# <a name="qualifyassembly-element"></a>\<qualifyAssembly> Elemanı
Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<montajBağlama>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<uygunMontaj>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`partialName`|Gerekli öznitelik.<br /><br /> Kodda göründüğü gibi derlemenin kısmi adını belirtir.|  
|`fullName`|Gerekli öznitelik.<br /><br /> Derlemenin tam adını, genel derleme önbelleğinde göründüğü gibi belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemin <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> kısmi derleme adlarını kullanarak çağrılması, ortak dil çalışma zamanının yalnızca uygulama temel dizininde derlemeyi aramasına neden olur. Tam montaj bilgilerini (ad, sürüm, ortak anahtar belirteci ve kültür) sağlamak ve genel derleme önbelleğinde derlemeyi aramak için ortak dil çalışma süresine neden olmak için uygulama yapılandırma dosyanızdaki ** \<uygun Assembly>** öğesini kullanın.  
  
 **FullName** özniteliği, montaj kimliğinin dört alanını içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür. **PartialName** özniteliği kısmen bir derleme başvuru gerekir. En azından derlemenin metin adını (en yaygın durum) belirtmeniz gerekir, ancak sürüm, ortak anahtar belirteci veya kültür (veya dördünün herhangi bir birleşimi, ancak dördünü de eklemeyin) de ekleyebilirsiniz. **PartialName,** aramanızda belirtilen adla eşleşmelidir. Örneğin, yapılandırma dosyanızda **kısmi Ad** özniteliği olarak belirtemezsiniz `Assembly.Load("math, Version=3.3.3.3")` `"math"` ve kodunuzda arama yapamazsınız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aramayı `Assembly.Load("math")` mantıksal `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`olarak .  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Kısmi Montaj Başvuruları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
