---
title: <filter>İçin için <add> öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 2b83fd10da506202427aaeee454411822ff1ae5b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201687"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<filter>İçin için \<add> öğesi \<listeners>\<source>

İzleme kaynağı için koleksiyondaki bir dinleyiciye bir filtre ekler `Listeners` .  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a>Syntax  
  
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
|`type`|Gerekli öznitelik.<br /><br /> Sınıftan devralması gereken filtrenin türünü belirtir <xref:System.Diagnostics.TraceFilter> . Türün özelliğine karşılık gelen, türün ad alanı nitelenmiş adını kullanabilirsiniz <xref:System.Type.FullName%2A> veya, özelliğine karşılık gelen derleme bilgileri de dahil olmak üzere tam nitelikli tür adını kullanabilirsiniz <xref:System.Type.AssemblyQualifiedName%2A> . Tam nitelikli tür adları hakkında daha fazla bilgi için bkz. [tam nitelikli tür adlarını belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
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
|`add`|`Listeners`İzleme kaynağı için koleksiyona bir dinleyici ekler.|  
  
## <a name="remarks"></a>Açıklamalar  

 `<filter>`Öğesi, `<add>` yalnızca içinde tanımlanan bir dinleyicinin adı değil, dinleyicinin türünü belirten bir izleme kaynağı dinleyicisi için bir öğe içinde bulunmalıdır [\<sharedListeners>](sharedlisteners-element.md) . Dinleyici bir içinde tanımlanmışsa [\<sharedListeners>](sharedlisteners-element.md) , bu dinleyicinin filtresi o öğede tanımlanmalıdır.  
  
 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `<filter>` `console` `Listeners` izleme kaynağı için koleksiyondaki dinleyiciye bir filtre eklemek için öğesinin nasıl kullanılacağını gösterir `myTraceSource` `Error` .  
  
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
- [İzleme ve hata ayıklama ayarları şeması](index.md)
