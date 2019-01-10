---
title: '&lt;kod tabanı&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7e52899a953644fc3cf7189bf557f5ade2863161
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613160"
---
# <a name="ltcodebasegt-element"></a>&lt;kod tabanı&gt; öğesi
Ortak dil çalışma zamanının bir derlemeyi nerede belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<assemblyBinding >  
\<dependentAssembly >  
\<codeBase >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`href`|Gerekli öznitelik.<br /><br /> Çalışma zamanı derlemenin belirtilen sürümü nereden URL'sini belirtir.|  
|`version`|Gerekli öznitelik.<br /><br /> Kod temeli uygulandığı derleme sürümünü belirtir. Bir derleme sürümü numarasının biçimi *major.minor.build.revision*.|  
  
## <a name="version-attribute"></a>Sürüm özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sürüm numarasının her bölüm için geçerli değerler 0 ile 65535 arasındadır.|Uygulanamaz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`buildproviders`|Özel kaynak dosyalarını derlemek için kullanılan derleme sağlayıcıları koleksiyonu tanımlar. Herhangi bir sayıda derleme sağlayıcıları olabilir.|  
|`compilation`|ASP.NET kullanan tüm derleme ayarlarını yapılandırır.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`System.web`|ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanı kullanmak için  **\<codeBase >** bir makine yapılandırma dosyası ya da Yayımcı ilkesi dosyası ayarı dosyası da derleme sürümünü yeniden yönlendirmeniz gerekir. Uygulama yapılandırma dosyaları, derleme sürümü yeniden yönlendirme olmadan bir kod temeli ayarı olabilir. Hangi derleme sürümünün kullanılacağını belirledikten sonra çalışma zamanı sürümünü belirleyen dosyasından codebase ayarı uygulanır. Herhangi bir kod temelinde belirtilirse, çalışma zamanı derlemesi için her zamanki yolla araştırmaları.  
  
 Derlemeyi tanımlayıcı bir ada sahip, codebase ayar herhangi bir yerel intranet veya Internet üzerinde olabilir. Derleme özel bir derleme ise, kod tabanının ayarı uygulamanın dizinine göreli bir yol olmalıdır.  
  
 Güçlü adı olmayan derlemeler için sürüm göz ardı edilir ve ilk görünümünü yükleyicisi kullanır \<codebase > içinde \<dependentAssembly >. Başka bir derleme için bağlama yeniden yönlendirmeleri uygulama yapılandırma dosyasında bir girdi varsa, bağlama isteği derleme sürümü eşleşmiyor olsa bile yönlendirme öncelikli olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çalışma zamanının bir derlemeyi nerede belirtmek gösterilmektedir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Bütünleştirilmiş Kodun Konumunu Belirtme](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
