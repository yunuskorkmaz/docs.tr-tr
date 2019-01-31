---
title: <source> Öğesi
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: a528e0f77efea6df7379a0f01495bc09d2ed0b24
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254489"
---
# <a name="source-element"></a>\<Kaynak > öğesi
İzleme iletileri başlatan bir izleme kaynağı belirtir.  
  
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
|`switchName`|İsteğe bağlı öznitelik.<br /><br /> Uygulamada bir izleme anahtarı örneğinin adını belirtir. İçindeki anahtar tanımlanmamışsa bir `<switches>` öğesi, değeri anahtar düzeyini belirtir.|  
|`switchType`|İsteğe bağlı öznitelik.<br /><br /> İzleme anahtarı türünü belirtir. Varsa, türü geçerli bir sınıf adı olmalı ve boş bir dize olamaz.|  
|`extraAttribute`|İsteğe bağlı öznitelik.<br /><br /> Tarafından tanımlanan bir izleme kaynağı özel özniteliğinin değeri belirtir <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntemi için bu izleme kaynağı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dinleyicileri >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve bir izleme anahtarı ayarlandığı düzeyi izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletileri başlatmak iz kaynakları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<source>` iz eklenecek öğe `mySource` ve kaynak anahtarı düzeyini ayarlamak için adlı `sourceSwitch`. Bir konsol iz dinleyicisi, izleme bilgileri konsola yazar eklenir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [İzleme Anahtarları](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
