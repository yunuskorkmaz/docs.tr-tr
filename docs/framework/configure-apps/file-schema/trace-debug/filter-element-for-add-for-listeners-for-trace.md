---
title: <filter><add> Için <listeners> element<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153472"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<izleme> \<için> \<dinleyiciler \<için> eklemek için> Öğesi'ni filtreleyin
`Listeners` İzleme için koleksiyondaki bir dinleyiciye filtre ekler.  

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<izleme>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dinleyici ler>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filtre>**

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
|`trace`|İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir.|  
|`listeners`|İletileri toplayan, depolayan ve yönlendiren dinleyicileri içerir. Dinleyiciler izleme çıktısını uygun bir hedefe yönlendirir.|  
|`add`|`Listeners` Koleksiyona bir dinleyici ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, `<filter>` yalnızca paylaşılan `<add>` Dinleyici [ \<>](sharedlisteners-element.md)tanımlanan bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme dinleyicisi için bir öğede bulunmalıdır. Dinleyici [ \<paylaşılan ](sharedlisteners-element.md)dinleyici>tanımlanırsa, bu dinleyicinin filtresi bu öğede tanımlanmalıdır.  
  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, izleme `<filter>` için `console` `Listeners` koleksiyondaki dinleyiciye bir filtre eklemek için öğenin nasıl kullanılacağı `Error`gösterilmektedir ve filtre olay düzeyini .  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
