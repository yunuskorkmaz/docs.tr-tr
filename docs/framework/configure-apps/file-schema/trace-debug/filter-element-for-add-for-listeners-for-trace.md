---
title: <filter><add> İçin için<listeners> öğesi<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: afde5381a7dd7dfe6a1a9d238a2029511bd9bae2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927131"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a>\<Trace için \< \< >forListeners>için\<> öğesini filtreleyin >
İzleme için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<İzleme >  
\<dinleyiciler >  
\<> Ekle  
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
|`type`|Gerekli öznitelik.<br /><br /> <xref:System.Diagnostics.TraceFilter> Sınıftan devralması gereken filtrenin türünü belirtir. Türün <xref:System.Type.FullName%2A> özelliğine karşılık gelen, türün ad alanı nitelenmiş adını kullanabilirsiniz veya, <xref:System.Type.AssemblyQualifiedName%2A> özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam nitelikli tür adını kullanabilirsiniz. Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|İsteğe bağlı öznitelik.<br /><br /> Belirtilen filtre sınıfı için oluşturucuya geçirilen dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`trace`|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
|`listeners`|İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir. Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.|  
|`add`|`Listeners` Koleksiyona bir dinleyici ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, [yalnızca \<sharedListeners >](sharedlisteners-element.md)tanımlı `<add>` bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme dinleyicisi öğesi içinde bulunmalıdır. `<filter>` Dinleyici bir [ \<sharedListeners >](sharedlisteners-element.md)tanımlanmışsa, bu dinleyicinin filtresi o öğede tanımlanmalıdır.  
  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `<filter>` örnek, `console` izlemeiçin`Listeners` koleksiyondaki dinleyiciye filtre eklemek için öğesinin nasıl kullanılacağını gösterir. `Error`  
  
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
