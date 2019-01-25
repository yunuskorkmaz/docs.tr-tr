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
ms.openlocfilehash: c0060115360cd077fd1e390be916f2f8afbadd9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713999"
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
|**xmlns**|Gerekli öznitelik.<br /><br /> Derleme bağlama için gerekli XML ad alanı belirtir. Use the string "urn:schemas-microsoft-com:asm.v1" as the value.|  
|**AppliesTo**|.NET Framework derleme yeniden yönlendirme uygulandığı çalışma zamanı sürümünü belirtir. İsteğe bağlı bu öznitelik, bir .NET Framework sürüm numarası geçerli hangi sürüm olduğunu belirlemek için kullanır. Hayır ise **appliesTo** özniteliği belirtilirse,  **\<assemblyBinding >** öğe tüm .NET Framework sürümleri için geçerlidir. **AppliesTo** özniteliği, .NET Framework sürüm 1.1 sunulmuştur; .NET Framework sürüm 1.0 tarafından göz ardı edilir. Bunun anlamı tüm  **\<assemblyBinding >** öğeleri kullanırken bile, .NET Framework sürüm 1.0 uygulanır bir **appliesTo** özniteliği belirtildi.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Bir derleme için bağlama ilkesi ve derleme konumunu saklar. Bir  **\<dependentAssembly >** her derleme için etiket.|  
|[\<yoklama >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Ortak dil çalışma zamanı derlemeleri yüklenirken arama alt dizinleri belirtir.|  
|[\<publisherPolicy >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Çalışma zamanı Yayımcı ilkesi uygulanıp uygulanmayacağını belirtir.|  
|[\<qualifyAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Kısmi bir adı kullanıldığında dinamik olarak yüklenmesi gereken bütünleştirilmiş kodun tam adını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir derleme sürümünü diğerine yeniden yönlendirme ve bir kod temeli sağlamak gösterilmektedir.  
  
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
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir **appliesTo** bir .NET Framework derlemesinin bağlama yeniden yönlendirme için özniteliği.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
