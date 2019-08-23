---
title: <filter><add> İçin için<listeners> öğesi<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0d25d0b955a94986147922914068c8a1cf2d96c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920526"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<Kaynak > için \< \<dinleyicileriçin> eklemekiçin>öğesinifiltreleyin\<>
İzleme kaynağı için `Listeners` koleksiyondaki bir dinleyiciye bir filtre ekler.  
  
 \<Yapılandırma >  
\<System. Diagnostics >  
\<Kaynaklar >  
\<Kaynak >  
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
|`sources`|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
|`source`|İzleme iletilerini Başlatan bir izleme kaynağını belirtir.|  
|`listeners`|İletileri toplayacak, depolayan ve yönlendiren dinleyicileri içerir. Dinleyiciler izleme çıkışını uygun bir hedefe yönlendirir.|  
|`add`|İzleme kaynağı için `Listeners` koleksiyona bir dinleyici ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe, [yalnızca \<sharedListeners >](sharedlisteners-element.md)tanımlı `<add>` bir dinleyicinin adını değil, dinleyicinin türünü belirten bir izleme kaynağı dinleyicisi için bir öğe içinde bulunmalıdır. `<filter>` Dinleyici bir [ \<sharedListeners >](sharedlisteners-element.md)tanımlanmışsa, bu dinleyicinin filtresi o öğede tanımlanmalıdır.  
  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, izleme `<filter>` `Listeners` `console` kaynağı`myTraceSource`içinkoleksiyondaki dinleyiciye bir filtre eklemek için öğesinin nasıl kullanılacağını gösterir. `Error`  
  
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
