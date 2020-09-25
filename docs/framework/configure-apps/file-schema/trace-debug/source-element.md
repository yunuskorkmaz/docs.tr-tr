---
title: <source> Öğesi
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: e9c6a06ca9e481ecc2277e1d1ea76a0b99edb158
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173828"
---
# <a name="source-element"></a>\<source> Öğesi

İzleme iletilerini Başlatan bir izleme kaynağını belirtir.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a>Syntax  
  
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
|`extraAttribute`|İsteğe bağlı öznitelik.<br /><br /> Bu izleme kaynağı için yöntemi tarafından tanımlanan izleme kaynağına özgü bir özniteliğin değerini belirtir <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> .|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `<source>` izleme kaynağını eklemek `mySource` ve adlı kaynak anahtarın düzeyini ayarlamak için öğesinin nasıl kullanılacağını gösterir `sourceSwitch` . İzleme bilgilerini konsola yazan bir konsol izleme dinleyicisi eklenir.  
  
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

- [İzleme ve hata ayıklama ayarları şeması](index.md)
- [İzleme Anahtarları](../../../debug-trace-profile/trace-switches.md)
