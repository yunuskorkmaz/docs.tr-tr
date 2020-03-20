---
title: <filter><add> Için <listeners> element<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153522"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<kaynak> \<için> \<dinleyiciler \<için> eklemek için> Öğesi'ni filtreleyin
İzleme kaynağı için `Listeners` koleksiyondaki dinleyiciye filtre ekler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynaklar>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaynak>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtre>**

## <a name="syntax"></a>Sözdizimi  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`type`|Gerekli öznitelik.<br /><br /> <xref:System.Diagnostics.TraceFilter> Sınıftan devralması gereken filtrenin türünü belirtir. Türün <xref:System.Type.FullName%2A> özelliğine karşılık gelen ad alanı nitelikli adını kullanabilir veya <xref:System.Type.AssemblyQualifiedName%2A> derleme bilgilerini de içeren ve özelliğe karşılık gelen tam nitelikli tür adını kullanabilirsiniz. Tam nitelikli tür adları hakkında bilgi için [bkz.](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Dize, belirtilen filtre sınıfı için oluşturucuya geçti.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.|  
|`sources`|İletileri izlemeyi başlatan izleme kaynakları içerir.|  
|`source`|İletilerin izlenmesini başlatan bir izleme kaynağı belirtir.|  
|`listeners`|İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir. Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.|  
|`add`|İzleme kaynağı için `Listeners` koleksiyona dinleyici ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `<filter>` yalnızca paylaşılan `<add>` [ \<Dinleyiciler>](sharedlisteners-element.md)tanımlanan bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme kaynağı dinleyicisi için bir öğeiçermelidir. Dinleyici [ \<paylaşılan ](sharedlisteners-element.md)dinleyici>tanımlanırsa, bu dinleyicinin filtresi bu öğede tanımlanmalıdır.  
  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, izleme kaynağı `<filter>` `console` `myTraceSource`için `Error` `Listeners` koleksiyondaki dinleyiciye bir filtre eklemek için öğenin nasıl kullanılacağını gösterir ve filtre olay düzeyini .  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
