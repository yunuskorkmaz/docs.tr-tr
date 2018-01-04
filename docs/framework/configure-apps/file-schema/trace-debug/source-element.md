---
title: "&lt;Kaynak&gt; öğesi"
ms.date: 09/29/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d6c5c65be8a540fdbba64d5a604c0963f9797e0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsourcegt-element"></a>&lt;Kaynak&gt; öğesi
İzleme iletileri başlatan bir izleme kaynağını belirtir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<Kaynakları >  
\<Kaynak >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|İsteğe bağlı öznitelik.<br /><br /> İzleme kaynağı adını belirtir.|  
|`switchName`|İsteğe bağlı öznitelik.<br /><br /> Uygulama izleme anahtar örneğinin adını belirtir. Anahtar belirlediyseniz değil, bir `<switches>` öğesi, değer anahtar düzeyini belirtir.|  
|`switchType`|İsteğe bağlı öznitelik.<br /><br /> İzleme anahtarı türünü belirtir. Varsa, türü geçerli bir sınıf adı olmalı ve boş bir dize olamaz.|  
|`extraAttribute`|İsteğe bağlı öznitelik.<br /><br /> Tarafından tanımlanan bir izleme kaynağı özgü öznitelik değerini belirtir <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntemi için bu izleme kaynağı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dinleyicileri >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletileri başlatmak izleme kaynaklarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `<source>` izleme kaynağı eklemek için öğesi `mySource` ve kaynak anahtarı düzeyini ayarlamak için adlandırılmış `sourceSwitch`. Bir konsol İzleme dinleyicisi, izleme bilgilerini konsola eklenir.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [İzleme Anahtarları](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
