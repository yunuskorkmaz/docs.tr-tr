---
title: '&lt;assemblyBinding&gt; öğesi için &lt;çalışma zamanı&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d84c134b8e2b048f39836bbc10af06039e96719e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a>&lt;assemblyBinding&gt; öğesi için &lt;çalışma zamanı&gt;
Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<assemblyBinding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**Xmlns**|Gerekli öznitelik.<br /><br /> Derleme bağlama için gereken XML ad alanı belirtir. Dize kullanma "urn: şemaları-microsoft-com:asm.v1" değeri olarak.|  
|**appliesTo**|.NET Framework derleme yeniden yönlendirme uygulandığı çalışma zamanı sürümü belirtir. Bu isteğe bağlı öznitelik uygulandığı hangi sürümünün belirtmek için bir .NET Framework sürüm numarası kullanır. Öyle değilse **appliesTo** özniteliği belirtilirse  **\<assemblyBinding >** öğesi tüm .NET Framework sürümleri için geçerlidir. **AppliesTo** özniteliği, .NET Framework sürüm 1.1 sunulmuştur; .NET Framework sürüm 1.0 göz ardı edilir. Bunun anlamı tüm  **\<assemblyBinding >** öğeleri kullanırken bile, .NET Framework sürüm 1.0 uygulanır bir **appliesTo** özniteliği belirtildi.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Derleme bağlama ilkesi ve derleme konumu yalıtır. Kullanmayı  **\<dependentAssembly >** her derleme için etiket.|  
|[\<yoklama >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Ortak dil çalışma zamanı derlemeleri yükleme sırasında arama alt dizinleri belirtir.|  
|[\<publisherPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Çalışma zamanı Yayımcı ilkesi geçerli olup olmadığını belirtir.|  
|[\<qualifyAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir derleme sürümünü yeniden yönlendirme ve bir codebase sağlamak gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir **appliesTo** bir .NET Framework Derleme bağlaması yeniden yönlendirme için öznitelik.  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
