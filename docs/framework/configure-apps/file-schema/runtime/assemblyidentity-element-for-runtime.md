---
title: '&lt;assemblyIdentity&gt; öğesi için &lt;çalışma zamanı&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5d985d1620b7dec324c0113bcd5652cede044950
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744973"
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a>&lt;assemblyIdentity&gt; öğesi için &lt;çalışma zamanı&gt;
Derleme hakkında tanımlayıcı bilgileri içerir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<assemblyBinding >  
\<dependentAssembly >  
\<assemblyIdentity >  
  
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
|`name`|Gerekli öznitelik.<br /><br /> Derleme adı|  
|`culture`|İsteğe bağlı öznitelik.<br /><br /> Derlemenin ülke/bölge ve dil belirten bir dize.|  
|`publicKeyToken`|İsteğe bağlı öznitelik.<br /><br /> Derleme güçlü adını belirtir. bir onaltılık değer.|  
|`processorArchitecture`|İsteğe bağlı öznitelik.<br /><br /> Biri değerleri "x86", "amd64", "MSIL" veya "IA64" İşlemci mimarisi işlemciye özgü kodu içeren bir derleme için belirtme. Değerleri büyük küçük harfe duyarlı değildir. Öznitelik başka bir değer, tüm atanıp atanmadığını `<assemblyIdentity>` öğesi göz ardı edilir. Bkz: <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`amd64`|Bir 64-bit AMD işlemci yalnızca.|  
|`ia64`|Bir 64-bit Intel işlemci yalnızca.|  
|`msil`|İşlemci ve word başına BITS göre nötr|  
|`x86`|32-bit Intel işlemci, ya da yerel ya da Windows 64-bit platformu üzerinde Windows (WOW) ortamında.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`dependentAssembly`|Her bir derleme için bağlama ilkesi ve derleme konumunu saklar. Kullanmayı `<dependentAssembly>` her derleme için öğesi.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her  **\<dependentAssembly >** öğesinin biri olmalı  **\<assemblyIdentity >** alt öğesi.  
  
 Varsa `processorArchitecture` özniteliği varsa, `<assemblyIdentity>` öğesi uygulandığı yalnızca derleme karşılık gelen İşlemci mimarisi ile. Varsa `processorArchitecture` özniteliği yoksa, `<assemblyIdentity>` öğesi, tüm işlemci mimarisine sahip bir derleme uygulayabilirsiniz.  
  
 Aşağıdaki örnekte, iki farklı iki işlemci mimarileri hedef ve sürümleri eşitlenmiş tutulmuş olmayan iki derlemeler için aynı ada sahip bir yapılandırma dosyası gösterir. Ne zaman uygulama yürütür üzerinde x86 platform ilk `<assemblyIdentity>` öğesine uygular ve diğer göz ardı edilir. Uygulama x86 veya IA64 başka bir platformda yürütülürse, iki göz ardı edilir.  
  
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
  
 Bir yapılandırma dosyası içeriyorsa, bir `<assemblyIdentity>` hiçbir öğe `processorArchitecture` özniteliği ve öğesi olmadan platformuyla eşleşen bir öğe içermiyor `processorArchitecture` özniteliği kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir derleme hakkında bilgi sağlamak gösterilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
