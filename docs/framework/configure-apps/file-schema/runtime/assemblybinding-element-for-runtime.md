---
title: <runtime> için <assemblyBinding> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154328"
---
# <a name="assemblybinding-element-for-runtime"></a>\<AssemblyÇalışma zamanı \<> için> Öğesi bağlama
Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<montajBağlama>**  
  
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
|**Xmlns**|Gerekli öznitelik.<br /><br /> Derleme bağlama için gereken XML ad alanını belirtir. Değer olarak "urn:schemas-microsoft-com:asm.v1" dizesini kullanın.|  
|**Appliesto**|.NET Framework derlemeyeniden yönlendirmesinin geçerli olduğu çalışma zamanı sürümünü belirtir. Bu isteğe bağlı öznitelik, hangi sürüme uygulandığını belirtmek için bir .NET Framework sürüm numarası kullanır. Hiçbir **öznitelik** belirtilmemişse, ** \<derlemeBağlama>** öğesi .NET Framework'ün tüm sürümlerine uygulanır. **aapplyTo** özniteliği .NET Framework sürüm 1.1'de tanıtıldı; .NET Framework sürüm 1.0 tarafından yoksayılır. Bu, .NET Framework sürüm 1.0 kullanılırken tüm ** \<derlemebağlayıcı>** öğelerinin **uygulandığı** anlamına gelir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağımlıAssembly>](dependentassembly-element.md)|Bir derleme için bağlama ilkesini ve derleme konumunu kapsüller. Her derleme için bir ** \<bağımlıAssembly>** etiketi kullanın.|  
|[\<sondalama>](probing-element.md)|Derlemeleri yüklerken ortak dil çalışma zamanı aramalarını alt dizinler belirtir.|  
|[\<publisherPolicy>](publisherpolicy-element.md)|Çalışma zamanının yayımcı ilkesini kullanıp uygulamayacağını belirtir.|  
|[\<uygunMontaj>](qualifyassembly-element.md)|Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yönlendirilen ve bir kod tabanı nın nasıl sağlayabileceğini gösterir.  
  
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
  
 Aşağıdaki örnek, bir .NET Framework derlemesinin bağlamasını yeniden yönlendirmek için **aapplyTo** özniteliğinin nasıl kullanılacağını gösterir.  
  
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

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../redirect-assembly-versions.md)
