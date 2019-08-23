---
title: <source> Öğesi
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 55120e292ac2a2c822c5510563d1aa167ca921e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920449"
---
# <a name="source-element"></a>\<Kaynak > öğesi
İzleme iletilerini Başlatan bir izleme kaynağını belirtir.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<Kaynaklar >  
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
|`name`|İsteğe bağlı öznitelik.<br /><br /> İzleme kaynağının adını belirtir.|  
|`switchName`|İsteğe bağlı öznitelik.<br /><br /> Uygulamadaki bir izleme anahtarı örneğinin adını belirtir. Anahtar bir `<switches>` öğesinde tanımlanmamışsa, değer anahtar düzeyini belirtir.|  
|`switchType`|İsteğe bağlı öznitelik.<br /><br /> İzleme anahtarının türünü belirtir. Varsa, türün geçerli bir sınıf adı olması ve boş bir dize olmaması gerekir.|  
|`extraAttribute`|İsteğe bağlı öznitelik.<br /><br /> Bu izleme kaynağı için <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> yöntemi tarafından tanımlanan izleme kaynağına özgü bir özniteliğin değerini belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dinleyiciler >](listeners-element-for-source.md)|İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, izleme kaynağını `<source>` `mySource` eklemek ve adlı `sourceSwitch`kaynak anahtarın düzeyini ayarlamak için öğesinin nasıl kullanılacağını gösterir. İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.  
  
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

- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
- [İzleme Anahtarları](../../../debug-trace-profile/trace-switches.md)
