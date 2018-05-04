---
title: '&lt;Filtre&gt; öğesi için &lt;ekleme&gt; için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 763d15a1391d8c9539d5fb92d4ad50132c17c065
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Filtre&gt; öğesi için &lt;ekleme&gt; için &lt;dinleyicileri&gt; için &lt;kaynağı&gt;
Bir dinleyici için bir filtre ekler `Listeners` koleksiyonu için bir izleme kaynağı.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<Kaynakları >  
\<Kaynak >  
\<dinleyicileri >  
\<ekleme >  
\<Filtre >  
  
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
|`type`|Gerekli öznitelik.<br /><br /> Devralınan filtre türünü belirtir <xref:System.Diagnostics.TraceFilter> sınıfı. Tür için karşılık gelen türü ad alanı tam adını kullanabilirsiniz <xref:System.Type.FullName%2A> özelliği veya karşılık gelen derleme bilgileri dahil tam olarak nitelenmiş tür adını kullanabilir <xref:System.Type.AssemblyQualifiedName%2A> özelliği. Tam olarak nitelenmiş tür adları hakkında daha fazla bilgi için bkz: [belirtme tam olarak nitelenmiş tür adları](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Dize belirtilen filtre sınıfı oluşturucuya geçirilen.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|Toplamak, depolamak ve iletileri ve izleme anahtarı ayarlandığı düzeyi rota izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletileri başlatmak izleme kaynaklarını içerir.|  
|`source`|İzleme iletileri başlatan bir izleme kaynağını belirtir.|  
|`listeners`|Toplamak, depolamak ve iletileri yönlendirmek dinleyicileri içerir. Dinleyicileri uygun hedef İzleme çıkışı yönlendirir.|  
|`add`|Bir dinleyici ekler `Listeners` koleksiyonu için bir izleme kaynağı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `<filter>` Öğesi içeriyordu, içinde bir `<add>` yalnızca bir dinleyici adını öğesi dinleyicisi türünü belirtir. bir izleme kaynağı dinleyicisi için tanımlanmış bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md). Dinleyici tanımlanmış olması durumunda bir [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtre bu dinleyici için bu öğe tanımlanmış olması gerekir.  
  
 Bu öğe makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `<filter>` dinleyiciye filtre eklemek için öğesi `console` içinde `Listeners` izleme kaynağı toplamalarında `myTraceSource`, filtre olay düzeyi olarak belirterek `Error`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
