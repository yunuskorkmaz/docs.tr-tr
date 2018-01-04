---
title: "&lt;codeBase&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 272a4262295b5dd67414dd0ef6523f90b2125836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcodebasegt-element"></a>&lt;codeBase&gt; öğesi
Ortak dil çalışma zamanı bütünleştirilmiş bulabileceğiniz belirtir.  
  
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
|`href`|Gerekli öznitelik.<br /><br /> Çalışma zamanı derlemesi belirtilen sürümünü bulabileceğiniz URL'yi belirtir.|  
|`version`|Gerekli öznitelik.<br /><br /> Codebase uygulandığı derleme sürümünü belirtir. Bir derleme sürüm numarası biçimi *major.minor.build.revision*.|  
  
## <a name="version-attribute"></a>Version özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sürüm numarasını her kısmı için geçerli değerler 0 ile 65535 arasındadır.|Yok.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`buildproviders`|Özel kaynak dosyalarını derlemek için kullanılan yapı sağlayıcıları koleksiyonu tanımlar. Yapı sağlayıcıları herhangi bir sayıda olabilir.|  
|`compilation`|ASP.NET kullanan tüm derleme ayarlarını yapılandırır.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`System.web`|ASP.NET yapılandırma bölümü için kök öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanı için  **\<codeBase >** bir makine yapılandırma dosyası veya yayımcı ilkesi dosyası ayarı dosyası ayrıca derleme sürümünü yönlendirme gerekir. Uygulama yapılandırma dosyaları, derleme sürümünü yeniden yönlendirme olmadan codebase ayarı olabilir. Hangi derleme sürümün kullanılacağını belirlendikten sonra çalışma zamanı sürümü belirler dosyasından codebase ayar uygulanır. Hiçbir codebase belirtilirse, çalışma zamanı derlemesi için Normal yollardan araştırmaları.  
  
 Derleme tanımlayıcı adı varsa, codebase ayarı Yerel intranet veya Internet üzerinde herhangi bir yere olabilir. Derleme özel bir derleme ise codebase ayarı uygulama dizinindeki göreli bir yol olmalıdır.  
  
 Güçlü bir ad olmadan derlemeler için sürüm dikkate alınmaz ve ilk görünümünü yükleyicisi kullanır \<codebase > içinde \<dependentAssembly >. Başka bir derlemeye bağlama yeniden yönlendirmelerini uygulama yapılandırma dosyasında bir girdi ise, yeniden yönlendirme derleme sürümünü bağlama isteği eşleşmiyor olsa bile öncelikli olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çalışma zamanı bütünleştirilmiş bulabileceğiniz belirtin gösterilmektedir.  
  
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
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Bütünleştirilmiş Kodun Konumunu Belirtme](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
