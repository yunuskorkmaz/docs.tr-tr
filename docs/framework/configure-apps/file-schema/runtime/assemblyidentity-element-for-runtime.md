---
title: <runtime> için <assemblyIdentity> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154315"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<çalışma zamanı> \<için assemblyIdentity> Öğesi
Derleme hakkında tanımlayıcı bilgileri içerir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<montajBağlama>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bağımlıAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
   <assemblyIdentity
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli öznitelik.<br /><br /> Derlemenin adı|  
|`culture`|İsteğe bağlı öznitelik.<br /><br /> Derlemenin dilini ve ülkesini/bölgesini belirten bir dize.|  
|`publicKeyToken`|İsteğe bağlı öznitelik.<br /><br /> Derlemenin güçlü adını belirten bir hexadecimal değer.|  
|`processorArchitecture`|İsteğe bağlı öznitelik.<br /><br /> "x86", "amd64", "msil" veya "ia64" değerlerinden biri, işlemciye özgü kod içeren bir derlemenin işlemci mimarisini belirtir. Değerler büyük/küçük harf duyarlı değildir. Öznitelik başka bir değer atanırsa, tüm `<assemblyIdentity>` öğe yoksayılır. Bkz. <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorMimari Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`amd64`|Sadece AMD x86-64 mimarisi.|  
|`ia64`|Intel Itanium mimarisi sadece.|  
|`msil`|İşlemci ve kelime başına bit açısından nötr.|  
|`x86`|32 bit x86 işlemci, 64 bit platformda yerel veya Windows Windows (WOW) ortamında.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`dependentAssembly`|Her bir derleme için bağlama ilkesi ve derleme konumunu saklar. Her `<dependentAssembly>` montaj için bir öğe kullanın.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her ** \<bağımlıAssembly>** öğesi bir ** \<assemblyIdentity>** alt öğesi olmalıdır.  
  
 `processorArchitecture` Öznitelik varsa, `<assemblyIdentity>` öğe yalnızca ilgili işlemci mimarisi ile derleme için geçerlidir. `processorArchitecture` Öznitelik yoksa, `<assemblyIdentity>` öğe herhangi bir işlemci mimarisi olan bir derlemeye uygulayabilir.  
  
 Aşağıdaki örnek, iki farklı iki işlemci mimarisini hedefleyen ve sürümleri eşitlemede korunmayan aynı ada sahip iki derleme için bir yapılandırma dosyası gösterir. Uygulama x86 platformunda yürütüldüğünde `<assemblyIdentity>` ilk öğe uygulanır ve diğeri yoksayılır. Uygulama x86 veya ia64 dışında bir platformda yürütülürse, her ikisi de yoksayılır.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Yapılandırma dosyası özniteliği `<assemblyIdentity>` olmayan `processorArchitecture` bir öğe içeriyorsa ve platformla eşleşen bir öğe `processorArchitecture` içermiyorsa, özniteliği olmayan öğe kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir derleme hakkında nasıl bilgi verilebildiğini gösterir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../redirect-assembly-versions.md)
