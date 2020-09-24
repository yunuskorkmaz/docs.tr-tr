---
title: <runtime> için <assemblyIdentity> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: f3e74b05ac0fd7c57963f2aad047ba3f2d63a10a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170187"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<runtime> için \<assemblyIdentity> Öğesi

Derlemeyle ilgili tanımlama bilgilerini içerir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`culture`|İsteğe bağlı öznitelik.<br /><br /> Derlemenin dil ve ülke/bölge bilgisini belirten bir dize.|  
|`publicKeyToken`|İsteğe bağlı öznitelik.<br /><br /> Derlemenin tanımlayıcı adını belirten onaltılık bir değer.|  
|`processorArchitecture`|İsteğe bağlı öznitelik.<br /><br /> "X86", "amd64", "MSIL" veya "ia64" değerlerinden biri, işlemciye özgü kod içeren bir derlemenin işlemci mimarisini belirleyen. Değerler büyük/küçük harfe duyarlı değildir. Özniteliği başka bir değer atanırsa, tüm `<assemblyIdentity>` öğesi yok sayılır. Bkz. <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`amd64`|Yalnızca AMD x86-64 mimarisi.|  
|`ia64`|Yalnızca Intel Itanium mimarisi.|  
|`msil`|İşlemci ve sözcüğe göre bit başına açısından nötr.|  
|`x86`|64 bit platformda yerel veya Windows üzerinde Windows (WOW) ortamındaki 32 bitlik bir x86 işlemcisi.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`dependentAssembly`|Her bir derleme için bağlama ilkesi ve derleme konumunu saklar. `<dependentAssembly>`Her derleme için bir öğe kullanın.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Her **\<dependentAssembly>** öğenin bir **\<assemblyIdentity>** alt öğesi olmalıdır.  
  
 `processorArchitecture`Öznitelik varsa, `<assemblyIdentity>` öğe yalnızca karşılık gelen işlemci mimarisine sahip derleme için geçerlidir. `processorArchitecture`Özniteliği yoksa, `<assemblyIdentity>` öğesi herhangi bir işlemci mimarisine sahip bir derleme için uygulanabilir.  
  
 Aşağıdaki örnek, iki farklı iki işlemci mimarisinden oluşan aynı ada sahip iki derleme için bir yapılandırma dosyası gösterir ve sürümleri eşitlenmiş olarak korunmaz. Uygulama x86 platformunda yürütüldüğünde ilk `<assemblyIdentity>` öğe uygulanır ve diğeri yok sayılır. Uygulama, x86 veya ia64 dışında bir platformda yürütülüyorsa her ikisi de yok sayılır.  
  
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
  
 Bir yapılandırma dosyası özniteliği olmayan bir `<assemblyIdentity>` öğe içeriyorsa `processorArchitecture` ve platformla eşleşen bir öğe içermiyorsa, özniteliği olmayan öğesi `processorArchitecture` kullanılır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir derleme hakkında nasıl bilgi sağlayagösterdiğini gösterir.  
  
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

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Derleme Sürümlerini Yönlendirme](../../redirect-assembly-versions.md)
