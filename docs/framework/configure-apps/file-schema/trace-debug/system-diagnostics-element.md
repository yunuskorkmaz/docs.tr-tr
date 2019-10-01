---
title: < System. Diagnostics > öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699188"
---
# <a name="systemdiagnostics-element"></a>\<system. Diagnostics > öğesi
İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1 **\<system. diagnostics >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<onaylama >](assert-element.md)|@No__t-0 yöntemini çağırdığınızda bir ileti kutusunun görüntülenip görüntülenmeyeceğini belirtir; Ayrıca, iletilerin yazılacağı dosyanın adını da belirtir.|  
|[\<performanceCounters >](performancecounters-element.md)|Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.|  
|[\<sharedListeners >](sharedlisteners-element.md)|Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik dinleyicileri içerir. Paylaşılan dinleyiciler ada göre kaynaklara veya izlemelere eklenebilir olarak tanımlanan dinleyiciler.|  
|[\<kaynak >](sources-element.md)|İzleme iletilerini Başlatan izleme kaynaklarını belirtir.|  
|[\<anahtarlar >](switches-element.md)|İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyleri içerir.|  
|[\<trace >](trace-element.md)|İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir izleme anahtarı ve bir İzleme dinleyicisinin **\<System. diagnostics >** öğesinin içine nasıl ekleneceğini gösterir. @No__t-0 izleme anahtarı <xref:System.Diagnostics.TraceLevel> düzeyine ayarlanır. @No__t-0 adlı izleme dinleyicisi, `MyListener.log` adlı bir dosya oluşturur ve çıktıyı dosyaya yazar.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' de, bir anahtarın değerini belirtmek için metin kullanabilirsiniz. Örneğin, bir <xref:System.Diagnostics.BooleanSwitch> için `true` belirtebilir veya bir <xref:System.Diagnostics.TraceSwitch> için `Error` gibi bir sabit listesi değerini temsil eden metni kullanabilirsiniz. @No__t-0 satırı `<add name="myTraceSwitch" value="1" />` ' e eşdeğerdir.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
